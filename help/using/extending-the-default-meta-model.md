---
title: Estender o metamodelo padrão
description: Estenda o metamodelo padrão para adicionar padrões, validações e entidades específicos à sua organização e aplicar configurações a campos de formulário adaptáveis ao executar o serviço do Automated forms conversion (AFCS).
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Administration
topic-tags: forms
role: Admin, Developer
level: Beginner, Intermediate
exl-id: f679059c-18aa-4cb5-8368-ed27e96c20de
source-git-commit: c2392932d1e29876f7a11bd856e770b8f7ce3181
workflow-type: tm+mt
source-wordcount: '2569'
ht-degree: 1%

---

# Estender o metamodelo padrão {#extend-the-default-meta-model}

O serviço de automated forms conversion (AFCS) identifica e extrai objetos de formulário de formulários de origem. O Mapeador semântico ajuda o serviço a decidir como os objetos extraídos são representados em um formulário adaptável. Por exemplo, um formulário de origem pode ter vários tipos diferentes de representações de uma data. O mapeador semântico ajuda a mapear todas as representações de objetos de formulário de data do formulário de origem com o componente de data dos formulários adaptáveis. O mapeador semântico também permite que o serviço pré-configure e aplique validações, regras, padrões de dados, texto de ajuda e propriedades de acessibilidade aos componentes de formulário adaptáveis durante a conversão.

![](assets/meta-model.gif)

O modelo meta é um esquema JSON. Antes de começar com o metamodelo, verifique se você está familiarizado com JSON. Você deve ter experiência em criação, edição e leitura de dados salvos no formato JSON.

## Metamodelo padrão {#default-meta-model}

O serviço do Automated forms conversion (AFCS) tem um metamodelo padrão. É um esquema JSON e reside na Adobe Cloud com outros componentes do serviço do Automated forms conversion (AFCS). Você pode encontrar uma cópia do meta modelo em seu servidor AEM local em: http://&lt;server>:&lt;port>/aem/forms.html/content/dam/formsanddocuments/metamodel/`global.schema.json`. Também é possível [clique aqui](assets/en.globalschema.json) para acessar ou baixar o esquema de idioma inglês. O metamodelo para [Francês](assets/fr.globalschema.json), [Alemão](assets/de.globalschema.json) [Espanhol](assets/es.globalschema.json), [Italiano](assets/it.globalschema.json), e [Português](assets/pt_br.globalschema.json) Os idiomas também estão disponíveis para download.

O esquema do modelo meta é derivado de entidades de esquema em https://schema.org/docs/schemas.html. Ele tem Pessoa, PostalAddress, LocalBusiness e mais entidades, conforme definido em https://schema.org. Cada entidade do metamodelo adere ao tipo de objeto de esquema JSON. O código a seguir representa um exemplo de estrutura de metamodelo:

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

## Baixar o metamodelo padrão {#download-the-default-meta-model}

Execute as seguintes etapas para baixar o metamodelo padrão no sistema de arquivos local:

1. Faça logon na sua instância do AEM Forms.
1. Navegue até a **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]** **>** **[!UICONTROL Meta Model]** pasta.
1. Selecione o **[!UICONTROL global.schema.json]** arquivo e toque em **[!UICONTROL Download]**. Uma caixa de diálogo de download é exibida. Selecione o **[!UICONTROL Download asset(s) as binary files]** opção. Toque **[!UICONTROL Download]**. Um arquivo é baixado.

   <!--
   Comment Type: draft

   <li><p>Extract the archive and open the global.schema.json file for editing. </p> </li>
   -->

   <!--
   Comment Type: draft

   <li>Step text</li>
   -->

## Noções básicas sobre o metamodelo {#understanding-the-meta-model}

Um metamodelo refere-se a um arquivo de esquema JSON que contém entidades. Todas as entidades no arquivo de esquema JSON incluem um nome e uma id. Cada entidade pode incluir várias propriedades. As entidades e suas propriedades podem variar com base no domínio. Você pode aumentar um arquivo de esquema com palavras-chave e configurações de campo para mapear propriedades de esquema para componentes de formulário adaptáveis.

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

Neste exemplo, **Evento** representa o nome de uma entidade com um valor para **id** as **Eventid**. A entidade Evento inclui várias propriedades:

* startDate
* endDate
* localização

A variável **allOf** a construção no metamodelo permite a herança entre entidades.

Cada propriedade pode incluir ainda:

* [Propriedades do esquema JSON](#jsonschemaproperties)
* [Pesquisa baseada em palavra-chave para aplicar propriedades a campos de formulário adaptáveis gerados](#keywordsearch)
* [Propriedades adicionais](#additionalproperties)

![Propriedades do modelo meta](assets/meta_model_elements.gif)

Com base nas palavras-chave referenciadas usando **aem:affKeyword**, o serviço de conversão executa uma operação de pesquisa nos campos de formulário de origem. O serviço de conversão aplica as propriedades do esquema JSON e as propriedades adicionais aos campos que atendem aos critérios de pesquisa.

Neste exemplo, o serviço de conversão procura palavras-chave de telefone, telefone, celular, telefone comercial, telefone residencial, número de telefone, número de telefone e número de telefone no formulário de origem. Com base nos campos que incluem essas palavras-chave, o serviço de conversão aplica o tipo, o padrão e aem:afProperties aos campos de formulário adaptáveis após a conversão.

### Propriedades do esquema JSON para campos de formulário adaptável gerados {#jsonschemaproperties}

O metamodelo é compatível com as seguintes propriedades comuns do esquema JSON para campos de formulário adaptáveis gerados usando o serviço do Automated forms conversion (AFCS):

<table> 
 <tbody> 
  <tr> 
   <th><strong>Nome de propriedade</strong></th> 
   <th><strong>Descrição</strong></th> 
  </tr> 
  <tr> 
   <td><p>cargo</p></td> 
   <td> 
    <p>O texto mencionado na propriedade title em um metamodelo serve como uma palavra-chave de pesquisa para executar ações nos campos de formulário adaptáveis gerados. Por exemplo, modificar o rótulo de um campo de formulário adaptável. Para obter mais informações, consulte <strong>Modificar o rótulo de um campo de formulário</strong> in <a href="#custommetamodelexamples">Exemplos de metamodelo personalizado.</a></p> </td> 
  </tr>
  <td><p>descrição</p></td> 
   <td> 
    <p>A propriedade description define o texto de Ajuda para o campo de formulário adaptável gerado. Para obter mais informações, consulte <strong>Adicionar texto de ajuda a um campo de formulário</strong> in <a href="#custommetamodelexamples">Exemplos de metamodelo personalizado.</a></p> </td> 
  </tr>
  <td><p>tipo</p></td> 
   <td> 
    <p>A propriedade type define o tipo de dados do campo de formulário adaptável gerado. Os valores possíveis para a propriedade title incluem:</p>
    <ul> 
     <li>string: gera um campo de formulário adaptável do tipo de dados text.</li> 
     <li>number: gera um campo de formulário adaptável do tipo de dados numérico.</li>
     <li>inteiro: gera um campo de formulário adaptável do tipo de dados numérico com o subtipo definido como inteiro.</li>
     <li>booleano: gera um componente de formulário adaptável de comutador.</li>
     </ul><p>Para obter mais informações sobre o uso da propriedade type em um metamodelo, consulte <strong>Modificar o tipo de um campo de formulário</strong> in <a href="#custommetamodelexamples">Exemplos de metamodelo personalizado.</a></p></td> 
  </tr>
  <td><p>padrão</p></td> 
   <td> 
    <p>A propriedade pattern restringe o valor do campo de formulário adaptável gerado com base em uma expressão regular. Por exemplo, o código a seguir no metamodelo restringe o valor do campo de formulário adaptável gerado para dez dígitos:<br>"pattern": "/\\d{10}/"<br>Da mesma forma, o código a seguir no metamodelo restringe o valor de um campo a um formato de data específico.<br> "pattern": "date{DD MMMM, YYYY}",</p> </td> 
  </tr>
  <td><p>formato</p></td> 
   <td> 
    <p>A propriedade format restringe o valor do campo de formulário adaptável gerado com base em um padrão nomeado em vez de uma expressão regular. Os valores possíveis para a propriedade de formato incluem:<ul><li>email: gera um componente de formulário adaptável de email.</li><li>nome do host: gera um componente de formulário adaptável caixa de texto.</li></ul>Para obter mais informações sobre o uso da propriedade format em um metamodelo, consulte <strong>Modificar o formato de um campo de formulário</strong> in <a href="#custommetamodelexamples">Exemplos de metamodelo personalizado.</a></p> </td> 
  </tr>
  <td><p>enum e enumNames</p></td> 
   <td> 
    <p>As propriedades enum e enumNames restringem os valores dos campos de botão de opção, caixa de seleção ou lista suspensa a um conjunto fixo. Os valores listados em enumNames são exibidos na interface do usuário. Os valores listados usando a propriedade enum são usados para cálculo.<br>Para obter mais informações, consulte <strong>Converter um campo de formulário em caixas de seleção de múltipla escolha no formulário adaptável</strong>, <strong>Converter um campo de texto em lista suspensa no formulário adaptável</strong>, e <strong>Adicionar mais opções à lista suspensa</strong> in <a href="#custommetamodelexamples">Exemplos de metamodelo personalizado.</a></p> </td> 
  </tr>
 </tbody> 
</table>

### Pesquisa baseada em palavra-chave para aplicar propriedades a campos de formulário adaptáveis gerados {#keywordsearch}

O serviço Automated forms conversion (AFCS) executa uma pesquisa por palavra-chave no formulário de origem durante a conversão. Depois de filtrar os campos que atendem aos critérios de pesquisa, o serviço de conversão aplica as propriedades definidas para esses campos no metamodelo aos campos de formulário adaptáveis gerados.

As palavras-chave são referenciadas usando o **aem:affKeyword** propriedade.

```
{
  "numberfields": {
      "type": "number",
      "aem:affKeyword": ["Bank account number"]
 }
}
```

Neste exemplo, o serviço de conversão usa o texto dentro de **aem:affKeyword** como uma palavra-chave de pesquisa. Depois de recuperar o **Número da conta bancária** texto no formulário, o serviço de conversão converte o campo em uma **número** digite usando o **type** propriedade.

### Propriedades adicionais para campos de formulário adaptável gerados {#additionalproperties}

Você pode usar o **aem:afProperties** no modelo meta para definir as seguintes propriedades adicionais para campos de formulários adaptáveis gerados usando o serviço do Automated forms conversion (AFCS):

<table> 
 <tbody> 
  <tr> 
   <th><strong>Nome de propriedade</strong></th> 
   <th><strong>Descrição</strong></th> 
  </tr> 
  <tr> 
   <td><p>multiLine</p></td> 
   <td> 
    <p>A propriedade multiLine converte um campo de formulário de origem em um campo de várias linhas no formulário adaptável após a conversão. Para obter mais informações, consulte <strong>Converter um campo de sequência em um campo de várias linhas</strong> in <a href="#custommetamodelexamples">Exemplos de metamodelo personalizado.</a></p> </td> 
  </tr>
  <td><p>obrigatório</p></td> 
   <td> 
    <p>A propriedade mandatory define a entrada de um campo de formulário adaptável após a conversão como obrigatória.<br>Para obter mais informações, consulte <strong>Adicionar validações a campos de formulário adaptáveis</strong> in <a href="#custommetamodelexamples">Exemplos de metamodelo personalizado.</a></p>
    </td> 
  </tr>
  <td><p>jcr:title</p></td> 
   <td> 
    <p>A propriedade jcr:title, com a propriedade de esquema JSON title, permite modificar o rótulo de um campo de formulário adaptável após a conversão.<br>Para obter mais informações, consulte <strong>Modificar o rótulo de um campo de formulário</strong> in <a href="#custommetamodelexamples">Exemplos de metamodelo personalizado.</a><br>Consulte <a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/adaptive-form-json-schema-form-model.html" target="_blank">Criação de formulários adaptáveis usando o esquema JSON</a> para obter informações sobre mais propriedades que podem ser aplicadas aos campos de formulário adaptáveis usando o esquema JSON.</p>
    <p></p></td> 
  </tr>
  <td><p>sling:resourceType e guideNodeClass</p></td> 
   <td> 
    <p>as propriedades sling:resourceType e guideNodeClass permitem mapear um campo de formulário para um componente de formulário adaptável correspondente.<br>Para obter mais informações, consulte <strong>Converter um campo de formulário em caixas de seleção de múltipla escolha no formulário adaptável</strong> e <strong>Converter um campo de texto em lista suspensa no formulário adaptável</strong> in <a href="#custommetamodelexamples">Exemplos de metamodelo personalizado.</a></p> </td> 
  </tr>
  <td><p>validatePictureClause</p></td> 
   <td> 
    <p>A propriedade validatePictureClause define uma validação no formato permitido no campo de formulário adaptável após a conversão.<br>Para obter mais informações, consulte <strong>Adicionar validações a campos de formulário adaptáveis</strong> in <a href="#custommetamodelexamples">Exemplos de metamodelo personalizado.</p> </td> 
  </tr>
 </tbody> 
</table>

## Criar um modelo personalizado no seu próprio idioma{#language-specific-meta-model}

Você pode criar um metamodelo específico de idioma. Esse metamodelo ajuda a criar regras de mapeamento no idioma de sua escolha. O serviço Automated forms conversion (AFCS) permite criar metamodelos nos seguintes idiomas:

* Inglês (EN)
* Francês (França)
* Alemão (Alemanha)
* Espanhol (Espanha)
* Italiano (Itália)
* Português (pt-br)

Adicione o *aem:Idioma* metatag à parte superior um metamodelo para especificar seu idioma. Por exemplo,

```JSON
"metaTags": {
        "aem:Language": "fr"
    }
```

Quando nenhum idioma é especificado, o serviço considera que o metamodelo está em inglês.

### Considerações para a criação de um metamodelo específico de idioma

* Verifique se o nome de cada chave está no idioma inglês. Por exemplo, emailAddress.
* Garantir que todas as referências de entidade e os valores predefinidos de toda a chave de id incluam apenas caracteres ASCII. Por exemplo &quot;id&quot;: &quot;ContactPoint&quot; / &quot;$ref&quot;: &quot;#ContactPoint&quot;.
* Verifique se todos os valores correspondentes às seguintes chaves estão no idioma do metamodelo especificado:
   * aem:affKeyword
   * cargo
   * descrição
   * enumName
   * shortDescription
   * validatePictureClauseMessage

  Por exemplo, quando o idioma do metamodelo for francês (&quot;aem:Language&quot;: &quot;fr&quot;), verifique se todas as descrições e mensagens estão em francês.

* Assegurar todos [Propriedades do esquema JSON](#jsonschemaproperties) usar somente valores compatíveis. Por exemplo, a propriedade de tipo só pode abranger valores selecionados de String, Número, Inteiro e Booleano.

A imagem a seguir exibe exemplos de metamodelo de idioma inglês e do metamodelo de idioma francês correspondente:

![](assets/language-specific-meta-model-comparison.png)

## Modificar campos de formulário adaptáveis usando o metamodelo personalizado {#modify-adaptive-form-fields-using-custom-meta-model}

Sua organização pode ter padrões e validações, além daqueles listados no metamodelo padrão. É possível estender o metamodelo padrão para adicionar padrões, validações e entidades específicas à sua organização. O serviço do Automated forms conversion (AFCS) aplica o metamodelo personalizado aos campos de formulário durante a conversão. É possível continuar atualizando o metamodelo à medida que novos padrões, validações e entidades específicos da sua organização são descobertos.

O serviço do Automated forms conversion (AFCS) usa um metamodelo padrão salvo no seguinte local para mapear campos de formulário de origem para os campos de formulário adaptáveis durante a conversão:

http://&lt;server>:&lt;port>/aem/forms.html/content/dam/formsanddocuments/metamodel/global.schema.json

No entanto, você pode salvar um metamodelo personalizado em uma pasta e modificar as propriedades do serviço de conversão para usar o metamodelo personalizado durante a conversão.

### Usar meta modelo personalizado durante a conversão {#use-custom-meta-model-during-conversion}

Execute as seguintes etapas para usar um metamodelo personalizado durante a conversão:

1. Criar uma pasta no **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]** e faça upload do arquivo de esquema JSON do metamodelo personalizado para a pasta.
1. Abra as propriedades do serviço de conversão usando:

   **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Automated Forms Conversion Configuration]** > **&lt;properties of=&quot;&quot; selected=&quot;&quot; configuration=&quot;&quot;>**

1. No **[!UICONTROL Basic]** especifique o local do metamodelo personalizado na guia **[!UICONTROL Custom Meta-model]** e toque em **[!UICONTROL Save & Close]**.
1. [Executar a conversão](convert-existing-forms-to-adaptive-forms.md#start-the-conversion-process) para aplicar o metamodelo personalizado ao processo de conversão.

### Exemplos de metamodelo personalizado {#custommetamodelexamples}

Alguns exemplos comuns de uso de um metamodelo personalizado para modificar propriedades de campos de formulário adaptáveis incluem:

* Modificar o rótulo de um campo de formulário
* Modificar o tipo de um campo de formulário
* Adicionar texto de ajuda a um campo de formulário
* Conversão de um campo de formulário em botões de opção de múltipla escolha no formulário adaptável
* Modificar o formato de um campo de formulário
* Adicionar validações a campos de formulário adaptáveis
* Converter um campo de formulário em opções de lista suspensa no formulário adaptável
* Adicionar mais opções à lista suspensa
* Converter um campo de sequência em um campo de várias linhas

#### Modificar o rótulo de um campo de formulário {#modify-the-label-of-a-form-field}

**Exemplo:** Modifique o rótulo Bank account number no formulário para Custom account Number no formulário adaptável após a conversão.

Neste metamodelo personalizado, o serviço de conversão usa o **título** propriedade como uma palavra-chave de pesquisa. Depois de recuperar o **Número da conta bancária** texto no formulário, o serviço de conversão substitui o texto pela **Número da conta do cliente** sequência de caracteres mencionada com o **jcr:title** propriedade na **aem:afProperties** seção.

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

**Exemplo**: modifique o **Número da conta bancária** campo de tipo de texto no formulário antes da conversão para um campo de tipo de número no formulário adaptável após a conversão.

Neste metamodelo personalizado, o serviço de conversão usa o texto dentro de **aem:affKeyword** como uma palavra-chave de pesquisa. Depois de recuperar o **Número da conta bancária** texto no formulário, o serviço de conversão converte o campo em um tipo de número usando o **type** propriedade.

```
{
  "numberfields": {
      "type": "number",
      "aem:affKeyword": ["Bank account number"]
 }
}
```

#### Adicionar texto de ajuda a um campo de formulário {#add-help-text-to-a-form-field}

**Exemplo**: Adicionar texto de ajuda à **Número da conta bancária** campo de formulário adaptável.

Neste metamodelo personalizado, o serviço de conversão usa o texto dentro de **aem:affKeyword** como uma palavra-chave de pesquisa. Depois de recuperar o **Número da conta bancária** texto no formulário, o serviço de conversão adiciona o texto da Ajuda ao campo de formulário adaptável usando o **descrição** propriedade.

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

**Exemplo**: converta o **País** campo do tipo string no formulário antes da conversão para caixas de seleção no formulário adaptável após a conversão.

Neste metamodelo personalizado, o serviço de conversão usa texto dentro de **aem:affKeyword** como uma palavra-chave de pesquisa. Depois de recuperar o **País** texto no formulário, o serviço de conversão converte o campo nas seguintes caixas de seleção usando o **enum** propriedade:

* Índia
* Inglaterra
* Austrália
* Nova Zelândia

**sling:resourceType** e **guideNodeClass** propriedades mapeie um campo de formulário para a caixa de seleção componente de formulário adaptável.

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

**Exemplo**: modifique o formato do **Endereço de e-mail** para um formato de email.

Neste metamodelo personalizado, o serviço de conversão usa texto dentro de **aem:affKeyword** como uma palavra-chave de pesquisa. Depois de recuperar o **Endereço de e-mail** texto no formulário, o serviço de conversão converte o campo em um formato de email usando o **formato** propriedade.

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

**Exemplo 1:** Adicione uma validação à **Código postal** do formulário adaptável.

Neste metamodelo personalizado, o serviço de conversão usa texto dentro de **aem:affKeyword** como a palavra-chave de pesquisa. Depois de recuperar o **Código postal** texto no formulário, o serviço de conversão adiciona uma validação ao campo usando o **validatePictureClause** propriedade definida na variável **aem:afProperties** seção. Com base na validação, a entrada especificada para a variável **Código postal** no formulário adaptável após a conversão deve incluir seis caracteres.

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

**Exemplo 2:** Adicione uma validação à **Número da conta bancária** do formulário adaptável.

Neste metamodelo personalizado, o serviço de conversão usa texto dentro de **aem:affKeyword** como a palavra-chave de pesquisa. Depois de recuperar o **Número da conta bancária** texto no formulário, o serviço de conversão adiciona uma validação ao campo usando o **obrigatório** propriedade definida na variável **aem:afProperties** seção. Com base na validação, você deve especificar um valor para a variável **Número da conta bancária** antes de enviar o formulário após a conversão.

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

**Exemplo**: converta o **País** campo do tipo string no formulário antes da conversão para as opções suspensas no formulário adaptável após a conversão.

Neste metamodelo personalizado, o serviço de conversão usa texto dentro de **aem:affKeyword** como a palavra-chave de pesquisa. Depois de recuperar o **País** texto no formulário, o serviço de conversão converte o campo nas seguintes opções de lista suspensa usando o **enum** propriedade:

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

#### Adicionar mais opções à lista suspensa {#add-additional-options-to-the-drop-down-list}

**Exemplo:** Adicionar **Sri Lanka** como uma opção extra para uma lista suspensa existente usando um metamodelo personalizado.

Para adicionar uma opção extra, atualize o **enum** com a nova opção. Neste exemplo, atualize o **enum** propriedade com **Sri Lanka** como uma opção extra. Valores listados em **enum** propriedade são exibidas na lista suspensa.

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

#### Converter um campo de sequência em um campo de várias linhas {#convert-a-string-field-to-a-multi-line-field}

**Exemplo:** Converta o **Endereço** campo do tipo string para um campo de várias linhas no formulário após a conversão.

Neste metamodelo personalizado, o serviço de conversão usa texto dentro de **aem:affKeyword** como a palavra-chave de pesquisa. Depois de recuperar o **Endereço** texto no formulário, o serviço converte o campo de texto em um campo de várias linhas usando o **multiLine** propriedade definida na variável **aem:afProperties** seção.

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
