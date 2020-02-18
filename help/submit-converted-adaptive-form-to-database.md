---
title: Enviar os formulários adaptativos convertidos com um esquema JSON para o banco de dados
description: Envie os formulários adaptativos convertidos com um esquema JSON para o banco de dados criando um modelo de dados de formulário e fazendo referência a ele em um fluxo de trabalho do AEM.
uuid: f98b4cca-f0a3-4db8-aef2-39b8ae462628
topic-tags: forms
discoiquuid: cad72699-4a4b-4c52-88a5-217298490a7c
translation-type: tm+mt
source-git-commit: b879a0ddecd5370c754dfe9e1bf33121dd5ecc97

---


# Integrar formulário adaptável ao banco de dados usando o fluxo de trabalho do AEM {#submit-forms-to-database-using-forms-portal}

O serviço de conversão de formulários automatizada permite converter um formulário PDF não interativo, um formulário Acro ou um formulário PDF baseado em XFA em um formulário adaptável. Ao iniciar o processo de conversão, você tem a opção de gerar um formulário adaptável com ou sem vínculos de dados.

Se você optar por gerar um formulário adaptável sem vínculos de dados, poderá integrar o formulário adaptável convertido a um modelo de dados de formulário, esquema XML ou esquema JSON após a conversão. Para o modelo de dados de formulário, é necessário vincular manualmente os campos adaptáveis ao modelo de dados de formulário. Entretanto, se um formulário adaptável for gerado com vínculos de dados, o serviço de conversão associará automaticamente os formulários adaptáveis a um esquema JSON e criará um vínculo de dados entre os campos disponíveis no formulário adaptável e no esquema JSON. Em seguida, é possível integrar o formulário adaptável a um banco de dados de sua escolha, preencher dados no formulário e enviá-lo ao banco de dados. Da mesma forma, após uma integração bem-sucedida com o banco de dados, é possível configurar os campos no formulário adaptável convertido para recuperar valores do banco de dados e preencher previamente os campos do formulário adaptável.

A figura a seguir descreve diferentes estágios de integração de um formulário adaptável convertido em um banco de dados:

![integração de banco de dados](assets/integrate-adaptive-form-with-database.png)

Este artigo descreve as instruções passo a passo para executar com êxito todas essas etapas de integração.

## Pré-requisitos {#pre-requisites}

* Instância de autor do AEM 6.5 com o AEM 6.5 Service Pack mais recente
* Versão mais recente do pacote complementar AEM Forms
* [Serviço de conversão de formulários automatizado](configure-service.md)
* Um banco de dados para integrar. O banco de dados usado na implementação de amostra é MySQL 5.6.24. Entretanto, é possível integrar o formulário adaptável convertido a qualquer banco de dados de sua escolha.

## Exemplo de formulário adaptável {#sample-adaptive-form}

Para executar o caso de uso para integrar formulários adaptativos convertidos ao banco de dados usando um fluxo de trabalho AEM, baixe o arquivo PDF de amostra a seguir.

É possível baixar o formulário de amostra Entrar em contato conosco usando:

[Obter arquivo](assets/sample_contact_us_form.pdf)

O arquivo PDF serve como entrada para o serviço de Conversão de formulários automatizados. O serviço converte esse arquivo em um formulário adaptável. A imagem a seguir descreve o formulário de contato de amostra em um formato PDF.

![formulário de pedido de empréstimo de amostra](assets/sample_contact_us_form.png)

## Instale o arquivo mysql-Connector-java-5.1.39-bin.jar {#install-mysql-connector-java-file}

Execute as seguintes etapas, em todas as instâncias de autor e publicação, para instalar o arquivo mysql-Connector-java-5.1.39-bin.jar:

1. Navegue até `http://server:port/system/console/depfinder` o pacote com.mysql.jdbc e procure-o.
1. Na coluna Exportado por, verifique se o pacote é exportado por qualquer pacote. Continue se o pacote não for exportado por nenhum pacote.
1. Navegue até `http://server:port/system/console/bundles` e clique em **[!UICONTROL Install/Update]**.
1. Clique **[!UICONTROL Choose File]** e navegue para selecionar o arquivo mysql-Connector-java-5.1.39-bin.jar. Além disso, marque **[!UICONTROL Start Bundle]** e **[!UICONTROL Refresh Packages]** caixas de seleção.
1. Clique em **[!UICONTROL Install]** ou **[!UICONTROL Update]**. Após a conclusão, reinicie o servidor.
1. (Somente Windows) Desligue o firewall do sistema para o seu sistema operacional.

## Preparar dados para o modelo de formulário {#prepare-data-for-form-model}

A integração de dados do AEM Forms permite configurar e conectar-se a fontes de dados diferentes. Depois de gerar um formulário adaptável usando o processo de conversão, você pode definir o modelo de formulário com base em um modelo de dados de formulário, XSD ou um esquema JSON. Você pode usar um banco de dados, o Microsoft Dynamics ou qualquer outro serviço de terceiros para criar um modelo de dados de formulário.

Este tutorial usa o banco de dados MySQL como a fonte para criar um modelo de dados de formulário. Crie um esquema no banco de dados e adicione a tabela **contactus** ao esquema com base nos campos disponíveis no formulário adaptável.

![Dados de amostra mysql](assets/db_entries_sample_form.png)

Você pode usar a seguinte instrução DDL para criar a tabela **contactus** no banco de dados.

```sql
CREATE TABLE `contactus` (
   `name` varchar(45) NOT NULL,
   `email` varchar(45) NOT NULL,
   `phonenumber` varchar(10) DEFAULT NULL,
   `issuedesc` varchar(1000) DEFAULT NULL,
   PRIMARY KEY (`email`)
 ) ENGINE=InnoDB DEFAULT CHARSET=utf8
```

## Configurar a conexão entre a instância do AEM e o banco de dados {#configure-connection-between-aem-instance-and-database}

Execute as seguintes etapas de configuração para criar uma conexão entre a instância do AEM e o banco de dados MYSQL:

1. Vá para a página Configuração do console da Web do AEM em `http://server:port/system/console/configMgr`.
1. Localize e clique em para abrir **[!UICONTROL Apache Sling Connection Pooled DataSource]** no modo de edição na Configuração do console da Web. Especifique os valores para as propriedades conforme descrito na tabela a seguir:

   <table> 
    <tbody> 
    <tr> 
    <th><strong>Propriedade</strong></th> 
    <th><strong>Valor</strong></th> 
    </tr> 
    <tr> 
    <td><p>Nome da fonte de dados</p></td> 
    <td><p>Um nome de fonte de dados para filtrar drivers do pool de fontes de dados.</p></td>
    </tr>
    <tr> 
    <td><p>Classe de driver JDBC</p></td> 
    <td><p>com.mysql.jdbc.Driver</p></td>
    </tr>
    <tr> 
    <td><p>URI de conexão JDBC</p></td> 
    <td><p>jdbc:mysql://[host]:[porta]/[nome_esquema]</p></td>
    </tr>
    <tr> 
    <td><p>Nome de usuário</p></td> 
    <td><p>Um nome de usuário para autenticar e executar ações em tabelas de banco de dados</p></td>
    </tr>
    <tr> 
    <td><p>Senha</p></td> 
    <td><p>Senha associada ao nome de usuário</p></td>
    </tr>
    <tr> 
    <td><p>Isolamento da transação</p></td> 
    <td><p>READ_COMMTED</p></td>
    </tr>
    <tr> 
    <td><p>Máximo de conexões ativas</p></td> 
    <td><p>1000</p></td>
    </tr>
    <tr> 
    <td><p>Máximo de conexões inativas</p></td> 
    <td><p>100</p></td>
    </tr>
    <tr> 
    <td><p>Conexões inativas mínimas</p></td> 
    <td><p>10</p></td>
    </tr>
    <tr> 
    <td><p>Tamanho inicial</p></td> 
    <td><p>10</p></td>
    </tr>
    <tr> 
    <td><p>Espera máxima</p></td> 
    <td><p>100000</p></td>
    </tr>
     <tr> 
    <td><p>Teste de emprestado</p></td> 
    <td><p>Marcado</p></td>
    </tr>
     <tr> 
    <td><p>Testar enquanto ocioso</p></td> 
    <td><p>Marcado</p></td>
    </tr>
     <tr> 
    <td><p>Consulta de validação</p></td> 
    <td><p>Exemplos de valores são SELECT 1(mysql), select 1 from dual(oracle), SELECT 1(MS Sql Server) (validationQuery)</p></td>
    </tr>
     <tr> 
    <td><p>Tempo limite da consulta de validação</p></td> 
    <td><p>10000</p></td>
    </tr>
    </tbody> 
    </table>

## Create form data model {#create-form-data-model}

Depois de configurar o MYSQL como a fonte de dados, execute as seguintes etapas para criar um modelo de dados de formulário:

1. Na instância do autor de AEM, navegue até **[!UICONTROL Forms]** > **[!UICONTROL Data Integrations]**.

1. Tocar **[!UICONTROL Create]** > **[!UICONTROL Form Data Model]**.

1. No **[!UICONTROL Create Form Data Model]** assistente, especifique **workflow_submit** como o nome do modelo de dados do formulário. Tocar **[!UICONTROL Next]**.

1. Selecione a fonte de dados MYSQL configurada na seção anterior e toque em **[!UICONTROL Create]**.

1. Toque **[!UICONTROL Edit]** e expanda a fonte de dados listada no painel esquerdo para selecionar a tabela de **contatos** , **[!UICONTROL get]** os serviços e **[!UICONTROL insert]** os serviços, e toque **[!UICONTROL Add Selected]**.

   ![Dados de amostra mysql](assets/fdm_details_workfdlow_submit.png)

1. Selecione o objeto de modelo de dados no painel direito e toque **[!UICONTROL Edit Properties]**. Selecione **[!UICONTROL get]** e **[!UICONTROL insert]** de listas **[!UICONTROL Read Service]** e **[!UICONTROL Write Service]** suspensas. Especifique os argumentos para o serviço de Leitura e toque **[!UICONTROL Done]**.

1. Na **[!UICONTROL Services]** guia, selecione o **[!UICONTROL get]** serviço e toque **[!UICONTROL Edit Properties]**. Selecione o **[!UICONTROL Output Model Object]**, desative a **[!UICONTROL Return array]** alternância e toque **[!UICONTROL Done]**.

1. Selecione o **[!UICONTROL Insert]** serviço e toque em **[!UICONTROL Edit Properties]**. Selecione o **[!UICONTROL Input Model Object]** e toque **[!UICONTROL Done]**.

1. Toque em **[!UICONTROL Save]** para salvar o modelo de dados do formulário.

É possível baixar a amostra do Modelo de dados de formulário usando:

[Obter arquivo](assets/DownloadedFormsPackage_1497728018502500.zip)

## Gerar formulários adaptáveis com vínculo JSON {#generate-adaptive-forms-with-json-binding}

Use o serviço de Conversão de formulários [automatizados para converter](convert-existing-forms-to-adaptive-forms.md) o formulário [](#sample-adaptive-form) Fale conosco em um formulário adaptável com vínculo de dados. Certifique-se de não marcar a caixa de **[!UICONTROL Generate adaptive form(s) without data bindings]** seleção ao gerar o formulário adaptável.

![Formulário adaptável com vínculo JSON](assets/generate_af_with_data_bindings.png)

Selecione o formulário **** Entre em contato conosco convertido disponível na **[!UICONTROL output]** pasta em **[!UICONTROL Forms & Documents]** e toque em **[!UICONTROL Edit]**. Toque em **[!UICONTROL Preview]**, digite os valores nos campos do formulário adaptável e toque em **[!UICONTROL Submit]**.

Faça logon no **crx-repository** e navegue até */content/forms/fp/admin/submit/data* para exibir os valores enviados no formato JSON. Estes são os dados de amostra no formato JSON quando você envia o formulário adaptativo **Entrar em contato conosco** convertido:

```json
{
  "afData": {
    "afUnboundData": {
      "data": {}
    },
    "afBoundData": {
      "data": {
        "name1": "Gloria",
        "email": "abc@xyz.com",
        "phone_number": "2346578965",
        "issue_description": "Test message"
      }
    },
    "afSubmissionInfo": {
      "computedMetaInfo": {},
      "stateOverrides": {},
      "signers": {},
      "afPath": "/content/dam/formsanddocuments/docs_conversion/output/sample_form_json",
      "afSubmissionTime": "20191204014007"
    }
  }
}
```

Agora é necessário criar um modelo de fluxo de trabalho que possa processar esses dados e enviá-los ao banco de dados MYSQL usando o modelo de dados de formulário criado nas seções anteriores.

## Criar um modelo de fluxo de trabalho para processar dados JSON {#create-workflow-model}

Execute as seguintes etapas para criar um modelo de fluxo de trabalho para enviar os dados do formulário adaptável ao banco de dados:

1. Abra o console Modelos de fluxo de trabalho. O URL padrão é `https://server:port/libs/cq/workflow/admin/console/content/models.html/etc/workflow/models`.

1. Selecione **[!UICONTROL Create]**, em seguida **[!UICONTROL Create Model]**. A **[!UICONTROL Add Workflow Model]** caixa de diálogo é exibida.

1. Insira o **[!UICONTROL Title]** e **[!UICONTROL Name]** (opcional). Por exemplo, **workflow_json_submit**. Toque em **[!UICONTROL Done]** para criar o modelo.

1. Selecione o modelo de fluxo de trabalho e toque **[!UICONTROL Edit]** para abrir o modelo no modo de edição. Toque em + e adicione **[!UICONTROL Invoke Form Data Model Service]** etapa ao modelo de fluxo de trabalho.

1. Toque na **[!UICONTROL Invoke Form Data Model Service]** etapa e toque em ![Configurar](assets/configure_icon.png).

1. Na **[!UICONTROL Form Data Model]** guia, selecione o modelo de dados de formulário criado no **[!UICONTROL Form Data Model path]** campo e selecione **[!UICONTROL insert]** na lista **[!UICONTROL Service]** suspensa.

1. Na **[!UICONTROL Input for Service]** guia, selecione **[!UICONTROL Provide input data using literal, variable, or a workflow metadata, and a JSON file]** na lista suspensa, marque a caixa de seleção **[!UICONTROL Map input fields from input JSON]** , selecione **[!UICONTROL Relative to payload]** e forneça **data.xml** como o valor do **[!UICONTROL Select input JSON document using]** campo.

1. Na **[!UICONTROL Service Arguments]** seção, forneça os seguintes valores para os argumentos do modelo de dados de formulário:

   ![Invocar serviço de modelo de dados de formulário](assets/invoke_form_data_model_service.png)

   Observe que os campos do modelo de dados do formulário, por exemplo, nome do ponto de contato, são mapeados para **afData.afBoundData.data.name1**, que se refere aos vínculos do esquema JSON para o formulário adaptativo enviado.

## Configurar envio de formulário adaptável {#configure-adaptive-form-submission}

Execute as seguintes etapas para enviar o formulário adaptável ao modelo de fluxo de trabalho criado na seção anterior:

1. Selecione o formulário Fale conosco convertido disponível na **[!UICONTROL output]** pasta em **[!UICONTROL Forms & Documents]** e toque em **[!UICONTROL Edit]**.

1. Abra as propriedades do formulário adaptável tocando **[!UICONTROL Form Container]** e tocando em ![Configurar](assets/configure_icon.png).

1. Na **[!UICONTROL Submission]** seção, selecione **[!UICONTROL Invoke an AEM workflow]** na lista **[!UICONTROL Submit Action]** suspensa, selecione o modelo de fluxo de trabalho criado na seção anterior e especifique **data.xml** no **[!UICONTROL Data File Path]** campo.

1. Toque em ![Salvar](assets/save_icon.png) para salvar as propriedades.

1. Toque em **[!UICONTROL Preview]**, digite os valores nos campos do formulário adaptável e toque em **[!UICONTROL Submit]**. Os valores enviados agora são exibidos na tabela do banco de dados MYSQL em vez do repositório **** crx.

## Configurar formulário adaptável para preencher previamente valores do banco de dados

Execute as seguintes etapas para configurar o formulário adaptável para preencher previamente valores do banco de dados MYSQL com base na chave primária definida na tabela (neste caso, Email):

1. Toque no campo **Email** no formulário adaptável e toque em ![Editar regra](assets/edit-rules.png).

1. Toque **[!UICONTROL Create]** e selecione **[!UICONTROL is changed]** na lista **[!UICONTROL Select State]** suspensa na **[!UICONTROL When]** seção.

1. Na **[!UICONTROL Then]** seção, selecione **[!UICONTROL Invoke Service]** e **obtenha** como serviço para o modelo de dados de formulário criado em uma seção anterior deste artigo.

1. Selecione **Email** na seção **[!UICONTROL Input]** e os outros três campos do modelo de dados do formulário, **Nome**, Número **de** telefone e Descrição **da** edição na **[!UICONTROL Output]** seção. Toque em **[!UICONTROL Done]** para salvar as configurações.

   ![Definir configurações de preenchimento de email](assets/email_prefill_settings.png)

   Como resultado, com base nas entradas de E-mail existentes no banco de dados MYSQL, você pode pré-preencher os valores dos três restantes campos no **[!UICONTROL Preview]** modo do formulário adaptável. Por exemplo, se você especificar aya.tan@xyz.com no campo **Email** (com base nos dados existentes na seção [Preparar modelo](#prepare-data-for-form-model) de dados de formulário deste artigo) e sair do campo, os três campos restantes, **Nome**, Número **de** telefone e Descrição **da** edição serão exibidos automaticamente no formulário adaptável.

É possível fazer download do formulário adaptativo convertido de amostra usando:

[Obter arquivo](assets/DownloadedFormsPackage_1498226829041200.zip)
