---
title: Perguntas frequentes
seo-title: Perguntas frequentes
description: Perguntas comuns ou perguntas frequentes
seo-description: perguntas frequentes sobre o Automated forms conversion Service
uuid: 0f6dc39c-99b7-49a4-8e9e-ecc4a35110c0
topic-tags: introduction
discoiquuid: e17c2d2c-8300-4467-aa01-57365697939f
exl-id: 3a29f8d4-8ea0-49eb-bfe0-0eab5f0c52c7
source-git-commit: af05922f9eb76b7b0a30601824c6006fe555ea80
workflow-type: tm+mt
source-wordcount: '1830'
ht-degree: 4%

---

# Perguntas frequentes{#frequently-asked-questions}

1. **Qual versão do AEM Forms o serviço Automated forms conversion suporta?**

   <p>O serviço Automated forms conversion suporta AEM 6.4 Forms e AEM 6.5 Forms. Funciona com o AEM Forms em formulários OSGi e AEM no JEE. Você precisa do pacote complementar mais recente do AEM Forms sobre AEM instância do autor para usar o serviço. Para obter instruções detalhadas, consulte Configurar o serviço Automated forms conversion</a>.<a href="configure-service.md"></a></p> 
    <br>

1. **O serviço pode ser instalado no local?**

   <p>O Adobe treina algoritmos de IA e ML do serviço Automated forms conversion regularmente com novos conjuntos de dados para melhorar a precisão da conversão. Os algoritmos atualizados são implantados no serviço de conversão em execução na Adobe Cloud em intervalos periódicos. Todos os clientes do serviço são beneficiados pelos algoritmos atualizados. Portanto, a implantação central hospedada na nuvem é mais adequada para o serviço Automated forms conversion para aprender e fornecer melhorias continuamente a todos os clientes.</p> 
    <p>O serviço converte formulários em branco em formulários adaptáveis. O serviço não oferece suporte a formulários preenchidos e à extração de dados de formulários preenchidos. Remova os dados dos formulários preenchidos e remova ou lista de permissões as informações proprietárias dos formulários antes de enviar os formulários ao serviço para conversão</p> <br>

1. **O serviço oferece suporte a todos os formatos de PDF forms? Quais são os idiomas suportados?**

   <p>O serviço pode converter PDF forms não interativos, XDP e PDF forms baseados em XFA e AcroForms em formulários adaptáveis. O serviço não oferece suporte a formulários digitalizados ou preenchidos. Para outras limitações, consulte o artigo <a href="known-issues.md">problemas conhecidos</a>.<br /> </p> 
    <p>Estamos adicionando regularmente suporte para outros tipos de fonte. Mantenha a seção <a href="introduction.md">supportedPDF forms</a> na lista de permissões para obter uma atualização regular sobre recursos e funcionalidades recém-adicionados.</p>

   O serviço pode converter somente formulários em inglês, francês, alemão e espanhol em formulários adaptáveis. Você pode traduzir os formulários adaptáveis gerados para outro idioma usando o [fluxo de trabalho de tradução do AEM.](https://helpx.adobe.com/br/experience-manager/6-5/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.html)</br> </br>

1. **O serviço pode produzir um XDP em vez de um formulário adaptável?**

   <p>O serviço não produz uma saída XDP. Estamos adicionando regularmente recursos e ao serviço. Mantenha a seção <a href="introduction.md">idiomas suportados e PDF forms</a> na lista de permissões para obter uma atualização regular sobre recursos e funcionalidades recém-adicionados.</p> <br>

1. **Qual é o tipo de esquema gerado?**

   <p>Você pode usar o serviço para gerar: </p>

   * um formulário adaptável vinculado a um esquema JSON e
   * um formulário adaptável não vinculado a nenhum schema <br><br>

1. **O serviço pode converter um formulário do Microsoft Word em formulários adaptáveis?**

   <p>Não, o serviço não converte um formulário do Microsoft Word em formulário adaptável. É possível salvar formulários do Microsoft Word em formulário PDF e converter o formulário PDF em um formulário adaptável. O processo completo é </p> <br>

   1. Use o Adobe Acrobat para [converter documento do Word em um PDF não interativo](https://helpx.adobe.com/acrobat/how-to/create-pdf-files-word-excel-website.html).
   1. Use o Adobe Acrobat para [converter as PDF forms produzidas em formulário PDF que pode ser preenchido](https://helpx.adobe.com/acrobat/how-to/convert-word-excel-paper-pdf-forms.html).
   1. Use o Adobe Acrobat para atualizar e corrigir manualmente os campos do formulário.
   1. Salve o formulário PDF. Agora, você pode usar o formulário com o serviço de conversão para gerar um formulário adaptável. Também é possível usar o formulário como um modelo de Documento de registro.


1. **O serviço pode converter formulários em papel digitalizados e formulários coloridos em formulários adaptáveis?**

   <p>O serviço pode converter PDF forms de cores em formulários adaptáveis. O serviço não oferece suporte a formulários digitalizados ou preenchidos. Para outras limitações, consulte o artigo <a href="known-issues.md">known issues</a> .</p> <br>

1. **O serviço pode converter um formulário digitalizado ou apenas uma imagem de um formulário em um formulário adaptável?**

   <p>O serviço não oferece suporte à conversão de formulários digitalizados ou de uma imagem de um formulário para um formulário pronto para uso adaptável. No entanto, você usa o Adobe Acrobat para converter a imagem de um formulário em um formulário PDF. Em seguida, use o serviço para converter o formulário PDF em um formulário adaptável. Sempre use uma imagem de alta qualidade do formulário para conversão no Acrobat. Melhora a qualidade da conversão.</p> <br>

1. **Alguns formulários baseados em XDP usam fragmentos de formulário, onde esses fragmentos de formulário devem ser carregados?**

   <p class="MsoNormal">Carregue fragmentos de formulário na pasta de conversão e preserve a estrutura de pasta original. Ajuda a preservar os caminhos relativos usados em formulários baseados em XDP e fragmentos de formulário.</p> <br>

1. **O serviço suporta formulários XDP vinculados ao esquema? Se eu tiver um XDP vinculado a um esquema, preciso incorporar esquema ao XDP?**

   <p>Sim, o serviço oferece suporte a formulários XDP vinculados ao esquema e requer que o esquema seja incorporado ao formulário XDP de origem. Ao converter um formulário XDP vinculado ao esquema, o serviço gera um esquema JSON. O esquema JSON é estruturalmente semelhante ao esquema XSD de formulários XDP de origem.</p> <br>

1. **Falha do serviço ao converter formulários. Qual é o motivo e como resolver o problema?**
Os motivos mais comuns para a conversão falhar são:
</p>
   * PDF forms seguros são fornecidos para a conversão. Não use PDF forms protegidos por senha ou protegidos para conversão.
   * A conexão com a Internet foi interrompida. Certifique-se de estar conectado à Internet durante a conversão.
   * O PDF de origem tem uma imagem do formulário em vez do formulário real.
   * O serviço está configurado incorretamente, a URL de serviço não é fornecida ou o URL de serviço fornecido está incorreto. Verifique a [configuração de serviço](configure-service.md#configure-the-cloud-service) em **[!UICONTROL AEM]** > **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Automated Forms Conversion configuration]**.
   * A Configuração IMS não está configurada corretamente. Execute uma verificação de integridade na configuração IMS para garantir que ela funcione corretamente. Para verificar se a configuração IMS está correta ou não:
      1. Ir para `http://[servername]:[port]/libs/cq/adobeims-configuration/content/configurations.html`
      2. Selecione a configuração. Clique em **[!UICONTROL Check Health]** no cabeçalho e clique em **[!UICONTROL Check]**. Se bem-sucedido, você receberá a mensagem **[!UICONTROL Token retrieved successfully!]**. <br> <br>

1. **O uso de fontes personalizadas afeta a conversão?**

   <p>Quando um formulário PDF não interativo é convertido em um formulário adaptável, para melhorar a qualidade da conversão, as fontes são incorporadas no formulário PDF. O suporte para incorporação de fontes é restrito a PDF forms não interativos. Para otimizar a conversão de PDF forms AcroForm e baseados em XFA, são usadas fontes de fallback.</p> 
    <p>Somente os formulários disponíveis no diretório de fontes personalizadas listado no campo <strong>Diretório de fontes do cliente</strong> da configuração <strong> CQ-DAM-Handler-Gibson Font Manager Service</strong> são incorporados no formulário PDF não interativo.</p> 
    <p> </p> <br>

1. **O serviço identifica e usa fontes de PDF de origem em formulários adaptáveis de saída?**

   <p>O estilo e o layout de um formulário HTML responsivo geralmente são diferentes de um formulário PDF ou em papel. Para oferecer suporte ao layout e ao estilo consistentes em todas as organizações, os formulários adaptáveis usam <a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/themes.html">temas para criar um estilo em um formulário</a>. O serviço de conversão usa as fontes e os estilos de fonte especificados no tema aplicado durante a conversão. É possível alterar fontes e estilos de fonte do tema para fornecer uma aparência distinta aos componentes de um formulário adaptável.</p> <br>

1. **O serviço extrai automaticamente o JavaScript de formulários baseados em XDP e o aplica a formulários adaptáveis correspondentes?**

   <p>O serviço não converte automaticamente scripts de formulários baseados em XFA ou Acro Forms para as regras de formulário adaptáveis correspondentes. Você (autores de formulários) pode usar o <a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/rule-editor.html">Editor de regras</a> para adicionar interatividade a um formulário adaptável.</p> <br>

1. **Alguns objetos de formulário não são convertidos corretamente em componentes de formulário adaptáveis. Como resolver o problema?**

   <p>O serviço Automated forms conversion é treinado em um grande conjunto de formulários. Mas os aplicativos baseados em IA/ML são limitados por seus dados e padrões de treinamento. Pode haver vários tipos de campo, layouts, padrões e contexto discernível para a percepção humana, mas difícil para o reconhecimento automatizado. O serviço pode não conseguir identificar esses objetos ou pode reconhecê-los incorretamente. Você pode usar o editor <a href="review-correct-ui-edited.md" target="_blank">Revisar e corrigir</a> para fazer as modificações necessárias no layout de formulário em papel familiar do formulário de entrada.</p> <br/>

1. **Algumas correções são repetidas em todos os formulários. O serviço pode identificar e corrigir todas essas instâncias em conversões futuras?**

   O serviço está treinando de forma consistente em seus formulários e padrões. Ele aprende novos padrões diariamente. Ainda é necessário iniciar a aplicação automática de correções repetidas nos formulários. Fique atento aos formulários de pré-lançamento para a disponibilidade desse recurso. <br/><br/>

   Você pode usar o metamodelo para mapear os objetos de formulário para um componente de formulário adaptável de sua escolha e pré-configurar validações, regras, padrões de dados, texto de ajuda e propriedades de acessibilidade dos componentes. Todas as propriedades especificadas são aplicadas durante a conversão. Você pode usar o metamodelo para aplicar propriedades comuns a campos. Isso pode ajudá-lo a reduzir alguns problemas repetidos em todos os formulários.<br/><br/>

1. **Quais são as opções para formulários com dados confidenciais como informações de identificação pessoal (PII)?**
O serviço oferece suporte somente a formulários em branco ou não preenchidos. Não carregue formulários preenchidos ou formulários com informações de identificação pessoal (PII). Além disso, remova os dados pré-preenchidos, as informações de identificação pessoal (PII), as informações confidenciais e de propriedade nos formulários de origem. 
<br/>

1. **Onde o cabeçalho e os rodapés devem ser colocados?**

   <p>Coloque o cabeçalho e o rodapé em um modelo de formulários adaptáveis. Se o formulário PDF de origem tiver cabeçalho e rodapé, o serviço detectará e substituirá o cabeçalho e o rodapé detectados pelo cabeçalho e rodapé disponíveis no modelo de formulário adaptável durante a conversão. Se qualquer cabeçalho ou rodapé extra for incluído no formulário adaptável, você poderá usar o editor <a href="review-correct-ui-edited.md">Revisar e corrigir</a> para corrigir ou remover esse cabeçalho ou rodapé.</p> <br />

1. **Quanto tempo o serviço economiza em comparação ao processo manual de planejamento, criação de ativos (temas, modelos), criação e publicação de um formulário adaptável?**

   <p>O tempo depende do tamanho e da complexidade dos formulários de entrada e do número de solicitações. O serviço pretende reduzir significativamente o tempo de conversão, convertendo PDF forms em formulários adaptáveis a um ritmo muito mais rápido em comparação ao processo manual de conversão de formulários. </p> <br />

1. **O que fazer se encontrar um erro relacionado às bibliotecas RSA? A mensagem de erro é semelhante à mensagem mencionada abaixo:** <br/>

O erro acima ocorre quando a delegação de inicialização não está configurada para bibliotecas RSA/BouncyCastle. Execute as etapas abaixo para resolver o problema:   `*ERROR* [0:0:0:0:0:0:0:1 [1565757652491] POST /content/dam/formsanddocuments/demo004.affBatchProcessor.html HTTP/1.1] org.apache.sling.engine.impl.SlingRequestProcessorImpl service: Uncaught Throwable java.lang.NoClassDefFoundError: Could not initialize class com.rsa.cryptoj.o.dl at com.rsa.jsafe.JSAFE_SecureRandom.getInstance(Unknown Source) at com.adobe.internal.pdfm.util.Util.appendRandomNumberToPrefix(Util.java: 169) [com.adobe.aemfd.adobe-aemfd-assembler:6.0.34] at com.adobe.internal.pdfm.logging.JobLog.&amp;lt;init&amp;gt;(JobLog.java:126) [com.adobe.aemfd.adobe-aemfd-assembler:6.0.34]` <br>
O erro acima ocorre quando a delegação de inicialização não está configurada para bibliotecas RSA/BouncyCastle. Execute as etapas abaixo para resolver o problema:
   <p> </p>

   1. Pare a instância de AEM. Navegue até a pasta `[AEM installation directory]\crx-quickstart\conf\`. Abra o arquivo sling.properties para edição. Se você usar `[AEM installation directory]\crx-quickstart\bin\start.bat` para iniciar uma instância de AEM, edite o sling.properties localizado em `[AEM_root]\crx-quickstart\`.
   1. Adicione as seguintes propriedades ao arquivo sling.properties:<br/> `sling.bootdelegation.class.com.rsa.jsafe.provider.JsafeJCE=com.rsa.*`<br />  `sling.bootdelegation.class.org.bouncycastle.jce.provider.BouncyCastleProvider=org.bouncycastle.*`<br /> `sling.bootdelegation.xerces=org.apache.xerces.*`
   1. Salve e feche o arquivo. <br/>
   1. Inicie a instância de AEM.<br/>

   <br/>

1. **Como alterar automaticamente a capitalização do texto de formulário adaptável?**

   <p>Você pode usar adaptativos de temas ou editor de estilos para alterar a capitalização de um campo de formulário adaptável. Por exemplo, é possível abrir o editor de temas e definir o valor da propriedade Case de todo o texto do formulário como maiúsculo, minúsculo ou camelCase. Você também pode usar a opção Substituição de CSS no editor de temas para criar diferentes tipos de estilos.</p>

1. **Posso usar tags de texto do Adobe Sign com o serviço Automated forms conversion?**

   <p> Ao usar o Automated forms conversion Service para converter um formulário PDF em um formulário adaptável e o formulário PDF tiver tags de texto Adobe Sign, essas tags são convertidas em campos de formulário adaptáveis correspondentes e os detalhes do assinante são automaticamente preenchidos.  O recurso está disponível somente para Acro Forms e os formulários adaptáveis suportam um número limitado de campos Adobe Sign.</p>  </br>

1. **Como criar um formulário PDF habilitado para Adobe Sign?**

   </p>Para criar um formulário PDF habilitado para Adobe Sign:</p>

   Adicione [Adobe Sign text tags](https://helpx.adobe.com/sign/using/text-tag.html) a nomes de campos ou use a opção [Converter em Adobe Sign Form](https://helpx.adobe.com/sign/using/create-forms-with-acrobat.html).
