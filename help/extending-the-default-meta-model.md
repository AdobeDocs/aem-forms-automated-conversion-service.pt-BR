---
title: Ampliar o meta modelo padrão
seo-title: Ampliar o meta modelo padrão
description: Estenda o metrosmodelo padrão para adicionar padrões, validações e entidades específicas à sua organização e aplique configurações a campos de formulário adaptáveis enquanto executa o serviço de Conversão de formulários automatizados.
seo-description: Estenda o metrosmodelo padrão para adicionar padrões, validações e entidades específicas à sua organização e aplique configurações a campos de formulário adaptáveis enquanto executa o serviço de Conversão de formulários automatizados.
uuid: f98b4cca-f0a3-4db8-aef2-39b8ae462628
topic-tags: forms
discoiquuid: cad72699-4a4b-4c52-88a5-217298490a7c
translation-type: tm+mt
source-git-commit: ffab4d916cbd545078f4b72b8de5c9968f23b0da

---


# Ampliar o meta modelo padrão {#extend-the-default-meta-model}

O serviço de conversão de formulários automatizada identifica e extrai objetos de formulário de formulários de origem. O mapeador semântico ajuda o serviço a decidir como os objetos extraídos são representados em um formulário adaptável. Por exemplo, um formulário de origem pode ter muitos tipos diferentes de representações de uma data. O mapeador semântico ajuda a mapear todas as representações de objetos de formulário de data do formulário de origem com o componente de data dos formulários adaptáveis. O mapeador semântico também permite que o serviço pré-configure e aplique validações, regras, padrões de dados, texto da Ajuda e propriedades de acessibilidade a componentes de formulário adaptáveis durante a conversão.

![](assets/meta-model.gif)

O metrosmodelo é um schema JSON. Antes de start com meta-modelo, verifique se você está familiarizado com o JSON. Você deve ter experiência em criar, editar e ler dados salvos no formato JSON.

## Modelo meta padrão {#default-meta-model}

O serviço de Conversão de formulários automatizados tem um meta-modelo padrão. É um schema JSON e reside na Adobe Cloud com outros componentes do serviço de conversão de formulários automatizados. Você pode encontrar uma cópia do meta-modelo em seu servidor AEM local em:

http://&lt;servidor>:&lt;porta>/aem/forms.html/content/dam/formsanddocuments/metamodel/global.schema.json.

O schema de meta-modelo é derivado de entidades de schemas em https://schema.org/docs/schemas.html. Ele tem Pessoa, PostalAddress, LocalBusiness e mais entidades, conforme definido em https://schema.org. Cada entidade do metamodelo adere ao tipo de objeto de schema JSON. O código a seguir representa uma estrutura meta-modelo de amostra:

```
   "Entity": {
      "id": "Entity",
      "properties": {
        "name": {
          "type": "string"
        },

        "description": {
          "type": "string",
          "description": "Description of the item"
        }
      }
    }
```

## Baixar o modelo meta padrão {#download-the-default-meta-model}

Execute as seguintes etapas para baixar o meta-modelo padrão no sistema de arquivos local:

1. Faça logon na instância do AEM Forms.
1. Navegue até a pasta **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]** > **** **[!UICONTROL Meta Model]** .
1. Selecione o **[!UICONTROL global.schema.json]** arquivo e toque em **[!UICONTROL Download]**. Uma caixa de diálogo de download é exibida. Selecione a **[!UICONTROL Download asset(s) as binary files]** opção. Tocar **[!UICONTROL Download]**. Um arquivo é baixado.

   <!--
   Comment Type: draft

   <li><p>Extract the archive and open the global.schema.json file for editing. </p> </li>
   -->

   <!--
   Comment Type: draft

   <li>Step text</li>
   -->

## Noções básicas sobre o meta-modelo {#understanding-the-meta-model}

Um modelo meta se refere a um arquivo de schema JSON que contém entidades. Todas as entidades no arquivo de schema JSON incluem um nome e uma id. Cada entidade pode incluir várias propriedades. As entidades e suas propriedades podem variar com base no domínio. É possível aumentar um arquivo de schema com palavras-chave e configurações de campo para mapear as propriedades do schema para os componentes de formulário adaptáveis.

```
"Event": {
      "id": "Eventid",
      "allOf": [
        {
          "$ref": "#Entity"
        },
        {
          "properties": {
            "startDate": {
              "type": "string",
              "format": "date",
              "description": "Specify the start date and time of the event in ISO 8601 date format."
            },
            "endDate": {
              "type": "string",
              "format": "date",
              "description": "Specify the end date and time of the event in ISO 8601 date format."
            },
            "location": {
              "$ref": "#PostalAddress",
              "description": "Specify the location of the event."
            }
          }
        }
      ]
    }
```

Neste exemplo, o **Evento** representa o nome de uma entidade com um valor para **id** como **Eventid**. A entidade Evento inclui várias propriedades:

* startDate
* endDate
* localização

A construção **allOf** no metamodelo permite a herança entre as entidades.

Cada propriedade pode ainda incluir:

* [Propriedades do schema JSON](#jsonschemaproperties)
* [Pesquisa baseada em palavras-chave para aplicar propriedades aos campos de formulário adaptativo gerados](#keywordsearch)
* [Propriedades adicionais](#additionalproperties)

![Propriedades de modelo Meta](assets/meta_model_elements.gif)

Com base nas palavras-chave referenciadas usando **aem:affKeyword**, o serviço de conversão executa uma operação de pesquisa nos campos de formulário de origem. O serviço de conversão aplica as propriedades do schema JSON e propriedades adicionais aos campos que atendem aos critérios de pesquisa.

Neste exemplo, o serviço de conversão pesquisa palavras-chave telefone, telefone, telefone celular, telefone de trabalho, telefone residencial, número de telefone, número de telefone e número de telefone no formulário de origem. Com base nos campos que incluem essas palavras-chave, o serviço de conversão aplica o tipo, o padrão e aem:afProperties aos campos de formulário adaptáveis após a conversão.

### Propriedades do schema JSON para campos de formulário adaptável gerados {#jsonschemaproperties}

O modelo meta suporta as seguintes propriedades comuns do schema JSON para campos de formulário adaptáveis gerados usando o serviço de Conversão de formulários automatizados:

<table> 
 <tbody> 
  <tr> 
   <th><strong>Nome da Propriedade</strong></th> 
   <th><strong>Descrição</strong></th> 
  </tr> 
  <tr> 
   <td><p>título</p></td> 
   <td> 
    <p>O texto mencionado na propriedade title em um meta-modelo serve como uma palavra-chave de pesquisa para executar ações nos campos de formulário adaptável gerados. Por exemplo, modificar o rótulo de um campo de formulário adaptável. Para obter mais informações, consulte <strong>Modificar o rótulo de um campo</strong> de formulário em exemplos <a href="#custommetamodelexamples">personalizados de meta-modelo.</a></p> </td> 
  </tr>
  <td><p>descrição</p></td> 
   <td> 
    <p>A propriedade description define o texto da Ajuda para o campo de formulário adaptativo gerado. Para obter mais informações, consulte <strong>Adicionar texto da Ajuda a um campo</strong> de formulário em exemplos de metammodelo <a href="#custommetamodelexamples">personalizado.</a></p> </td> 
  </tr>
  <td><p>tipo</p></td> 
   <td> 
    <p>A propriedade type define o tipo de dados para o campo de formulário adaptativo gerado. Os possíveis valores para a propriedade title incluem:</p>
    <ul> 
     <li>string: Gera um campo de formulário adaptável do tipo de dados de texto.</li> 
     <li>número: Gera um campo de formulário adaptável de tipo de dados numéricos.</li>
     <li>integer: Gera um campo de formulário adaptável de tipo de dados numéricos com subtipo definido como inteiro.</li>
     <li>booleano: Gera um componente de formulário adaptável de switch.</li>
     </ul><p>Para obter mais informações sobre como usar a propriedade type em um metrosmodelo, consulte <strong>Modificar o tipo de um campo</strong> de formulário em exemplos de meta-modelo <a href="#custommetamodelexamples">personalizado.</a></p></td> 
  </tr>
  <td><p>pattern</p></td> 
   <td> 
    <p>A propriedade pattern restringe o valor do campo de formulário adaptativo gerado com base em uma expressão regular. Por exemplo, o código a seguir no modelo meta restringe o valor do campo de formulário adaptativo gerado a dez dígitos:<br>"padrão": "/\\d{10}/"<br>Da mesma forma, o código a seguir no modelo de meta restringe o valor de um campo a um formato de data específico.<br> "padrão": "date{DD MMMM, AAAA}",</p> </td> 
  </tr>
  <td><p>format</p></td> 
   <td> 
    <p>A propriedade format restringe o valor do campo de formulário adaptativo gerado com base em um padrão nomeado em vez de uma expressão regular. Os valores possíveis para a propriedade format incluem:<ul><li>email: Gera um componente de formulário adaptável por email.</li><li>nome do host: Gera um componente de formulário adaptável de caixa de texto.</li></ul>Para obter mais informações sobre como usar a propriedade format em um modelo de meta, consulte <strong>Modificar o formato de um campo</strong> de formulário em exemplos de modelo de meta <a href="#custommetamodelexamples">personalizado.</a></p> </td> 
  </tr>
  <td><p>enum e enumNames</p></td> 
   <td> 
    <p>As propriedades enum e enumNames restringem os valores dos campos suspensos, da caixa de seleção ou de botões de opção a um conjunto fixo. Os valores listados em enumNames são exibidos na interface do usuário. Os valores listados usando a propriedade enum são usados para o cálculo.<br>Para obter mais informações, consulte <strong>Converter um campo de formulário em caixas de seleção de múltipla escolha no formulário</strong>adaptável, <strong>Converter um campo de texto em lista suspensa no formulário</strong>adaptável e <strong>Adicionar opções adicionais à lista</strong> suspensa em exemplos de metmodelo <a href="#custommetamodelexamples">personalizado.</a></p> </td> 
  </tr>
 </tbody> 
</table>

### Pesquisa baseada em palavras-chave para aplicar propriedades aos campos de formulário adaptativo gerados {#keywordsearch}

O serviço de Conversão de formulários automatizados realiza uma pesquisa por palavra-chave no formulário de origem durante a conversão. Depois de filtrar os campos que atendem aos critérios de pesquisa, o serviço de conversão aplica as propriedades definidas para esses campos no modelo de meta aos campos de formulário adaptativo gerados.

As palavras-chave são referenciadas usando a propriedade **aem:affKeyword** .

```
{
  "numberfields": {
      "type": "number",
      "aem:affKeyword": ["Bank account number"]
 }
}
```

Neste exemplo, o serviço de conversão usa o texto em **aem:affKeyword** como uma palavra-chave de pesquisa. Após recuperar o texto do número **da conta** bancária no formulário, o serviço de conversão converte o campo em um tipo de **número** usando a propriedade **type** .

### Propriedades adicionais para campos de formulário adaptável gerados {#additionalproperties}

Você pode usar a propriedade **aem:afProperties** no metrosmodelo para definir as seguintes propriedades adicionais para campos de formulários adaptáveis gerados usando o serviço de Conversão de formulários automatizados:

<table> 
 <tbody> 
  <tr> 
   <th><strong>Nome da Propriedade</strong></th> 
   <th><strong>Descrição</strong></th> 
  </tr> 
  <tr> 
   <td><p>multiLine</p></td> 
   <td> 
    <p>A propriedade multiLine converte um campo de formulário de origem em um campo de várias linhas no formulário adaptável após a conversão. Para obter mais informações, consulte <strong>Converter um campo de string em um campo</strong> de várias linhas em exemplos <a href="#custommetamodelexamples">personalizados de meta-modelo.</a></p> </td> 
  </tr>
  <td><p>mandatory</p></td> 
   <td> 
    <p>A propriedade mandatory define a entrada de um campo de formulário adaptável após a conversão como obrigatório.<br>Para obter mais informações, consulte <strong>Adicionar validações a campos</strong> de formulário adaptáveis em exemplos <a href="#custommetamodelexamples">personalizados de metmodelo.</a></p>
    </td> 
  </tr>
  <td><p>jcr:title</p></td> 
   <td> 
    <p>A propriedade jcr:title, com o título propriedade schema JSON, permite modificar o rótulo de um campo de formulário adaptável após a conversão.<br>Para obter mais informações, consulte <strong>Modificar o rótulo de um campo</strong> de formulário em exemplos <a href="#custommetamodelexamples">personalizados de meta-modelo.</a><br>Consulte <a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/adaptive-form-json-schema-form-model.html" target="_blank">Criação de formulários adaptáveis usando o schema</a> JSON para obter informações sobre mais propriedades que podem ser aplicadas a campos de formulário adaptáveis usando o schema JSON.</p>
    <p></p></td> 
  </tr>
  <td><p>sling:resourceType e guideNodeClass</p></td> 
   <td> 
    <p>as propriedades sling:resourceType e guideNodeClass permitem mapear um campo de formulário para um componente de formulário adaptável correspondente.<br>Para obter mais informações, consulte <strong>Converter um campo de formulário em caixas de seleção de múltipla escolha no formulário</strong> adaptável e <strong>Converter um campo de texto em lista suspensa no formulário</strong> adaptável em exemplos de metmodelo <a href="#custommetamodelexamples">personalizado.</a></p> </td> 
  </tr>
  <td><p>validatePictureClause</p></td> 
   <td> 
    <p>A propriedade validatePictureClause define uma validação no formato permitido no campo de formulário adaptável após a conversão.<br>Para obter mais informações, consulte <strong>Adicionar validações a campos</strong> de formulário adaptáveis em exemplos <a href="#custommetamodelexamples">personalizados de metmodelo.</p> </td> 
  </tr>
 </tbody> 
</table>

## Modificar campos de formulário adaptáveis usando metammodelo personalizado {#modify-adaptive-form-fields-using-custom-meta-model}

Sua organização pode ter padrões e validações além daqueles listados no metmodelo padrão. Você pode estender o meta-modelo padrão para adicionar padrões, validações e entidades específicas à sua organização. O serviço de Conversão de formulários automatizados aplica o meta-modelo personalizado aos campos de formulário durante a conversão. Você pode continuar atualizando o meta-modelo à medida que novos padrões, validações e entidades específicas à sua organização forem descobertos.

O serviço de Conversão de formulários automatizados usa um meta-modelo padrão salvo no seguinte local para mapear os campos do formulário de origem para os campos do formulário adaptável durante a conversão:

http://&lt;servidor>:&lt;porta>/aem/forms.html/content/dam/formsanddocuments/metamodel/global.schema.json

No entanto, você pode salvar um meta-modelo personalizado em uma pasta e modificar as propriedades do serviço de conversão para usar o meta-modelo personalizado durante a conversão.

### Usar meta-modelo personalizado durante a conversão {#use-custom-meta-model-during-conversion}

Execute as seguintes etapas para usar um meta-modelo personalizado durante a conversão:

1. Crie uma pasta em **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]** e carregue o arquivo de schema JSON meta-model personalizado para a pasta.
1. Abra as propriedades do serviço de conversão usando:

   **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Automated Forms Conversion Configuration]**> **&lt;** Propriedades da configuração **selecionada>**

1. Na **[!UICONTROL Basic]** guia, especifique o local do meta-modelo personalizado no **[!UICONTROL Custom Meta-model]** campo e toque em **[!UICONTROL Save & Close]**.
1. [Execute a conversão](convert-existing-forms-to-adaptive-forms.md#start-the-conversion-process) para aplicar o meta-modelo personalizado ao processo de conversão.

### Exemplos personalizados de meta-modelo {#custommetamodelexamples}

Alguns exemplos comuns de uso de um metrosmodelo personalizado para modificar propriedades adaptáveis de campos de formulário incluem:

* Modificar o rótulo de um campo de formulário
* Modificar o tipo de um campo de formulário
* Adicionar texto de Ajuda a um campo de formulário
* Converter um campo de formulário em botões de opção de múltipla escolha no formulário adaptável
* Modificar o formato de um campo de formulário
* Adicionar validações a campos de formulário adaptáveis
* Converter um campo de formulário em opções de lista suspensas no formulário adaptável
* Adicionar opções adicionais à lista suspensa
* Converter um campo de string em um campo de várias linhas

#### Modificar o rótulo de um campo de formulário {#modify-the-label-of-a-form-field}

**Exemplo:** Modifique o rótulo do número de conta bancária no formulário para Número de conta personalizado no formulário adaptável após a conversão.

Neste meta-modelo personalizado, o serviço de conversão usa a propriedade **title** como uma palavra-chave de pesquisa. Após recuperar o texto do número **da conta** bancária no formulário, o serviço de conversão substitui o texto pela string do número **da conta do** Cliente mencionada pela propriedade **jcr:title** na seção **aem:afProperties** .

```
{
  "numberfields": {
      "type": "number",
   "title": "Bank account number",
   "aem:afProperties" : {
    "jcr:title" : "Customer account number"
   }
   }
}
```

#### Modificar o tipo de um campo de formulário {#modify-the-type-of-a-form-field}

**Exemplo**: Modifique o campo Número **da conta** bancária do tipo de texto no formulário antes da conversão para um campo de tipo de número no formulário adaptável após a conversão.

Neste meta-modelo personalizado, o serviço de conversão usa o texto em **aem:affKeyword** como uma palavra-chave de pesquisa. Após recuperar o texto do número **da conta** bancária no formulário, o serviço de conversão converte o campo em um tipo de número usando a propriedade **type** .

```
{
  "numberfields": {
      "type": "number",
      "aem:affKeyword": ["Bank account number"]
 }
}
```

#### Adicionar texto de Ajuda a um campo de formulário {#add-help-text-to-a-form-field}

**Exemplo**: Adicione o texto Ajuda ao campo Número **da conta** bancária do formulário adaptável.

Neste meta-modelo personalizado, o serviço de conversão usa o texto em **aem:affKeyword** como uma palavra-chave de pesquisa. Após recuperar o texto do número **da conta** bancária no formulário, o serviço de conversão adiciona o texto Ajuda ao campo de formulário adaptável usando a propriedade **description** .

```
{
  "numberfields": {
      "type": "number",
      "aem:affKeyword": ["Bank account number"],
   "description": "Specify your bank account number."
 }
}
```

#### Converter um campo de formulário em caixas de seleção de múltipla escolha no formulário adaptável {#convert-a-form-field-to-multiple-choice-check-boxes-in-the-adaptive-form}

**Exemplo**: Converta o campo **País** do tipo de string no formulário antes da conversão em caixas de seleção no formulário adaptável após a conversão.

Neste meta-modelo personalizado, o serviço de conversão usa texto em **aem:affKeyword** como uma palavra-chave de pesquisa. Após recuperar o texto do **País** no formulário, o serviço de conversão converte o campo nas seguintes caixas de seleção usando a propriedade **enum** :

* Índia
* Inglaterra
* Austrália
* Nova Zelândia

**sling:resourceType** e **guideNodeClass** as propriedades mapeiam um campo de formulário para o componente de formulário adaptável da caixa de seleção.

```
{
"title": {
    "aem:affKeyword": [
      "country"
    ],
    "type" : "string",
    "enum": [
      "India",
      "England",
      "Australia",
      "New Zealand"
    ],
    "aem:afProperties": {
      "sling:resourceType": "fd/af/components/guidecheckbox",
      "guideNodeClass": "guidecheckbox"
    }
  }
}
```

#### Modificar o formato de um campo de formulário {#modify-the-format-of-a-form-field}

**Exemplo**: Modifique o formato do campo Endereço **de** email para um formato do email.

Neste meta-modelo personalizado, o serviço de conversão usa texto em **aem:affKeyword** como uma palavra-chave de pesquisa. Após recuperar o texto Endereço **de** email no formulário, o serviço de conversão converte o campo em um formato do email usando a propriedade **format** .

```
{
   "additionalDetails" : {
      "aem:affKeyword": ["E-mail Address"],
       "type" : "string",
       "format" : "email"
  } 
}
```

#### Adicionar validações a campos de formulário adaptáveis {#add-validations-to-adaptive-form-fields}

**Exemplo 1:** Adicione uma validação ao campo Código **** postal do formulário adaptável.

Neste meta-modelo personalizado, o serviço de conversão usa texto em **aem:affKeyword** como palavra-chave de pesquisa. Após recuperar o texto do Código **** postal no formulário, o serviço de conversão adiciona uma validação ao campo usando a propriedade **validatePictureClause** definida na seção **aem:afProperties** . Com base na validação, a entrada especificada para o campo Código **** postal no formulário adaptável após a conversão deve incluir seis caracteres.

```
{
   "postalCode" : {
      "aem:affKeyword": ["Postal Code"],
      "type" : "string",
      "aem:afProperties" : {
        "validatePictureClause" : "\\d{6}"
      } 
   }
}
```

**Exemplo 2:** Adicione uma validação ao campo Número **da conta** bancária do formulário adaptável.

Neste meta-modelo personalizado, o serviço de conversão usa texto em **aem:affKeyword** como palavra-chave de pesquisa. Após recuperar o texto do número **da conta** bancária no formulário, o serviço de conversão adiciona uma validação ao campo usando a propriedade **obrigatória** definida na seção **aem:afProperties** . Com base na validação, você deve especificar um valor para o campo de número **de conta** bancária antes de enviar o formulário após a conversão.

```
{
  "numberfields": {
      "type": "number",
      "aem:affKeyword": ["Bank account number"],
   "aem:afProperties" : {
        "mandatory": "true"
      }   
   }
}
```

#### Converter um campo de texto em lista suspensa no formulário adaptável {#convert-a-text-field-to-drop-down-list-in-the-adaptive-form}

**Exemplo**: Converta o campo **País** do tipo de string no formulário antes da conversão em opções suspensas no formulário adaptável após a conversão.

Neste meta-modelo personalizado, o serviço de conversão usa texto em **aem:affKeyword** como palavra-chave de pesquisa. Após recuperar o texto do **País** no formulário, o serviço de conversão converte o campo nas seguintes opções de lista suspensa usando a propriedade **enum** :

* Índia
* Inglaterra
* Austrália
* Nova Zelândia

**sling:resourceType** e **guideNodeClass** as propriedades mapeiam um campo de formulário para o componente de formulário adaptável suspenso.

```
{
"title": {
    "aem:affKeyword": [
      "country"
    ],
    "type" : "string",
    "enum": [
      "India",
      "England",
      "Australia",
      "New Zealand"
    ],
    "aem:afProperties": {
      "sling:resourceType": "fd/af/components/guidedropdownlist",
      "guideNodeClass": "guideDropDownlist"
    }
  }
}
```

#### Adicionar opções adicionais à lista suspensa {#add-additional-options-to-the-drop-down-list}

**Exemplo:** Adicione o **Sri Lanka** como uma opção extra a uma lista suspensa existente usando um meta-modelo personalizado.

Para adicionar uma opção extra, atualize a propriedade **enum** com a nova opção. Neste exemplo, atualize a propriedade **enum** com o **Sri Lanka** como uma opção extra. Os valores listados na propriedade **enum** são exibidos na lista suspensa.

```
{
"title": {
    "aem:affKeyword": [
      "country"
    ],
    "type" : "string",
    "enum": [
      "India",
      "England",
      "Australia",
      "New Zealand",
   "Sri Lanka"
    ],
    "aem:afProperties": {
      "sling:resourceType": "fd/af/components/guidecheckbox",
      "guideNodeClass": "guidecheckbox"
    }
  }
}
```

#### Converter um campo de string em um campo de várias linhas {#convert-a-string-field-to-a-multi-line-field}

**Exemplo:** Converta o campo **Endereço** do tipo de string em um campo de várias linhas no formulário após a conversão.

Neste meta-modelo personalizado, o serviço de conversão usa texto em **aem:affKeyword** como palavra-chave de pesquisa. Após recuperar o texto **Endereço** no formulário, o serviço converte o campo de texto em um campo de várias linhas usando a propriedade **multiLine** definida na seção **aem:afProperties** .

```
{
 "multiLine" : {
   "aem:affKeyword": [
      "Address"
    ],
    "type" : "string",
    "aem:afProperties": {
      "multiLine": "true"
    }
  }
}
```
