---
title: Configurar o serviço de conversão automática de formulários
description: Prepare sua instância do AEM para usar o serviço do Automated forms conversion
role: User, Admin
exl-id: 8f21560f-157f-41cb-ba6f-12a4d6e18555
source-git-commit: 47261710e6616c27c210ac53bffcc2387a06ea7a
workflow-type: tm+mt
source-wordcount: '2684'
ht-degree: 6%

---

# Configurar o serviço de conversão automática de formulários {#about-this-help}

Esta ajuda descreve como um administrador do AEM pode configurar o serviço do Automated forms conversion para automatizar a conversão de seus PDF forms em formulários adaptáveis. Esta ajuda é para administradores de TI e AEM em sua organização. As informações fornecidas baseiam-se na suposição de que qualquer pessoa que leia esta Ajuda está familiarizada com as seguintes tecnologias:

* Instalação, configuração e administração de pacotes Adobe Experience Manager e AEM,

* Usando os sistemas operacionais Linux® e Microsoft® Windows®,

* Configurando servidores de email SMTP

<!--- >[!VIDEO](https://video.tv.adobe.com/v/29267/) 

**Watch the video or read the article to configure Automated Forms Conversion service** -->

## Integração{#onboarding}

O serviço está disponível gratuitamente para clientes de vigência no local AEM 6.4 Forms e AEM 6.5 Forms e clientes corporativos de serviço gerenciado Adobe. Você pode entrar em contato com a equipe de vendas da Adobe ou com seu representante da Adobe para solicitar acesso ao serviço. O serviço também está disponível gratuitamente e é pré-ativado para clientes do AEM Forms as a Cloud Service.

A Adobe habilita o acesso para sua organização e fornece os privilégios necessários à pessoa designada como administrador em sua organização. O administrador pode conceder acesso aos desenvolvedores (usuários) do AEM Forms de sua organização para se conectar ao serviço.

## Pré-requisitos {#prerequisites}

Você precisa do seguinte para usar o Automated forms conversion Service:

* O serviço Automated forms conversion está habilitado para sua organização
* Uma conta do Adobe ID com privilégios de administrador para o serviço de conversão
* Uma instância de autor ativa e em execução do AEM 6.4, AEM 6.5 ou AEM Forms as a Cloud Service AEM com o Service Pack mais recente do ou as atualizações mais recentes.
* Um usuário AEM (na instância AEM) que é membro do grupo de usuários de formulários

## Configurar o ambiente {#setuptheservice}

Antes de usar o serviço, prepare a instância do autor do AEM para se conectar ao serviço em execução na Adobe Cloud. Execute as seguintes etapas na sequência listada para preparar sua instância para o serviço:

1. [Baixe e instale o AEM 6.4, AEM 6.5 ou o AEM Forms as a Cloud Service integrado](#aemquickstart)
1. [Baixe e instale o Service Pack mais recente do AEM](#servicepack)
1. [Baixe e instale o pacote complementar mais recente do AEM Forms](#downloadaemformsaddon)
1. (opcional) [Baixe e instale o pacote de conectores mais recente](#installConnectorPackage)
1. [Criar temas e modelos personalizados](#referencepackage)

### Baixe e instale o AEM 6.4, AEM 6.5 ou o AEM Forms as a Cloud Service integrado {#aemquickstart}


O serviço Automated forms conversion é executado na instância do autor AEM. Você precisa do AEM 6.4, AEM 6.5 ou do AEM Forms as a Cloud Service AEM para configurar uma instância de autor do.

* Se você não tiver o AEM 6.4 ou AEM 6.5 ativo e em execução, baixe-o dos locais abaixo. Depois de baixar o AEM, para obter instruções sobre como configurar uma instância de autor AEM, consulte [implantação e manutenção](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/deploy.html#defaultlocalinstall).:

   * Se você for um cliente AEM existente, baixe AEM 6.4 ou AEM 6.5 de [Site de licenciamento do Adobe](http://licensing.adobe.com).

   * Se você for um parceiro de Adobe, use [Programa de treinamento para parceiros Adobe](https://adobe.allegiancetech.com/cgi-bin/qwebcorporate.dll?idx=82357Q) para solicitar o AEM 6.4 ou AEM 6.5.

* Se você estiver usando o AEM Forms as a Cloud Service, consulte a bordo para [AEM Forms as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/setup-environment/setup-forms-cloud-service.html?lang=en#setup-environment) e [configurar um ambiente de desenvolvimento local](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/setup-environment/setup-local-development-environment.html?lang=en#setup-environment).

### (Somente para AEM 6.4 e AEM 6.5) Baixar e instalar o AEM Service Pack mais recente {#servicepack}

Baixe e instale o AEM Service Pack mais recente. Para obter instruções detalhadas, consulte ou [Notas de versão do AEM 6.4 Service Pack](https://helpx.adobe.com/br/experience-manager/6-4/release-notes/sp-release-notes.html) ou [Notas de versão do AEM 6.5 Service Pack](https://helpx.adobe.com/br/experience-manager/6-5/release-notes/sp-release-notes.html).

### (Somente para AEM 6.4 e AEM 6.5) Baixar e instalar o pacote complementar do AEM Forms  {#downloadaemformsaddon}

Uma instância do AEM contém recursos básicos de formulários. O serviço de conversão exige todos os recursos do AEM Forms. Baixe e instale o pacote complementar do AEM Forms para aproveitar todos os recursos do AEM Forms. O pacote é necessário para configurar e executar o serviço de conversão. Para obter instruções detalhadas, consulte [Instalar e configurar recursos de captura de dados.](https://helpx.adobe.com/br/experience-manager/6-5/forms/using/installing-configuring-aem-forms-osgi.html)

>[!NOTE]
> Execute as configurações obrigatórias após a instalação do pacote complementar.

<!-- ### (Optional) Download and install connector package  {#installConnectorPackage}

The connector package provides early access to the [Auto-detect logical sections](convert-existing-forms-to-adaptive-forms.md#run-the-conversion) features and improvements delivered in release AFC-2020.03.1. Do not install the package if you do not require feature and improvements delivered in AFC-2020.03.1.  You can [download the connector package from AEM Package Share](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/featurepack/AFCS-Connector-2020.03.1). -->


### Criar temas e modelos personalizados {#referencepackage}

Se você iniciar o AEM 6,4 ou AEM 6,5 pol [modo de produção](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/production-ready.html) (modo de execução nosamplecontent), os pacotes de referência não são instalados. Os pacotes de referência contêm exemplos de temas e modelos. O serviço Automated forms conversion requer pelo menos um tema e um modelo para converter um formulário PDF em um formulário adaptável. Crie um tema e um modelo personalizados para você mesmo e aponte [configuração do serviço](#configure-the-cloud-service) para usar modelos e temas personalizados antes de usar o serviço.

Você também pode baixar e instalar o [Ativos de referência do AEM Forms](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) pacote na sua instância do Author. Ele cria alguns temas de referência e template.

## Configurar o serviço {#configure-the-service}

Antes de continuar a configurar o serviço e conectar sua instância local ao serviço em execução na Adobe Cloud, saiba mais sobre as personas e os privilégios necessários para se conectar ao serviço. O serviço usa dois tipos diferentes de personas, administradores e desenvolvedores:

* **Administradores**: os administradores são responsáveis pelo gerenciamento de software e serviços Adobe para sua organização. Os administradores concedem acesso aos desenvolvedores em sua organização para se conectarem ao serviço do Automated forms conversion em execução na Adobe Cloud. Quando um administrador é provisionado para uma organização, o administrador recebe um email com o título **[!UICONTROL 'You now have administrator rights to manage Adobe software and services for your organization']**. Se você for um administrador, verifique se há emails na sua caixa de correio com o título mencionado anteriormente e prossiga para [conceder acesso aos desenvolvedores de sua organização](#adduseranddevs).

![Email de concessão de acesso de administrador](assets/admin-console-adobe-io-access-grantedx75.png)

* **Desenvolvedores**: um desenvolvedor conecta uma instância de autor local do AEM Forms ao serviço do Automated forms conversion em execução na Adobe Cloud. Quando um administrador concede direitos a um desenvolvedor para se conectar ao serviço do Automated forms conversion, um email com o título Você agora tem acesso de desenvolvedor para gerenciar integrações de API do Adobe para sua organização é enviado ao desenvolvedor. Se você for um desenvolvedor, verifique se há emails em sua caixa de entrada com o título mencionado anteriormente e prossiga para [Conecte sua instância local do AEM ao serviço do Automated forms conversion na Adobe Cloud.](#connectafcadobeio)

![Email de concessão de acesso do desenvolvedor](assets/email-developer-accessx94.png)

### (Somente para administradores do AEM 6.4 e AEM 6.5) Conceder acesso aos desenvolvedores de sua organização {#adduseranddevs}

Depois que o Adobe habilitar o acesso para sua organização e fornecer os privilégios necessários ao administrador, este poderá fazer logon no Admin Console (instruções detalhadas abaixo), criar um perfil e adicionar desenvolvedores ao perfil. Os desenvolvedores podem conectar uma instância local do AEM Forms ao serviço do Automated forms conversion na Adobe Cloud.

Desenvolvedores são membros de sua organização designados para executar o serviço de conversão. Somente os desenvolvedores adicionados ao perfil de serviço do Adobe Automated forms conversion têm direito a usar o serviço do Automated forms conversion. Execute as etapas abaixo para criar um perfil e adicionar desenvolvedores a ele. É necessário pelo menos um perfil para conceder o acesso necessário aos desenvolvedores de sua organização:

1. Efetue logon no [Admin Console](https://adminconsole.adobe.com/). Uso **Adobe ID** de administradores provisionados para usar o serviço Automated forms conversion para fazer logon. Não use outra ID ou Federated ID para fazer logon.
1. Clique em **[!UICONTROL Automated Forms Conversion]** opção.
1. Clique em **[!UICONTROL New Profile]** no **[!UICONTROL Products]** guia.
1. Especificar **[!UICONTROL Name]**, **[!UICONTROL Display Name]**, e **[!UICONTROL Description]** para o perfil. Clique em **[!UICONTROL Done]**. Um perfil é criado.

   ![Especifique os detalhes do novo perfil.](assets/create-new-profile-details.png)

1. Adicionar desenvolvedor ao perfil. Para adicionar os desenvolvedores:
   1. No [Admin Console](https://adminconsole.adobe.com/enterprise), navegue até a guia Visão geral.
   1. Clique em **[!UICONTROL Assign Developers]** no cartão de produto necessário.
   1. Insira o endereço de email dos desenvolvedores e, opcionalmente, o nome e sobrenome.
   1. Selecione perfis de produto. Toque **[!UICONTROL Save]**.

Repita as etapas acima para todos os usuários. Para obter mais detalhes sobre como adicionar desenvolvedores, consulte [Gerenciar desenvolvedores](https://helpx.adobe.com/enterprise/using/manage-developers.html).

Depois que um administrador adiciona desenvolvedores ao perfil Adobe I/O, eles são notificados por email. Após receber o email, os desenvolvedores podem prosseguir para [conectar uma instância do AEM Forms local com o serviço Automated forms conversion na Adobe Cloud](#connectafcadobeio).

### (Somente para desenvolvedores) Conecte sua instância local do AEM Forms ao serviço do Automated forms conversion na Adobe Cloud {#connectafcadobeio}

Depois que um administrador fornecer acesso de desenvolvedor, você poderá conectar sua instância do AEM Forms local ao serviço do Automated forms conversion em execução na Adobe Cloud. Execute as seguintes etapas na sequência listada para conectar sua instância do AEM Forms ao serviço:

* [Configurar notificações por email](configure-service.md#configureemailnotification)
* [Adicionar usuário ao grupo de formulários-usuários](#adduserstousergroup)
* [Obter certificados públicos](#obtainpubliccertificates)
* [Configurar as APIs de serviço no console do Adobe Developer](#createintegration)
* [Configurar o serviço em nuvem](configure-service.md#configure-the-cloud-service)

#### Configurar notificação por email {#configureemailnotification}

O serviço do Automated forms conversion usa o serviço de email Day CQ para enviar notificações por email. Essas notificações por email contêm informações sobre conversões bem-sucedidas ou com falha. Se você optar por não receber a notificação, ignore essas etapas. Execute as seguintes etapas para configurar o Day CQ Mail Service:

* Para AEM 6.4 Forms ou AEM 6.5 Forms:

   1. Vá para o gerenciador de configuração do AEM em `http://localhost:4502/system/console/configMgr`
   1. Abra a configuração do Day CQ Mail Service. Especifique um valor para o **[!UICONTROL SMTP server host name]**, **[!UICONTROL SMTP server port]**, e **[!UICONTROL From address]** campos. Clique em **[!UICONTROL Save]**.

      Você pode entrar em contato com seu provedor de serviços de e-mail ou administrador de TI para obter informações sobre o nome do host e a porta do servidor SMTP. Você pode usar qualquer endereço de email válido no campo de. Por exemplo, notification@example.com ou donotreply@example.com.

   1. Abra o **[!UICONTROL Day CQ Link Externalizer]** configuração. No **[!UICONTROL Domains]** especifique o nome do host real ou o endereço IP e o número da porta para as instâncias locais, de criação e de publicação. Clique em **[!UICONTROL Save]**.

* Para o AEM Forms as a Cloud Service, [registrar um tíquete de suporte para habilitar o serviço de email](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=en#sending-email).

#### Adicionar usuário ao grupo de formulários-usuários {#adduserstousergroup}

Especifique um endereço de email no perfil do usuário AEM designado para executar o serviço. Certifique-se de que o usuário é o membro do [usuário de formulários](https://experienceleague.adobe.com/docs/experience-manager-65/forms/manage-administer-aem-forms/forms-groups-privileges-tasks.html) grupo. Os emails são enviados para o endereço de email do usuário que está executando a conversão. Para especificar um endereço de email para o usuário e adicionar o usuário ao grupo de usuários de formulários:

1. Faça logon na instância de autor do AEM Forms como administrador AEM. Use suas credenciais locais do AEM para fazer logon. Não use o Adobe ID para fazer logon. Toque **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Users]**.

1. Selecione um usuário designado para executar o serviço de conversão e toque em **[!UICONTROL Properties]**. A página Editar configurações do usuário é aberta.
1. Especifique um endereço de email no **[!UICONTROL Email]** e toque em **[!UICONTROL Save]**. Os emails são enviados para o endereço de email especificado após a conclusão bem-sucedida ou a falha da conversão.
1. Toque no **Grupos** guia. Na guia Selecionar grupo, digite e selecione o **forms-users** grupo. Toque **Salvar e fechar**. O usuário agora é membro do grupo de formulários-usuários.

#### (Somente para AEM 6.4 e AEM 6.5) Obter certificados públicos {#obtainpubliccertificates}

Um certificado público permite autenticar seu perfil no Adobe I/O.

1. Faça logon na instância de autor do AEM Forms. Vá até **[!UICONTROL Tools]**> **[!UICONTROL Security]** > **[!UICONTROL Adobe IMS Configurations]**. Toque **[!UICONTROL Create]**. A variável **[!UICONTROL Adobe IMS Technical Account Configuration]** é exibida.

   ![A página Configuração de conta técnica do Adobe IMS](assets/adobe-ims-technical-account-configuration.png)

1. Selecionar **[!UICONTROL Automated Forms Conversion Service]** na Solução da nuvem.

1. Selecione o **[!UICONTROL Create new certificate]** e especifique um alias. O alias atua como nome da caixa de diálogo. Toque **[!UICONTROL Create certificate]**. Uma caixa de diálogo é exibida. Clique em **[!UICONTROL OK]**. O certificado é criado.

1. Toque **[!UICONTROL Download Public Key]** e salve a variável *AEM-Adobe-IMS.crt* arquivo de certificado na sua máquina. O arquivo de certificado é usado para [Configurar as APIs de serviço no console do Adobe Developer](#createintegration). Toque **[!UICONTROL Next]**.

1. Especifique os seguintes:

   * Título: especifique um título.
   * Servidor de autorização: [https://ims-na1.adobelogin.com](https://ims-na1.adobelogin.com)\

   Deixe os outros campos em branco por enquanto (a serem fornecidos posteriormente). Mantenha a página aberta.

   <!--
   Comment Type: draft

   <li> </li>
   -->

   <!--
   Comment Type: draft

   <li>Step text</li>
   -->

#### (Somente para AEM 6.4 e AEM 6.5) Configure as APIs de serviço no console do Adobe Developer {#createintegration}

Para usar o serviço do Automated forms conversion, crie um projeto e adicione a API do serviço de configuração automatizado do Forms ao projeto no console da Adobe Developer. A integração gera a chave da API, o segredo do cliente e a carga (JWT).

1. Efetue logon no [https://console.adobe.io/](https://console.adobe.io/). Use sua conta de desenvolvedor do Adobe ID provisionada pelo administrador para fazer logon no console do Adobe I/O para fazer logon.
1. Selecione sua organização no canto superior direito. Se não souber sua organização, entre em contato com o administrador.
1. Toque **[!UICONTROL Create new project]**. Uma tela para começar a usar o novo projeto é exibida. Toque **[!UICONTROL Add API]**. Uma tela com a lista de todas as APIs ativadas para sua conta é exibida.
1. Selecionar **[!UICONTROL Automated Forms Conversion service]** e toque em **[!UICONTROL Next]**. Uma tela para configurar a API é exibida.
1. Selecione o [!UICONTROL Upload your public key] , carregue o arquivo AEM-Adobe-IMS.crt baixado na [Obter certificados públicos](#obtainpubliccertificates) seção e toque em **[!UICONTROL Next]**. A opção Criar uma nova credencial de conta de serviço (JWT) é exibida. Toque **[!UICONTROL Next]**.
1. Selecione um perfil de produto e toque em **[!UICONTROL Save configured API]**. Selecione o perfil criado enquanto [conceder acesso aos desenvolvedores de sua organização](#adduseranddevs). Caso não saiba o perfil a ser selecionado, entre em contato com o administrador.
1. Toque **[!UICONTROL Service Account (JWT)]** para visualizar a chave da API, o segredo do cliente e outras informações necessárias para conectar sua instância do AEM local ao serviço do Automated forms conversion. As informações na página são usadas para criar a configuração IMS no computador local.

1. Abra a página Configuração IMS na instância local. Você manteve a página aberta no final da seção, [Obter certificado público](#obtainpubliccertificates).

   ![Especifique o Título, a Chave da API, o Segredo do cliente e a carga ](assets/ims-configuration-details.png)

1. Na página Técnica do Adobe IMS, especifique a Chave da API e o Segredo do cliente. Use os valores especificados na Conta de serviço (JWT) da página do console do Adobe Developer.

   >[!NOTE]
   >
   >
   >Para carga útil, use o código fornecido na guia Gerar JWT da página Conta de Serviço (JWT) do Console do Adobe Developer.

1. Toque **[!UICONTROL Save]**. A configuração IMS é criada.

   >[!CAUTION]
   >
   >Crie apenas uma configuração IMS. Não crie mais de uma configuração IMS.

1. Selecione a configuração IMS e toque em **[!UICONTROL Check Health]**. Uma caixa de diálogo é exibida. Toque **[!UICONTROL Check]**. Ao se conectar com êxito, a mensagem *Token recuperado com êxito* é exibida.

   ![Ao se conectar com êxito, a mensagem token recuperado com êxito é exibida. ](assets/health-check.png)

   <br/> <br/>

#### Configurar o Cloud Service {#configure-the-cloud-service}

Crie uma configuração de Cloud Service para conectar sua instância AEM ao serviço de conversão. Também permite especificar um modelo, tema e fragmentos de formulário para uma conversão. Você pode criar várias configurações do Cloud Service separadas para cada conjunto de formulários. Por exemplo, você pode ter uma configuração separada para formulários do departamento de vendas e outra separada para formulários de suporte ao cliente. Execute as seguintes etapas para criar uma configuração do Cloud Service:

1. Na instância do AEM Forms, toque em **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Tools]**> **[!UICONTROL Cloud Services]** > **[!UICONTROL Automate Forms Conversion Configuration]**.
1. Toque no **[!UICONTROL Global]** pasta e toque em **[!UICONTROL Create]**. A página para criar a configuração do Automated forms conversion é exibida. A configuração é criada na pasta Global. Você também pode criar a configuração em uma pasta diferente que exista ou criar uma pasta para suas configurações.

1. No **[!UICONTROL Create Automated Forms Conversion Configuration]** especifique o valor para os seguintes campos e toque em **[!UICONTROL Next]**.

   | Texto | Descrição |
   |--- |--- |
   | Título | Título exclusivo da configuração. O título é exibido na interface usada para iniciar a conversão. |
   | Nome | Nome exclusivo da configuração. A configuração é salva no repositório CRX com o nome especificado. O nome pode ser idêntico ao título. |
   | Local da miniatura | Local da miniatura da configuração. |
   | URL do serviço | URL do serviço Automated forms conversion na Adobe Cloud. Use o `https://aemformsconversion.adobe.io/` URL. |
   | Modelo | Modelo padrão a ser aplicado aos formulários convertidos. Você sempre pode especificar um modelo diferente antes de iniciar a conversão. Um modelo contém a estrutura básica e o conteúdo inicial de um formulário adaptável. Você pode escolher um modelo entre os modelos fornecidos prontos para uso. Você também pode criar um modelo personalizado. |
   | Tema | Tema padrão a ser aplicado aos formulários convertidos. Você sempre pode especificar um tema diferente antes de iniciar a conversão.  Você pode clicar no ícone para escolher um tema fornecido imediatamente. Você também pode criar um tema personalizado. |
   | Fragmentos existentes | Local dos fragmentos existentes, se houver. |
   | Modelo meta personalizado | Caminho do arquivo .schema.json do modelo meta personalizado. É possível criar metamodelos separados para inglês, francês, alemão, espanhol, italiano e português. |

1. No **[!UICONTROL Advanced]** guia do **[!UICONTROL Create Automated Forms Conversion Configuration]** especifique o valor para o seguinte campo:

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
   <td>Selecione a opção para gerar automaticamente o Documento de registro para formulários convertidos. A opção é somente para formulários baseados em XFA (XDP e PDF forms). Ao ativar a opção, após enviar um formulário, você pode permitir que seus clientes mantenham um registro, em formato impresso ou de documento, das informações que preencheram no formulário para referência futura. Isso é chamado de documento de registro.</td>
   </tr>
   <tr>
   <td>Ativar Analytics</td>
   <td>(Somente para AEM 6.4 e AEM 6.5) Selecione a opção para ativar o Adobe Analytics em todos os formulários convertidos. Antes de usar a opção, verifique se o Adobe Analytics está ativado para a sua instância do AEM Forms.</td>
   </tr>
   </tbody>
   </table>

   * Quando a origem é um formulário baseado em XFA com extensão .XDP, o DOR de saída retém o layout XFA ou o serviço de conversão usa um modelo pronto para uso para gerar DOR para outros formulários baseados em XFA.
   * Quando um formulário XFA é enviado, os dados de envio do formulário são salvos como um elemento XML ou um atributo. Por exemplo, `<Amount currency="USD"> 10.00 </Amount>`. A moeda é salva como um atributo e a quantia da moeda, 10,00 é salva como um elemento. Os dados enviados de um formulário adaptável não têm atributos, têm apenas elementos. Assim, quando um formulário baseado em XFA é convertido em um formulário adaptável, os dados de envio do formulário adaptável contêm um elemento para cada atributo. Por exemplo,

   ```css
      {
         "Type": "Principal",
   
         "Amount": "10.00",
   
         "currency": "USD"
      }
   ```

1. Toque **[!UICONTROL Create]**. A configuração da nuvem é criada. Sua instância do AEM Forms está pronta para começar a converter formulários herdados em formulários adaptáveis.
