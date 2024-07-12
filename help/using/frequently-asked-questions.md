---
title: Perguntas frequentes
description: Consultas comuns ou perguntas frequentes
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Administration
topic-tags: introduction
role: Admin, Developer
level: Beginner, Intermediate
exl-id: 3a29f8d4-8ea0-49eb-bfe0-0eab5f0c52c7
source-git-commit: c2392932d1e29876f7a11bd856e770b8f7ce3181
workflow-type: tm+mt
source-wordcount: '1777'
ht-degree: 3%

---

# Perguntas frequentes{#frequently-asked-questions}

1. **A qual versão do AEM Forms o serviço Automated forms conversion (AFCS) oferece suporte?**
   <p>O serviço Automated forms conversion (AFCS) é compatível com AEM 6.4 Forms e AEM 6.5 Forms. Ele funciona com AEM Forms em formulários OSGi e AEM no JEE. Você precisa do pacote complementar mais recente do AEM Forms sobre a instância de autor AEM para usar o serviço. Para obter instruções detalhadas, consulte <a href="configure-service.md">Configurar o serviço Automated forms conversion</a>.</p> 
    <br>

1. **O serviço pode ser instalado no local?**
   <p>O Adobe treina algoritmos de IA e ML do serviço do Automated forms conversion (AFCS) regularmente com um novo conjunto de dados para melhorar a precisão da conversão. Os algoritmos atualizados são implantados no serviço de conversão em execução na Adobe Cloud em intervalos periódicos. Todos os clientes do serviço são beneficiados com os algoritmos atualizados. Assim, a implantação central hospedada na nuvem é mais adequada para o serviço Automated forms conversion (AFCS) para aprender e fornecer continuamente melhorias a todos os clientes.</p> 
    <p>O serviço converte formulários em branco em formulários adaptáveis. O serviço não oferece suporte a formulários preenchidos e extração de dados de formulários preenchidos. Remover dados de formulários preenchidos e remover ou incluir na lista de permissões informações proprietárias dos formulários antes de enviá-los ao serviço para conversão</p> <br>

1. **O serviço oferece suporte a todos os formatos de PDF forms? Há suporte para quais idiomas?**
   <p>O serviço pode converter PDF forms não interativos, XDP e PDF forms baseados em XFA e AcroForms em formulários adaptáveis. O serviço não suporta formulários digitalizados ou preenchidos. Para outras limitações, consulte o artigo <a href="known-issues.md">problemas conhecidos</a>.<br /> </p> 
    <p>Estamos adicionando suporte regularmente para outros tipos de fonte. Mantenha a seção <a href="introduction.md">formulários PDF compatíveis</a> na sua lista de observação para obter uma atualização regular sobre recursos e funcionalidades recém-adicionados.</p>

   O serviço pode converter somente formulários em inglês, francês, alemão, espanhol, italiano e português em formulários adaptáveis. Você pode traduzir os formulários adaptáveis gerados para outro idioma usando o [fluxo de trabalho de tradução do AEM.](https://helpx.adobe.com/br/experience-manager/6-5/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.html)</br> </br>

1. **O serviço pode produzir um XDP em vez de um formulário adaptável?**
   <p>O serviço não produz uma saída XDP. Estamos adicionando recursos e ao serviço regularmente. Mantenha os <a href="introduction.md">idiomas e a seção de PDF forms</a> com suporte na sua lista de observação para obter uma atualização regular sobre os recursos e funcionalidades recém-adicionados.</p> <br>

1. **Qual é o tipo de esquema gerado?**
   <p>Você pode usar o serviço para gerar: </p>

   * um formulário adaptável vinculado a um esquema JSON e
   * um formulário adaptável não vinculado a nenhum esquema <br><br>

1. **O serviço pode converter um formulário do Microsoft Word em formulários adaptáveis?**
   <p>Não, o serviço não converte um formulário do Microsoft Word em um formulário adaptável. Você pode salvar um formulário do Microsoft Word no formato PDF e converter o formulário PDF em um formulário adaptável. O processo completo é </p> <br>

   1. Use o Adobe Acrobat para [converter um documento do Word para um PDF não interativo](https://helpx.adobe.com/acrobat/how-to/create-pdf-files-word-excel-website.html).
   1. Use o Adobe Acrobat para [converter os PDF forms produzidos em PDF Form](https://helpx.adobe.com/acrobat/how-to/convert-word-excel-paper-pdf-forms.html) preenchível.
   1. Use o Adobe Acrobat para atualizar e corrigir manualmente os campos de formulário.
   1. Salve o formulário PDF. Agora, você pode usar o formulário com o serviço de conversão para gerar um formulário adaptável. Você também pode usar o formulário como um documento de modelo de registro.


1. **O serviço pode converter formulários impressos digitalizados e formulários coloridos em formulários adaptáveis?**
   <p>O serviço pode converter PDF forms de cores em formulários adaptáveis. O serviço não suporta formulários digitalizados ou preenchidos. Para outras limitações, consulte o artigo <a href="known-issues.md">problemas conhecidos</a>.</p> <br>

1. **O serviço pode converter um formulário digitalizado ou apenas uma imagem de um formulário em um formulário adaptável?**
   <p>O serviço não oferece suporte à conversão de formulários digitalizados ou de uma imagem de um formulário para um formulário pronto para uso adaptável. No entanto, você usa o Adobe Acrobat para converter a imagem de um formulário em um formulário PDF. Em seguida, use o serviço para converter o formulário PDF em um formulário adaptável. Sempre use uma imagem de alta qualidade do formulário para conversão no Acrobat. Melhora a qualidade da conversão.</p> <br>

1. **Alguns formulários baseados em XDP usam fragmentos de formulário, para onde eles devem ser carregados?**
   <p class="MsoNormal">Faça upload de fragmentos de formulário para a pasta de conversão e preserve a estrutura de pastas original. Ajuda a preservar caminhos relativos usados em formulários e fragmentos de formulário baseados em XDP.</p> <br>

1. **O serviço oferece suporte a formulários XDP associados a esquemas? Se eu tiver um XDP associado a um esquema, preciso incorporar o esquema ao XDP?**
   <p>Sim, o serviço oferece suporte a formulários XDP vinculados a esquemas e requer que o esquema seja incorporado ao formulário XDP de origem. Quando você converte um formulário XDP vinculado a esquema, o serviço gera um esquema JSON. O esquema JSON é estruturalmente semelhante ao esquema XSD dos formulários XDP de origem.</p> <br>

1. **Falha do serviço ao converter formulários. Qual é o motivo e como resolver o problema?**
Os motivos mais comuns para a conversão em falha são:</p>
   * São fornecidos PDF forms seguros para a conversão. Não use PDF forms protegidos por senha ou protegidos para conversão.
   * Conexão com a Internet interrompida. Verifique se você está conectado à Internet durante a conversão.
   * O Source PDF tem uma imagem do formulário em vez do formulário real.
   * O serviço está configurado incorretamente, a URL do serviço não foi fornecida ou a URL do serviço fornecida está incorreta. Verifique a [configuração do serviço](configure-service.md#configure-the-cloud-service) em **[!UICONTROL AEM]** > **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Automated Forms Conversion configuration]**.
   * A configuração do IMS não está configurada corretamente. Execute uma verificação de integridade na configuração do IMS para garantir que ela esteja funcionando corretamente. Para verificar se a configuração do IMS está correta ou não:
      1. Ir para `http://[servername]:[port]/libs/cq/adobeims-configuration/content/configurations.html`
      2. Selecione a configuração. Clique no **[!UICONTROL Check Health]** no cabeçalho e clique em **[!UICONTROL Check]**. Se tiver êxito, você receberá a mensagem **[!UICONTROL Token retrieved successfully!]**. <br> <br>

1. **O uso de fontes personalizadas afeta a conversão?**
   <p>Quando um formulário de PDF não interativo é convertido em um formulário adaptável, para melhorar a qualidade da conversão, as fontes são incorporadas no formulário de PDF. O suporte para incorporação de fontes está restrito a PDF forms não interativos. Para otimizar a conversão de AcroForm e PDF forms baseados em XFA, fontes de fallback são usadas.</p> 
    <p>Somente formulários disponíveis no diretório de fontes personalizadas listado no campo <strong>Diretório de fontes do cliente</strong> da configuração <strong> do CQ-DAM-Handler-Gibson Font Manager Service</strong> são inseridos em formulários PDF não interativos.</p> 
    <p> </p> <br>

1. **O serviço identifica e usa fontes de PDF de origem em formulários adaptáveis de saída?**
   <p>O estilo e o layout de um formulário de HTML responsivo geralmente são diferentes de um formulário baseado em PDF ou em papel. Para oferecer suporte a layout e estilo consistentes em todas as organizações, os formulários adaptáveis usam <a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/themes.html">temas para estilizar um formulário</a>. O serviço de conversão usa as fontes e os estilos de fonte especificados no tema aplicado durante a conversão. É possível alterar as fontes e os estilos de fonte do tema para fornecer uma aparência distinta aos componentes de um formulário adaptável.</p> <br>

1. **O serviço extrai automaticamente o JavaScript de formulários baseados em XDP e o aplica aos formulários adaptáveis correspondentes?**
   <p>O serviço não converte automaticamente scripts de formulários baseados em XFA ou do Acro Forms em regras de formulário adaptáveis correspondentes. Você (autores-formulários) pode usar o <a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/rule-editor.html">Editor de regras</a> para adicionar interatividade a um formulário adaptável.</p> <br>

1. **Alguns objetos de formulário não são convertidos corretamente em componentes de formulário adaptáveis. Como resolver o problema?**
   <p>O serviço de automated forms conversion (AFCS) é treinado em um grande conjunto de formulários. Mas os aplicativos baseados em IA/ML são limitados por seus dados e padrões de treinamento. Pode haver vários tipos de campos, layouts, padrões e contexto discerníveis para a percepção humana, mas difíceis de reconhecer automaticamente. O serviço pode não identificar esses objetos ou reconhecê-los incorretamente. Você pode usar o editor de <a href="review-correct-ui-edited.md" target="_blank">Revisar e corrigir</a> para fazer as modificações necessárias no layout familiar baseado em formulário de papel do formulário de entrada.</p> <br/>

1. **Algumas correções são repetidas em vários formulários. O serviço pode identificar e corrigir todas essas instâncias em conversões futuras?**

   O serviço oferece treinamento consistente em seus formulários e padrões. Ele aprende novos padrões diariamente. Ainda será necessário iniciar a aplicação automática de correções repetidas nos formulários. Fique de olho nos formulários de pré-lançamento para ver a disponibilidade desse recurso. <br/><br/>

   Você pode usar o metamodelo para mapear os objetos de formulário para o componente de formulário adaptável de sua escolha e pré-configurar validações, regras, padrões de dados, texto de ajuda e propriedades de acessibilidade para os componentes. Todas as propriedades especificadas são aplicadas durante a conversão. Você pode usar o metamodelo para aplicar propriedades comuns a campos. Isso pode ajudá-lo a reduzir alguns problemas repetidos nos formulários.<br/><br/>

1. **Quais são as opções para formulários com dados confidenciais, como informações de identificação pessoal (PII)?**
O serviço só oferece suporte a formulários em branco ou não preenchidos. Não carregue formulários preenchidos ou formulários com informações de identificação pessoal (PII). Além disso, remova dados pré-preenchidos, informações de identificação pessoal (PII), informações confidenciais e proprietárias em formulários de origem. <br/>

1. **Onde o cabeçalho e os rodapés devem ser colocados?**
   <p>Coloque o cabeçalho e o rodapé em um modelo de formulários adaptável. Se o formulário de PDF de origem tiver cabeçalho e rodapé, o serviço detecta e substitui o cabeçalho e rodapé detectados pelo cabeçalho e rodapé disponíveis no modelo de formulário adaptável, durante a conversão. Se qualquer cabeçalho ou rodapé extra for incluído no formulário adaptável, você poderá usar o editor <a href="review-correct-ui-edited.md">Revisar e corrigir</a> para corrigir ou remover esse cabeçalho ou rodapé.</p> <br />

1. **Quanto tempo o serviço economiza em comparação ao processo manual de planejamento, criação de ativos (temas, modelos), criação e publicação de um formulário adaptável?**
   <p>O tempo depende do tamanho e da complexidade dos formulários de entrada e do número de solicitações. O serviço pretende reduzir significativamente o tempo de implantação convertendo PDF forms em formulários adaptáveis em um ritmo muito mais rápido em comparação ao processo manual de conversão de formulários. </p> <br />

1. **O que devo fazer se encontrar um erro relacionado às bibliotecas RSA? A mensagem de erro é semelhante à mensagem mencionada abaixo:** <br/>
   `*ERROR* [0:0:0:0:0:0:0:1 [1565757652491] POST /content/dam/formsanddocuments/demo004.affBatchProcessor.html HTTP/1.1] org.apache.sling.engine.impl.SlingRequestProcessorImpl service: Uncaught Throwable java.lang.NoClassDefFoundError: Could not initialize class com.rsa.cryptoj.o.dl at com.rsa.jsafe.JSAFE_SecureRandom.getInstance(Unknown Source) at com.adobe.internal.pdfm.util.Util.appendRandomNumberToPrefix(Util.java: 169) [com.adobe.aemfd.adobe-aemfd-assembler:6.0.34] at com.adobe.internal.pdfm.logging.JobLog.&amp;lt;init&amp;gt;(JobLog.java:126) [com.adobe.aemfd.adobe-aemfd-assembler:6.0.34]` <br>
O erro acima ocorre quando a delegação de inicialização não está configurada para bibliotecas RSA/BouncyCastle. Execute as etapas abaixo para resolver o problema:
   <p> </p>

   1. Pare a instância do AEM. Navegue até a pasta `[AEM installation directory]\crx-quickstart\conf\`. Abra o arquivo sling.properties para edição. Se você usar `[AEM installation directory]\crx-quickstart\bin\start.bat` para iniciar uma instância de AEM, edite o sling.properties localizado em `[AEM_root]\crx-quickstart\`.
   1. Adicione as seguintes propriedades ao arquivo sling.properties:<br/> `sling.bootdelegation.class.com.rsa.jsafe.provider.JsafeJCE=com.rsa.*`<br />  `sling.bootdelegation.class.org.bouncycastle.jce.provider.BouncyCastleProvider=org.bouncycastle.*`<br /> `sling.bootdelegation.xerces=org.apache.xerces.*`
   1. Salvar e fechar o arquivo. <br/>
   1. Iniciar a instância do AEM.<br/>
   <br/>

1. **Como alterar automaticamente a capitalização do texto do formulário adaptável?**
   <p>Você pode usar adaptável de temas ou editor de estilos para alterar a capitalização de um campo de formulário adaptável. Por exemplo, você pode abrir o editor de temas e definir o valor da propriedade Case de todo o texto do formulário para maiúsculas, minúsculas ou camelCase. Você também pode usar a opção Substituição de CSS no editor de tema para criar diferentes tipos de estilos.</p>

1. **Posso usar marcas de texto do Adobe Sign com o serviço do Automated forms conversion (AFCS)?**
   <p> Quando você usa o Serviço de Automated forms conversion (AFCS) para converter um formulário de PDF em um formulário adaptável e o formulário de PDF tem tags de texto Adobe Sign, essas tags são convertidas em campos de formulário adaptáveis correspondentes e os detalhes do assinante são preenchidos automaticamente.  O recurso está disponível somente para o Acro Forms e os formulários adaptáveis são compatíveis com um número limitado de campos do Adobe Sign.</p>  </br>

1. **Como criar um formulário PDF habilitado para Adobe Sign?**
   </p>Para criar um formulário PDF habilitado para Adobe Sign:</p>

   Adicione [marcas de texto do Adobe Sign](https://helpx.adobe.com/sign/using/text-tag.html) a nomes de campos ou use a opção [Converter em Formulário do Adobe Sign](https://helpx.adobe.com/sign/using/create-forms-with-acrobat.html).
