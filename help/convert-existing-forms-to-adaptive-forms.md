---
title: 'Converter formulários PDF em formulários adaptáveis '
seo-title: 'Converter formulários PDF em formulários adaptáveis '
description: Execute o serviço de Conversão de formulários automatizados para converter formulários PDF em formulários adaptáveis
seo-description: Execute o serviço de Conversão de formulários automatizados para converter formulários PDF em formulários adaptáveis
uuid: 49fcd5c0-0e72-496d-9831-00f79d582f57
contentOwner: khsingh
topic-tags: forms
discoiquuid: 9358219c-6079-4552-92b9-b427a23811af
translation-type: tm+mt
source-git-commit: bbf39e3bae55654f92a50f52a22cee5da938236d

---


# Converter formulários PDF em formulários adaptáveis {#convert-print-forms-to-adaptive-forms}

O serviço de Conversão de formulários automatizados do AEM Forms, desenvolvido pelo Adobe Sensei, converte automaticamente seus formulários PDF em formulários adaptativos responsivos e amigáveis ao dispositivo. Quer você esteja usando formulários PDF não interativos, formulários Acro Forms ou formulários PDF baseados em XFA, o serviço de Conversão de formulários automatizados pode converter esses formulários facilmente em formulários adaptáveis. Para obter informações sobre recursos, fluxo de trabalho de conversão e informações de onboard, consulte o serviço de conversão [de formulários](introduction.md) automatizados.

## Pré-requisitos {#pre-requisites}

* [**Configurar o serviço de conversão **](configure-service.md)

* **[Prepare os](https://helpx.adobe.com/experience-manager/6-5/forms/using/template-editor.html)modelos** a serem aplicados aos formulários convertidos: Usar um modelo permite aplicar marcas consistentes em todos os formulários adaptativos. Além disso, o serviço de Conversão de formulários automatizados não extrai nem usa cabeçalho e rodapé de documentos PDF de origem. Você pode usar modelos de formulário adaptáveis para especificar cabeçalho e rodapé. O cabeçalho e o rodapé especificados no modelo são aplicados aos formulários adaptáveis durante a conversão.

* **[Prepare os](https://helpx.adobe.com/experience-manager/6-5/forms/using/themes.html)temas** a serem aplicados aos formulários convertidos: O uso de um tema permite que você aplique um estilo consistente a todas as formas adaptáveis de sua organização.

## Iniciar o processo de conversão {#start-the-conversion-process}

Depois de conectar sua instância do AEM com o serviço de conversão de formulários AEM, é possível converter formulários PDF em formulários adaptáveis. Execute as seguintes etapas na ordem listada para converter os formulários:

* [Carregar formulários PDF no servidor do AEM Forms](convert-existing-forms-to-adaptive-forms.md#upload-pdf-forms-to-your-aem-forms-server)
* [Executar a conversão](convert-existing-forms-to-adaptive-forms.md#run-the-conversion)
* [Revisar e corrigir os formulários convertidos](review-correct-ui-edited.md)

### Carregar formulários PDF no servidor do AEM Forms {#upload-pdf-forms-to-your-aem-forms-server}

O serviço de conversão converte formulários PDF disponíveis na instância do AEM Forms em formulários adaptáveis. Você pode carregar todos os formulários PDF de uma vez ou em fases, conforme necessário. Antes de carregar os formulários, considere o seguinte:

* Mantenha o número de formulários em uma pasta menor que 15 e mantenha o número total de páginas em uma pasta menor que 50.
* Mantenha o tamanho da pasta com menos de 10 MB. Não mantenha formulários em uma subpasta.
* Mantenha o número de páginas em um formulário menor que 15.
* Não carregue os formulários protegidos. O serviço não converte formulários protegidos por senha e protegidos.
* Não carregue formulários de origem com espaços no nome do arquivo. Remova o espaço do nome do arquivo antes de fazer upload dos formulários.
* Não carregue portfólios [PDF](https://helpx.adobe.com/acrobat/using/overview-pdf-portfolios.html). O serviço não converte um Portfólio PDF em formulários adaptáveis.
* Leia as seções [Problemas](known-issues.md) conhecidos e [Práticas recomendadas e considerações](styles-and-pattern-considerations-and-best-practices.md) e faça as alterações sugeridas nos formulários.

Execute as seguintes etapas para carregar os formulários a serem convertidos em uma pasta na instância do AEM Forms:

1. Faça logon na instância do AEM Forms.

1. Tap **[!UICONTROL Adobe Experience Manager]** ![](assets/adobeexperiencemanager.png) > **[!UICONTROL Navigation]** ![](assets/compass.png) > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**.
1. Tocar **[!UICONTROL Create]**> **[!UICONTROL Folder]**. Especifique **Título** e **Nome** da pasta. Tocar **[!UICONTROL Create]**. Uma pasta é criada.
1. Toque em para abrir a pasta recém-criada.
1. Tocar **[!UICONTROL Create]**> **[!UICONTROL File Upload]**. Selecione os formulários a serem carregados, clique em **[!UICONTROL Open]** e clique em **[!UICONTROL Upload]**. Os formulários são carregados.

### Executar a conversão {#run-the-conversion}

Após carregar os formulários e configurar o serviço, execute as seguintes etapas para iniciar a conversão:

1. Na instância do AEM Forms, toque em Caixa de diálogo **[!UICONTROL Adobe Experience Manager]** Configurações de ![conversão >](assets/adobeexperiencemanager.png) > **[!UICONTROL Navigation]** > ![](assets/compass.png) **[!UICONTROL Forms]** **[!UICONTROL Forms & Documents]**.
1. Selecione um formulário ou a pasta que contém formulários PDF (formulários a serem convertidos) e toque em **[!UICONTROL Start Automated Conversion]**. A **[!UICONTROL Conversion Settings]** caixa de diálogo é exibida.

   ![Especificar as configurações](assets/conversion-settings-dialog.png)

1. Na **[!UICONTROL Basic]** guia da caixa de diálogo Configurações de conversão:

   * **[!UICONTROL Select a cloud configuration]**. Quando você seleciona uma configuração, o modelo padrão e o tema já são especificados. Você pode especificar um modelo ou um tema diferente, se necessário.
   * Especifique um local para salvar formulários adaptativos gerados e o esquema correspondente. Você pode usar caminhos padrão ou especificar caminhos personalizados.
   * Use a opção **Gerar formulários adaptáveis sem vínculos** de modelo de dados para selecionar se deseja gerar um formulário adaptável com ou sem vínculos de modelo de dados.
Se essa opção não for selecionada, o serviço de conversão associará automaticamente os formulários adaptáveis a um esquema JSON e criará um vínculo de dados entre os campos disponíveis no formulário adaptável e no esquema JSON. O **[!UICONTROL Save generated data model schema at]** campo exibe o local padrão para salvar o esquema JSON gerado. Você também pode personalizar o local para salvar o esquema gerado.
Se você selecionar essa opção, o serviço de conversão gerará um formulário adaptável sem vínculos de modelo de dados. Após uma conversão bem-sucedida, você pode associar um formulário adaptável a um Modelo de dados de formulário, esquema XML ou esquema JSON. Para obter mais informações, consulte [Criação de um formulário](https://helpx.adobe.com/experience-manager/6-5/forms/using/creating-adaptive-form.html)adaptável.
   <!--
   Comment Type: draft

   <note type="note">
   <p>The XDP or XFA-based PDF form is not used to generate the Document of Record. The conversion service auto-generates the Document of Record only if you enable the Tools &gt; Cloud Services &gt; Automated Forms Conversion Configuration &gt; <strong>&lt;Properties of selected configuration&gt; &gt;</strong> Advanced &gt; Generate Document of Record option.</p>
   <p> </p>
   </note>
   -->

1. Na **[!UICONTROL Additional]** guia da caixa de diálogo Configurações de conversão,
   * Selecione a **[!UICONTROL Extract fragment from adaptive forms]** opção para permitir que o serviço de conversão identifique, extraia e baixe fragmentos de formulário para formulários convertidos. Quando você seleciona a **[!UICONTROL Extract fragment from adaptive forms]** opção, as opções para especificar caminhos para salvar fragmentos de formulário extraídos e esquemas correspondentes de fragmentos de formulário são ativadas.
   * Especifique o local de **[!UICONTROL existing adaptive form fragments]**, se você tiver alguns fragmentos de formulário com base em esquema JSON e menos adaptáveis do esquema, e planeja usar esses fragmentos em formulários adaptáveis gerados automaticamente. O serviço de conversão corresponde aos fragmentos de formulário disponíveis baseados em esquema JSON e menos adaptáveis ao esquema com os formulários PDF de entrada (somente formulários PDF não interativos), se houver uma correspondência, o fragmento de formulário adaptável correspondente será usado nos formulários adaptáveis correspondentes.
   >[!NOTE]
   >
   >
   > * Você pode usar somente **[!UICONTROL  Extract Fragment]** ou **[!UICONTROL Use existing adaptive form fragments]** a opção por vez. Não é possível usar ambas as opções simultaneamente.
   > * É possível usar a **[!UICONTROL Use existing adaptive form fragments]** opção somente com formulários PDF não interativos. Outros tipos de formulário ainda não são suportados.
   > * Você pode usar apenas fragmentos ou fragmentos não vinculados a um esquema JSON com Serviço de conversão automatizada. Não use fragmentos XFA. Fragmentos XFA não são suportados.


   * Selecione a **[!UICONTROL Auto-detect multi-column layout of input forms]** opção para manter o layout do formulário de origem para telas grandes, como desktops e laptops. A opção é útil para preservar o layout de várias colunas dos formulários de origem. Por exemplo, quando um PDF de origem tem um layout de duas colunas, o serviço gera um formulário adaptável de saída com um layout de duas colunas para telas grandes e um layout de coluna única para dispositivos de tela pequena, como telefones celulares. O recurso tem alguns problemas conhecidos com a estrutura do esquema da fonte de dados. Para obter detalhes, consulte o artigo sobre problemas [](known-issues.md) conhecidos.



1. Tocar **[!UICONTROL Start Conversion]**. A Conversão é iniciada. O progresso da conversão é exibido na pasta ou no formulário até que a conversão esteja em andamento. A mensagem é substituída por outra mensagem de status (Convertido, Parcialmente convertido ou Falha de conversão) após a conversão ser concluída. Um email de status também é enviado no endereço de email configurado após a conclusão da conversão:

   * Em uma conversão bem-sucedida, o formulário adaptativo convertido e o esquema relacionado são baixados para o caminho especificado na **[!UICONTROL Basic]** guia da caixa de diálogo de conversão. Os fragmentos de formulário e o esquema correspondente são baixados somente se a opção Extrair fragmento estiver selecionada antes de iniciar a conversão.
   * Em uma conversão com falha, a **[!UICONTROL Conversion Failed]** mensagem será exibida se todos os formulários de entrada falharem na conversão ou se a mensagem **[!UICONTROL Partially Failed]** for exibida quando apenas alguns de todos os formulários de entrada falharem na conversão. Um email de status é enviado no endereço [de email](configure-service.md#configureemailnotification) configurado e um erro é registrado no arquivo error.log.
   Se um formulário PDF baseado em XFA for convertido em um formulário adaptável, o serviço de conversão associará automaticamente o formulário PDF ao formulário adaptável convertido como modelo Documento de registro. Após a conversão, é possível abrir as propriedades do formulário adaptável para exibir o modelo Documento de registro na **[!UICONTROL Document of Record Template Configuration]** seção da **[!UICONTROL Form Model]** guia. </br>

   O serviço de conversão carrega automaticamente o formulário PDF no formulário adaptável convertido como o modelo Documento de registro somente se você ativar a opção **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Automated Forms Conversion Configuration]** > **[!UICONTROL Properties of selected configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Generate Document of Record]** .

   <!--
   Comment Type: draft

   <note type="note">
   <p>By default, the adaptive form produces a JSON schema instead of XML schema on submission. JSON schema of a converted adaptive form is complaint with XML schema of an XFA-based form. You can use the <a href="https://sling.apache.org/apidocs/sling5/org/apache/sling/commons/json/xml/XML.html#toString">org.apache.sling.commons.json.xml API</a> to convert a JSON schema to XML schema. You can also use the following sample code for conversion:</p>
   <p><code class="code">import org.apache.sling.commons.json.JSONException;
   <discoiqbr /> import org.apache.sling.commons.json.JSONObject;
   <discoiqbr /> import org.apache.sling.commons.json.xml.XML;
   <discoiqbr />
   <discoiqbr /> public class ConversionUtils {
   <discoiqbr />
   <discoiqbr /> public static String jsonToXML(String jsonString) throws JSONException {
   <discoiqbr /> //https://sling.apache.org/apidocs/sling5/org/apache/sling/commons/json/xml/XML.html#toString(java.lang.Object)
   <discoiqbr /> //jar - http://maven.ibiblio.org/maven2/org/apache/sling/org.apache.sling.commons.json/2.0.18/
   <discoiqbr /> //Note: Need to extract boundData part before converting to XML
   <discoiqbr /> return XML.toString(new JSONObject(jsonString));
   <discoiqbr /> }
   <discoiqbr /> }</code><br /> </p>
   </note>
   -->

   >[!NOTE]
   >
   >Se o processo de conversão levar mais de 60 minutos e o formulário PDF ainda não for convertido em um formulário adaptável, crie uma nova pasta na instância do AEM Forms, carregue o formulário PDF na pasta recém-criada e reinicie a conversão.

## Revisar e corrigir os formulários convertidos {#review-and-correct-the-converted-forms}

Os formulários do mundo real têm requisitos complexos de captura de dados. Quando a conversão automática estiver concluída, os clientes poderão revisar a qualidade de conversão do formulário e fazer as atualizações necessárias para o formulário. O AEM Forms fornece um editor de [revisão e correção](review-correct-ui-edited.md) para fazer as alterações necessárias. Permite melhorar a identificação automatizada de campos de formulário e converter campos identificados de um tipo para outro. Por exemplo, você pode ajudar a identificar o layout de duas colunas de um formulário e alterar um campo identificado automaticamente como botão de opção para o campo de várias opções.