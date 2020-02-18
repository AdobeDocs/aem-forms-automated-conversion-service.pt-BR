---
title: Enviar formulários adaptáveis ao banco de dados usando o Portal de Formulários
description: Estenda o metrosmodelo padrão para adicionar padrões, validações e entidades específicas à sua organização e aplique configurações a campos de formulário adaptáveis enquanto executa o serviço de Conversão de formulários automatizados.
uuid: f98b4cca-f0a3-4db8-aef2-39b8ae462628
topic-tags: forms
discoiquuid: cad72699-4a4b-4c52-88a5-217298490a7c
translation-type: tm+mt
source-git-commit: 040b0ddb489b5bdfd640a93b22cd7bc512a39aea

---


# Integre formulários adaptáveis ao banco de dados usando o Portal do Forms {#submit-forms-to-database-using-forms-portal}

O serviço de conversão de formulários automatizada permite converter um formulário PDF não interativo, um formulário Acro ou um formulário PDF baseado em XFA em um formulário adaptável. Ao iniciar o processo de conversão, você tem a opção de gerar um formulário adaptável com ou sem vínculos de dados.

Se você optar por gerar um formulário adaptável sem vínculos de dados, poderá integrar o formulário adaptável convertido a um Modelo de dados de formulário, esquema XML ou esquema JSON após a conversão. Entretanto, se um formulário adaptável for gerado com vínculos de dados, o serviço de conversão associará automaticamente os formulários adaptáveis a um esquema JSON e criará um vínculo de dados entre os campos disponíveis no formulário adaptável e no esquema JSON. Em seguida, é possível integrar o formulário adaptável a um banco de dados de sua escolha, preencher dados no formulário e enviá-lo ao banco de dados usando o Portal de Formulários.

A figura a seguir descreve diferentes estágios de integração de um formulário adaptável convertido a um banco de dados usando o Portal do Forms:

![integração de banco de dados](assets/database_integration.gif)

Este artigo descreve as instruções passo a passo para executar com êxito todas essas etapas de integração.

A amostra, discutida neste artigo, é uma implementação de referência de serviços personalizados de dados e metadados para integrar uma página do Portal do Forms a um banco de dados. O banco de dados usado na implementação de amostra é MySQL 5.6.24. No entanto, é possível integrar a página do Portal do Forms a qualquer banco de dados de sua escolha.

## Pré-requisitos {#pre-requisites}

* Instância de autor do AEM 6.5 com o AEM 6.5 Service Pack mais recente
* Versão mais recente do pacote complementar AEM Forms
* [Serviço de conversão de formulários automatizado](configure-service.md)
* Um banco de dados para integrar. O banco de dados usado na implementação de amostra é MySQL 5.6.24. No entanto, você pode integrar o Portal do Forms a qualquer banco de dados de sua escolha.

## Configurar conexão entre a instância do AEM e o banco de dados {#set-up-connection-aem-instance-database}

A configuração de uma conexão entre uma instância do AEM e um banco de dados MYSQL consiste em:

* [Instalação de um pacote de conector MYSQL](#install-mysql-connector-java-file)

* [Criação de esquema e tabelas no banco de dados](#create-schema-and-tables-in-database)

* [Definição das configurações de conexão](#configure-connection-between-aem-instance-and-database)

* [Configuração e configuração do pacote de amostra para integração com o Portal do Forms](#set-up-and-configure-sample)

### Instale o arquivo mysql-Connector-java-5.1.39-bin.jar {#install-mysql-connector-java-file}

Execute as seguintes etapas, em todas as instâncias de autor e publicação, para instalar o arquivo mysql-Connector-java-5.1.39-bin.jar:

1. Navegue até http://[server]:[port]/system/console/depfinder e pesquise pelo pacote com.mysql.jdbc.
1. Na coluna Exportado por, verifique se o pacote é exportado por qualquer pacote. Continue se o pacote não for exportado por nenhum pacote.
1. Navegue até http://[server]:[port]/system/console/bundles e clique em **[!UICONTROL Install/Update]**.
1. Clique **[!UICONTROL Choose File]** e navegue para selecionar o arquivo mysql-Connector-java-5.1.39-bin.jar. Além disso, marque **[!UICONTROL Start Bundle]** e **[!UICONTROL Refresh Packages]** caixas de seleção.
1. Clique em **[!UICONTROL Install]** ou **[!UICONTROL Update]**. Após a conclusão, reinicie o servidor.
1. (Somente Windows) Desligue o firewall do sistema para o seu sistema operacional.

### Criar esquema e tabelas no banco de dados {#create-schema-and-tables-in-database}

Execute as seguintes etapas para criar esquema e tabelas no banco de dados:

1. Crie um esquema no banco de dados usando a seguinte instrução SQL:

   ```sql
   CREATE SCHEMA `formsportal` ;
   ```

   onde **formsportal** se refere ao nome do esquema.

1. Crie uma tabela de **dados** no esquema do banco de dados usando a seguinte instrução SQL:

   ```sql
    CREATE TABLE `data` (
        `owner` varchar(255) DEFAULT NULL,
        `data` longblob,
        `metadataId` varchar(45) DEFAULT NULL,
        `id` varchar(45) NOT NULL,
        PRIMARY KEY (`id`)
        ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
   ```

1. Crie uma tabela de **metadados** no esquema do banco de dados usando a seguinte instrução SQL:

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

1. Crie uma tabela de metadados **adicionais** no esquema do banco de dados usando a seguinte instrução SQL:

   ```sql
   CREATE TABLE `additionalmetadatatable` (
       `value` text,
       `key` varchar(255) NOT NULL,
       `id` varchar(60) NOT NULL,
       PRIMARY KEY (`id`,`key`),
       CONSTRAINT ‘additionalmetadatatable_fk’ FOREIGN KEY (`id`) REFERENCES `metadata` (`id`) ON DELETE CASCADE
       ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
   ```

1. Crie uma tabela **comentável** no esquema do banco de dados usando a seguinte instrução SQL:

   ```sql
   CREATE TABLE `commenttable` (
       `commentId` varchar(255) DEFAULT NULL,
       `comment` text DEFAULT NULL,
       `ID` varchar(255) DEFAULT NULL,
       `commentowner` varchar(255) DEFAULT NULL,
       `time` varchar(255) DEFAULT NULL);
   ```

### Configurar a conexão entre a instância do AEM e o banco de dados {#configure-connection-between-aem-instance-and-database}

Execute as seguintes etapas de configuração para criar uma conexão entre a instância do AEM e o banco de dados MYSQL:

1. Vá para a página Configuração do console da Web do AEM em *http://[host]:[port]/system/console/configMgr*.
1. Clique para abrir **[!UICONTROL Forms Portal Draft and Submission Configuration]** no modo de edição.
1. Especifique os valores para as propriedades conforme descrito na tabela a seguir:

   <table> 
    <tbody> 
    <tr> 
    <th><strong>Propriedade</strong></th> 
    <th><strong>Descrição</strong></th>
    <th><strong>Valor</strong></th> 
    </tr> 
    <tr> 
    <td><p>Serviço de Dados de Rascunho do Portal de Formulários</p></td> 
    <td><p>Identificador do serviço de dados preliminar</p></td>
    <td><p>formsportal.sampledataservice</p></td> 
    </tr>
    <tr> 
    <td><p>Serviço de Metadados de Rascunho do Portal de Formulários</p></td> 
    <td><p>Identificador do serviço de metadados de rascunho</p></td>
    <td><p>formsportal.samples emetadataservice</p></td> 
    </tr>
    <tr> 
    <td><p>Serviço de dados de envio do Portal de formulários</p></td> 
    <td><p>Identificador para enviar serviço de dados</p></td>
    <td><p>formsportal.sampledataservice</p></td> 
    </tr>
    <tr> 
    <td><p>Serviço de Metadados de Envio do Portal de Formulários</p></td> 
    <td><p>Identificador do serviço de metadados de envio</p></td>
    <td><p>formsportal.samples emetadataservice</p></td> 
    </tr>
    <tr> 
    <td><p>Serviço de Dados de Assinatura Pendente do Portal de Formulários</p></td> 
    <td><p>Identificador do serviço de dados de assinatura pendente</p></td>
    <td><p>formsportal.sampledataservice</p></td> 
    </tr>
    <tr> 
    <td><p>Serviço de Metadados de Assinatura Pendente do Portal de Formulários</p></td> 
    <td><p>Identificador do serviço de metadados de assinatura pendente</p></td>
    <td><p>formsportal.samples emetadataservice</p></td> 
    </tr>
    </tbody> 
    </table>
1. Deixe outras configurações como estão e clique em **[!UICONTROL Save]**.
1. Localize e clique em para abrir **[!UICONTROL Apache Sling Connection Pooled DataSource]** no modo de edição na Configuração do console da Web. Especifique os valores para as propriedades conforme descrito na tabela a seguir:

   <table> 
    <tbody> 
    <tr> 
    <th><strong>Propriedade</strong></th> 
    <th><strong>Valor</strong></th> 
    </tr> 
    <tr> 
    <td><p>Nome da fonte de dados</p></td> 
    <td><p>Um nome de fonte de dados para filtrar drivers do pool de fontes de dados. A implementação de amostra usa o FormsPortal como o nome da fonte de dados.</p></td>
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

### Configurar e configurar a amostra {#set-up-and-configure-sample}

Execute as seguintes etapas, em todas as instâncias de autor e publicação, para instalar e configurar a amostra:

1. Baixe o seguinte pacote **aem-fp-db-integration-sample-pkg-6.1.2.zip** no seu sistema de arquivos.

   [Obter arquivo](assets/aem-fp-db-integration-sample-pkg-6.1.2.zip)

1. Vá para o gerenciador de pacote AEM em *http://[host]:[port]/crx/packmgr/*.
1. Clique em **[!UICONTROL Upload Package]**.
1. Navegue para selecionar o pacote **aem-fp-db-integration-sample-pkg-6.1.2.zip** e clique em **[!UICONTROL OK]**.
1. Clique **[!UICONTROL Install]** ao lado do pacote para instalá-lo.

## Configurar o formulário adaptável convertido para integração com o Portal do Forms {#configure-converted-adaptive-form-for-forms-portal-integration}

Execute as seguintes etapas para habilitar o envio de formulário adaptável usando a página Portal de formulários:
1. [Execute a conversão](convert-existing-forms-to-adaptive-forms.md#start-the-conversion-process) para converter um formulário de origem em um formulário adaptável.
1. Abra o formulário adaptável no modo de edição.
1. Toque em Contêiner de formulário e selecione Configurar ![formulário](assets/configure-adaptive-form.png)adaptável.
1. Na **[!UICONTROL Submission]** seção, selecione **[!UICONTROL Forms Portal Submit Action]** na lista **[!UICONTROL Submit Action]** suspensa.
1. Toque em ![Salvar política](assets/edit_template_done.png) de modelo para salvar as configurações.

## Criar e configurar a página do Portal de formulários {#create-configure-forms-portal-page}

Execute as seguintes etapas para criar uma página do Portal de formulários e configurá-la para que você possa enviar formulários adaptáveis usando esta página:

1. Faça logon na instância do autor do AEM e toque em **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Sites]**.
1. Selecione o local onde deseja salvar a nova página do Portal de formulários e toque em **[!UICONTROL Create]** > **[!UICONTROL Page]**.
1. Selecione o modelo para a página, toque em **[!UICONTROL Next]**, especifique um título para a página e toque em **[!UICONTROL Create]**.
1. Toque em **[!UICONTROL Edit]** para configurar a página.
1. No cabeçalho da página, toque em ![Editar modelo](assets/edit_template_sites.png) > **[!UICONTROL Edit Template]** para abrir o modelo da página.
1. Toque em Contêiner de layout e toque em ![Editar política](assets/edit_template_policy.png)de modelo. Na **[!UICONTROL Allowed Components]** guia, ative as opções **[!UICONTROL Document Services]** e **[!UICONTROL Document Services Predicates]** e toque em ![Salvar política](assets/edit_template_done.png)de modelo.
1. Inserir **[!UICONTROL Search & Lister]** componente na página. Como resultado, todos os formulários adaptativos existentes disponíveis na sua instância do AEM são listados na página.
1. Inserir **[!UICONTROL Drafts & Submissions]** componente na página. Duas guias **[!UICONTROL Draft Forms]** e **[!UICONTROL Submitted Forms]**, são exibidas na página Portal de formulários. A **[!UICONTROL Draft Forms]** guia também exibe o formulário adaptativo convertido gerado usando as etapas mencionadas em [Configurar o formulário adaptativo convertido para integração com o Portal de formulários](#configure-converted-adaptive-form-for-forms-portal-integration)

1. Toque **[!UICONTROL Preview]**, toque no formulário adaptável convertido, especifique valores para campos de formulário adaptáveis e envie-o. Os valores especificados para campos de formulário adaptáveis são enviados ao banco de dados integrado.
