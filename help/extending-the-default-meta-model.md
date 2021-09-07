---
title: Ampliar o meta modelo padrão
seo-title: Extend the default meta-model
description: Estenda o metamodelo padrão para adicionar padrões, validações e entidades específicas à sua organização e aplique configurações a campos de formulário adaptáveis enquanto executa o serviço Automated forms conversion.
seo-description: Extend the default meta-model to add pattern, validations, and entities specific to your organization and apply configurations to adaptive form fields while running the Automated Forms Conversion service.
uuid: f98b4cca-f0a3-4db8-aef2-39b8ae462628
topic-tags: forms
discoiquuid: cad72699-4a4b-4c52-88a5-217298490a7c
exl-id: f679059c-18aa-4cb5-8368-ed27e96c20de
source-git-commit: 47261710e6616c27c210ac53bffcc2387a06ea7a
workflow-type: tm+mt
source-wordcount: '2565'
ht-degree: 1%

---

# Ampliar o meta modelo padrão {#extend-the-default-meta-model}

O serviço Automated forms conversion identifica e extrai objetos de formulário de formulários de origem. O mapeador semântico ajuda o serviço a decidir como os objetos extraídos são representados em um formulário adaptável. Por exemplo, um formulário de origem pode ter vários tipos diferentes de representações de uma data. O mapeador semântico ajuda a mapear todas as representações de objetos de formulário de data do formulário de origem com o componente de data dos formulários adaptáveis. O mapeador semântico também permite que o serviço pré-configure e aplique validações, regras, padrões de dados, texto da Ajuda e propriedades de acessibilidade a componentes de formulário adaptáveis durante a conversão.

![](assets/meta-model.gif)

O metamodelo é um esquema JSON. Antes de começar com o metamodelo, verifique se você está familiarizado com o JSON. Você deve ter experiência na criação, edição e leitura de dados salvos no formato JSON.

## Metamodelo padrão {#default-meta-model}

O serviço Automated forms conversion tem um meta modelo padrão. É um esquema JSON e reside na Adobe Cloud com outros componentes do serviço Automated forms conversion. Você pode encontrar uma cópia do metamodelo em seu servidor de AEM local em: http://&lt;server>:&lt;port>/aem/forms.html/content/dam/formsanddocuments/metamodel/`global.schema.json`. Você também pode [clicar aqui](assets/en.globalschema.json) para acessar ou baixar o schema do idioma inglês. O metamodelo dos idiomas [Francês](assets/fr.globalschema.json), [Alemão](assets/de.globalschema.json) [Espanhol](assets/es.globalschema.json), [Italiano](assets/it.globalschema.json) e [Português](assets/pt_br.globalschema.json) também está disponível para download.

O esquema do metamodelo é derivado de entidades de esquema em https://schema.org/docs/schemas.html. Ele tem Pessoa, PostalAddress, LocalBusiness e mais entidades, conforme definido em https://schema.org. Cada entidade do metamodelo adere ao tipo de objeto de esquema JSON. O código a seguir representa uma estrutura de metamodelo de amostra:

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

## Baixe o metamodelo padrão {#download-the-default-meta-model}

Execute as seguintes etapas para baixar o metamodelo padrão no sistema de arquivos local:

1. Faça logon na instância do AEM Forms.
1. Navegue até a pasta **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]** **** **[!UICONTROL Meta Model]**.
1. Selecione o arquivo **[!UICONTROL global.schema.json]** e toque em **[!UICONTROL Download]**. Uma caixa de diálogo de download é exibida. Selecione a opção **[!UICONTROL Download asset(s) as binary files]**. Tocar **[!UICONTROL Download]**. Um arquivo é baixado.

   <!--
   Comment Type: draft

   <li><p>Extract the archive and open the global.schema.json file for editing. </p> </li>
   -->

   <!--
   Comment Type: draft

   <li>Step text</li>
   -->

## Noções básicas do metamodelo {#understanding-the-meta-model}

Um metamodelo refere-se a um arquivo de esquema JSON que contém entidades. Todas as entidades no arquivo de esquema JSON incluem um nome e uma id. Cada entidade pode incluir várias propriedades. As entidades e suas propriedades podem variar com base no domínio . É possível aumentar um arquivo de esquema com palavras-chave e configurações de campo para mapear propriedades de esquema a componentes de formulário adaptáveis.

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

Neste exemplo, **Event** representa o nome de uma entidade com um valor para **id** como **Eventid**. A entidade Evento inclui várias propriedades:

* startDate
* endDate
* localização

A construção **allOf** no metamodelo permite herança entre entidades.

Cada propriedade pode incluir ainda mais:

* [Propriedades do schema JSON](#jsonschemaproperties)
* [Pesquisa por palavra-chave para aplicar propriedades aos campos de formulário adaptáveis gerados](#keywordsearch)
* [Propriedades adicionais](#additionalproperties)

![Propriedades do metamodelo](assets/meta_model_elements.gif)

Com base nas palavras-chave referenciadas usando **aem:affKeyword**, o serviço de conversão executa uma operação de pesquisa nos campos de formulário de origem. O serviço de conversão aplica as propriedades do esquema JSON e propriedades adicionais aos campos que atendem aos critérios de pesquisa.

Neste exemplo, o serviço de conversão pesquisa por telefone, telefone, celular, telefone celular, telefone fixo, telefone celular, número de telefone, número de telefone e palavras-chave do número de telefone no formulário de origem. Com base nos campos que incluem essas palavras-chave, o serviço de conversão aplica o tipo, padrão e aem:afProperties aos campos do formulário adaptável após a conversão.

### Propriedades do esquema JSON para campos de formulário adaptáveis gerados {#jsonschemaproperties}

O metamodelo oferece suporte às seguintes propriedades comuns do esquema JSON para campos de formulário adaptáveis gerados usando o serviço Automated forms conversion:

<table> 
 <tbody> 
  <tr> 
   <th><strong>Nome da Propriedade</strong></th> 
   <th><strong>Descrição</strong></th> 
  </tr> 
  <tr> 
   <td><p>título</p></td> 
   <td> 
    <p>O texto mencionado na propriedade title em um metamodelo serve como uma palavra-chave de pesquisa para executar ações nos campos de formulário adaptáveis gerados. Por exemplo, modificar o rótulo de um campo de formulário adaptável. Para obter mais informações, consulte <strong>Modificar o rótulo de um campo de formulário</strong> em <a href="#custommetamodelexamples">Exemplos de metamodelo personalizados.</a></p> </td> 
  </tr>
  <td><p>descrição</p></td> 
   <td> 
    <p>A propriedade description define o texto Ajuda para o campo de formulário adaptável gerado. Para obter mais informações, consulte <strong>Adicionar texto da Ajuda a um campo de formulário</strong> em <a href="#custommetamodelexamples">Exemplos de metamodelo personalizados.</a></p> </td> 
  </tr>
  <td><p>tipo</p></td> 
   <td> 
    <p>A propriedade type define o tipo de dados do campo de formulário adaptável gerado. Os valores possíveis para a propriedade title incluem:</p>
    <ul> 
     <li>sequência de caracteres: Gera um campo de formulário adaptável do tipo de dados de texto.</li> 
     <li>número: Gera um campo de formulário adaptável do tipo de dados numéricos.</li>
     <li>número inteiro: Gera um campo de formulário adaptável de tipo de dados numéricos com subtipo definido como inteiro.</li>
     <li>booleano: Gera um componente de formulário adaptável de switch.</li>
     </ul><p>Para obter mais informações sobre como usar a propriedade type em um metamodelo, consulte <strong>Modificar o tipo de campo de formulário</strong> em <a href="#custommetamodelexamples">Metamodelos personalizados.</a></p></td> 
  </tr>
  <td><p>pattern</p></td> 
   <td> 
    <p>A propriedade pattern restringe o valor do campo de formulário adaptável gerado com base em uma expressão regular. Por exemplo, o código a seguir no metamodelo restringe o valor do campo de formulário adaptável gerado a dez dígitos:<br>"padrão": "/\\d{10}/"<br>Da mesma forma, o código a seguir no metamodelo restringe o valor de um campo a um formato de data específico.<br> "padrão": "date{DD MMMM, AAAA}",</p> </td> 
  </tr>
  <td><p>format</p></td> 
   <td> 
    <p>A propriedade format restringe o valor do campo de formulário adaptável gerado com base em um padrão nomeado em vez de uma expressão regular. Os valores possíveis para a propriedade format incluem:<ul><li>email: Gera um componente de formulário adaptável por email.</li><li>nome do host: Gera um componente de formulário adaptável de caixa de texto.</li></ul>Para obter mais informações sobre como usar a propriedade format em um metamodelo, consulte <strong>Modificar o formato de um campo de formulário</strong> em <a href="#custommetamodelexamples">Exemplos de metamodelo personalizados.</a></p> </td> 
  </tr>
  <td><p>enum e enumNames</p></td> 
   <td> 
    <p>As propriedades enum e enumNames restringem os valores dos campos suspensos, de caixa de seleção ou de botão de opção a um conjunto fixo. Os valores listados em enumNames são exibidos na interface do usuário. Os valores listados usando a propriedade enum são usados para o cálculo.<br>Para obter mais informações, consulte  <strong>Converter um campo de formulário em caixas de seleção de múltipla escolha no formulário</strong> adaptável,  <strong>Converter um campo de texto em lista suspensa no formulário</strong> adaptável e  <strong>Adicionar opções adicionais à </strong> lista suspensa em exemplos de metamodelo  <a href="#custommetamodelexamples">personalizado.</a></p> </td> 
  </tr>
 </tbody> 
</table>

### Pesquisa por palavra-chave para aplicar propriedades aos campos de formulário adaptáveis gerados {#keywordsearch}

O serviço Automated forms conversion realiza uma pesquisa por palavra-chave no formulário de origem durante a conversão. Depois de filtrar os campos que atendem aos critérios de pesquisa, o serviço de conversão aplica as propriedades definidas para esses campos no metamodelo aos campos de formulário adaptável gerados.

As palavras-chave são referenciadas usando a propriedade **aem:affKeyword**.

```
{
  "numberfields": {
      "type": "number",
      "aem:affKeyword": ["Bank account number"]
 }
}
```

Neste exemplo, o serviço de conversão usa o texto em **aem:affKeyword** como uma palavra-chave de pesquisa. Depois de recuperar o texto **Bank account number** no formulário, o serviço de conversão converte o campo em um tipo **number** usando a propriedade **type**.

### Propriedades adicionais para campos de formulário adaptáveis gerados {#additionalproperties}

Você pode usar a propriedade **aem:afProperties** no metamodelo para definir as seguintes propriedades adicionais para campos de formulários adaptáveis gerados usando o serviço Automated forms conversion:

<table> 
 <tbody> 
  <tr> 
   <th><strong>Nome da Propriedade</strong></th> 
   <th><strong>Descrição</strong></th> 
  </tr> 
  <tr> 
   <td><p>multiLine</p></td> 
   <td> 
    <p>A propriedade multiLine converte um campo de formulário de origem em um campo de várias linhas no formulário adaptável após a conversão. Para obter mais informações, consulte <strong>Converter um campo de cadeia de caracteres em um campo de várias linhas</strong> em <a href="#custommetamodelexamples">Exemplos de metamodelo personalizados.</a></p> </td> 
  </tr>
  <td><p>mandatory</p></td> 
   <td> 
    <p>A propriedade mandatory define a entrada de um campo de formulário adaptável após a conversão como obrigatória.<br>Para obter mais informações, consulte  <strong>Adicionar validações a </strong> campos de formulário adaptáveis em exemplos de metamodelo  <a href="#custommetamodelexamples">personalizado.</a></p>
    </td> 
  </tr>
  <td><p>jcr:title</p></td> 
   <td> 
    <p>A propriedade jcr:title, com o título propriedade de esquema JSON, permite modificar o rótulo de um campo de formulário adaptável após a conversão.<br>Para obter mais informações, consulte  <strong>Modificar o rótulo de um campo de formulário </strong> em exemplos de metamodelo  <a href="#custommetamodelexamples">personalizado .</a><br>Consulte  <a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/adaptive-form-json-schema-form-model.html" target="_blank">Criação de formulários adaptáveis usando o </a> esquema JSON para obter informações sobre mais propriedades que podem ser aplicadas a campos de formulários adaptáveis usando o esquema JSON.</p>
    <p></p></td> 
  </tr>
  <td><p>sling:resourceType e guideNodeClass</p></td> 
   <td> 
    <p>as propriedades sling:resourceType e guideNodeClass permitem mapear um campo de formulário para um componente de formulário adaptável correspondente.<br>Para obter mais informações, consulte  <strong>Converter um campo de formulário em caixas de seleção de múltipla escolha no </strong> formulário adaptável e  <strong>Converter um campo de texto em lista suspensa nos exemplos de </strong> formulário adaptável  <a href="#custommetamodelexamples">Custom meta-model.</a></p> </td> 
  </tr>
  <td><p>validatePictureClause</p></td> 
   <td> 
    <p>A propriedade validatePictureClause define uma validação no formato permitido no campo de formulário adaptável após a conversão.<br>Para obter mais informações, consulte  <strong>Adicionar validações a </strong> campos de formulário adaptáveis em exemplos de metamodelo  <a href="#custommetamodelexamples">personalizado.</p> </td> 
  </tr>
 </tbody> 
</table>

## Criar um modelo personalizado em seu próprio idioma{#language-specific-meta-model}

Você pode criar um meta modelo específico de idioma. Esse metamodelo ajuda a criar regras de mapeamento no idioma de sua escolha. O serviço Automated forms conversion permite criar meta modelos nos seguintes idiomas:

* Inglês (EN)
* Francês (França)
* Alemão (Alemanha)
* Espanhol (Espanha)
* Italiano (Itália)
* Português (pt-br)

Adicione a tag de metatag *aem:Language* na parte superior de um metamodelo para especificar seu idioma. Por exemplo,

```JSON
"metaTags": {
        "aem:Language": "fr"
    }
```

Quando nenhum idioma é especificado, o serviço considera que o metamodelo está em inglês.

### Considerações para a criação de um meta modelo específico de idioma

* Verifique se o nome de cada chave está em inglês. Por exemplo, emailAddress.
* Certifique-se de que todas as referências de entidade e valores predefinidos de todas as chaves de id contenham apenas caracteres ASCII. Por exemplo, &quot;id&quot;: &quot;ContactPoint&quot; / &quot;$ref&quot;: &quot;#ContactPoint&quot;.
* Verifique se todos os valores correspondentes às seguintes chaves estão na linguagem do metamodelo especificado:
   * aem:affKeyword
   * título
   * descrição
   * enumNames
   * shortDescription
   * validatePictureClauseMessage

   Por exemplo, quando o idioma do metamodelo é francês (&quot;aem:Language&quot;: &quot;fr&quot;), assegurar que todas as descrições e mensagens estejam em francês.

* Certifique-se de que todas as [propriedades do esquema JSON](#jsonschemaproperties) usem apenas os valores suportados. Por exemplo, a propriedade type só pode abranger valores selecionados de String, Number, Integer e Boolean.

A imagem a seguir exibe exemplos do metamodelo de idioma inglês e o metamodelo de idioma francês correspondente:

![](assets/language-specific-meta-model-comparison.png)

## Modificar campos de formulário adaptáveis usando metamodelo personalizado {#modify-adaptive-form-fields-using-custom-meta-model}

Sua organização pode ter padrões e validações além dos listados no metamodelo padrão. É possível estender o metamodelo padrão para adicionar padrões, validações e entidades específicas à sua organização. O serviço Automated forms conversion aplica o metamodelo personalizado aos campos de formulário durante a conversão. Você pode continuar atualizando o metamodelo à medida que novos padrões, validações e entidades específicas da sua organização são descobertos.

O serviço Automated forms conversion usa um metamodelo padrão salvo no seguinte local para mapear campos de formulário de origem para os campos de formulário adaptáveis durante a conversão:

http://&lt;server>:&lt;port>/aem/forms.html/content/dam/formsanddocuments/metamodel/global.schema.json

No entanto, você pode salvar um metamodelo personalizado em uma pasta e modificar as propriedades do serviço de conversão para usar o metamodelo personalizado durante a conversão.

### Usar metamodelo personalizado durante a conversão {#use-custom-meta-model-during-conversion}

Execute as seguintes etapas para usar um metamodelo personalizado durante a conversão:

1. Crie uma pasta em **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]** e faça upload do arquivo de esquema JSON personalizado do metamodelo para a pasta.
1. Abra as propriedades do serviço de conversão usando:

   **[!UICONTROL Tools]** >  **[!UICONTROL Cloud Services]** >  **[!UICONTROL Automated Forms Conversion Configuration]**>  **&lt;>Propriedades da configuração** selecionada>****

1. Na guia **[!UICONTROL Basic]** , especifique o local do metamodelo personalizado no campo **[!UICONTROL Custom Meta-model]** e toque em **[!UICONTROL Save & Close]**.
1. [Execute a ](convert-existing-forms-to-adaptive-forms.md#start-the-conversion-process) conversão para aplicar o metamodelo personalizado ao processo de conversão.

### Exemplos de metamodelo personalizado {#custommetamodelexamples}

Alguns exemplos comuns de uso de um metamodelo personalizado para modificar propriedades de campos de formulário adaptáveis incluem:

* Modificar o rótulo de um campo de formulário
* Modificar o tipo de campo de formulário
* Adicionar texto de Ajuda a um campo de formulário
* Converter um campo de formulário em botões de opção de múltipla escolha no formulário adaptável
* Modificar o formato de um campo de formulário
* Adicionar validações a campos de formulário adaptáveis
* Converter um campo de formulário em opções de lista suspensa no formulário adaptável
* Adicionar opções adicionais à lista suspensa
* Converter um campo de cadeia de caracteres em um campo de várias linhas

#### Modificar o rótulo de um campo de formulário {#modify-the-label-of-a-form-field}

**Exemplo:** Modifique o rótulo do número de conta bancária no formulário para Número de conta personalizado no formulário adaptável após a conversão.

Neste metamodelo personalizado, o serviço de conversão usa a propriedade **title** como uma palavra-chave de pesquisa. Depois de recuperar o texto **Bank account number** no formulário, o serviço de conversão substitui o texto pela sequência **Customer account number** mencionada com a propriedade **jcr:title** na seção **aem:afProperties**.

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

#### Modificar o tipo de campo de formulário {#modify-the-type-of-a-form-field}

**Exemplo**: Modifique o campo  **Bank account** number do tipo de texto no formulário antes da conversão para um campo de tipo de número no formulário adaptável após a conversão.

Neste metamodelo personalizado, o serviço de conversão usa o texto dentro de **aem:affKeyword** como uma palavra-chave de pesquisa. Depois de recuperar o texto **Bank account number** no formulário, o serviço de conversão converte o campo em um tipo de número usando a propriedade **type**.

```
{
  "numberfields": {
      "type": "number",
      "aem:affKeyword": ["Bank account number"]
 }
}
```

#### Adicionar texto de Ajuda a um campo de formulário {#add-help-text-to-a-form-field}

**Exemplo**: Adicione o texto Ajuda ao campo  **Número da conta** bancária do formulário adaptável.

Neste metamodelo personalizado, o serviço de conversão usa o texto dentro de **aem:affKeyword** como uma palavra-chave de pesquisa. Depois de recuperar o texto **Bank account number** no formulário, o serviço de conversão adiciona o texto Ajuda ao campo de formulário adaptável usando a propriedade **description**.

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

**Exemplo**: Converta o campo  **** País do tipo string no formulário antes da conversão em caixas de seleção no formulário adaptável após a conversão.

Neste metamodelo personalizado, o serviço de conversão usa o texto dentro de **aem:affKeyword** como uma palavra-chave de pesquisa. Depois de recuperar o texto **Country** no formulário, o serviço de conversão converte o campo nas seguintes caixas de seleção usando a propriedade **enum**:

* Índia
* Inglaterra
* Austrália
* Nova Zelândia

**sling:** resourceType e  **** guideNodeClassproperties mapeiam um campo de formulário para o componente de formulário adaptável da caixa de seleção.

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

**Exemplo**: Modifique o formato do campo  **Endereço de** email para um formato de email.

Neste metamodelo personalizado, o serviço de conversão usa o texto dentro de **aem:affKeyword** como uma palavra-chave de pesquisa. Após recuperar o texto **Endereço de email** no formulário, o serviço de conversão converte o campo em um formato de email usando a propriedade **format**.

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

**Exemplo 1:** adicione uma validação ao campo  **** CEP do formulário adaptável.

Neste metamodelo personalizado, o serviço de conversão usa texto dentro de **aem:affKeyword** como palavra-chave de pesquisa. Após recuperar o texto **CEP** no formulário, o serviço de conversão adiciona uma validação ao campo usando a propriedade **validatePictureClause** definida na seção **aem:afProperties**. Com base na validação, a entrada especificada para o campo **CEP** no formulário adaptável após a conversão deve incluir seis caracteres.

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

**Exemplo 2:** Adicione uma validação ao campo  **Bank account** number do formulário adaptável.

Neste metamodelo personalizado, o serviço de conversão usa texto dentro de **aem:affKeyword** como palavra-chave de pesquisa. Depois de recuperar o texto **Bank account number** no formulário, o serviço de conversão adiciona uma validação ao campo usando a propriedade **mandatory** definida na seção **aem:afProperties**. Com base na validação, você deve especificar um valor para o campo **Bank account number** antes de enviar o formulário após a conversão.

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

**Exemplo**: Converta o campo  **** País do tipo string no formulário antes da conversão em opções suspensas no formulário adaptável após a conversão.

Neste metamodelo personalizado, o serviço de conversão usa texto dentro de **aem:affKeyword** como palavra-chave de pesquisa. Depois de recuperar o texto **Country** no formulário, o serviço de conversão converte o campo nas seguintes opções da lista suspensa usando a propriedade **enum**:

* Índia
* Inglaterra
* Austrália
* Nova Zelândia

**sling:** resourceType e  **** guideNodeClassproperties mapeiam um campo de formulário para o componente de formulário adaptável suspenso.

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

**Exemplo:** adicione  **Sri** Lankas uma opção extra a uma lista suspensa existente usando um metamodelo personalizado.

Para adicionar uma opção extra, atualize a propriedade **enum** com a nova opção. Neste exemplo, atualize a propriedade **enum** com **Sri Lanka** como uma opção extra. Os valores listados na propriedade **enum** são exibidos na lista suspensa.

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

#### Converter um campo de cadeia de caracteres em um campo de várias linhas {#convert-a-string-field-to-a-multi-line-field}

**Exemplo:** Converta o campo  **** Endereço do tipo sequência de caracteres em um campo de várias linhas no formulário após a conversão.

Neste metamodelo personalizado, o serviço de conversão usa texto dentro de **aem:affKeyword** como palavra-chave de pesquisa. Após recuperar o texto **Address** no formulário, o serviço converte o campo de texto em um campo de várias linhas usando a propriedade **multiLine** definida na seção **aem:afProperties**.

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
