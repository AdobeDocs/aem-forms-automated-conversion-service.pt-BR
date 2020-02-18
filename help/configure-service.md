---
title: Configurar o serviço de conversão de formulários automatizados
description: Prepare sua instância do AEM para usar o serviço de Conversão de formulários automatizados
translation-type: tm+mt
source-git-commit: ef5789dabccc65dcf988b9424b435aa036017691

---


# Configurar o serviço de conversão de formulários automatizados {#about-this-help}

Esta ajuda descreve como um administrador do AEM pode configurar o serviço de Conversão de formulários automatizados para automatizar a conversão de seus formulários PDF em formulários adaptáveis. Esta ajuda é para administradores de TI e AEM em sua organização. As informações fornecidas baseiam-se no pressuposto de que qualquer pessoa que leia esta Ajuda está familiarizada com as seguintes tecnologias:

* Instalação, configuração e administração de pacotes do Adobe Experience Manager e do AEM,

* Usando sistemas operacionais Linux e Microsoft Windows,

* Configuração de servidores de correio SMTP

>[!VIDEO](https://video.tv.adobe.com/v/29267/)

**Assista ao vídeo ou leia o artigo para configurar o serviço de Conversão de formulários automatizados**

## Integração{#onboarding}

O serviço está disponível gratuitamente para clientes de termo de AEM 6.5 Forms e AEM 6.4 Forms no local e clientes corporativos Adobe Managed Service. Você pode entrar em contato com a equipe de vendas da Adobe ou com seu representante da Adobe para solicitar acesso ao serviço.

A Adobe habilita o acesso para sua organização e fornece os privilégios necessários à pessoa designada como administrador em sua organização. O administrador pode conceder acesso aos desenvolvedores (usuários) do AEM Forms de sua organização para se conectar ao serviço.

## Pré-requisitos {#prerequisites}

É necessário o seguinte para usar o serviço de conversão de formulários automatizados:

* O serviço de conversão de formulários automatizada está habilitado para sua organização
* Uma conta da Adobe ID com privilégios de administrador para o serviço de conversão
* Uma instância do autor do AEM 6.5 ou AEM 6.4 está ativa e em execução com o AEM Service Pack mais recente
* Um usuário do AEM (em sua instância do AEM) que é membro do grupo de usuários de formulários

## Configurar o ambiente {#setuptheservice}

Antes de usar o serviço, prepare a instância do autor de AEM para se conectar ao serviço em execução na Adobe Cloud. Execute as seguintes etapas na sequência listada para preparar sua instância para o serviço:

1. [Baixe e instale o AEM 6.5 ou AEM 6.4](#aemquickstart)
1. [Baixe e instale o AEM Service Pack mais recente](#servicepack)
1. [Baixar e instalar o pacote de complementos AEM Forms mais recente](#downloadaemformsaddon)
1. [Criar temas e modelos personalizados](#referencepackage)

### Baixe e instale o AEM 6.5 ou AEM 6.4 {#aemquickstart}


O serviço de conversão de formulários automatizada é executado na instância do autor de AEM. Você precisa do AEM 6.5 ou do AEM 6.4 para configurar uma instância do autor do AEM. Se o AEM não estiver funcionando, baixe-o dos seguintes locais:

* Se você for um cliente do AEM, baixe o AEM 6.5 ou o AEM 6.4 do site [de licenciamento da](http://licensing.adobe.com)Adobe.

* Se você for um parceiro da Adobe, use o Programa [de treinamento para parceiros da](https://adobe.allegiancetech.com/cgi-bin/qwebcorporate.dll?idx=82357Q) Adobe para solicitar o AEM 6.5 ou o AEM 6.4.

Depois de baixar o AEM, para obter instruções sobre como configurar uma instância do autor de AEM, consulte [implantação e manutenção](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/deploy.html#defaultlocalinstall).

### Baixar e instalar o Service Pack mais recente do AEM {#servicepack}

Baixe e instale o AEM Service Pack mais recente. Para obter instruções detalhadas, consulte Notas [de versão do Service Pack do](https://helpx.adobe.com/experience-manager/6-5/release-notes/sp-release-notes.html) AEM 6.5 ou Notas [de versão do Service Pack do](https://helpx.adobe.com/experience-manager/6-4/release-notes/sp-release-notes.html)AEM 6.4.

### Baixar e instalar o pacote complementar do AEM Forms {#downloadaemformsaddon}

Uma instância do AEM contém recursos básicos de formulários. O serviço de conversão requer todos os recursos do AEM Forms. Baixe e instale o pacote complementar AEM Forms para aproveitar todos os recursos do AEM Forms. O pacote é necessário para configurar e executar o serviço de conversão. Para obter instruções detalhadas, consulte [Instalar e configurar recursos de captura de dados.](https://helpx.adobe.com/experience-manager/6-5/forms/using/installing-configuring-aem-forms-osgi.html)

>[!NOTE]
> Se você já for um usuário do serviço de Conversão de formulários automatizados, instale o complemento AEM Forms mais recente para continuar usando o serviço. O pacote do conector é unido ao pacote do complemento AEM Forms. O pacote de conector adicional não é mais necessário.
> Certifique-se de executar as configurações obrigatórias pós-instalação depois de instalar o pacote suplementar.


### Criar temas e modelos personalizados {#referencepackage}

Se você iniciar o AEM no modo [](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/production-ready.html) de produção (nosamplecontent runmode), os pacotes de referência não serão instalados. Os pacotes de referência contêm exemplos de temas e modelos. O serviço de Conversão de formulários automatizada requer pelo menos um tema e um modelo para converter formulários PDF em formulários adaptáveis. Crie um tema e modelo personalizados de sua própria configuração [de](#configure-the-cloud-service) serviço de ponto e ponto para usar modelos e temas personalizados antes de usar o serviço.

## Configurar o serviço {#configure-the-service}

Antes de configurar o serviço e conectar sua instância local com o serviço em execução na Adobe Cloud, saiba mais sobre as pessoas e os privilégios necessários para se conectar ao serviço. O serviço usa dois tipos diferentes de personas, administradores e desenvolvedores:

* **Administradores**: Os administradores são responsáveis pelo gerenciamento de software e serviços da Adobe para sua organização. Os administradores concedem acesso aos desenvolvedores em sua organização para se conectarem ao serviço de Conversão de formulários automatizados em execução na Adobe Cloud. Quando um administrador é provisionado para uma organização, o administrador recebe um email com título **[!UICONTROL 'You now have administrator rights to manage Adobe software and services for your organization']**. Se você for um administrador, verifique seu email de caixa de correio com o título acima mencionado e prossiga para [conceder acesso aos desenvolvedores de sua organização](#adduseranddevs).

![email de concessão de acesso do administrador](assets/admin-console-adobe-io-access-grantedx75.png)

* **Desenvolvedores**: Um desenvolvedor conecta uma instância local do autor do AEM Forms ao serviço de Conversão de formulários automatizados em execução na Adobe Cloud. Quando um administrador concede direitos a um desenvolvedor para se conectar ao serviço de Conversão de formulários automatizados, um email com o título Você agora tem acesso de desenvolvedor para gerenciar integrações de API da Adobe para sua organização é enviado ao desenvolvedor. Se você for um desenvolvedor, verifique seu email de caixa de correio com o título acima mencionado e prossiga para [Conectar sua instância local do AEM ao serviço de Conversão de formulários automatizados na Adobe Cloud.](#connectafcadobeio)

![email de concessão de acesso do desenvolvedor](assets/email-developer-accessx94.png)

### (Somente para administradores) Conceda acesso aos desenvolvedores de sua organização {#adduseranddevs}

Depois que a Adobe ativar o acesso para sua organização e fornecer os privilégios necessários ao administrador, o administrador poderá fazer logon no Admin Console (instruções detalhadas abaixo), criar um perfil e adicionar desenvolvedores ao perfil. Os desenvolvedores podem conectar uma instância local do AEM Forms ao serviço de conversão de formulários automatizados na Adobe Cloud.

Os desenvolvedores são membros de sua organização designados para executar o serviço de conversão. Somente os desenvolvedores adicionados ao perfil do serviço de Conversão de formulários automatizados da Adobe têm direito a usar o serviço de Conversão de formulários automatizados. Execute as etapas abaixo para criar um perfil e adicionar desenvolvedores a ele:

1. Faça logon no [Admin Console](https://adminconsole.adobe.com/). Use a ID **da** Adobe do administrador provisionada para usar o serviço de Conversão de formulários automatizados para fazer logon. Não faça logon em nenhuma outra ID ou Federated ID.
1. Clique na **[!UICONTROL Automated Forms Conversion]** opção.
1. Clique **[!UICONTROL New Profile]** na **[!UICONTROL Products]** guia.
1. Especifique **[!UICONTROL Name]**, **[!UICONTROL Display Name]** e **[!UICONTROL Description]** para o perfil. Clique em **[!UICONTROL Done]**. Um perfil é criado.

   ![Especifique detalhes para o novo perfil.](assets/create-new-profile-details.png)

1. Adicione desenvolvedor ao perfil. Para adicionar os desenvolvedores:
   1. No [Admin Console](https://adminconsole.adobe.com/enterprise), navegue até a guia Visão geral.
   1. Clique **[!UICONTROL Assign Developers]** no cartão de produto desejado.
   1. Insira o endereço de email dos desenvolvedores e, opcionalmente, o nome e o sobrenome.
   1. Selecione perfis de produto. Tocar **[!UICONTROL Save]**.

Repita as etapas acima para todos os usuários.  Para obter mais detalhes sobre como adicionar desenvolvedores, consulte [Gerenciar desenvolvedores](https://helpx.adobe.com/enterprise/using/manage-developers.html).

Quando um administrador adiciona desenvolvedores ao perfil de E/S da Adobe, eles são notificados por email. Depois de receber o email, os desenvolvedores podem continuar a [conectar uma instância local do AEM Forms com o serviço de Conversão de formulários automatizados na Adobe Cloud](#connectafcadobeio).

### (Somente para desenvolvedores) Conecte sua instância local do AEM Forms ao serviço de conversão de formulários automatizada na Adobe Cloud {#connectafcadobeio}

Depois que um administrador fornecer acesso de desenvolvedor, você poderá conectar sua instância local do AEM Forms ao serviço de conversão de Formulários Automatizados em execução na Adobe Cloud. Execute as seguintes etapas na sequência listada para conectar sua instância do AEM Forms ao serviço:

* [Configurar notificações por email](configure-service.md#configureemailnotification)
* [Adicionar usuário ao grupo de usuários de formulários](#adduserstousergroup)
* [Obter certificados públicos](#obtainpubliccertificates)
* [Criar integração de E/S da Adobe](#createintegration)
* [Configurar o serviço de nuvem](configure-service.md#configure-the-cloud-service)

#### Configurar notificação por email {#configureemailnotification}

O serviço de conversão de formulários automatizada usa o serviço de email Day CQ para enviar notificações por email. Essas notificações por email contêm informações sobre conversões bem-sucedidas ou com falha. Se você escolher não receber notificação, ignore essas etapas. Execute as seguintes etapas para configurar o Day CQ Mail Service:

1. Ir para o gerenciador de configuração AEM em `http://localhost:4502/system/console/configMgr`
1. Abra a configuração do serviço Day CQ Mail. Especifique um valor para os campos **[!UICONTROL SMTP server host name]**, **[!UICONTROL SMTP server port]** e **[!UICONTROL From address]** . Clique em **[!UICONTROL Save]**.

   Você pode entrar em contato com seu provedor de serviços de email ou administrador de TI para obter informações sobre o nome do host e a porta do servidor SMTP. Você pode usar qualquer endereço de email válido no campo de formulário. Por exemplo, notification@example.com ou donotreply@example.com.

1. Abra a **[!UICONTROL Day CQ Link Externalizer]** configuração. No **[!UICONTROL Domains]** campo, especifique o nome do host ou endereço IP real e o número da porta para instâncias locais, de autor e de publicação. Clique em **[!UICONTROL Save]**.

#### Add user to the forms-users group {#adduserstousergroup}

Especifique um endereço de email no perfil do usuário do AEM designado para executar o serviço. Verifique se o usuário é o membro do grupo de usuários [de](https://helpx.adobe.com/experience-manager/6-4/forms/using/forms-groups-privileges-tasks.html) formulários. Os emails são enviados para o endereço de email do usuário que está executando a conversão. Para especificar um endereço de email para o usuário e adicionar o usuário ao grupo de usuários de formulários:

1. Faça logon na instância do autor do AEM Forms como um administrador do AEM. Use suas credenciais do AEM local para fazer logon. Não use a Adobe ID para fazer logon. Tap **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Users]**.

1. Selecione um usuário designado para executar o serviço de conversão e toque em **[!UICONTROL Properties]**. A página Editar configurações do usuário é aberta.
1. Especifique um endereço de email no **[!UICONTROL Email]** campo e toque **[!UICONTROL Save]**. Os e-mails são enviados para o endereço de e-mail especificado após a conclusão ou falha da conversão.
1. Toque na guia **Grupos** . Na guia Selecionar grupo, digite e selecione o grupo de **formulários-usuários** . Toque em **Salvar e fechar**. O usuário agora é membro do grupo de usuários de formulários.

#### Obter certificados públicos {#obtainpubliccertificates}

Um certificado público permite autenticar seu perfil em E/S da Adobe.

1. Faça logon na instância do autor do AEM Forms. Vá até **[!UICONTROL Tools]**> **[!UICONTROL Security]** > **[!UICONTROL Adobe IMS Configurations]**. Tocar **[!UICONTROL Create]**. A **[!UICONTROL Adobe IMS Technical Account Configuration]** página é exibida.

   ![A página Configuração técnica da conta do Adobe IMS](assets/adobe-ims-technical-account-configuration.png)

1. Selecione **[!UICONTROL Automated Forms Conversion Service]** em Solução em nuvem.

1. Marque a caixa de **[!UICONTROL Create new certificate]** seleção e especifique um alias. O alias serve como nome da caixa de diálogo. Tocar **[!UICONTROL Create certificate]**. Uma caixa de diálogo é exibida. Clique em **[!UICONTROL OK]**. O certificado é criado.

1. Toque **[!UICONTROL Download Public Key]** e salve o arquivo de certificado *AEM-Adobe-IMS.crt* em seu computador. O arquivo de certificado é usado para [criar integração no Console](#createintegration)de E/S da Adobe. Tocar **[!UICONTROL Next]**.

1. Especifique o seguinte:

   * Título: Especifique um título.
   * Servidor de autorização: [https://ims-na1.adobelogin.com](https://ims-na1.adobelogin.com)
   Deixe os outros campos em branco por enquanto (a ser fornecido posteriormente). Mantenha a página aberta.

   <!--
   Comment Type: draft

   <li> </li>
   -->

   <!--
   Comment Type: draft

   <li>Step text</li>
   -->

#### Criar integração de E/S da Adobe {#createintegration}

Para usar o serviço de Conversão de formulários automatizados, crie uma integração em E/S da Adobe. A integração gera a chave da API, o segredo do cliente, a carga (JWT).

1. Faça logon em [https://console.adobe.io/](https://console.adobe.io/). Use sua ID da Adobe, conta de desenvolvedor provisionada pelo administrador para fazer logon no console de E/S da Adobe para fazer logon.

1. Tocar **[!UICONTROL View Integrations]**. Uma tela com todas as integrações disponíveis é exibida.
1. Selecione sua organização no menu suspenso em **[!UICONTROL Integrations]**. Toque **[!UICONTROL New Integration]**, selecione **[!UICONTROL Access an API]** e toque **[!UICONTROL Continue]**.
1. Selecione **[!UICONTROL Experience Cloud]** > **[!UICONTROL Automated Forms Conversion]** e toque **[!UICONTROL Continue]**. Se a opção Conversão de formulários automatizada estiver desativada para você, verifique se você selecionou a organização correta na caixa suspensa acima da **[!UICONTROL Adobe Services]** opção. Se você não souber sua organização, entre em contato com o administrador.

   ![Selecionar conversão de formulários automatizada](assets/create-new-integration.png)

1. Especifique o nome e a descrição da integração. Toque **[!UICONTROL Select a File from your computer]** e carregue o arquivo AEM-Adobe-IMS.crt baixado na seção [Obter certificados](#obtainpubliccertificates) públicos.
1. Selecione o perfil criado ao [conceder acesso aos desenvolvedores de sua organização](#adduseranddevs) e toque em **[!UICONTROL Create Integration]**. A integração é criada.
1. Toque em **[!UICONTROL Continue to integration details]** para exibir as informações de integração. A página contém a chave da API, o segredo do cliente e outras informações necessárias para conectar sua instância do AEM local ao serviço de conversão de formulários automatizados. As informações na página são usadas para criar a configuração IMS na máquina local.

   ![Chave da API, segredo do cliente e informações de carga de uma integração](assets/integration-details.png)

1. Abra a página Configuração IMS na instância local. Você manteve a página aberta no final da seção, [Obter certificado](#obtainpubliccertificates)público.

   ![Especificar título, chave da API, segredo do cliente e carga ](assets/ims-configuration-details.png)

1. Na página Técnica do Adobe IMS, especifique a chave da API e o segredo do cliente. Use os valores especificados na página de integração.

   **Para a carga, use o código fornecido na guia JWT da página de integração.** Tocar  **[!UICONTROL Save]**. A configuração IMS é criada. Feche a página de integração.

   ![Usar valores do campo JWT para o campo de carga](assets/jwt.png)

   >[!CAUTION]
   >
   >Crie apenas uma configuração IMS. Não crie mais de uma configuração IMS.

1. Selecione a configuração IMS e toque **[!UICONTROL Check Health]**. Uma caixa de diálogo é exibida. Tocar **[!UICONTROL Check]**. Na conexão bem-sucedida, a mensagem *Token recuperado com êxito* é exibida.

   ![Na conexão bem-sucedida, a mensagem do token recuperado com êxito é exibida. ](assets/health-check.png)

   <br/> <br/>

#### Configurar o serviço de nuvem {#configure-the-cloud-service}

Crie uma configuração de serviço em nuvem para conectar sua instância do AEM ao serviço de conversão. Também permite especificar um modelo, tema e fragmentos de formulário para uma conversão. É possível criar várias configurações de serviço em nuvem separadas para cada conjunto de formulários. Por exemplo, você pode ter uma configuração separada para formulários do departamento de vendas e outra separada para formulários de suporte ao cliente. Execute as seguintes etapas para criar uma configuração de serviço em nuvem:

1. Na instância do AEM Forms, toque em **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Tools]**> **[!UICONTROL Cloud Services]** > **[!UICONTROL Automate Forms Conversion Configuration]**.
1. Toque na **[!UICONTROL Global]** pasta e toque **[!UICONTROL Create]**. A página para criar a configuração de Conversão de formulários automatizados é exibida. A configuração é criada na pasta Global. Você também pode criar a configuração em uma pasta diferente que já existe ou criar uma nova pasta para suas configurações.

1. Na **[!UICONTROL Create Automated Forms Conversion Configuration]** página, especifique o valor para os seguintes campos e toque em **[!UICONTROL Next]**.

   | Texto | Descrição |
   |--- |--- |
   | Título | Título exclusivo para a configuração. O título é exibido na interface do usuário usada para iniciar a conversão. |
   | Nome | Nome exclusivo para a configuração. A configuração é salva no CRX-Repository com o nome especificado. O nome pode ser idêntico ao título. |
   | Localização em miniatura | Localização da miniatura da configuração. |
   | URL do serviço | URL do serviço de Conversão de formulários automatizada na Adobe Cloud. Use o `https://aemformsconversion.adobe.io/` URL. |
   | Modelo | Modelo padrão a ser aplicado aos formulários convertidos. Você sempre pode especificar um modelo diferente antes de iniciar a conversão. Um modelo contém estrutura básica e conteúdo inicial para um formulário adaptável. Você pode escolher um modelo dos modelos fornecidos prontos para uso. Você também pode criar um modelo personalizado. |
   | Tema | O tema padrão a ser aplicado aos formulários convertidos. Você sempre pode especificar um tema diferente antes de iniciar a conversão.  Você pode clicar no ícone para escolher um tema fornecido fora da caixa. Você também pode criar um tema personalizado. |
   | Fragmentos existentes | Localização dos fragmentos existentes, se houver. |
   | Meta-modelo personalizado | Caminho do arquivo .schema.json do meta-modelo personalizado. |



1. Na **[!UICONTROL Advanced]** guia da **[!UICONTROL Create Automated Forms Conversion Configuration]** página, especifique o valor para o seguinte campo:

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
   <td>Selecione a opção para gerar automaticamente o Documento de registro para formulários convertidos. A opção é somente para formulários baseados em XFA (XDP e PDF Forms). Ao ativar a opção, após enviar um formulário, é possível permitir que seus clientes mantenham um registro, em formato impresso ou de documento, das informações que preencheram no formulário para referência futura. Isso é chamado de documento de registro.</td>
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

1. Tocar **[!UICONTROL Create]**.  A configuração da nuvem é criada. Sua instância do AEM Forms está pronta para iniciar a conversão de formulários legados em formulários adaptáveis.
