---
title: Configurar o serviço de conversão automática de formulários
description: Prepare sua instância AEM para usar o serviço de Automated forms conversion
translation-type: tm+mt
source-git-commit: 741ff89370a5215b70d90c49eea220171efe9339
workflow-type: tm+mt
source-wordcount: '2547'
ht-degree: 8%

---


# Configurar o serviço de conversão automática de formulários {#about-this-help}

Esta ajuda descreve como um administrador de AEM pode configurar o serviço de Automated forms conversion para automatizar a conversão de seus PDF forms em formulários adaptáveis. Esta ajuda é para administradores de TI e AEM em sua organização. As informações fornecidas baseiam-se no pressuposto de que qualquer pessoa que leia esta Ajuda está familiarizada com as seguintes tecnologias:

* Instalação, configuração e administração de pacotes Adobe Experience Manager e AEM,

* Usando sistemas operacionais Linux e Microsoft Windows,

* Configuração de servidores de correio SMTP

<!--- >[!VIDEO](https://video.tv.adobe.com/v/29267/) 

**Watch the video or read the article to configure Automated Forms Conversion service** -->

## Integração{#onboarding}

O serviço está disponível gratuitamente para clientes de vigência no local do AEM 6.4 Forms e AEM6.5 Forms e clientes corporativos do Adobe Managed Service. Você pode entrar em contato com a equipe de vendas da Adobe ou com seu representante da Adobe para solicitar acesso ao serviço.

A Adobe habilita o acesso para sua organização e fornece os privilégios necessários à pessoa designada como administrador em sua organização. O administrador pode conceder acesso aos desenvolvedores (usuários) do AEM Forms de sua organização para se conectar ao serviço.

## Pré-requisitos {#prerequisites}

É necessário o seguinte para usar o Serviço de Automated forms conversion:

* O serviço de automated forms conversion está habilitado para sua organização
* Uma conta Adobe ID com privilégios de administrador para o serviço de conversão
* Uma instância do autor AEM 6.4 ou AEM 6.5 com o Service Pack AEM mais recente
* Um usuário AEM (em sua instância AEM) que é membro do grupo de usuários de formulários

## Configurar o ambiente {#setuptheservice}

Antes de usar o serviço, prepare a instância do autor AEM para se conectar ao serviço em execução na Adobe Cloud. Execute as seguintes etapas na sequência listada para preparar sua instância para o serviço:

1. [Baixe e instale o AEM 6.4 ou o AEM 6.5](#aemquickstart)
1. [Baixe e instale o AEM Service Pack mais recente](#servicepack)
1. [Baixe e instale o pacote complementar AEM Forms mais recente](#downloadaemformsaddon)
1. (opcional) [Baixe e instale o pacote do conector mais recente](#installConnectorPackage)
1. [Criar temas e modelos personalizados](#referencepackage)

### Baixe e instale o AEM 6.4 ou o AEM 6.5 {#aemquickstart}


O serviço de automated forms conversion é executado AEM instância do autor. É necessário AEM 6.4 ou AEM 6.5 para configurar uma instância do autor AEM. Se você não tiver AEM funcionando, baixe-o dos seguintes locais:

* Se você for um cliente AEM existente, baixe AEM 6.4 ou AEM 6.5 do [site de licenciamento do Adobe](http://licensing.adobe.com).

* Se você for um parceiro Adobe, use [Programa Adobe Partner Training](https://adobe.allegiancetech.com/cgi-bin/qwebcorporate.dll?idx=82357Q) para solicitar AEM 6.4 ou AEM 6.5.

Depois de baixar o AEM, para obter instruções sobre como configurar uma instância do autor AEM, consulte [implantando e mantendo](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/deploy.html#defaultlocalinstall).

### Baixe e instale AEM Service Pack mais recente {#servicepack}

Baixe e instale o AEM Service Pack mais recente. Para obter instruções detalhadas, consulte [AEM 6.4 Notas de versão do Service Pack](https://helpx.adobe.com/experience-manager/6-4/release-notes/sp-release-notes.html) ou [AEM 6.5 Notas de versão do Service Pack](https://helpx.adobe.com/experience-manager/6-5/release-notes/sp-release-notes.html).

### Baixe e instale o pacote de complementos do AEM Forms {#downloadaemformsaddon}

Uma instância AEM contém recursos básicos de formulários. O serviço de conversão requer recursos completos da AEM Forms. Baixe e instale o pacote suplementar do AEM Forms para aproveitar todos os recursos do AEM Forms. O pacote é necessário para configurar e executar o serviço de conversão. Para obter instruções detalhadas, consulte [Instalar e configurar recursos de captura de dados.](https://helpx.adobe.com/experience-manager/6-5/forms/using/installing-configuring-aem-forms-osgi.html)

>[!NOTE]
> Certifique-se de executar as configurações obrigatórias pós-instalação depois de instalar o pacote suplementar.


### (Opcional) Download e instalação do pacote do conector {#installConnectorPackage}

O pacote do conector fornece acesso antecipado aos recursos e melhorias [Detectar automaticamente seções lógicas](convert-existing-forms-to-adaptive-forms.md#run-the-conversion) fornecidos na versão AFC-2020.03.1. Não instale o pacote se você não precisar do recurso e das melhorias fornecidas no AFC-2020.03.1.  Você pode [baixar o pacote do conector AEM Compartilhamento de pacotes](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/featurepack/AFCS-Connector-2020.03.1).


### Criar temas e modelos personalizados {#referencepackage}

Se você start AEM no [modo de produção](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/production-ready.html) (nosamplecontent runmode), os pacotes de referência não são instalados. Os pacotes de referência contêm temas e modelos de amostra. O serviço de automated forms conversion requer pelo menos um tema e um modelo para converter PDF forms em um formulário adaptável. Crie um tema e modelo personalizados próprios e aponte [configuração de serviço](#configure-the-cloud-service) para usar modelos e temas personalizados antes de usar o serviço.

## Configurar o serviço {#configure-the-service}

Antes de continuar a configurar o serviço e conectar sua instância local com o serviço em execução na Adobe Cloud, saiba mais sobre as pessoas e os privilégios necessários para se conectar ao serviço. O serviço usa dois tipos diferentes de personas, administradores e desenvolvedores:

* **Administradores**: Os administradores são responsáveis pelo gerenciamento de software e serviços de Adobe para sua organização. Os administradores concedem acesso aos desenvolvedores em sua organização para se conectarem ao serviço de Automated forms conversion executado na Adobe Cloud. Quando um administrador é provisionado para uma organização, o administrador recebe um email com o título **[!UICONTROL 'You now have administrator rights to manage Adobe software and services for your organization']**. Se você for um administrador, verifique seu email de caixa de correio com o título acima mencionado e vá para [conceder acesso aos desenvolvedores de sua organização](#adduseranddevs).

![email de concessão de acesso do administrador](assets/admin-console-adobe-io-access-grantedx75.png)

* **Desenvolvedores**: Um desenvolvedor conecta uma instância local do autor do AEM Forms ao serviço do Automated forms conversion em execução na Adobe Cloud. Quando um administrador concede direitos a um desenvolvedor para se conectar ao serviço do Automated forms conversion, um email com o título Você agora tem acesso de desenvolvedor para gerenciar integrações de API do Adobe para sua organização é enviado ao desenvolvedor. Se você for um desenvolvedor, procure em sua caixa de correio o email com o título mencionado e vá para [Conecte sua instância AEM local ao serviço do Automated forms conversion na Adobe Cloud.](#connectafcadobeio)

![email de concessão de acesso do desenvolvedor](assets/email-developer-accessx94.png)

### (Somente para administradores) Conceda acesso a desenvolvedores de sua organização {#adduseranddevs}

Depois que o Adobe ativar o acesso para sua organização e fornecer os privilégios necessários ao administrador, o administrador poderá fazer logon no Admin Console (instruções detalhadas abaixo), criar um perfil e adicionar desenvolvedores ao perfil. Os desenvolvedores podem conectar uma instância local do AEM Forms ao serviço do Automated forms conversion na Adobe Cloud.

Os desenvolvedores são membros de sua organização designados para executar o serviço de conversão. Somente os desenvolvedores adicionados ao perfil de serviço do Automated forms conversion têm direito a usar o serviço do Automated forms conversion. Execute as etapas abaixo para criar um perfil e adicionar desenvolvedores a ele. É necessário, no mínimo, um perfil para conceder o acesso necessário aos desenvolvedores de sua organização:

1. Faça logon em [Admin Console](https://adminconsole.adobe.com/). Use **Adobe ID** do administrador provisionado para usar o serviço de Automated forms conversion para fazer logon. Não faça logon com outra ID ou Federated ID.
1. Clique na opção **[!UICONTROL Automated Forms Conversion]**.
1. Clique em **[!UICONTROL New Profile]** na guia **[!UICONTROL Products]**.
1. Especifique **[!UICONTROL Name]**, **[!UICONTROL Display Name]** e **[!UICONTROL Description]** para o perfil. Clique em **[!UICONTROL Done]**. Um perfil é criado.

   ![Especifique detalhes para o novo perfil.](assets/create-new-profile-details.png)

1. Adicione desenvolvedor ao perfil. Para adicionar os desenvolvedores:
   1. Na [Admin Console](https://adminconsole.adobe.com/enterprise), navegue até a guia Visão geral.
   1. Clique em **[!UICONTROL Assign Developers]** no cartão de produto desejado.
   1. Insira o endereço de email dos desenvolvedores e, opcionalmente, o nome e o sobrenome.
   1. Selecione perfis de produtos. Tocar **[!UICONTROL Save]**.

Repita as etapas acima para todos os usuários.  Para obter mais detalhes sobre como adicionar desenvolvedores, consulte [Gerenciar desenvolvedores](https://helpx.adobe.com/enterprise/using/manage-developers.html).

Quando um administrador adiciona desenvolvedores ao perfil Adobe I/O, eles são notificados por email. Depois de receber o email, os desenvolvedores podem continuar a [conectar uma instância local do AEM Forms com o serviço de Automated forms conversion na Adobe Cloud](#connectafcadobeio).

### (Somente para desenvolvedores) Conecte sua instância local do AEM Forms ao serviço de Automated forms conversion na Adobe Cloud {#connectafcadobeio}

Depois que um administrador fornecer acesso de desenvolvedor, você poderá conectar sua instância local do AEM Forms ao serviço de Automated forms conversion em execução na Adobe Cloud. Execute as seguintes etapas na sequência listada para conectar sua instância do AEM Forms ao serviço:

* [Configurar notificações por email](configure-service.md#configureemailnotification)
* [Adicionar usuário ao grupo de usuários de formulários](#adduserstousergroup)
* [Obter certificados públicos](#obtainpubliccertificates)
* [Configure as APIs de serviço no Console do desenvolvedor do Adobe](#createintegration)
* [Configurar o serviço de nuvem](configure-service.md#configure-the-cloud-service)

#### Configurar notificação por email {#configureemailnotification}

O serviço Automated forms conversion usa o serviço de correio Day CQ para enviar notificações por email. Essas notificações por email contêm informações sobre conversões bem-sucedidas ou com falha. Se você escolher não receber notificação, ignore essas etapas. Execute as seguintes etapas para configurar o Day CQ Mail Service:

1. Vá para AEM gerenciador de configuração em `http://localhost:4502/system/console/configMgr`
1. Abra a configuração do serviço Day CQ Mail. Especifique um valor para os campos **[!UICONTROL SMTP server host name]**, **[!UICONTROL SMTP server port]** e **[!UICONTROL From address]**. Clique em **[!UICONTROL Save]**.

   Você pode entrar em contato com seu provedor de serviço de email ou administrador de TI para obter informações sobre o nome do host e a porta do servidor SMTP. Você pode usar qualquer endereço de email válido no campo de formulário. Por exemplo, notification@example.com ou donotreply@example.com.

1. Abra a configuração **[!UICONTROL Day CQ Link Externalizer]**. No campo **[!UICONTROL Domains]**, especifique o nome do host ou endereço IP real e o número da porta para instâncias locais, de autor e de publicação. Clique em **[!UICONTROL Save]**.

#### Adicionar usuário ao grupo de usuários de formulários {#adduserstousergroup}

Especifique um endereço de email no perfil do usuário AEM designado para executar o serviço. Certifique-se de que o usuário seja membro do grupo [usuário](https://helpx.adobe.com/experience-manager/6-4/forms/using/forms-groups-privileges-tasks.html) de formulários. Os emails são enviados para o endereço de email do usuário que está executando a conversão. Para especificar um endereço de email para o usuário e adicionar o usuário ao grupo de usuários`e formulários:

1. Faça logon na instância do autor do AEM Forms como um administrador AEM. Use suas credenciais AEM locais para fazer logon. Não use o Adobe ID para fazer login. Toque em **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Users]**.

1. Selecione um usuário designado para executar o serviço de conversão e toque em **[!UICONTROL Properties]**. A página Editar configurações do usuário é aberta.
1. Especifique um endereço de email no campo **[!UICONTROL Email]** e toque em **[!UICONTROL Save]**. Os e-mails são enviados para o endereço de e-mail especificado após a conclusão ou falha da conversão.
1. Toque na guia **Grupos**. Na guia Selecionar grupo, digite e selecione o grupo **forms-users**. Toque em **Salvar e fechar**. O usuário agora é membro do grupo de usuários de formulários.

#### Obter certificados públicos {#obtainpubliccertificates}

Um certificado público permite autenticar seu perfil no Adobe I/O.

1. Faça logon na instância do autor do AEM Forms. Vá até **[!UICONTROL Tools]**> **[!UICONTROL Security]** > **[!UICONTROL Adobe IMS Configurations]**. Tocar **[!UICONTROL Create]**. A página **[!UICONTROL Adobe IMS Technical Account Configuration]** é exibida.

   ![A página Configuração técnica da conta do Adobe IMS](assets/adobe-ims-technical-account-configuration.png)

1. Selecione **[!UICONTROL Automated Forms Conversion Service]** na Solução em nuvem.

1. Marque a caixa de seleção **[!UICONTROL Create new certificate]** e especifique um alias. O alias atua como nome da caixa de diálogo. Tocar **[!UICONTROL Create certificate]**. Uma caixa de diálogo é exibida. Clique em **[!UICONTROL OK]**. O certificado é criado.

1. Toque em **[!UICONTROL Download Public Key]** e salve o arquivo de certificado *AEM-Adobe-IMS.crt* no computador. O arquivo de certificado é usado para [Configurar as APIs de serviço no Console de desenvolvedor do Adobe](#createintegration). Tocar **[!UICONTROL Next]**.

1. Especifique o seguinte:

   * Título: Especifique um título.
   * Servidor de autorização: [https://ims-na1.adobelogin.com](https://ims-na1.adobelogin.com)\

   Deixe os outros campos em branco por enquanto (a ser fornecido posteriormente). Mantenha a página aberta.

   <!--
   Comment Type: draft

   <li> </li>
   -->

   <!--
   Comment Type: draft

   <li>Step text</li>
   -->

#### Configure as APIs de serviço no Console do desenvolvedor do Adobe {#createintegration}

Para usar o serviço de Automated forms conversion, crie um projeto e adicione a Automated Forms Configuration Service API ao projeto no Adobe Developer Console. A integração gera a chave da API, o segredo do cliente, a carga (JWT).

1. Faça logon em [https://console.adobe.io/](https://console.adobe.io/). Use sua conta de desenvolvedor Adobe ID que seu administrador provisionou para fazer login no console do Adobe I/O para fazer login.
1. Selecione sua organização no canto superior direito. Se não souber sua organização, entre em contato com o administrador.
1. Tocar **[!UICONTROL Create new project]**. Uma tela para começar a usar seu novo projeto é exibida. Tocar **[!UICONTROL Add API]**. Uma tela com lista de todas as APIs ativadas para sua conta é exibida.
1. Selecione **[!UICONTROL Automated Forms Conversion service]** e toque em **[!UICONTROL Next]**. Uma tela para configurar a API é exibida.
1. Selecione a opção [!UICONTROL Upload your public key], carregue o arquivo AEM-Adobe-IMS.crt baixado na seção [Obter certificados públicos](#obtainpubliccertificates) e toque em **[!UICONTROL Next]**. A opção Criar uma nova credencial de conta de serviço (JWT) é exibida. Tocar **[!UICONTROL Next]**.
1. Selecione um Perfil de produto e toque em **[!UICONTROL Save configured API]**. Selecione o perfil criado enquanto [concede acesso aos desenvolvedores de sua organização](#adduseranddevs). Se você não souber o perfil a ser selecionado, entre em contato com o administrador.
1. Toque em **[!UICONTROL Service Account (JWT)]** para visualização a chave da API, o segredo do cliente e outras informações necessárias para conectar sua instância AEM local ao serviço de Automated forms conversion. As informações na página são usadas para criar a configuração IMS na máquina local.

1. Abra a página Configuração IMS na instância local. Você manteve a página aberta no final da seção, [Obter certificado público](#obtainpubliccertificates).

   ![Especificar título, chave da API, segredo do cliente e carga  ](assets/ims-configuration-details.png)

1. Na página Técnica do Adobe IMS, especifique a chave da API e o segredo do cliente. Use os valores especificados em Service Account (JWT) da página do console do Desenvolvedor do Adobe.

   >[!NOTE]
   >
   >
   >Para a carga, use o código fornecido na guia Gerar JWT da página Conta de serviço (JWT) do Console do desenvolvedor do Adobe.

1. Tocar **[!UICONTROL Save]**. A configuração IMS é criada.

   >[!CAUTION]
   >
   >Crie apenas uma configuração IMS. Não crie mais de uma configuração IMS.

1. Selecione a configuração IMS e toque em **[!UICONTROL Check Health]**. Uma caixa de diálogo é exibida. Tocar **[!UICONTROL Check]**. Ao se conectar com êxito, a mensagem *Token recuperado com êxito* é exibida.

   ![Na conexão bem-sucedida, a mensagem do token recuperado com êxito é exibida.  ](assets/health-check.png)

   <br/> <br/>

#### Configurar o serviço de nuvem {#configure-the-cloud-service}

Crie uma configuração de serviço em nuvem para conectar sua instância de AEM ao serviço de conversão. Também permite especificar um modelo, tema e fragmentos de formulário para uma conversão. É possível criar várias configurações de serviço em nuvem separadas para cada conjunto de formulários. Por exemplo, você pode ter uma configuração separada para formulários do departamento de vendas e outra separada para formulários de suporte ao cliente. Execute as seguintes etapas para criar uma configuração de serviço em nuvem:

1. Na instância do AEM Forms, toque em **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Tools]**> **[!UICONTROL Cloud Services]** > **[!UICONTROL Automate Forms Conversion Configuration]**.
1. Toque na pasta **[!UICONTROL Global]** e toque em **[!UICONTROL Create]**. A página para criar a configuração do Automated forms conversion é exibida. A configuração é criada na pasta Global. Você também pode criar a configuração em uma pasta diferente que já existe ou criar uma nova pasta para suas configurações.

1. Na página **[!UICONTROL Create Automated Forms Conversion Configuration]**, especifique o valor para os seguintes campos e toque em **[!UICONTROL Next]**.

   | Texto | Descrição |
   |--- |--- |
   | Título | Título exclusivo para a configuração. O título é exibido na interface do usuário usada para conversão de start. |
   | Nome | Nome exclusivo para a configuração. A configuração é salva no CRX-Repository com o nome especificado. O nome pode ser idêntico ao título. |
   | Localização em miniatura | Localização da miniatura da configuração. |
   | URL do serviço | URL do serviço de Automated forms conversion na Adobe Cloud. Use o URL `https://aemformsconversion.adobe.io/`. |
   | Modelo | Modelo padrão a ser aplicado aos formulários convertidos. Você sempre pode especificar um modelo diferente antes de iniciar a conversão. Um modelo contém estrutura básica e conteúdo inicial para um formulário adaptável. Você pode escolher um modelo dos modelos fornecidos prontos para uso. Você também pode criar um modelo personalizado. |
   | Tema | O tema padrão a ser aplicado aos formulários convertidos. Você sempre pode especificar um tema diferente antes de iniciar a conversão.  Você pode clicar no ícone para escolher um tema fornecido fora da caixa. Você também pode criar um tema personalizado. |
   | Fragmentos existentes | Localização dos fragmentos existentes, se houver. |
   | Meta-modelo personalizado | Caminho do arquivo .schema.json do metrosmodelo personalizado. |



1. Na guia **[!UICONTROL Advanced]** da página **[!UICONTROL Create Automated Forms Conversion Configuration]**, especifique o valor para o seguinte campo:

   <table>
   <thead>
   <tr>
   <th>Texto</th>
   <th>Descrição</th>
   </tr>
   </thead>
   <tbody>
   <tr>
   <td >Gerar documento de registro</td>
   <td>Selecione a opção para gerar automaticamente o Documento de Registro para formulários convertidos. A opção é somente para formulários baseados em XFA (XDP e PDF forms). Ao ativar a opção, após enviar um formulário, é possível permitir que seus clientes mantenham um registro, em formato impresso ou em formato de documento, das informações que preencheram no formulário para referência futura. Isso é conhecido como um documento de registro.</td>
   </tr>
   <tr>
   <td>Ativar Analytics</td>
   <td>Selecione a opção para ativar o Adobe Analytics em todos os formulários convertidos. Antes de usar a opção, verifique se o Adobe Analytics está habilitado para sua instância do AEM Forms.</td>
   </tr>
   </tbody>
   </table>

   * Quando a fonte é um formulário baseado em XFA com extensão .XDP, o DOR de saída retém o layout XFA; caso contrário, o serviço de conversão usa um modelo predefinido para gerar DOR para outros formulários baseados em XFA.
   * Quando um formulário XFA é enviado, os dados de envio do formulário são salvos como um elemento XML ou um atributo. Por exemplo, `<Amount currency="USD"> 10.00 </Amount>`. A moeda é salva como um atributo e valor monetário, 10,00 é salvo como um elemento. Enviar dados de um formulário adaptável não tem atributos, tem apenas elementos. Portanto, quando um formulário baseado em XFA é convertido em formulário adaptável, os dados de envio do formulário adaptável contêm um elemento para cada atributo. Por exemplo,

   ```css
      {
         "Type": "Principal",
   
         "Amount": "10.00",
   
         "currency": "USD"
      }
   ```

1. Tocar **[!UICONTROL Create]**. A configuração da nuvem é criada. Sua instância do AEM Forms está pronta para start, convertendo formulários legados em formulários adaptáveis.
