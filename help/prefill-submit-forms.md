---
title: Preenchimento e fluxos de trabalho recomendados com base na fonte de dados para formulários adaptáveis
seo-title: Opções de preenchimento prévio e envio para formulários adaptáveis
description: Workflows de pré-preenchimento e envio baseados na fonte de dados para formulários adaptáveis gerados usando o Serviço de Automated forms conversion.
seo-description: Workflows de pré-preenchimento e envio baseados na fonte de dados para formulários adaptáveis gerados usando o Serviço de Automated forms conversion.
uuid: 91409a82-141c-4233-82b1-1539a0b250f8
contentOwner: khsingh
topic-tags: forms
discoiquuid: cad34fff-7f9f-4a27-8b5c-d0a523903eec
privatebeta: true
translation-type: tm+mt
source-git-commit: caccb547a5741eb0e70ddf75630a661f8fe75cb3
workflow-type: tm+mt
source-wordcount: '2459'
ht-degree: 1%

---


# Preenchimento e fluxos de trabalho recomendados com base na fonte de dados para formulários adaptáveis {#recommended-data-source-btased-prefill-and-submit-workflows-for-adaptive-forms}

É possível usar qualquer uma das seguintes fontes de dados com formulários adaptáveis convertidos usando o serviço de Automated forms conversion:

* Modelo de dados de formulário, OData ou qualquer outro serviço de terceiros
* Schema JSON
* Schema XSD

Com base na fonte de dados, você pode optar por gerar um formulário adaptável com ou sem um modelo de dados.

Este artigo descreve os workflows recomendados para preencher previamente os valores de campo e as opções de envio depois de selecionar uma fonte de dados e gerar um formulário adaptável usando o serviço de conversão.

<table> 
 <tbody> 
  <tr> 
   <th><strong>Fonte de Dados</strong></th> 
   <th><strong>Fluxo de trabalho recomendado</strong></th> 
  </tr> 
  <tr> 
   <td><p>Modelo de dados de formulário, OData ou qualquer outro serviço de terceiros</p></td> 
   <td> 
    <p><strong>Opção 1</strong>: Você seleciona o modelo de dados de formulário, OData ou qualquer outro serviço de terceiros como a fonte de dados. Você <a href="#generate-adaptive-forms-with-no-data-binding">gera um formulário adaptável sem vínculo de dados</a> usando o serviço de Automated forms conversion. Vincule os campos de formulário adaptáveis às entidades do modelo de dados manualmente e use a opção Serviço de preenchimento prévio do modelo de dados de formulário para preencher previamente os valores de campo. Use a opção Enviar usando o Modelo de dados de formulário para enviar o formulário adaptável.</p></td> 
  </tr>
  <tr> 
   <td></td> 
   <td> 
   <p><strong>Opção 2</strong>: Você seleciona o modelo de dados de formulário, OData ou qualquer outro serviço de terceiros como a fonte de dados. Você <a href="#generate-adaptive-forms-with-no-data-binding">gera um formulário adaptável sem vínculo de dados</a> usando o serviço de Automated forms conversion. Vincule os campos de formulário adaptáveis usando o editor de regras para preencher previamente os valores de campo. Modifique os valores de campo, se necessário, e envie dados para o repositório crx.</p>
    </td> 
  </tr>
  <tr> 
   <td></td> 
   <td> 
    <p>Para obter instruções passo a passo para executar esses workflows, consulte <a href="#sqldatasource">Usar banco de dados, OData ou qualquer serviço de terceiros como a fonte de dados.</a></p> </td> 
  </tr>
  <tr>
  <td><p>Schema JSON</p></td> 
   <td> 
    <p>Você seleciona schema JSON como a fonte de dados. Com base na fonte de dados selecionada:</p></td> 
  </tr>
  <tr>
  <td></td> 
   <td> 
    <p><strong>Opção 1</strong>: Você  <a href="#generate-adaptive-forms-with-no-data-binding">gera um formulário adaptável sem </a> vínculo de dados usando o serviço de Automated forms conversion e configura o schema JSON como a fonte de dados. Vincule os campos de formulário adaptáveis ao schema JSON manualmente e <a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/prepopulate-adaptive-form-fields.html#Supportedprotocolsforprefillinguserdata" target="_blank">use qualquer um dos protocolos suportados</a> para preencher os valores de campo antecipadamente. Modifique os valores de campo, se necessário, e envie dados para o repositório crx.</p></td> 
  </tr>
  <tr>
  <td></td> 
   <td> 
    <p>Para obter instruções passo a passo para executar os workflows, consulte <a href="#jsondatasource">Usar o schema JSON como a fonte de dados.</p></td> 
  </tr>
  <tr>
  <td></td> 
   <td> 
    <p><strong>Opção 2</strong>: Você  <a href="#generate-adaptive-forms-with-json-binding">gera um formulário adaptável com </a> vínculo de dados JSON usando o serviço de Automated forms conversion. O serviço de preenchimento prévio e a função de envio de formulário funcionam perfeitamente. Você não precisa de nenhuma etapa de configuração.</p> </td> 
  </tr>
   <tr>
  <td></td> 
   <td> 
    <p>Para obter instruções passo a passo para executar os workflows, consulte <a href="#jsonwithdatabinding">Usar o schema JSON como a fonte de dados.</a></p> </td> 
  </tr>
  <tr>
  <td><p>Schema XSD</p></td> 
   <td> 
    <p>Você seleciona schema XSD como a fonte de dados. Com base na fonte de dados selecionada, você <a href="#generate-adaptive-forms-with-no-data-binding">gera um formulário adaptável sem vínculo de dados</a> usando o serviço de Automated forms conversion e configura o schema XSD como a fonte de dados. Vincule os campos de formulário adaptáveis ao schema XSD manualmente e <a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/prepopulate-adaptive-form-fields.html#Supportedprotocolsforprefillinguserdata" target="_blank">use qualquer um dos protocolos suportados</a> para preencher os valores de campo antecipadamente. Modifique os valores de campo, se necessário, e envie dados para o repositório crx.</p>
    </td> 
  </tr>
  <tr>
  <td></td> 
   <td> 
    <p>Para obter instruções passo a passo para executar os workflows, consulte <a href="#xsddatasource">Usar o schema XSD como a fonte de dados.</a></p>
    </td> 
  </tr>
 </tbody> 
</table>


Para obter mais informações sobre o serviço de Automated forms conversion, consulte os seguintes artigos:

* [Introdução ao serviço de conversão automática de formulários](introduction.md)
* [Configurar o serviço de conversão automática de formulários](configure-service.md)
* [Converter formulários impressos em formulários adaptáveis](convert-existing-forms-to-adaptive-forms.md)
* [Revisar e corrigir formulários convertidos](review-correct-ui-edited.md)

As informações fornecidas neste artigo baseiam-se no pressuposto de que qualquer pessoa que as leia tem conhecimento básico dos conceitos de formas adaptativas.

## Pré-requisitos {#pre-requisites}

* Configurar uma instância do autor [AEM](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/deploy.html)
* Configure [o serviço de Automated forms conversion na instância do autor AEM](configure-service.md)

## Exemplo de formulário adaptável {#sample-adaptive-form}

Para executar os casos de uso para preencher previamente valores de campo em um formulário adaptável e enviá-los para a fonte de dados, baixe o arquivo PDF de amostra a seguir.

Formulário de pedido de empréstimo de amostra

[Obter arquivo](assets/sample_loan_application_form.pdf)

O arquivo PDF serve como entrada para o serviço do Automated forms conversion. O serviço converte esse arquivo em um formulário adaptável. A imagem a seguir descreve o aplicativo de empréstimo de amostra em um formato PDF.

![formulário de pedido de empréstimo de amostra](assets/sample_form_new.png)

## Preparar dados para o modelo de formulário {#prepare-data-for-form-model}

A Integração de dados da AEM Forms permite que você configure e conecte-se a fontes de dados diferentes. Depois de gerar um formulário adaptável usando o processo de conversão, você pode definir o modelo de formulário com base em um modelo de dados de formulário, XSD ou um schema JSON. Você pode usar um banco de dados, o Microsoft Dynamics ou qualquer outro serviço de terceiros para criar um modelo de dados de formulário.

Este tutorial usa o banco de dados MySQL como a fonte para criar um modelo de dados de formulário. Crie um schema **loanapplication** no banco de dados e adicione uma tabela **candidato** ao schema com base nos campos disponíveis no formulário adaptável.

![Dados de amostra mysql](assets/sample_data_mysql.png)

Você pode usar a seguinte instrução DDL para criar a tabela **candidato** no banco de dados.

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

Se você estiver usando um schema XSD como modelo de formulário para executar os casos de uso, crie um arquivo XSD com o seguinte texto:

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

Ou baixe o schema XSD no sistema de arquivos local.

Schema XSD do aplicativo de empréstimo de amostra

[Obter arquivo](assets/loanapplication.xsd)

Para obter mais informações sobre como usar o schema XSD como modelo de formulário em formulários adaptáveis, consulte [Criar formulários adaptáveis usando o schema XML](https://helpx.adobe.com/experience-manager/6-5/forms/using/adaptive-form-xml-schema-form-model.html).

Se você estiver usando um schema JSON como o modelo de formulário para executar os casos de uso, crie um arquivo JSON com o seguinte texto:

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

Ou baixe o schema JSON no sistema de arquivos local.

Amostra de schema JSON

[Obter arquivo](assets/demo_schema.json)

Para obter mais informações sobre como usar o schema JSON como modelo de formulário em formulários adaptáveis, consulte [Criar formulários adaptáveis usando o schema JSON](https://helpx.adobe.com/experience-manager/6-5/forms/using/adaptive-form-json-schema-form-model.html).

## Gerar formulários adaptáveis sem vínculo de dados {#generate-adaptive-forms-with-no-data-binding}

Use o serviço de [Automated forms conversion para converter](convert-existing-forms-to-adaptive-forms.md) o [formulário de aplicação de empréstimo de exemplo](#sample-adaptive-form) para um formulário adaptável sem vínculo de dados. Certifique-se de marcar a caixa de seleção **[!UICONTROL Generate adaptive form(s) without data bindings]** para gerar o formulário adaptável sem vínculo de dados.

![Formulário adaptável sem vínculo de dados](assets/generate_af_without_binding.png)

Depois de gerar um formulário adaptável sem vínculo de dados, selecione uma fonte de dados para o formulário adaptável:

* [Banco de dados, OData ou qualquer serviço de terceiros](#sqldatasource)
* [Schema JSON](#jsondatasource)
* [Schema XSD](#xsddatasource)

>[!NOTE]
> Se o formulário adaptável que você converte usando o serviço de Automated forms conversion contiver vários campos com o mesmo nome, verifique se esses campos estão vinculados a entidades de fonte de dados para evitar uma possível perda de dados durante o envio.


### Usar banco de dados, OData ou qualquer serviço de terceiros como a fonte de dados {#sqldatasource}

Caso de uso: Você gera um formulário adaptável sem vínculo de dados usando o serviço de Automated forms conversion e configura o banco de dados MYSQL como a fonte de dados. Vincule os campos de formulário adaptáveis às entidades do modelo de dados manualmente e use a opção **[!UICONTROL Form Data Model Prefill Service]** para preencher previamente os valores de campo. Use a opção **[!UICONTROL Submit using Form Data Model]** para enviar o formulário adaptável.

Antes de executar o caso de uso:

* [Configurar o banco de dados MySQL como a fonte de dados](https://helpx.adobe.com/experience-manager/6-5/forms/using/configure-data-sources.html#configurerelationaldatabase)
* [Criar o modelo de dados de formulário](https://helpx.adobe.com/experience-manager/6-5/forms/using/work-with-form-data-model.html)

Com base no caso de uso, crie o modelo de dados de formulário **loanapplication** e vincule o argumento de serviço de leitura a um valor **[!UICONTROL Literal]**. O valor literal de número de telefone deve ser de um dos registros configurados no schema **candidato** do banco de dados MySQL. Os serviços usam o valor como um argumento para buscar detalhes da fonte de dados. Você também pode selecionar [Atributo do Perfil do usuário ou Atributo de solicitação](https://helpx.adobe.com/experience-manager/6-5/forms/using/work-with-form-data-model.html#bindargument) na lista suspensa **[!UICONTROL Binding To]**

![Configurar modelo de dados de formulário](assets/configure_model_object.png)

>[!NOTE]
>
>Certifique-se de adicionar **get** e **inserir** serviços ao modelo de dados de formulário, configurar e testar os serviços antes de executar o caso de uso.

Execute as seguintes etapas:

1. Selecione o **formulário de aplicação de empréstimo de amostra** convertido disponível na pasta **[!UICONTROL output]** e toque em **[!UICONTROL Properties]**.
1. Toque na guia **[!UICONTROL Form Model]**, selecione **[!UICONTROL Form Data Model]** na lista suspensa **[!UICONTROL Select From]** e toque em **[!UICONTROL Select Form Data Model]** para selecionar o modelo de dados de formulário **loanapplication**. Toque em **[!UICONTROL Save & Close]** para salvar o formulário.
1. Selecione o **formulário de aplicação de empréstimo de amostra** e toque em **[!UICONTROL Edit]**.
1. Na guia **[!UICONTROL Content]**, toque no ícone de configuração:

   ![configurar container de formulário](assets/configure_form_container.png)

   1. Na seção **[!UICONTROL Basic]**, selecione **[!UICONTROL Form Data Model Prefill service]** na lista suspensa **[!UICONTROL Prefill Service]**.

   1. Na seção **[!UICONTROL Submission]**, selecione **[!UICONTROL Submit using Form Data Model]** na lista suspensa **[!UICONTROL Submit Action]**.

   1. Selecione o modelo de dados usando o campo **[!UICONTROL Data Model to submit]**.
   1. Toque em ![ícone concluído](assets/save_icon.svg) para salvar as propriedades.

1. Toque na caixa de texto Nome do candidato e selecione ![ícone de configuração](assets/configure_icon.svg) (Configurar).

   1. No campo Vincular referência, selecione **Candidato** > **Nome** e toque em ![ícone concluído](assets/save_icon.svg) para salvar as propriedades. Da mesma forma, crie um vínculo de dados para **Endereço**, **Número de telefone**, **Email**, **Ocupação**, **Salário anual (em dólares)** e **Não. dos campos de membros da família dependentes** com as entidades do modelo de dados de formulário.

   ![Referências de vinculação](assets/bind_references.png)

1. Toque em **[!UICONTROL Preview]** para visualização os valores de campo de formulário adaptável pré-preenchido.
1. Modifique os valores de campo, se necessário, e envie o formulário adaptável. Os valores de campo são submetidos ao banco de dados MySQL. Você pode atualizar a tabela **candidato** no banco de dados para visualização dos valores atualizados na tabela.

**Caso de uso:** você gera um formulário adaptável sem vínculo de dados usando o serviço de Automated forms conversion e configura o banco de dados MYSQL como a fonte de dados. Vincule os campos de formulário adaptáveis usando o editor de regras para preencher previamente os valores de campo. Modifique os valores de campo, se necessário, e envie dados para o repositório crx.

Execute as seguintes etapas para usar [editor de regras](https://helpx.adobe.com/experience-manager/6-5/forms/using/rule-editor.html) para chamar o serviço de modelo de dados de formulário para vincular campos e valores de preenchimento prévio em um formulário adaptável:

1. Selecione o **formulário de aplicação de empréstimo de amostra** na pasta **[!UICONTROL output]** e toque em **[!UICONTROL Edit]**.
1. Na guia **[!UICONTROL Content]**, toque no ícone de configuração:

   ![configurar container de formulário](assets/configure_form_container.png)

   Na seção **[!UICONTROL Basic]**, selecione **[!UICONTROL Form Data Model Prefill service]** na lista suspensa **[!UICONTROL Prefill Service]**.

1. Toque na caixa de texto **[!UICONTROL Applicant Name]** e toque em **[!UICONTROL Edit Rules]**.

   ![Editar regras para criar vínculos de dados](assets/edit_rules_bind_reference.png)

1. Toque em **[!UICONTROL Create]** na página do Editor de regras.
1. Na página **[!UICONTROL Rule Editor]**:

   1. Selecione um estado para a caixa de texto Nome do Candidato. Por exemplo, **[!UICONTROL is initialized]**, que resulta na execução da condição **[!UICONTROL Then]** quando você renderiza o formulário no modo **[!UICONTROL Preview]**.

   1. Na seção **[!UICONTROL Then]**, selecione **[!UICONTROL Invoke Service]** na lista suspensa **[!UICONTROL Select Action]**. Todos os serviços em sua instância do Forms são exibidos na lista suspensa.

   1. Selecione um serviço **[!UICONTROL Get]** na seção que lista os modelos de dados do formulário. O campo Entrada exibe **phonenumber**, que é a chave primária definida para o modelo de dados **requerente**. O sistema recupera e preenche previamente os valores no formulário adaptável para campos na seção Saída com base nesse campo.

   1. Crie um vínculo para os campos de formulário adaptáveis com as entidades do modelo de dados de formulário usando a seção Saída. Por exemplo, vincule o campo de formulário adaptável **[!UICONTROL Applicant Name]** à entidade **name**.

   1. Tocar **[!UICONTROL Done]**. Toque em **[!UICONTROL Done]** novamente na página do Editor de regras.

   ![Editor de regras para vincular referências](assets/rule_editor_bind_references.png)

1. Toque em **[!UICONTROL Preview]** para visualização os valores de campo de formulário adaptável pré-preenchido.

   >[!NOTE]
   >
   >Certifique-se de que a propriedade **[!UICONTROL Return Array]** esteja definida como OFF para a propriedade de serviço **get** no modelo de dados de formulário associado ao formulário adaptável.

1. Modifique os valores de campo, se necessário, e envie o formulário adaptável. Os dados enviados estão disponíveis no seguinte local no repositório crx:

   `http://host name:port/crx/de/index.jsp#/content/forms/fp/admin/submit/data/latest file available in the folder`

### Usar o schema JSON como fonte de dados {#jsondatasource}

**Caso de uso:** você gera um formulário adaptável sem vínculo de dados usando o serviço do Automated forms conversion e configura o schema JSON como a fonte de dados. Vincule os campos de formulário adaptáveis ao schema JSON manualmente e use a opção **Pré-visualização com data** para preencher previamente os valores de campo. Modifique os valores de campo, se necessário, e envie dados para o repositório crx.

Antes de executar o caso de uso, verifique se você:

* [um schema JSON válido compatível com a estrutura do schema JSON](#prepare-data-for-form-model)
* [um formulário adaptável sem vínculo de dados](#generate-adaptive-forms-with-no-data-binding)

Execute as seguintes etapas:

1. Selecione o formulário **do aplicativo de empréstimo de amostra convertido** disponível na pasta **output** e toque em **[!UICONTROL Properties]**.
1. Toque na guia **[!UICONTROL Form Model]**, selecione **[!UICONTROL Schema]** na lista suspensa **[!UICONTROL Select From]** e toque em **[!UICONTROL Select Schema]** para fazer upload do schema **demo.schema JSON** salvo no sistema de arquivos local. Toque em **[!UICONTROL Save & Close]** para salvar o formulário.
1. Selecione o **formulário de aplicação de empréstimo de amostra** e toque em **[!UICONTROL Edit]**.
1. Toque na caixa de texto Nome do candidato e selecione ![ícone de configuração](assets/configure_icon.svg) (Configurar).

   No campo Vincular referência, selecione **Candidato** > **Nome** e toque em ![ícone concluído](assets/save_icon.svg) para salvar as propriedades. Da mesma forma, crie um vínculo de dados para **Endereço**, **Número de telefone**, **Email**, **Ocupação**, **Salário anual (em dólares)** e **Não. dos campos de membros da família dependentes** com as entidades do schema JSON.

1. Selecione novamente o formulário de aplicação de empréstimo de amostra **convertido** disponível na pasta **[!UICONTROL output]** e selecione **[!UICONTROL Preview]** > **[!UICONTROL Preview with Data]**.</br>

   Baixar arquivo de dados de amostra</br>

   [Obter arquivo](assets/json_data_file.txt)</br>

1. Modifique os valores de campo, se necessário, e envie o formulário adaptável. Os dados enviados estão disponíveis no seguinte local no repositório crx:

   `http://host name:port/crx/de/index.jsp#/content/forms/fp/admin/submit/data/latest file available in the folder`

### Usar o schema XSD como fonte de dados {#xsddatasource}

**Caso de uso:** você gera um formulário adaptável sem vínculo de dados usando o serviço de Automated forms conversion e configura o schema XSD como a fonte de dados. Vincule os campos de formulário adaptáveis ao schema XSD manualmente e use a Pré-visualização **com data** para preencher previamente os valores de campo. Modifique os valores de campo, se necessário, e envie dados para o repositório crx.

Antes de executar o caso de uso, verifique se você:

* [um schema XSD válido compatível com a estrutura do schema XML](#prepare-data-for-form-model)
* [um formulário adaptável sem vínculo de dados](#generate-adaptive-forms-with-no-data-binding)

Execute as seguintes etapas:

1. Selecione o **formulário de aplicação de empréstimo de amostra** convertido disponível na pasta **[!UICONTROL output]** e toque em **[!UICONTROL Properties]**.
1. Toque na guia **[!UICONTROL Form Model]**, selecione **[!UICONTROL Schema]** na lista suspensa **[!UICONTROL Select From]** e toque em **[!UICONTROL Select Schema]** para fazer upload do schema **loanapplication** XSD salvo no sistema de arquivos local. Selecione o elemento raiz para o schema XSD e toque em **[!UICONTROL Save & Close]** para salvar o formulário.
1. Selecione o **formulário de aplicação de empréstimo de amostra** e toque em **[!UICONTROL Edit]**.
1. Toque na caixa de texto Nome do candidato e selecione ![ícone de configuração](assets/configure_icon.svg) (Configurar).
No campo Vincular referência, selecione **Candidato** > **Nome** e toque em ![Ícone concluído](assets/save_icon.svg) para salvar as propriedades. Da mesma forma, crie um vínculo de dados para **Endereço**, **Número de telefone**, **Email**, **Ocupação**, **Salário anual (em dólares)** e **Não. dos campos de membros da família dependentes** com as entidades do schema XSD.

1. Selecione novamente o formulário de aplicação de empréstimo de amostra **convertido** disponível na pasta **output** e selecione **[!UICONTROL Preview]** > **[!UICONTROL Preview with Data]**.</br>

   Baixar arquivo de dados de amostra</br>

   [Obter arquivo](assets/loan-application-data-xml-data.zip)</br>


1. Modifique os valores de campo, se necessário, e envie o formulário adaptável. Os dados enviados estão disponíveis no seguinte local no repositório crx:

   `http://host name:port/crx/de/index.jsp#/content/forms/fp/admin/submit/data/latest file available in the folder`

## Gerar formulários adaptáveis com vínculo JSON {#generate-adaptive-forms-with-json-binding}

Use o serviço de [Automated forms conversion para converter](convert-existing-forms-to-adaptive-forms.md) o [formulário de aplicação de empréstimo de exemplo](#sample-adaptive-form) para um formulário adaptável com vínculo de dados. Certifique-se de não marcar a caixa de seleção **[!UICONTROL Generate adaptive form(s) without data bindings]** ao gerar o formulário adaptável.

![Formulário adaptável com vínculo JSON](assets/generate_af_with_data_bindings.png)

### Usar o schema JSON como fonte de dados {#jsonwithdatabinding}

**Caso de uso:** você gera um formulário adaptável com vínculo de dados JSON usando o serviço do Automated forms conversion. O serviço de preenchimento prévio e a função de envio de formulário funcionam perfeitamente. Você não precisa de nenhuma etapa de configuração.

Antes de executar o caso de uso, verifique se você tem [um formulário adaptável com vínculo de dados](#generate-adaptive-forms-with-json-binding).

Execute as seguintes etapas:

1. Selecione novamente o formulário de aplicação de empréstimo de amostra **convertido** disponível na pasta **[!UICONTROL output]** e selecione **[!UICONTROL Preview]** > **[!UICONTROL Preview with Data]**.</br>

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
