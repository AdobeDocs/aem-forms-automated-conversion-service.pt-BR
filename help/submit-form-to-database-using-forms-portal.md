---
title: Enviar formulários adaptáveis para o banco de dados usando o Forms Portal
description: Estenda o metamodelo padrão para adicionar padrões, validações e entidades específicos à sua organização e aplicar configurações a campos de formulário adaptáveis ao executar o serviço do Automated forms conversion.
uuid: f98b4cca-f0a3-4db8-aef2-39b8ae462628
topic-tags: forms
discoiquuid: cad72699-4a4b-4c52-88a5-217298490a7c
source-git-commit: ead1b4ee177029c60f095dc596b1f3db5878760e
workflow-type: tm+mt
source-wordcount: '1152'
ht-degree: 1%

---


# Integrar formulários adaptáveis ao banco de dados usando o Forms Portal {#submit-forms-to-database-using-forms-portal}

O serviço Automated forms conversion permite converter um formulário de PDF não interativo, um formulário Acro ou um formulário de PDF baseado em XFA em um formulário adaptável. Ao iniciar o processo de conversão, você tem a opção de gerar um formulário adaptável com ou sem vínculos de dados.

Se você optar por gerar um formulário adaptável sem associações de dados, será possível integrar o formulário adaptável convertido com um Modelo de dados de formulário, esquema XML ou esquema JSON após a conversão. No entanto, se você gerar um formulário adaptável com vinculações de dados, o serviço de conversão associará automaticamente os formulários adaptáveis a um esquema JSON e criará uma vinculação de dados entre os campos disponíveis no formulário adaptável e no esquema JSON. Em seguida, você pode integrar o formulário adaptável a um banco de dados de sua escolha, preencher dados no formulário e enviá-lo para o banco de dados usando o Portal do Forms.

A figura a seguir descreve os diferentes estágios de integração de um formulário adaptável convertido em um banco de dados usando o Forms Portal:

![integração de banco de dados](assets/database_integration.gif)

Este artigo descreve as instruções passo a passo para executar com êxito todos esses estágios de integração.

A amostra, discutida neste artigo, é uma implementação de referência de dados personalizados e serviços de metadados para integrar uma página do Forms Portal a um banco de dados. O banco de dados usado na implementação da amostra é o MySQL 5.6.24. No entanto, você pode integrar a página do Forms Portal a qualquer banco de dados de sua escolha.

## Pré-requisitos {#pre-requisites}

* Configurar uma instância de autor do AEM 6.4 ou 6.5
* Instalar [service pack mais recente](https://helpx.adobe.com/br/experience-manager/aem-releases-updates.html) para sua instância do AEM
* Versão mais recente do pacote complementar do AEM Forms
* Configurar [serviço Automated forms conversion](configure-service.md)
* Configurar um banco de dados. O banco de dados usado na implementação da amostra é o MySQL 5.6.24. No entanto, é possível integrar o formulário adaptável convertido a qualquer banco de dados de sua escolha.

## Configurar conexão entre a instância AEM e o banco de dados {#set-up-connection-aem-instance-database}

A configuração de uma conexão entre uma instância AEM e um banco de dados MYSQL consiste em:

* [Instalação de um pacote de conector MYSQL](#install-mysql-connector-java-file)

* [Criação de esquema e tabelas no banco de dados](#create-schema-and-tables-in-database)

* [Definição das configurações de conexão](#configure-connection-between-aem-instance-and-database)

* [Definição e configuração do pacote de amostra para integração com o Forms Portal](#set-up-and-configure-sample)

### Instale o arquivo mysql-connector-java-5.1.39-bin.jar {#install-mysql-connector-java-file}

Execute as seguintes etapas, em todas as instâncias de autor e publicação, para instalar o arquivo mysql-connector-java-5.1.39-bin.jar:

1. Navegue até http://[server]:[porta]/system/console/depfinder e procure o pacote com.mysql.jdbc.
1. Na coluna Exportado por, verifique se o pacote foi exportado por algum pacote. Continue se o pacote não for exportado por um pacote.
1. Navegue até http://[server]:[porta]/system/console/bundles e clique em **[!UICONTROL Install/Update]**.
1. Clique em **[!UICONTROL Choose File]** e navegue para selecionar o arquivo mysql-connector-java-5.1.39-bin.jar. Além disso, **[!UICONTROL Start Bundle]** e **[!UICONTROL Refresh Packages]** caixas de seleção.
1. Clique em **[!UICONTROL Install]** ou **[!UICONTROL Update]**. Após a conclusão, reinicie o servidor.
1. (Somente para Windows) Desative o firewall do sistema para o seu sistema operacional.

### Criar esquema e tabelas no banco de dados {#create-schema-and-tables-in-database}

Execute as seguintes etapas para criar esquema e tabelas no banco de dados:

1. Crie um schema no banco de dados usando a seguinte instrução SQL:

   ```sql
   CREATE SCHEMA `formsportal` ;
   ```

   onde **formsportal** refere-se ao nome do schema.

1. Criar um **dados** no esquema de banco de dados usando a seguinte instrução SQL:

   ```sql
    CREATE TABLE `data` (
        `owner` varchar(255) DEFAULT NULL,
        `data` longblob,
        `metadataId` varchar(45) DEFAULT NULL,
        `id` varchar(45) NOT NULL,
        PRIMARY KEY (`id`)
        ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
   ```

1. Criar um **metadados** no esquema de banco de dados usando a seguinte instrução SQL:

   ```sql
   CREATE TABLE `metadata` (
       `formPath` varchar(1000) DEFAULT NULL,
       `formType` varchar(100) DEFAULT NULL,
       `description` text,
       `formName` varchar(255) DEFAULT NULL,
       `owner` varchar(255) DEFAULT NULL,
       `enableAnonymousSave` varchar(45) DEFAULT NULL,
       `renderPath` varchar(1000) DEFAULT NULL,
       `nodeType` varchar(45) DEFAULT NULL,
       `charset` varchar(45) DEFAULT NULL,
       `userdataID` varchar(45) DEFAULT NULL,
       `status` varchar(45) DEFAULT NULL,
       `formmodel` varchar(45) DEFAULT NULL,
       `markedForDeletion` varchar(45) DEFAULT NULL,
       `showDorClass` varchar(255) DEFAULT NULL,
       `sling:resourceType` varchar(1000) DEFAULT NULL,
       `attachmentList` longtext,
       `draftID` varchar(45) DEFAULT NULL,
       `submitID` varchar(45) DEFAULT NULL,
       `id` varchar(60) NOT NULL,
       `profile` varchar(255) DEFAULT NULL,
       `submitUrl` varchar(1000) DEFAULT NULL,
       `xdpRef` varchar(1000) DEFAULT NULL,
       `agreementId` varchar(255) DEFAULT NULL,
       `nextSigners` varchar(255) DEFAULT NULL,
       `eSignStatus` varchar(45) DEFAULT NULL,
       `pendingSignID` varchar(45) DEFAULT NULL,
       `agreementDataId` varchar(255) DEFAULT NULL,
       `enablePortalSubmit` varchar(45) DEFAULT NULL,
       `submitType` varchar(45) DEFAULT NULL,
       `dataType` varchar(45) DEFAULT NULL,
       `jcr:lastModified` varchar(45) DEFAULT NULL,
       PRIMARY KEY (`id`),
       UNIQUE KEY `ID_UNIQUE` (`id`)
       ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
   ```

1. Criar um **additionalmetadatable** no esquema de banco de dados usando a seguinte instrução SQL:

   ```sql
   CREATE TABLE `additionalmetadatatable` (
       `value` text,
       `key` varchar(255) NOT NULL,
       `id` varchar(60) NOT NULL,
       PRIMARY KEY (`id`,`key`),
       CONSTRAINT ‘additionalmetadatatable_fk’ FOREIGN KEY (`id`) REFERENCES `metadata` (`id`) ON DELETE CASCADE
       ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
   ```

1. Criar um **tabela de comentários** no esquema de banco de dados usando a seguinte instrução SQL:

   ```sql
   CREATE TABLE `commenttable` (
       `commentId` varchar(255) DEFAULT NULL,
       `comment` text DEFAULT NULL,
       `ID` varchar(255) DEFAULT NULL,
       `commentowner` varchar(255) DEFAULT NULL,
       `time` varchar(255) DEFAULT NULL);
   ```

### Configurar conexão entre a instância do AEM e o banco de dados {#configure-connection-between-aem-instance-and-database}

Execute as seguintes etapas de configuração para criar uma conexão entre a instância do AEM e o banco de dados MYSQL:

1. Vá para a página Configuração do console da Web do AEM em *http://[host]:[porta]/system/console/configMgr*.
1. Clique para abrir **[!UICONTROL Forms Portal Draft and Submission Configuration]** no modo de edição.
1. Especifique os valores das propriedades conforme descrito na tabela a seguir:

   <table> 
    <tbody> 
    <tr> 
    <th><strong>Propriedade</strong></th> 
    <th><strong>Descrição</strong></th>
    <th><strong>Valor</strong></th> 
    </tr> 
    <tr> 
    <td><p>Serviço de Dados de Rascunho do Portal do Forms</p></td> 
    <td><p>Identificador do serviço de dados de rascunho</p></td>
    <td><p>formsportal.sampledataservice</p></td> 
    </tr>
    <tr> 
    <td><p>Serviço de Metadados de Rascunho do Portal do Forms</p></td> 
    <td><p>Identificador do serviço de metadados de rascunho</p></td>
    <td><p>formsportal.samplemetadataservice</p></td> 
    </tr>
    <tr> 
    <td><p>Serviço de Envio de Dados do Forms Portal</p></td> 
    <td><p>Identificador para enviar serviço de dados</p></td>
    <td><p>formsportal.sampledataservice</p></td> 
    </tr>
    <tr> 
    <td><p>Serviço de metadados de envio do portal do Forms</p></td> 
    <td><p>Identificador para enviar serviço de metadados</p></td>
    <td><p>formsportal.samplemetadataservice</p></td> 
    </tr>
    <tr> 
    <td><p>Serviço de Dados com Assinatura Pendente do Portal Forms</p></td> 
    <td><p>Identificador do serviço de dados com assinatura pendente</p></td>
    <td><p>formsportal.sampledataservice</p></td> 
    </tr>
    <tr> 
    <td><p>Serviço de Metadados de Assinatura Pendente do Forms Portal</p></td> 
    <td><p>Identificador do serviço de metadados com assinatura pendente</p></td>
    <td><p>formsportal.samplemetadataservice</p></td> 
    </tr>
    </tbody> 
    </table>
1. Deixe as outras configurações como estão e clique em **[!UICONTROL Save]**.
1. Localize e clique para abrir **[!UICONTROL Apache Sling Connection Pooled DataSource]** no modo de edição, na Configuração do console da Web. Especifique os valores das propriedades conforme descrito na tabela a seguir:

   <table> 
    <tbody> 
    <tr> 
    <th><strong>Propriedade</strong></th> 
    <th><strong>Valor</strong></th> 
    </tr> 
    <tr> 
    <td><p>Nome da fonte de dados</p></td> 
    <td><p>Um nome de fonte de dados para filtrar drivers do pool de fonte de dados. A implementação de amostra usa FormsPortal como o nome da fonte de dados.</p></td>
    </tr>
    <tr> 
    <td><p>Classe de driver JDBC</p></td> 
    <td><p>com.mysql.jdbc.Driver</p></td>
    </tr>
    <tr> 
    <td><p>URI da conexão JDBC</p></td> 
    <td><p>jdbc:mysql://[host]:[porta]/[nome_do_esquema]</p></td>
    </tr>
    <tr> 
    <td><p>Nome de usuário</p></td> 
    <td><p>Um nome de usuário para autenticar e executar ações em tabelas do banco de dados</p></td>
    </tr>
    <tr> 
    <td><p>Senha</p></td> 
    <td><p>Senha associada ao nome de usuário</p></td>
    </tr>
    <tr> 
    <td><p>Isolamento de transação</p></td> 
    <td><p>READ_COMMITTED</p></td>
    </tr>
    <tr> 
    <td><p>Máximo de conexões ativas</p></td> 
    <td><p>1000</p></td>
    </tr>
    <tr> 
    <td><p>Máximo de Conexões Ociosas</p></td> 
    <td><p>100</p></td>
    </tr>
    <tr> 
    <td><p>Mínimo de conexões ociosas</p></td> 
    <td><p>10</p></td>
    </tr>
    <tr> 
    <td><p>Tamanho inicial</p></td> 
    <td><p>10</p></td>
    </tr>
    <tr> 
    <td><p>Espera Máxima</p></td> 
    <td><p>100000</p></td>
    </tr>
     <tr> 
    <td><p>Teste ao tomar emprestado</p></td> 
    <td><p>Marcado</p></td>
    </tr>
     <tr> 
    <td><p>Teste enquanto ocioso</p></td> 
    <td><p>Marcado</p></td>
    </tr>
     <tr> 
    <td><p>Consulta de validação</p></td> 
    <td><p>Os valores de exemplo são SELECT 1(mysql), select 1 from dual(oracle), SELECT 1(MS Sql Server) (validationQuery)</p></td>
    </tr>
     <tr> 
    <td><p>Tempo limite de consulta de validação</p></td> 
    <td><p>10000</p></td>
    </tr>
    </tbody> 
    </table>

### Definir e configurar a amostra {#set-up-and-configure-sample}

Execute as seguintes etapas, em todas as instâncias de autor e publicação, para instalar e configurar a amostra:

1. Baixar o seguinte **aem-fp-db-integration-sample-pkg-6.1.2.zip** para o seu sistema de arquivos.

[Obter arquivo](assets/aem-fp-db-integration-sample-pkg-6.1.2.zip)

1. Ir para o gerenciador de pacotes AEM em *http://[host]:[porta]/crx/packmgr/*.
1. Clique em **[!UICONTROL Upload Package]**.
1. Navegue para selecionar o **aem-fp-db-integration-sample-pkg-6.1.2.zip** e clique em **[!UICONTROL OK]**.
1. Clique em **[!UICONTROL Install]** ao lado do pacote para instalar o pacote.

## Configurar o formulário adaptável convertido para integração com o Forms Portal {#configure-converted-adaptive-form-for-forms-portal-integration}

Execute as seguintes etapas para habilitar o envio do formulário adaptável usando a página do Forms Portal:
1. [Executar a conversão](convert-existing-forms-to-adaptive-forms.md#start-the-conversion-process) para converter um formulário de origem em um formulário adaptável.
1. Abra o formulário adaptável no modo de edição.
1. Toque em Contêiner de formulário e selecione Configurar ![Configurar formulário adaptável](assets/configure-adaptive-form.png).
1. No **[!UICONTROL Submission]** , selecione **[!UICONTROL Forms Portal Submit Action]** do **[!UICONTROL Submit Action]** lista suspensa.
1. Toque ![Salvar política de modelo](assets/edit_template_done.png) para salvar as configurações.

## Criar e configurar a página do Portal do Forms {#create-configure-forms-portal-page}

Execute as seguintes etapas para criar uma página do Forms Portal e configurá-la para enviar formulários adaptáveis usando esta página:

1. Faça logon na instância de autor do AEM e toque em **[!UICONTROL Adobe Experience Manager]** >  **[!UICONTROL Sites]**.
1. Selecione o local em que deseja salvar a nova página do Portal do Forms e toque em **[!UICONTROL Create]** > **[!UICONTROL Page]**.
1. Selecione o modelo para a página, toque em **[!UICONTROL Next]**, especifique um título para a página e toque em **[!UICONTROL Create]**.
1. Toque **[!UICONTROL Edit]** para configurar a página.
1. No cabeçalho da página, toque em ![Editar modelo](assets/edit_template_sites.png)  > **[!UICONTROL Edit Template]** para abrir o modelo da página.
1. Toque em Contêiner de layout e toque em ![Editar política de modelo](assets/edit_template_policy.png). No **[!UICONTROL Allowed Components]** , ative a opção **[!UICONTROL Document Services]** e **[!UICONTROL Document Services Predicates]** opções e toque em ![Salvar política de modelo](assets/edit_template_done.png).
1. Inserir **[!UICONTROL Search & Lister]** componente na página. Como resultado, todos os formulários adaptáveis existentes disponíveis na instância do AEM são listados na página.
1. Inserir **[!UICONTROL Drafts & Submissions]** componente na página. Duas guias, **[!UICONTROL Draft Forms]** e **[!UICONTROL Submitted Forms]**, exibir na página do Forms Portal. A variável **[!UICONTROL Draft Forms]** também exibe o formulário adaptável convertido gerado usando as etapas mencionadas em [Configurar o formulário adaptável convertido para integração com o Forms Portal](#configure-converted-adaptive-form-for-forms-portal-integration)

1. Toque **[!UICONTROL Preview]**, toque no formulário adaptável convertido, especifique valores para campos de formulário adaptável e envie-o. Os valores especificados para os campos de formulário adaptável são enviados ao banco de dados integrado.
