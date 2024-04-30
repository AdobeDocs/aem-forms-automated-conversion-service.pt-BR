---
title: Preenchimento e fluxos de trabalho recomendados com base na fonte de dados para formulários adaptáveis
description: Preenchimento e fluxos de trabalho baseados em fonte de dados para formulários adaptáveis gerados usando o Serviço de Automated forms conversion (AFCS).
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Administration
topic-tags: forms
role: Admin, Developer
level: Beginner, Intermediate
contentOwner: khsingh
exl-id: 5deef8f5-5098-47c1-b696-b2db59e92931
source-git-commit: c2392932d1e29876f7a11bd856e770b8f7ce3181
workflow-type: tm+mt
source-wordcount: '2397'
ht-degree: 1%

---

# Preenchimento e fluxos de trabalho recomendados com base na fonte de dados para formulários adaptáveis {#recommended-data-source-btased-prefill-and-submit-workflows-for-adaptive-forms}

Você pode usar qualquer uma das seguintes fontes de dados com formulários adaptáveis convertidos usando o serviço do Automated forms conversion (AFCS):

* Modelo de dados de formulário, OData ou qualquer outro serviço de terceiros
* Esquema JSON
* Esquema XSD

Com base na fonte de dados, você pode optar por gerar um formulário adaptável com ou sem um modelo de dados.

Este artigo descreve os fluxos de trabalho recomendados para preencher previamente os valores dos campos e as opções de envio após selecionar uma fonte de dados e gerar um formulário adaptável usando o serviço de conversão.

<table> 
 <tbody> 
  <tr> 
   <th><strong>Fonte de Dados</strong></th> 
   <th><strong>Fluxo de trabalho recomendado</strong></th> 
  </tr> 
  <tr> 
   <td><p>Modelo de dados de formulário, OData ou qualquer outro serviço de terceiros</p></td> 
   <td> 
    <p><strong>Opção 1</strong>: Você seleciona modelo de dados de formulário, OData ou qualquer outro serviço de terceiros como a fonte de dados. Você <a href="#generate-adaptive-forms-with-no-data-binding">gerar um formulário adaptável sem associação de dados</a> usando o serviço Automated forms conversion (AFCS). Você vincula os campos de formulário adaptáveis a entidades de modelo de dados de formulário manualmente e usa a opção Serviço de preenchimento prévio do modelo de dados de formulário para preencher previamente os valores de campo. Use a opção Enviar usando modelo de dados de formulário para enviar o formulário adaptável.</p></td> 
  </tr>
  <tr> 
   <td></td> 
   <td> 
   <p><strong>Opção 2</strong>: Você seleciona modelo de dados de formulário, OData ou qualquer outro serviço de terceiros como a fonte de dados. Você <a href="#generate-adaptive-forms-with-no-data-binding">gerar um formulário adaptável sem associação de dados</a> usando o serviço Automated forms conversion (AFCS). Você vincula os campos de formulário adaptáveis usando o editor de regras para preencher previamente os valores dos campos. Modifique os valores de campo, se necessário, e envie dados para o repositório crx.</p>
    </td> 
  </tr>
  <tr> 
   <td></td> 
   <td> 
    <p>Para obter instruções passo a passo sobre como executar esses workflows, consulte <a href="#sqldatasource">Use banco de dados, OData ou qualquer serviço de terceiros como fonte de dados.</a></p> </td> 
  </tr>
  <tr>
  <td><p>Esquema JSON</p></td> 
   <td> 
    <p>Selecione Esquema JSON como fonte de dados. Com base na fonte de dados selecionada:</p></td> 
  </tr>
  <tr>
  <td></td> 
   <td> 
    <p><strong>Opção 1</strong>: Você <a href="#generate-adaptive-forms-with-no-data-binding">gerar um formulário adaptável sem associação de dados</a> usando o serviço do Automated forms conversion (AFCS) e configure o esquema JSON como a fonte de dados. Você vincula os campos de formulário adaptáveis ao esquema JSON manualmente e <a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/prepopulate-adaptive-form-fields.html#Supportedprotocolsforprefillinguserdata" target="_blank">use qualquer um dos protocolos compatíveis</a> para preencher previamente os valores do campo. Modifique os valores de campo, se necessário, e envie dados para o repositório crx.</p></td> 
  </tr>
  <tr>
  <td></td> 
   <td> 
    <p>Para obter instruções passo a passo sobre como executar os workflows, consulte <a href="#jsondatasource">Use o esquema JSON como a fonte de dados.</p></td> 
  </tr>
  <tr>
  <td></td> 
   <td> 
    <p><strong>Opção 2</strong>: Você <a href="#generate-adaptive-forms-with-json-binding">gerar um formulário adaptável com vinculação de dados JSON</a> usando o serviço Automated forms conversion (AFCS). O serviço de preenchimento prévio e o envio de formulário funcionam perfeitamente. Você não precisa de nenhuma etapa de configuração.</p> </td> 
  </tr>
   <tr>
  <td></td> 
   <td> 
    <p>Para obter instruções passo a passo sobre como executar os workflows, consulte <a href="#jsonwithdatabinding">Use o esquema JSON como a fonte de dados.</a></p> </td> 
  </tr>
  <tr>
  <td><p>Esquema XSD</p></td> 
   <td> 
    <p>Selecione Esquema XSD como fonte de dados. Com base na fonte de dados selecionada, você <a href="#generate-adaptive-forms-with-no-data-binding">gerar um formulário adaptável sem associação de dados</a> usando o serviço do Automated forms conversion (AFCS) e configure o esquema XSD como a fonte de dados. Você vincula os campos de formulário adaptáveis ao esquema XSD manualmente e <a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/prepopulate-adaptive-form-fields.html#Supportedprotocolsforprefillinguserdata" target="_blank">use qualquer um dos protocolos compatíveis</a> para preencher previamente os valores do campo. Modifique os valores de campo, se necessário, e envie dados para o repositório crx.</p>
    </td> 
  </tr>
  <tr>
  <td></td> 
   <td> 
    <p>Para obter instruções passo a passo sobre como executar os workflows, consulte <a href="#xsddatasource">Use o esquema XSD como a fonte de dados.</a></p>
    </td> 
  </tr>
 </tbody> 
</table>


Para obter mais informações sobre o serviço Automated forms conversion (AFCS), consulte os seguintes artigos:

* [Introdução ao serviço do Automated forms conversion](introduction.md)
* [Configurar o serviço Automated forms conversion](configure-service.md)
* [Converter formulários impressos em formulários adaptáveis](convert-existing-forms-to-adaptive-forms.md)
* [Revisar e corrigir formulários convertidos](review-correct-ui-edited.md)

As informações fornecidas neste artigo baseiam-se no pressuposto de que qualquer pessoa que as leia tem conhecimento básico dos conceitos de formulários adaptáveis.

## Pré-requisitos {#pre-requisites}

* Configurar um [Instância de autor AEM](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/deploy.html)
* Configurar [Serviço Automated forms conversion (AFCS) na instância de autor AEM](configure-service.md)

## Exemplo de formulário adaptável {#sample-adaptive-form}

Para executar os casos de uso para preencher previamente os valores de campo em um formulário adaptável e enviá-los à fonte de dados, baixe o seguinte arquivo de PDF de amostra.

Exemplo de formulário de pedido de empréstimo

[Obter arquivo](assets/sample_loan_application_form.pdf)

O arquivo PDF serve como entrada para o serviço de Automated forms conversion (AFCS). O serviço converte esse arquivo em um formulário adaptável. A imagem a seguir mostra o aplicativo de empréstimo de exemplo em formato PDF.

![exemplo de formulário de pedido de empréstimo](assets/sample_form_new.png)

## Preparar dados para o modelo de formulário {#prepare-data-for-form-model}

A Integração de dados do AEM Forms permite configurar e conectar-se a diferentes fontes de dados. Depois de gerar um formulário adaptável usando o processo de conversão, você pode definir o modelo de formulário com base em um modelo de dados de formulário, XSD ou um esquema JSON. Você pode usar um banco de dados, o Microsoft Dynamics ou qualquer outro serviço de terceiros para criar um modelo de dados de formulário.

Este tutorial usa o banco de dados MySQL como a fonte para criar um modelo de dados de formulário. Criar um **aplicativo de empréstimo** esquema no banco de dados e adicionar um **candidato** para o esquema com base nos campos disponíveis no formulário adaptável.

![Dados de exemplo mysql](assets/sample_data_mysql.png)

Você pode usar a seguinte instrução DDL para criar a **candidato** tabela no banco de dados.

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

Se você estiver usando um esquema XSD como o modelo de formulário para executar os casos de uso, crie um arquivo XSD com o seguinte texto:

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

Ou baixe o esquema XSD para o sistema de arquivos local.

Exemplo de esquema XSD de aplicativo de empréstimo

[Obter arquivo](assets/loanapplication.xsd)

Para obter mais informações sobre como usar o esquema XSD como modelo de formulário em formulários adaptáveis, consulte [Criação de formulários adaptáveis usando o esquema XML](https://helpx.adobe.com/experience-manager/6-5/forms/using/adaptive-form-xml-schema-form-model.html).

Se estiver usando um esquema JSON como modelo de formulário para executar os casos de uso, crie um arquivo JSON com o seguinte texto:

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

Esquema JSON do aplicativo de empréstimo de exemplo

[Obter arquivo](assets/demo_schema.json)

Para obter mais informações sobre como usar o esquema JSON como modelo de formulário em formulários adaptáveis, consulte [Criação de formulários adaptáveis usando o esquema JSON](https://helpx.adobe.com/experience-manager/6-5/forms/using/adaptive-form-json-schema-form-model.html).

## Gerar formulários adaptáveis sem associação de dados {#generate-adaptive-forms-with-no-data-binding}

Use o [Serviço Automated forms conversion a ser convertido](convert-existing-forms-to-adaptive-forms.md) o [exemplo de formulário de pedido de empréstimo](#sample-adaptive-form) para um formulário adaptável sem vínculo de dados. Certifique-se de selecionar a variável **[!UICONTROL Generate adaptive form(s) without data bindings]** para gerar o formulário adaptável sem vínculo de dados.

![Formulário adaptável sem vínculo de dados](assets/generate_af_without_binding.png)

Depois de gerar um formulário adaptável sem associação de dados, selecione uma fonte de dados para o formulário adaptável:

* [Banco de dados, OData ou qualquer serviço de terceiros](#sqldatasource)
* [Esquema JSON](#jsondatasource)
* [Esquema XSD](#xsddatasource)

>[!NOTE]
> Se o formulário adaptável convertido usando o serviço Automated forms conversion (AFCS) contiver vários campos com o mesmo nome, verifique se esses campos estão vinculados a entidades de fonte de dados para evitar uma possível perda de dados durante o envio.
>

### Usar banco de dados, OData ou qualquer serviço de terceiros como fonte de dados {#sqldatasource}

Caso de uso: você gera um formulário adaptável sem vínculo de dados usando o serviço do Automated forms conversion (AFCS) e configura o banco de dados MYSQL como a fonte de dados. Você vincula os campos de formulário adaptáveis a entidades de modelo de dados de formulário manualmente e usa o **[!UICONTROL Form Data Model Prefill Service]** opção para preencher previamente os valores do campo. Você usa o **[!UICONTROL Submit using Form Data Model]** opção para enviar o formulário adaptável.

Antes de executar o caso de uso:

* [Configurar o banco de dados MySQL como a fonte de dados](https://helpx.adobe.com/experience-manager/6-5/forms/using/configure-data-sources.html#configurerelationaldatabase)
* [Criar o modelo de dados do formulário](https://helpx.adobe.com/experience-manager/6-5/forms/using/work-with-form-data-model.html)

Com base no caso de uso, crie o **aplicativo de empréstimo** modelo de dados de formulário e vincular o argumento do serviço de leitura a um **[!UICONTROL Literal]** valor. O valor literal do número de telefone deve ser de um dos registros configurados no **candidato** esquema do banco de dados MySQL. Os serviços usam o valor como argumento para buscar detalhes da fonte de dados. Também é possível selecionar [Atributo de Perfil de Usuário ou Atributo de Solicitação](https://helpx.adobe.com/experience-manager/6-5/forms/using/work-with-form-data-model.html#bindargument) do **[!UICONTROL Binding To]** lista suspensa

![Configurar modelo de dados do formulário](assets/configure_model_object.png)

>[!NOTE]
>
>Adicione **obter** e **inserir** para o modelo de dados de formulário, configure e teste os serviços antes de executar o caso de uso.

Execute as seguintes etapas:

1. Selecione o convertido **exemplo de formulário de pedido de empréstimo** disponível no **[!UICONTROL output]** pasta e toque em **[!UICONTROL Properties]**.
1. Toque no **[!UICONTROL Form Model]** selecione **[!UICONTROL Form Data Model]** do **[!UICONTROL Select From]** e toque em **[!UICONTROL Select Form Data Model]** para selecionar o **aplicativo de empréstimo** modelo de dados de formulário. Toque **[!UICONTROL Save & Close]** para salvar o formulário.
1. Selecione o **exemplo de formulário de pedido de empréstimo** e toque em **[!UICONTROL Edit]**.
1. No **[!UICONTROL Content]** toque no ícone configurar:

   ![configurar contêiner de formulário](assets/configure_form_container.png)

   1. No **[!UICONTROL Basic]** , selecione **[!UICONTROL Form Data Model Prefill service]** do **[!UICONTROL Prefill Service]** lista suspensa.

   1. No **[!UICONTROL Submission]** , selecione **[!UICONTROL Submit using Form Data Model]** do **[!UICONTROL Submit Action]** lista suspensa.

   1. Selecione o modelo de dados usando o **[!UICONTROL Data Model to submit]** campo.
   1. Toque ![ícone concluído](assets/save_icon.svg) para salvar as propriedades.

1. Toque na caixa de texto Nome do Candidato e selecione ![ícone de configuração](assets/configure_icon.svg) (Configurar).

   1. No campo Referência de vinculação, selecione **Candidato** > **Nome** e toque em ![ícone concluído](assets/save_icon.svg) para salvar as propriedades. Da mesma forma, crie uma vinculação de dados para o **Endereço**, **Número de telefone**, **E-mail**, **Ocupação**, **Salário Anual (em dólares)**, e **Não. de familiares dependentes** campos com as entidades do modelo de dados de formulário.

   ![Associar referências](assets/bind_references.png)

1. Toque **[!UICONTROL Preview]** para exibir os valores de campos de formulário adaptável preenchidos previamente.
1. Modifique os valores do campo, se necessário, e envie o formulário adaptável. Os valores de campo são enviados ao banco de dados MySQL. Você pode atualizar o **candidato** no banco de dados para exibir os valores atualizados na tabela.

**Caso de uso:** Você gera um formulário adaptável sem associação de dados usando o serviço Automated forms conversion (AFCS) e configura o banco de dados MYSQL como a fonte de dados. Você vincula os campos de formulário adaptáveis usando o editor de regras para preencher previamente os valores dos campos. Modifique os valores de campo, se necessário, e envie dados para o repositório crx.

Execute as seguintes etapas para usar [editor de regras](https://helpx.adobe.com/experience-manager/6-5/forms/using/rule-editor.html) para chamar o serviço de modelo de dados de formulário para vincular campos e preencher previamente valores em um formulário adaptável:

1. Selecione o **exemplo de formulário de pedido de empréstimo** no **[!UICONTROL output]** pasta e toque em **[!UICONTROL Edit]**.
1. No **[!UICONTROL Content]** toque no ícone configurar:

   ![configurar contêiner de formulário](assets/configure_form_container.png)

   No **[!UICONTROL Basic]** , selecione **[!UICONTROL Form Data Model Prefill service]** do **[!UICONTROL Prefill Service]** lista suspensa.

1. Toque no **[!UICONTROL Applicant Name]** caixa de texto e toque **[!UICONTROL Edit Rules]**.

   ![Editar regras para criar associação de dados](assets/edit_rules_bind_reference.png)

1. Toque **[!UICONTROL Create]** na página Editor de regras.
1. No **[!UICONTROL Rule Editor]** página:

   1. Selecione um estado para a caixa de texto Nome do Candidato. Por exemplo, **[!UICONTROL is initialized]**, que resulta na execução da **[!UICONTROL Then]** quando você renderiza o formulário em **[!UICONTROL Preview]** modo.

   1. No **[!UICONTROL Then]** , selecione **[!UICONTROL Invoke Service]** do **[!UICONTROL Select Action]** lista suspensa. Todos os serviços na instância do Forms são exibidos na lista suspensa.

   1. Selecione um **[!UICONTROL Get]** serviço na seção que lista os modelos de dados de formulário. O campo Entrada é exibido **phonenumber**, que é a chave primária definida para o **candidato** modelo de dados. O sistema recupera e preenche os valores no formulário adaptável para campos na seção Saída com base nesse campo.

   1. Crie uma associação para os campos de formulário adaptáveis com as entidades de modelo de dados de formulário usando a seção Saída. Por exemplo, vincular **[!UICONTROL Applicant Name]** campo de formulário adaptável com a variável **name** entidade.

   1. Toque **[!UICONTROL Done]**. Toque **[!UICONTROL Done]** novamente na página Editor de regras.

   ![Editor de regras para vincular referências](assets/rule_editor_bind_references.png)

1. Toque **[!UICONTROL Preview]** para exibir os valores de campos de formulário adaptável preenchidos previamente.

   >[!NOTE]
   >
   >Certifique-se de que o **[!UICONTROL Return Array]** A propriedade está definida como OFF para o **obter** propriedade de serviço no modelo de dados de formulário associado ao formulário adaptável.

1. Modifique os valores do campo, se necessário, e envie o formulário adaptável. Os dados enviados estão disponíveis no seguinte local no repositório crx:

   `http://host name:port/crx/de/index.jsp#/content/forms/fp/admin/submit/data/latest file available in the folder`

### Usar esquema JSON como fonte de dados {#jsondatasource}

**Caso de uso:** Você gera um formulário adaptável sem associação de dados usando o serviço do Automated forms conversion (AFCS) e configura o esquema JSON como a fonte de dados. Você vincula os campos de formulário adaptáveis ao esquema JSON manualmente e usa o **Visualizar com dados** opção para preencher previamente os valores do campo. Modifique os valores de campo, se necessário, e envie dados para o repositório crx.

Antes de executar o caso de uso, verifique se você:

* [um esquema JSON válido compatível com a estrutura do esquema JSON](#prepare-data-for-form-model)
* [um formulário adaptável sem vínculo de dados](#generate-adaptive-forms-with-no-data-binding)

Execute as seguintes etapas:

1. Selecione o convertido **exemplo de formulário de pedido de empréstimo** disponível no **saída** pasta e toque em **[!UICONTROL Properties]**.
1. Toque no **[!UICONTROL Form Model]** selecione **[!UICONTROL Schema]** do **[!UICONTROL Select From]** e toque em **[!UICONTROL Select Schema]** para fazer upload do **demo.schema JSON** esquema salvo no sistema de arquivos local. Toque **[!UICONTROL Save & Close]** para salvar o formulário.
1. Selecione o **exemplo de formulário de pedido de empréstimo** e toque em **[!UICONTROL Edit]**.
1. Toque na caixa de texto Nome do Candidato e selecione ![ícone de configuração](assets/configure_icon.svg) (Configurar).

   No campo Referência de vinculação, selecione **Candidato** > **Nome** e toque em ![ícone concluído](assets/save_icon.svg) para salvar as propriedades. Da mesma forma, crie uma vinculação de dados para o **Endereço**, **Número de telefone**, **E-mail**, **Ocupação**, **Salário Anual (em dólares)**, e **Não. de familiares dependentes** campos com as entidades do esquema JSON.

1. Selecione o convertido **exemplo de formulário de pedido de empréstimo** disponível no **[!UICONTROL output]** pasta novamente e selecione **[!UICONTROL Preview]** > **[!UICONTROL Preview with Data]**.</br>

   Baixar arquivo de dados de amostra</br>

   [Obter arquivo](assets/json_data_file.txt)</br>

1. Modifique os valores do campo, se necessário, e envie o formulário adaptável. Os dados enviados estão disponíveis no seguinte local no repositório crx:

   `http://host name:port/crx/de/index.jsp#/content/forms/fp/admin/submit/data/latest file available in the folder`

### Usar esquema XSD como fonte de dados {#xsddatasource}

**Caso de uso:** Você gera um formulário adaptável sem associação de dados usando o serviço do Automated forms conversion (AFCS) e configura o esquema XSD como a fonte de dados. Você vincula os campos de formulário adaptáveis ao esquema XSD manualmente e usa o **Visualizar com dados** para preencher previamente os valores do campo. Modifique os valores de campo, se necessário, e envie dados para o repositório crx.

Antes de executar o caso de uso, verifique se você:

* [um esquema XSD válido compatível com a estrutura do esquema XML](#prepare-data-for-form-model)
* [um formulário adaptável sem vínculo de dados](#generate-adaptive-forms-with-no-data-binding)

Execute as seguintes etapas:

1. Selecione o convertido **exemplo de formulário de pedido de empréstimo** disponível no **[!UICONTROL output]** pasta e toque em **[!UICONTROL Properties]**.
1. Toque no **[!UICONTROL Form Model]** selecione **[!UICONTROL Schema]** do **[!UICONTROL Select From]** e toque em **[!UICONTROL Select Schema]** para fazer upload do **aplicativo de empréstimo** Esquema XSD salvo no sistema de arquivos local. Selecione o elemento raiz para o esquema XSD e toque em **[!UICONTROL Save & Close]** para salvar o formulário.
1. Selecione o **exemplo de formulário de pedido de empréstimo** e toque em **[!UICONTROL Edit]**.
1. Toque na caixa de texto Nome do Candidato e selecione ![ícone de configuração](assets/configure_icon.svg) (Configurar).
No campo Referência de vinculação, selecione **Candidato** > **Nome** e toque em ![Ícone Concluído](assets/save_icon.svg) para salvar as propriedades. Da mesma forma, crie uma vinculação de dados para o **Endereço**, **Número de telefone**, **E-mail**, **Ocupação**, **Salário Anual (em dólares)**, e **Não. de familiares dependentes** com as entidades do esquema XSD.

1. Selecione o convertido **exemplo de formulário de pedido de empréstimo** disponível no **saída** pasta novamente e selecione **[!UICONTROL Preview]** > **[!UICONTROL Preview with Data]**.</br>

   Baixar arquivo de dados de amostra</br>

   [Obter arquivo](assets/loan-application-data-xml-data.zip)</br>


1. Modifique os valores do campo, se necessário, e envie o formulário adaptável. Os dados enviados estão disponíveis no seguinte local no repositório crx:

   `http://host name:port/crx/de/index.jsp#/content/forms/fp/admin/submit/data/latest file available in the folder`

## Gerar formulários adaptáveis com vinculação JSON {#generate-adaptive-forms-with-json-binding}

Use o [Serviço do Automated forms conversion (AFCS) para conversão](convert-existing-forms-to-adaptive-forms.md) o [exemplo de formulário de pedido de empréstimo](#sample-adaptive-form) para um formulário adaptável com vinculação de dados. Certifique-se de não selecionar a opção **[!UICONTROL Generate adaptive form(s) without data bindings]** ao gerar o formulário adaptável.

![Formulário adaptável com vinculação JSON](assets/generate_af_with_data_bindings.png)

### Usar esquema JSON como fonte de dados {#jsonwithdatabinding}

**Caso de uso:** Você gera um formulário adaptável com vinculação de dados JSON usando o serviço do Automated forms conversion (AFCS). O serviço de preenchimento prévio e o envio de formulário funcionam perfeitamente. Você não precisa de nenhuma etapa de configuração.

Antes de executar o caso de uso, verifique se [um formulário adaptável com vínculo de dados](#generate-adaptive-forms-with-json-binding).

Execute as seguintes etapas:

1. Selecione o convertido **exemplo de formulário de pedido de empréstimo** disponível no **[!UICONTROL output]** pasta novamente e selecione **[!UICONTROL Preview]** > **[!UICONTROL Preview with Data]**.</br>

   Baixar arquivo de dados de amostra</br>

   [Obter arquivo](assets/loan_application_data_source_json_data_binding.txt)</br>

1. Modifique os valores do campo, se necessário, e envie o formulário adaptável. Os dados enviados estão disponíveis no seguinte local no repositório crx:

   `http://host name:port/crx/de/index.jsp#/content/forms/fp/admin/submit/data/latest file available in the folder`

## Converter dados JSON do formulário adaptável enviado para o formato XML {#convert-submitted-adaptive-form-data-to-xml}

Quando você insere valores em campos de formulário adaptável e os envia, os dados são disponibilizados no formato JSON no repositório crx. É possível converter o formato dos dados JSON em XML usando [org.apache.sling.commons.json.xml](https://sling.apache.org/apidocs/sling5/org/apache/sling/commons/json/xml/XML.html#toString) ou o seguinte código de exemplo:

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
