---
title: Preenchimento e fluxos de trabalho recomendados com base na fonte de dados para formulários adaptáveis
seo-title: Opções de preenchimento prévio e envio para formulários adaptáveis
description: Fluxos de trabalho de preenchimento e envio baseados na fonte de dados para formulários adaptáveis gerados usando o Serviço de conversão de formulários automatizado.
seo-description: Fluxos de trabalho de preenchimento e envio baseados na fonte de dados para formulários adaptáveis gerados usando o Serviço de conversão de formulários automatizado.
uuid: 91409a82-141c-4233-82b1-1539a0b250f8
contentOwner: khsingh
topic-tags: forms
discoiquuid: cad34fff-7f9f-4a27-8b5c-d0a523903eec
privatebeta: true
translation-type: tm+mt
source-git-commit: f598871fd41c402f98d94d7b2174ab8b2e487075

---


# Preenchimento e fluxos de trabalho recomendados com base na fonte de dados para formulários adaptáveis {#recommended-data-source-btased-prefill-and-submit-workflows-for-adaptive-forms}

É possível usar qualquer uma das seguintes fontes de dados com formulários adaptáveis convertidos usando o serviço de conversão de formulários automatizados:

* Modelo de dados de formulário, OData ou qualquer outro serviço de terceiros
* Esquema JSON
* Esquema XSD

Com base na fonte de dados, você pode optar por gerar um formulário adaptável com ou sem um modelo de dados.

Este artigo descreve os fluxos de trabalho recomendados para preencher previamente valores de campo e opções de envio depois de selecionar uma fonte de dados e gerar um formulário adaptável usando o serviço de conversão.

<table> 
 <tbody> 
  <tr> 
   <th><strong>Fonte de Dados</strong></th> 
   <th><strong>Fluxo de trabalho recomendado</strong></th> 
  </tr> 
  <tr> 
   <td><p>Modelo de dados de formulário, OData ou qualquer outro serviço de terceiros</p></td> 
   <td> 
    <p><strong>Opção 1</strong>: Você seleciona o modelo de dados de formulário, OData ou qualquer outro serviço de terceiros como a fonte de dados. Você <a href="#generate-adaptive-forms-with-no-data-binding">gera um formulário adaptável sem vínculo</a> de dados usando o serviço de Conversão de formulários automatizados. Vincule os campos de formulário adaptáveis às entidades do modelo de dados manualmente e use a opção Serviço de preenchimento prévio do modelo de dados de formulário para preencher previamente os valores de campo. Use a opção Enviar usando o Modelo de dados de formulário para enviar o formulário adaptável.</p></td> 
  </tr>
  <tr> 
   <td></td> 
   <td> 
   <p><strong>Opção 2</strong>: Você seleciona o modelo de dados de formulário, OData ou qualquer outro serviço de terceiros como a fonte de dados. Você <a href="#generate-adaptive-forms-with-no-data-binding">gera um formulário adaptável sem vínculo</a> de dados usando o serviço de Conversão de formulários automatizados. Vincule os campos de formulário adaptáveis usando o editor de regras para preencher previamente os valores de campo. Modifique os valores de campo, se necessário, e envie dados para o repositório crx.</p>
    </td> 
  </tr>
  <tr> 
   <td></td> 
   <td> 
    <p>Para obter instruções passo a passo para executar esses fluxos de trabalho, consulte <a href="#sqldatasource">Usar banco de dados, OData ou qualquer serviço de terceiros como a fonte de dados.</a></p> </td> 
  </tr>
  <tr>
  <td><p>Esquema JSON</p></td> 
   <td> 
    <p>Você seleciona o esquema JSON como a fonte de dados. Com base na fonte de dados selecionada:</p></td> 
  </tr>
  <tr>
  <td></td> 
   <td> 
    <p><strong>Opção 1</strong>: Você <a href="#generate-adaptive-forms-with-no-data-binding">gera um formulário adaptável sem vínculo</a> de dados usando o serviço de Conversão de formulários automatizados e configura o esquema JSON como a fonte de dados. Vincule os campos de formulário adaptáveis ao esquema JSON manualmente e <a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/prepopulate-adaptive-form-fields.html#Supportedprotocolsforprefillinguserdata" target="_blank">use qualquer um dos protocolos</a> suportados para preencher os valores de campo previamente. Modifique os valores de campo, se necessário, e envie dados para o repositório crx.</p></td> 
  </tr>
  <tr>
  <td></td> 
   <td> 
    <p>Para obter instruções passo a passo para executar os fluxos de trabalho, consulte <a href="#jsondatasource">Usar o esquema JSON como a fonte de dados.</p></td> 
  </tr>
  <tr>
  <td></td> 
   <td> 
    <p><strong>Opção 2</strong>: Você <a href="#generate-adaptive-forms-with-json-binding">gera um formulário adaptável com vínculo</a> de dados JSON usando o serviço de Conversão de formulários automatizada. O serviço de preenchimento prévio e a função de envio de formulário funcionam perfeitamente. Você não precisa de nenhuma etapa de configuração.</p> </td> 
  </tr>
   <tr>
  <td></td> 
   <td> 
    <p>Para obter instruções passo a passo para executar os fluxos de trabalho, consulte <a href="#jsonwithdatabinding">Usar o esquema JSON como a fonte de dados.</a></p> </td> 
  </tr>
  <tr>
  <td><p>Esquema XSD</p></td> 
   <td> 
    <p>Você seleciona o esquema XSD como a fonte de dados. Com base na fonte de dados selecionada, você <a href="#generate-adaptive-forms-with-no-data-binding">gera um formulário adaptável sem vínculo</a> de dados usando o serviço de Conversão de formulários automatizados e configura o esquema XSD como a fonte de dados. Vincule os campos de formulário adaptáveis ao esquema XSD manualmente e <a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/prepopulate-adaptive-form-fields.html#Supportedprotocolsforprefillinguserdata" target="_blank">use qualquer um dos protocolos</a> suportados para preencher os valores de campo previamente. Modifique os valores de campo, se necessário, e envie dados para o repositório crx.</p>
    </td> 
  </tr>
  <tr>
  <td></td> 
   <td> 
    <p>Para obter instruções passo a passo para executar os fluxos de trabalho, consulte <a href="#xsddatasource">Usar esquema XSD como fonte de dados.</a></p>
    </td> 
  </tr>
 </tbody> 
</table>


Para obter mais informações sobre o serviço de Conversão de formulários automatizados, consulte os seguintes artigos:

* [Introdução ao serviço de conversão de formulários automatizados](introduction.md)
* [Configurar o serviço de conversão de formulários automatizados](configure-service.md)
* [Converter formulários impressos em formulários adaptáveis](convert-existing-forms-to-adaptive-forms.md)
* [Revisar e corrigir formulários convertidos](review-correct-ui-edited.md)

As informações fornecidas neste artigo baseiam-se no pressuposto de que qualquer pessoa que as leia tem conhecimento básico dos conceitos de formas adaptativas.

## Pré-requisitos {#pre-requisites}

* Configurar uma instância do autor [AEM](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/deploy.html)
* Configurar o serviço de conversão de formulários [automatizados na instância do autor de AEM](configure-service.md)

## Exemplo de formulário adaptável {#sample-adaptive-form}

Para executar os casos de uso para preencher previamente valores de campo em um formulário adaptável e enviá-los para a fonte de dados, baixe o arquivo PDF de amostra a seguir.

Formulário de pedido de empréstimo de amostra

[Obter arquivo](assets/sample_loan_application_form.pdf)

O arquivo PDF serve como entrada para o serviço de Conversão de formulários automatizados. O serviço converte esse arquivo em um formulário adaptável. A imagem a seguir descreve o aplicativo de empréstimo de amostra em um formato PDF.

![formulário de pedido de empréstimo de amostra](assets/sample_form_new.png)

## Preparar dados para o modelo de formulário {#prepare-data-for-form-model}

A integração de dados do AEM Forms permite configurar e conectar-se a fontes de dados diferentes. Depois de gerar um formulário adaptável usando o processo de conversão, você pode definir o modelo de formulário com base em um modelo de dados de formulário, XSD ou um esquema JSON. Você pode usar um banco de dados, o Microsoft Dynamics ou qualquer outro serviço de terceiros para criar um modelo de dados de formulário.

Este tutorial usa o banco de dados MySQL como a fonte para criar um modelo de dados de formulário. Crie um esquema de **aplicativo** de empréstimo no banco de dados e adicione uma tabela de **candidato** ao esquema com base nos campos disponíveis no formulário adaptável.

![Dados de amostra mysql](assets/sample_data_mysql.png)

Você pode usar a seguinte instrução DDL para criar a tabela do **candidato** no banco de dados.

```sql
CREATE TABLE `applicant` (
   `name` varchar(45) DEFAULT NULL,
   `address` varchar(45) DEFAULT NULL,
   `phonenumber` int(11) NOT NULL,
   `email` varchar(45) DEFAULT NULL,
   `occupation` varchar(45) DEFAULT NULL,
   `annualsalary` varchar(45) DEFAULT NULL,
   `familymembers` int(11) DEFAULT NULL,
   PRIMARY KEY (`phonenumber`)
 ) ENGINE=InnoDB DEFAULT CHARSET=utf8
```

Se você estiver usando um esquema XSD como modelo de formulário para executar os casos de uso, crie um arquivo XSD com o seguinte texto:

```xml
<?xml version="1.0" encoding="utf-8" ?>
    <xs:schema targetNamespace="http://adobe.com/sample.xsd"
                    xmlns="http://adobe.com/sample.xsd"
                    xmlns:xs="http://www.w3.org/2001/XMLSchema">

<xs:element name="sample" type="SampleType"/>

  <xs:complexType name="SampleType">
    <xs:sequence>
      <xs:element name="name" type="xs:string"/>
   <xs:element name="address" type="xs:string"/>
   <xs:element name="phonenumber" type="xs:int"/>
   <xs:element name="email" type="xs:string"/>
   <xs:element name="occupation" type="xs:string"/>
   <xs:element name="annualsalary" type="xs:string"/>
   <xs:element name="familymembers" type="xs:string"/>
 </xs:sequence>
  </xs:complexType>

  </xs:schema>
```

Ou faça o download do esquema XSD para o sistema de arquivos local.

Exemplo de esquema XSD do aplicativo de empréstimo

[Obter arquivo](assets/loanapplication.xsd)

Para obter mais informações sobre como usar o esquema XSD como modelo de formulário em formulários adaptáveis, consulte [Criar formulários adaptáveis usando o esquema](https://helpx.adobe.com/experience-manager/6-5/forms/using/adaptive-form-xml-schema-form-model.html)XML.

Se você estiver usando um esquema JSON como modelo de formulário para executar os casos de uso, crie um arquivo JSON com o seguinte texto:

```JSON
{
    "$schema": "http://json-schema.org/draft-04/schema#",
    "definitions": {
        "loanapplication": {
            "type": "object",
            "properties": {
                "name": {
                    "type": "string"
                },
                "address": {
                    "type": "string"
                },
    "phonenumber": {
                    "type": "number"
                },
    "email": {
                    "type": "string"
                },
    "occupation": {
                    "type": "string"
                },
    "annualsalary": {
                    "type": "string"
                },
    "familymembers": {
                    "type": "number"
                }
            }
        }
 },
 "type": "object",
    "properties": {
        "employee": {
            "$ref": "#/definitions/loanapplication"
        }
    }
}
```

Ou baixe o esquema JSON no sistema de arquivos local.

Amostra do aplicativo de empréstimo JSON

[Obter arquivo](assets/demo_schema.json)

Para obter mais informações sobre como usar o esquema JSON como modelo de formulário em formulários adaptáveis, consulte [Criar formulários adaptáveis usando o esquema](https://helpx.adobe.com/experience-manager/6-5/forms/using/adaptive-form-json-schema-form-model.html)JSON.

## Gerar formulários adaptáveis sem vínculo de dados {#generate-adaptive-forms-with-no-data-binding}

Use o serviço de Conversão de formulários [automatizados para converter](convert-existing-forms-to-adaptive-forms.md) o formulário [de aplicativo de empréstimo de](#sample-adaptive-form) amostra em um formulário adaptável sem vínculo de dados. Marque a caixa de **[!UICONTROL Generate adaptive form(s) without data bindings]** seleção para gerar o formulário adaptável sem vínculo de dados.

![Formulário adaptável sem vínculo de dados](assets/generate_af_without_binding.png)

Depois de gerar um formulário adaptável sem vínculo de dados, selecione uma fonte de dados para o formulário adaptável:

* [Banco de dados, OData ou qualquer serviço de terceiros](#sqldatasource)
* [Esquema JSON](#jsondatasource)
* [Esquema XSD](#xsddatasource)

>[!NOTE]
> Se o formulário adaptável que você converte usando o serviço de Conversão de formulários automatizados contiver vários campos com o mesmo nome, verifique se esses campos estão vinculados a entidades de fonte de dados para evitar uma possível perda de dados durante o envio.


### Usar banco de dados, OData ou qualquer serviço de terceiros como fonte de dados {#sqldatasource}

Caso de uso: Você gera um formulário adaptável sem vínculo de dados usando o serviço de Conversão de formulários automatizada e configura o banco de dados MYSQL como a fonte de dados. Vincule os campos de formulário adaptáveis às entidades do modelo de dados manualmente e use a **[!UICONTROL Form Data Model Prefill Service]** opção para preencher previamente os valores de campo. Use a **[!UICONTROL Submit using Form Data Model]** opção para enviar o formulário adaptável.

Antes de executar o caso de uso:

* [Configurar o banco de dados MySQL como a fonte de dados](https://helpx.adobe.com/experience-manager/6-5/forms/using/configure-data-sources.html#configurerelationaldatabase)
* [Criar o modelo de dados de formulário](https://helpx.adobe.com/experience-manager/6-5/forms/using/work-with-form-data-model.html)

Com base no caso de uso, crie o modelo de dados de formulário **loanapplication** e vincule o argumento de serviço de leitura a um **[!UICONTROL Literal]** valor. O valor literal de número de telefone deve ser de um dos registros configurados no esquema **candidato** do banco de dados MySQL. Os serviços usam o valor como um argumento para buscar detalhes da fonte de dados. Você também pode selecionar Atributo de perfil [do usuário ou Atributo](https://helpx.adobe.com/experience-manager/6-5/forms/using/work-with-form-data-model.html#bindargument) de solicitação na lista **[!UICONTROL Binding To]** suspensa

![Configurar modelo de dados de formulário](assets/configure_model_object.png)

>[!NOTE]
>
>Certifique-se de adicionar **obter** e **inserir** serviços ao modelo de dados do formulário, configurar e testar os serviços antes de executar o caso de uso.

Execute as seguintes etapas:

1. Selecione o formulário **do aplicativo de empréstimo de** amostra convertido disponível na **[!UICONTROL output]** pasta e toque em **[!UICONTROL Properties]**.
1. Toque na **[!UICONTROL Form Model]** guia, selecione **[!UICONTROL Form Data Model]** na lista **[!UICONTROL Select From]** suspensa e toque **[!UICONTROL Select Form Data Model]** para selecionar o modelo de dados de formulário **de aplicativo** de empréstimo. Toque em **[!UICONTROL Save & Close]** para salvar o formulário.
1. Selecione o formulário **de solicitação de empréstimo de** amostra e toque em **[!UICONTROL Edit]**.
1. Na **[!UICONTROL Content]** guia, toque no ícone de configuração:

   ![configurar contêiner de formulário](assets/configure_form_container.png)

   1. Na **[!UICONTROL Basic]** seção, selecione **[!UICONTROL Form Data Model Prefill service]** na lista **[!UICONTROL Prefill Service]** suspensa.

   1. Na **[!UICONTROL Submission]** seção, selecione **[!UICONTROL Submit using Form Data Model]** na lista **[!UICONTROL Submit Action]** suspensa.

   1. Selecione o modelo de dados usando o **[!UICONTROL Data Model to submit]** campo.
   1. Toque no ícone ![](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-4/forms/using/chart-component/Done_Icon.png) Concluído para salvar as propriedades.

1. Toque na caixa de texto Nome do candidato e selecione ![configurar ícone](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-4/forms/using/configure_icon.png) (Configurar).

   1. No campo Vincular referência, selecione **Candidato** > **Nome** e toque no ícone ![](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-4/forms/using/chart-component/Done_Icon.png) concluído para salvar as propriedades. Da mesma forma, crie um vínculo de dados para o **Endereço**, Número **de** telefone, **Email**, **Ocupação**, Salário **Anual (em dólares)****e Número de. de campos de membros** da família dependentes com as entidades do modelo de dados do formulário.
   ![Vincular referências](assets/bind_references.png)

1. Toque em **[!UICONTROL Preview]** para exibir os valores de campo de formulário adaptável pré-preenchido.
1. Modifique os valores de campo, se necessário, e envie o formulário adaptável. Os valores de campo são submetidos ao banco de dados MySQL. É possível atualizar a tabela **candidato** no banco de dados para exibir os valores atualizados na tabela.

**** Caso de uso: Você gera um formulário adaptável sem vínculo de dados usando o serviço de Conversão de formulários automatizada e configura o banco de dados MYSQL como a fonte de dados. Vincule os campos de formulário adaptáveis usando o editor de regras para preencher previamente os valores de campo. Modifique os valores de campo, se necessário, e envie dados para o repositório crx.

Execute as seguintes etapas para usar o editor [de](https://helpx.adobe.com/experience-manager/6-5/forms/using/rule-editor.html) regras para chamar o serviço de modelo de dados de formulário para vincular campos e valores de preenchimento prévio em um formulário adaptável:

1. Selecione o formulário **do aplicativo de empréstimo de** amostra na **[!UICONTROL output]** pasta e toque em **[!UICONTROL Edit]**.
1. Na **[!UICONTROL Content]** guia, toque no ícone de configuração:

   ![configurar contêiner de formulário](assets/configure_form_container.png)

   Na **[!UICONTROL Basic]** seção, selecione **[!UICONTROL Form Data Model Prefill service]** na lista **[!UICONTROL Prefill Service]** suspensa.

1. Toque na caixa de **[!UICONTROL Applicant Name]** texto e toque **[!UICONTROL Edit Rules]**.

   ![Editar regras para criar vínculos de dados](assets/edit_rules_bind_reference.png)

1. Toque **[!UICONTROL Create]** na página do Editor de regras.
1. Na **[!UICONTROL Rule Editor]** página:

   1. Selecione um estado para a caixa de texto Nome do Candidato. Por exemplo, **[!UICONTROL is initialized]**, o que resulta na execução da **[!UICONTROL Then]** condição ao renderizar o formulário no **[!UICONTROL Preview]** modo.

   1. Na **[!UICONTROL Then]** seção, selecione **[!UICONTROL Invoke Service]** na lista **[!UICONTROL Select Action]** suspensa. Todos os serviços em sua instância do Forms são exibidos na lista suspensa.

   1. Selecione um **[!UICONTROL Get]** serviço na seção que lista os modelos de dados do formulário. O campo Entrada exibe o **número do telefone**, que é a chave primária definida para o modelo de dados do **candidato** . O sistema recupera e preenche previamente os valores no formulário adaptável para campos na seção Saída com base nesse campo.

   1. Crie um vínculo para os campos de formulário adaptáveis com as entidades do modelo de dados de formulário usando a seção Saída. Por exemplo, vincule o campo de formulário **[!UICONTROL Applicant Name]** adaptável à entidade **name** .

   1. Tocar **[!UICONTROL Done]**. Toque **[!UICONTROL Done]** novamente na página do Editor de regras.
   ![Editor de regras para vincular referências](assets/rule_editor_bind_references.png)

1. Toque em **[!UICONTROL Preview]** para exibir os valores de campo de formulário adaptável pré-preenchido.

   >[!NOTE]
   >
   >Verifique se a **[!UICONTROL Return Array]** Propriedade está definida como OFF para a propriedade **get** service no modelo de dados de formulário associado ao formulário adaptável.

1. Modifique os valores de campo, se necessário, e envie o formulário adaptável. Os dados enviados estão disponíveis no seguinte local no repositório crx:

   `http://host name:port/crx/de/index.jsp#/content/forms/fp/admin/submit/data/latest file available in the folder`

### Usar esquema JSON como fonte de dados {#jsondatasource}

**** Caso de uso: Você gera um formulário adaptável sem vínculo de dados usando o serviço de Conversão de formulários automatizados e configura o esquema JSON como a fonte de dados. Vincule os campos de formulário adaptáveis ao esquema JSON manualmente e use a opção **Visualizar com dados** para preencher previamente os valores de campo. Modifique os valores de campo, se necessário, e envie dados para o repositório crx.

Antes de executar o caso de uso, verifique se você:

* [um esquema JSON válido compatível com a estrutura do esquema JSON](#prepare-data-for-form-model)
* [um formulário adaptável sem vínculo de dados](#generate-adaptive-forms-with-no-data-binding)

Execute as seguintes etapas:

1. Selecione o formulário **do aplicativo de empréstimo de** amostra convertido disponível na pasta de **saída** e toque em **[!UICONTROL Properties]**.
1. Toque na **[!UICONTROL Form Model]** guia, selecione **[!UICONTROL Schema]** na lista **[!UICONTROL Select From]** suspensa e toque **[!UICONTROL Select Schema]** para fazer upload do esquema **demo.schema JSON** salvo no sistema de arquivos local. Toque em **[!UICONTROL Save & Close]** para salvar o formulário.
1. Selecione o formulário **de solicitação de empréstimo de** amostra e toque em **[!UICONTROL Edit]**.
1. Toque na caixa de texto Nome do candidato e selecione ![configurar ícone](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-4/forms/using/configure_icon.png) (Configurar).

   No campo Vincular referência, selecione **Candidato** > **Nome** e toque no ícone ![](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-4/forms/using/chart-component/Done_Icon.png) concluído para salvar as propriedades. Da mesma forma, crie um vínculo de dados para o **Endereço**, Número **de** telefone, **Email**, **Ocupação**, Salário **Anual (em dólares)****e Número de. dos campos de membros** da família dependentes com as entidades do esquema JSON.

1. Selecione novamente o formulário **do aplicativo de empréstimo de** amostra convertido disponível na **[!UICONTROL output]** pasta e selecione **[!UICONTROL Preview]** > **[!UICONTROL Preview with Data]**.</br>

   Baixar arquivo de dados de amostra</br>

   [Obter arquivo](assets/json_data_file.txt)</br>

1. Modifique os valores de campo, se necessário, e envie o formulário adaptável. Os dados enviados estão disponíveis no seguinte local no repositório crx:

   `http://host name:port/crx/de/index.jsp#/content/forms/fp/admin/submit/data/latest file available in the folder`

### Usar esquema XSD como fonte de dados {#xsddatasource}

**** Caso de uso: Você gera um formulário adaptável sem vínculo de dados usando o serviço de Conversão de formulários automatizados e configura o esquema XSD como a fonte de dados. Vincule os campos de formulário adaptáveis ao esquema XSD manualmente e use a opção **Visualizar com dados** para preencher previamente os valores de campo. Modifique os valores de campo, se necessário, e envie dados para o repositório crx.

Antes de executar o caso de uso, verifique se você:

* [um esquema XSD válido compatível com a estrutura do esquema XML](#prepare-data-for-form-model)
* [um formulário adaptável sem vínculo de dados](#generate-adaptive-forms-with-no-data-binding)

Execute as seguintes etapas:

1. Selecione o formulário **do aplicativo de empréstimo de** amostra convertido disponível na **[!UICONTROL output]** pasta e toque em **[!UICONTROL Properties]**.
1. Toque na **[!UICONTROL Form Model]** guia, selecione **[!UICONTROL Schema]** na lista **[!UICONTROL Select From]** suspensa e toque **[!UICONTROL Select Schema]** para fazer upload do esquema XSD do **aplicativo** de empréstimo salvo no sistema de arquivos local. Selecione o elemento raiz para o esquema XSD e toque **[!UICONTROL Save & Close]** para salvar o formulário.
1. Selecione o formulário **de solicitação de empréstimo de** amostra e toque em **[!UICONTROL Edit]**.
1. Toque na caixa de texto Nome do candidato e selecione ![configurar ícone](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-4/forms/using/configure_icon.png) (Configurar).
No campo Vincular referência, selecione **Candidato** > **Nome** e toque em Ícone ![](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-4/forms/using/chart-component/Done_Icon.png) Concluído para salvar as propriedades. Da mesma forma, crie um vínculo de dados para o **Endereço**, Número **de** telefone, **Email**, **Ocupação**, Salário **Anual (em dólares)****e Número de. de campos de membros** da família dependentes com as entidades de esquema XSD.

1. Selecione novamente o formulário **do aplicativo de empréstimo de** amostra convertido disponível na pasta de **saída** e selecione **[!UICONTROL Preview]** > **[!UICONTROL Preview with Data]**.</br>

   Baixar arquivo de dados de amostra</br>

   [Obter arquivo](assets/loan-application-data-xml-data.zip)</br>


1. Modifique os valores de campo, se necessário, e envie o formulário adaptável. Os dados enviados estão disponíveis no seguinte local no repositório crx:

   `http://host name:port/crx/de/index.jsp#/content/forms/fp/admin/submit/data/latest file available in the folder`

## Gerar formulários adaptáveis com vínculo JSON {#generate-adaptive-forms-with-json-binding}

Use o serviço de Conversão de formulários [automatizados para converter](convert-existing-forms-to-adaptive-forms.md) o formulário [de aplicativo de empréstimo de](#sample-adaptive-form) amostra em um formulário adaptável com vínculo de dados. Certifique-se de não marcar a caixa de **[!UICONTROL Generate adaptive form(s) without data bindings]** seleção ao gerar o formulário adaptável.

![Formulário adaptável com vínculo JSON](assets/generate_af_with_data_bindings.png)

### Usar esquema JSON como fonte de dados {#jsonwithdatabinding}

**** Caso de uso: Você gera um formulário adaptável com vínculo de dados JSON usando o serviço de Conversão de formulários automatizados. O serviço de preenchimento prévio e a função de envio de formulário funcionam perfeitamente. Você não precisa de nenhuma etapa de configuração.

Antes de executar o caso de uso, verifique se você tem [um formulário adaptável com vínculo](#generate-adaptive-forms-with-json-binding)de dados.

Execute as seguintes etapas:

1. Selecione novamente o formulário **do aplicativo de empréstimo de** amostra convertido disponível na **[!UICONTROL output]** pasta e selecione **[!UICONTROL Preview]** > **[!UICONTROL Preview with Data]**.</br>

   Baixar arquivo de dados de amostra</br>

   [Obter arquivo](assets/loan_application_data_source_json_data_binding.txt)</br>

1. Modifique os valores de campo, se necessário, e envie o formulário adaptável. Os dados enviados estão disponíveis no seguinte local no repositório crx:

   `http://host name:port/crx/de/index.jsp#/content/forms/fp/admin/submit/data/latest file available in the folder`

## Converter dados JSON de formulário adaptável enviados para o formato XML {#convert-submitted-adaptive-form-data-to-xml}

Quando você insere valores em campos de formulário adaptáveis e os envia, os dados ficam disponíveis no formato JSON no repositório crx. Você pode converter o formato de dados JSON em XML usando a API [org.apache.sling.commons.json.xml](https://sling.apache.org/apidocs/sling5/org/apache/sling/commons/json/xml/XML.html#toString) ou o seguinte código de amostra:

```
import org.apache.sling.commons.json.JSONException;
import org.apache.sling.commons.json.JSONObject;
import org.apache.sling.commons.json.xml.XML;
 
public class ConversionUtils {
 
    public static String jsonToXML(String jsonString) throws JSONException {
        //https://sling.apache.org/apidocs/sling5/org/apache/sling/commons/json/xml/XML.html#toString(java.lang.Object)
        //jar - http://maven.ibiblio.org/maven2/org/apache/sling/org.apache.sling.commons.json/2.0.18/
        //Note: Need to extract boundData part before converting to XML
        return XML.toString(new JSONObject(jsonString));
    }
}
```
