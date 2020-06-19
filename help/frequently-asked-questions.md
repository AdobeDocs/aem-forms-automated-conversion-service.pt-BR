---
title: Perguntas frequentes
seo-title: Perguntas frequentes
description: query comuns ou perguntas frequentes
seo-description: perguntas frequentes sobre o serviço de conversão de formulários automatizado
uuid: 0f6dc39c-99b7-49a4-8e9e-ecc4a35110c0
topic-tags: introduction
discoiquuid: e17c2d2c-8300-4467-aa01-57365697939f
translation-type: tm+mt
source-git-commit: b1df14a331dc4aef7ce6383dec0091fa6db1fd7b
workflow-type: tm+mt
source-wordcount: '1685'
ht-degree: 5%

---


# Perguntas frequentes{#frequently-asked-questions}

1. **Qual versão de AEM Forms o serviço de Conversão de formulários automatizados oferece suporte?**
   <p>O serviço de Conversão de formulários automatizados oferece suporte aos formulários AEM 6.4 e AEM 6.5. Funciona com AEM Forms em formulários OSGi e AEM em JEE. Você precisa do pacote complementar de AEM Forms mais recente sobre a instância do autor de AEM para usar o serviço. For detailed instructions, see <a href="configure-service.md">Configure the Automated Forms Conversion</a> service.</p> 
    <br>

1. **O serviço pode ser instalado no local?**
   <p>A Adobe treina os algoritmos AI e ML do serviço de Conversão de formulários automatizada regularmente com novos conjuntos de dados para melhorar a precisão da conversão. Os algoritmos atualizados são implantados no serviço de conversão em execução na Adobe Cloud em intervalos periódicos. Todos os clientes do serviço são beneficiados pelos algoritmos atualizados. Portanto, a implantação central hospedada na nuvem é mais adequada para o serviço de Conversão de formulários automatizados para aprender e fornecer continuamente melhorias a todos os clientes.</p> 
    <p>O serviço converte formulários em branco em formulários adaptáveis. O serviço não oferece suporte para formulários preenchidos e extração de dados de formulários preenchidos. Remova os dados dos formulários preenchidos e remova ou permita informações proprietárias dos formulários antes de enviá-los para o serviço de conversão</p> <br>

1. **O serviço suporta todos os formatos de PDF forms? Quais são os idiomas suportados?**
   <p>O serviço pode converter PDF forms não interativos, XDP e PDF forms baseados em XFA e AcroForms em formulários adaptáveis. O serviço não suporta formulários digitalizados ou preenchidos. Para obter outras limitações, consulte o artigo sobre problemas <a href="known-issues.md"></a> conhecidos.<br /> </p> 
    <p>Estamos constantemente adicionando suporte para outros tipos de fonte. Mantenha a seção de formulários <a href="introduction.md">PDF</a> suportados em sua lista de monitoramento para obter uma atualização regular dos recursos e capacidades recém-adicionados.</p>

   O serviço pode converter somente formulários em inglês em formulários adaptáveis. Você pode traduzir os formulários adaptáveis gerados para outro idioma usando o [fluxo de trabalho de tradução do AEM.](https://helpx.adobe.com/br/experience-manager/6-5/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.html)</br> </br>

1. **O serviço pode produzir um XDP em vez de um formulário adaptável?**
   <p>O serviço não produz uma saída XDP. Estamos adicionando regularmente recursos e ao serviço. Mantenha a seção de idiomas e PDF forms <a href="introduction.md"></a> suportados em sua lista de observação para obter uma atualização regular dos recursos e capacidades recém-adicionados.</p> <br>

1. **Qual é o tipo de schema gerado?**
   <p>Você pode usar o serviço para gerar: </p>

   * um formulário adaptável vinculado a um schema JSON e
   * um formulário adaptável não vinculado a nenhum schema <br><br>

1. **O serviço pode converter um formulário do Microsoft Word em formulários adaptáveis?**
   <p>Não, o serviço não converte um formulário do Microsoft Word em um formulário adaptável. É possível salvar formulários do Microsoft Word em PDF e converter o formulário PDF em um formulário adaptável. O processo completo é </p> <br>

   1. Use o Adobe Acrobat para [converter o Word Document em um PDF](https://helpx.adobe.com/acrobat/how-to/create-pdf-files-word-excel-website.html)não interativo.
   1. Use o Adobe Acrobat para [converter os PDF forms produzidos em formulários](https://helpx.adobe.com/acrobat/how-to/convert-word-excel-paper-pdf-forms.html)PDF preenchíveis.
   1. Use o Adobe Acrobat para atualizar e corrigir campos de formulário manualmente.
   1. Salve o formulário PDF. Agora, você pode usar o formulário com o serviço de conversão para gerar um formulário adaptável. Também é possível usar o formulário como um Documento de modelo de Registro.


1. **O serviço pode converter formulários impressos digitalizados e formulários coloridos em formulários adaptáveis?**
   <p>O serviço pode converter PDF forms em formulários adaptáveis. O serviço não suporta formulários digitalizados ou preenchidos. Para obter outras limitações, consulte o artigo sobre problemas <a href="known-issues.md"></a> conhecidos.</p> <br>

1. **O serviço pode converter um formulário digitalizado ou apenas uma imagem de um formulário em um formulário adaptável?**
   <p>O serviço não suporta a conversão de formulários digitalizados ou de uma imagem de um formulário para um formulário pronto para uso. No entanto, você usa o Adobe Acrobat para converter a imagem de um formulário em um formulário PDF. Em seguida, use o serviço para converter o formulário PDF em um formulário adaptável. Sempre use uma imagem de alta qualidade do formulário para conversão no Acrobat. Melhora a qualidade da conversão.</p> <br>

1. **Alguns formulários baseados em XDP usam fragmentos de formulário, onde esses fragmentos de formulário devem ser carregados?**
   <p class="MsoNormal">Carregue fragmentos de formulário na pasta de conversão e preserve a estrutura da pasta original. Ajuda a preservar os caminhos relativos usados em formulários baseados em XDP e fragmentos de formulário.</p> <br>

1. **O serviço suporta formulários XDP vinculados ao schema? Se eu tiver um XDP vinculado a um schema, será necessário incorporar o schema ao XDP?**
   <p>Sim, o serviço suporta formulários XDP vinculados ao schema e requer que o schema seja incorporado ao formulário XDP de origem. Quando você converte um formulário XDP vinculado ao schema, o serviço gera um schema JSON. O schema JSON é estruturalmente semelhante ao schema XSD de formulários XDP de origem.</p> <br>

1. **Falha do serviço ao converter formulários. Qual é a razão e como resolver o problema?**
Os motivos mais comuns para a conversão falhar são:</p>
   * PDF forms seguros são fornecidos para a conversão. Não use PDF forms protegidos por senha ou protegidos para conversão.
   * A conexão com a Internet é interrompida. Verifique se você está conectado à Internet durante a conversão.
   * O PDF de origem tem uma imagem do formulário em vez do formulário real.
   * O serviço está configurado incorretamente, o URL do serviço não é fornecido ou o URL do serviço fornecido está incorreto. Verifique a configuração [do](configure-service.md#configure-the-cloud-service) serviço em **[!UICONTROL AEM]** > **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Automated Forms Conversion configuration]**.
   * A Configuração IMS não está configurada corretamente. Execute uma verificação de integridade na configuração do IMS para garantir que ela esteja funcionando corretamente. Para verificar se a Configuração IMS está correta ou não:
      1. Ir para `http://[servername]:[port]/libs/cq/adobeims-configuration/content/configurations.html`
      2. Selecione a configuração. Clique no cabeçalho **[!UICONTROL Check Health]** e clique em **[!UICONTROL Check]**. Se tiver sucesso, você receberá **[!UICONTROL Token retrieved successfully!]** mensagem. <br> <br>

1. **O uso de fontes personalizadas afeta a conversão?**
   <p>Quando um formulário PDF não interativo é convertido em um formulário adaptável, para melhorar a qualidade da conversão, as fontes são incorporadas no formulário PDF. O suporte para incorporação de fontes está restrito a PDF forms não interativos. Para otimizar a conversão de PDF forms baseados em AcroForm e XFA, são usadas fontes de fallback.</p> 
    <p>Somente os formulários disponíveis no diretório de fontes personalizadas listados no campo de diretório <strong>de fontes do</strong> Cliente da configuração do serviço <strong></strong> CQ-DAM-Handler-Gibson Font Manager são incorporados em formulários PDF não interativos.</p> 
    <p> </p> <br>

1. **O serviço identifica e usa fontes do PDF de origem em formulários adaptáveis de saída?**
   <p>O estilo e o layout de um formulário HTML responsivo são geralmente diferentes de um formulário PDF ou em papel. Para suportar layout e estilos consistentes em todas as organizações, os formulários adaptativos usam <a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/themes.html">temas para estilizar um formulário</a>. O serviço de conversão usa as fontes e os estilos de fonte especificados no tema aplicado durante a conversão. É possível alterar as fontes e os estilos de fonte do tema para fornecer uma aparência distinta aos componentes de um formulário adaptável.</p> <br>

1. **O serviço extrai automaticamente o JavaScript de formulários baseados em XDP e o aplica aos formulários adaptáveis correspondentes?**
   <p>O serviço não converte automaticamente scripts de formulários XFA ou Acro Forms para regras de formulário adaptáveis correspondentes. Você (autores de formulários) pode usar o editor <a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/rule-editor.html">de</a> regras para adicionar interatividade a um formulário adaptável.</p> <br>

1. **Alguns objetos de formulário não são convertidos corretamente em componentes de formulário adaptáveis. Como resolver o problema?**
   <p>O serviço de Conversão de formulários automatizada é treinado em um grande conjunto de formulários. Mas os aplicativos baseados em IA/ML são limitados por seus dados e padrões de treinamento. Podem existir vários tipos de campo, layouts, padrões e contexto perceptíveis à percepção humana, mas difíceis de reconhecer automaticamente. O serviço pode falhar ao identificar esses objetos ou pode reconhecê-los incorretamente. Você pode usar o editor <a href="review-correct-ui-edited.md" target="_blank">Revisar e corrigir</a> para fazer as modificações necessárias no layout familiar em papel baseado no formulário de entrada.</p> <br/>

1. **Algumas correções são repetidas nos formulários. O serviço pode identificar e corrigir todas essas instâncias em conversões futuras?**

   O serviço está consistentemente treinando em seus formulários e padrões. Aprende novos padrões diariamente. Ainda não foi possível start das correções de aplicação automática repetidas nos formulários. Fique de olho nos formulários de pré-lançamento para a disponibilidade de tal recurso. <br/><br/>

   Você pode usar o metrosmodelo para mapear os objetos de formulário para um componente de formulário adaptável de sua escolha e pré-configurar validações, regras, padrões de dados, texto de ajuda e propriedades de acessibilidade para os componentes. Todas as propriedades especificadas são aplicadas durante a conversão. Você pode usar o modelo meta para aplicar propriedades comuns a campos. Ele pode ajudar a reduzir alguns problemas repetidos em todos os formulários.<br/><br/>

1. **Quais são as opções para formulários com dados confidenciais, como informações de identificação pessoal (PII)?**
O serviço suporta apenas formulários em branco ou não preenchidos. Não carregue formulários preenchidos ou formulários com informações de identificação pessoal (PII). Além disso, remova os dados pré-preenchidos e as PII de rótulo branco, as informações confidenciais e proprietárias nos formulários de origem. <br/>

1. **Onde devem ser colocados o cabeçalho e os rodapés?**
   <p>Coloque cabeçalho e rodapé em um modelo de formulários adaptáveis. Se o formulário PDF de origem tiver cabeçalho e rodapé, o serviço detectará e substituirá o cabeçalho e rodapé detectados pelo cabeçalho e rodapé disponíveis no modelo de formulário adaptável, durante a conversão. Se algum cabeçalho ou rodapé extra estiver incluído no formulário adaptável, você poderá usar o editor <a href="review-correct-ui-edited.md">Revisar e corrigir</a> para corrigir ou remover esse cabeçalho ou rodapé.</p> <br />

1. **Quanto tempo o serviço economiza em comparação ao processo manual de planejamento, criação de ativos (temas, modelos), criação e publicação de um formulário adaptável?**
   <p>A quantidade de tempo depende do tamanho e da complexidade dos formulários de entrada e do número de solicitações. O serviço pretende reduzir significativamente o tempo de conversão de PDF forms em formulários adaptáveis a um ritmo muito mais rápido em comparação ao processo manual de conversão de formulários. </p> <br />

1. **O que fazer se encontrar um erro relacionado às bibliotecas RSA? A mensagem de erro é semelhante à mensagem mencionada abaixo:** <br/>
   `*ERROR* [0:0:0:0:0:0:0:1 [1565757652491] POST /content/dam/formsanddocuments/demo004.affBatchProcessor.html HTTP/1.1] org.apache.sling.engine.impl.SlingRequestProcessorImpl service: Uncaught Throwable java.lang.NoClassDefFoundError: Could not initialize class com.rsa.cryptoj.o.dl at com.rsa.jsafe.JSAFE_SecureRandom.getInstance(Unknown Source) at com.adobe.internal.pdfm.util.Util.appendRandomNumberToPrefix(Util.java: 169) [com.adobe.aemfd.adobe-aemfd-assembler:6.0.34] at com.adobe.internal.pdfm.logging.JobLog.&amp;lt;init&amp;gt;(JobLog.java:126) [com.adobe.aemfd.adobe-aemfd-assembler:6.0.34]` <br>
O erro mencionado anteriormente ocorre quando a delegação de inicialização não está configurada para bibliotecas RSA/BouncyCastle. Execute as etapas a seguir para resolver o problema:
   <p> </p>

   1. Pare a instância do AEM. Navegue até a `[AEM installation directory]\crx-quickstart\conf\` pasta. Abra o arquivo sling.properties para edição. Se você usar `[AEM installation directory]\crx-quickstart\bin\start.bat` para start de uma instância do AEM, edite sling.properties localizado em `[AEM_root]\crx-quickstart\`.
   1. Adicione as seguintes propriedades ao arquivo sling.properties:<br/> `sling.bootdelegation.class.com.rsa.jsafe.provider.JsafeJCE=com.rsa.*`<br />  `sling.bootdelegation.class.org.bouncycastle.jce.provider.BouncyCastleProvider=org.bouncycastle.*`<br /> `sling.bootdelegation.xerces=org.apache.xerces.*`
   1. Salve e feche o arquivo. <br/>
   1. Start da instância do AEM.<br/>
   <br/>

1. **Como alterar automaticamente a capitalização do texto de formulário adaptável?**
   <p>Você pode usar adaptativos de temas ou editor de estilos para alterar a capitalização de um campo de formulário adaptável. Por exemplo, você pode abrir o editor de temas e definir o valor da propriedade Case de todo o texto do formulário para maiúsculas, minúsculas ou camelCase. Você também pode usar a opção Substituição de CSS no editor de temas para criar diferentes tipos de estilos.</p>