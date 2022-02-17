---
title: 'Converter formulários PDF em formulários adaptáveis '
seo-title: Convert PDF forms to adaptive forms
description: Execute o serviço Automated forms conversion para converter PDF forms em formulários adaptáveis
seo-description: Run the Automated Forms Conversion service to convert PDF forms to adaptive forms
uuid: 49fcd5c0-0e72-496d-9831-00f79d582f57
contentOwner: khsingh
topic-tags: forms
discoiquuid: 9358219c-6079-4552-92b9-b427a23811af
exl-id: 415e05b5-5a90-490c-bf7c-d3365ce95e24
source-git-commit: 5f07f5df6369007a491cf0873839f84a61827cb5
workflow-type: tm+mt
source-wordcount: '1631'
ht-degree: 7%

---

# Converter formulários PDF em formulários adaptáveis {#convert-print-forms-to-adaptive-forms}

O serviço AEM Forms Automated forms conversion, desenvolvido pela Adobe Sensei, converte automaticamente seus PDF forms em formulários adaptáveis responsivos e compatíveis com dispositivos. Quer você esteja usando PDF forms não interativos, Acro Forms ou baseados em XFA, o serviço Automated forms conversion pode converter facilmente esses formulários em formulários adaptáveis. Para obter informações sobre recursos, fluxo de trabalho de conversão e integração, consulte [automated forms conversion](introduction.md) serviço.

## Pré-requisitos {#pre-requisites}

* [**Configurar o serviço de conversão**](configure-service.md)

* **Prepare o [modelos](https://helpx.adobe.com/experience-manager/6-5/forms/using/template-editor.html) a aplicar aos formulários convertidos:** Usar um modelo permite aplicar marcas consistentes em todos os formulários adaptáveis. Além disso, o serviço Automated forms conversion não extrai e usa o cabeçalho e o rodapé de documentos de origem do PDF. É possível usar modelos de formulário adaptáveis para especificar o cabeçalho e o rodapé. O cabeçalho e o rodapé especificados no modelo são aplicados ao formulário adaptável durante a conversão. Ao criar uma pasta para os modelos, selecione o **[!UICONTROL Browse configurations]** para todos.

* **Prepare o [temas](https://helpx.adobe.com/experience-manager/6-5/forms/using/themes.html) a aplicar aos formulários convertidos:** Usar um tema permite aplicar um estilo consistente a todas as formas adaptáveis de sua organização.

* **(opcional)** [**Converter o PDF forms de origem em formulário Adobe Sign**](frequently-asked-questions.md)

## Iniciar o processo de conversão {#start-the-conversion-process}

Depois de conectar a instância do AEM ao AEM Forms Conversion Service, é possível converter os PDF forms em formulários adaptáveis. Execute as seguintes etapas na ordem listada para converter os formulários:

* [Faça upload do PDF forms para o seu servidor AEM Forms](convert-existing-forms-to-adaptive-forms.md#upload-pdf-forms-to-your-aem-forms-server)
* [Executar a conversão](convert-existing-forms-to-adaptive-forms.md#run-the-conversion)
* [Revisar e corrigir os formulários convertidos](review-correct-ui-edited.md)

### Faça upload do PDF forms para o seu servidor AEM Forms {#upload-pdf-forms-to-your-aem-forms-server}

O serviço de conversão converte PDF forms disponíveis na instância do AEM Forms em formulários adaptáveis. Você pode fazer upload de todas as PDF forms de uma só vez ou em fases, conforme necessário. Antes de carregar os formulários, considere o seguinte:

* Mantenha o número de formulários em uma pasta menor que 15 e mantenha o número total de páginas em uma pasta menor que 50.
* Mantenha o tamanho da pasta menor que 10 MB. Não mantenha formulários em uma subpasta.
* Mantenha o número de páginas em um formulário menor que 15.
* Não carregue os formulários protegidos. O serviço não converte formulários protegidos por senha.
* Não carregue formulários de origem com espaços no nome do arquivo. Remova o espaço do nome do arquivo antes de fazer upload dos formulários.
* Não carregue [portfólios em PDF](https://helpx.adobe.com/br/acrobat/using/overview-pdf-portfolios.html). O serviço não converte um Portfolio PDF em um formulário adaptável.
* Leia o [Problemas conhecidos](known-issues.md) e [Práticas recomendadas e considerações](styles-and-pattern-considerations-and-best-practices.md) e fazer alterações sugeridas nos formulários.

Execute as seguintes etapas para carregar os formulários a serem convertidos em uma pasta na sua instância do AEM Forms:

1. Faça logon na instância do AEM Forms.

1. Toque **[!UICONTROL Adobe Experience Manager]** ![](assets/adobeexperiencemanager.png) > **[!UICONTROL Navigation]** ![](assets/compass.png) > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**.
1. Tocar **[!UICONTROL Create]**> **[!UICONTROL Folder]**. Especificar **Título** e **Nome** da pasta. Tocar **[!UICONTROL Create]**. Uma pasta é criada.
1. Toque em para abrir a pasta recém-criada.
1. Tocar **[!UICONTROL Create]**> **[!UICONTROL File Upload]**. Selecione os formulários a serem carregados e clique em **[!UICONTROL Open]** e clique em **[!UICONTROL Upload]**. Os formulários são carregados.

### Executar a conversão {#run-the-conversion}

Após carregar os formulários e configurar o serviço, execute as seguintes etapas para iniciar a conversão:

1. Na instância do AEM Forms, toque em **[!UICONTROL Adobe Experience Manager]** ![Caixa de diálogo Configurações de conversão](assets/adobeexperiencemanager.png) > **[!UICONTROL Navigation]** ![](assets/compass.png) > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**.
1. Selecione um formulário ou a pasta que contém PDF forms (formulários a serem convertidos) e toque em **[!UICONTROL Start Automated Conversion]**. O **[!UICONTROL Conversion Settings]** será exibida.

   ![Especificar as configurações](assets/conversion-settings-dialog.png)

1. No **[!UICONTROL Basic]** da caixa de diálogo Configurações de conversão:

   * **[!UICONTROL Select a cloud configuration]**. Ao selecionar uma configuração, o modelo padrão e o tema já são especificados. Você pode especificar um modelo diferente ou um tema, se necessário.
   * Especifique um local para salvar formulários adaptáveis gerados e o esquema correspondente. Você pode usar caminhos padrão ou especificar caminhos personalizados.
   * Use o **Gerar formulários adaptáveis sem vínculos com o modelo de dados** opção para selecionar se deseja gerar um formulário adaptável com ou sem vínculos de modelo de dados.
Se você não selecionar essa opção, o serviço de conversão associará automaticamente os formulários adaptáveis a um esquema JSON e criará um vínculo de dados entre os campos disponíveis no formulário adaptável e no esquema JSON. O **[!UICONTROL Save generated data model schema at]** exibe o local padrão para salvar o esquema JSON gerado. Você também pode personalizar o local para salvar o schema gerado.
Se você selecionar essa opção, o serviço de conversão gera um formulário adaptável sem vínculos de modelo de dados. Após uma conversão bem-sucedida, é possível associar um formulário adaptável a um Modelo de dados de formulário, esquema XML ou um esquema JSON. Para obter mais informações, consulte [Criação de um formulário adaptável](https://helpx.adobe.com/experience-manager/6-5/forms/using/creating-adaptive-form.html).

   <!--

   Comment Type: draft

   <note type="note">
   <p>The XDP or XFA-based PDF form is not used to generate the Document of Record. The conversion service auto-generates the Document of Record only if you enable the Tools &gt; Cloud Services &gt; Automated Forms Conversion Configuration &gt; <strong>&lt;Properties of selected configuration&gt; &gt;</strong> Advanced &gt; Generate Document of Record option.</p>
   <p> </p>
   </note>
   -->

1. No **[!UICONTROL Additional]** guia da caixa de diálogo Configurações de conversão,
   * Selecione o **[!UICONTROL Extract fragment from adaptive forms]** para permitir que o serviço de conversão identifique, extraia e baixe fragmentos de formulário para formulários convertidos. Ao selecionar a variável **[!UICONTROL Extract fragment from adaptive forms]** , as opções para especificar caminhos para salvar fragmentos de formulário extraídos e esquemas correspondentes de fragmentos de formulário são ativadas.
   * Especifique a localização de **[!UICONTROL existing adaptive form fragments]**, se você tiver alguns fragmentos de formulário baseados em esquema JSON e o esquema menos adaptáveis e planejar usar esses fragmentos em formulários adaptáveis gerados automaticamente. O serviço de conversão corresponde aos fragmentos de formulário JSON disponíveis com base em esquema e menos adaptáveis ao esquema com PDF forms de entrada (somente PDF forms não interativos), se houver uma correspondência, o fragmento de formulário adaptável correspondente será usado nos formulários adaptáveis correspondentes.

   >[!NOTE]
   >
   >
   > * Você pode usar somente **[!UICONTROL  Extract Fragment]** ou **[!UICONTROL Use existing adaptive form fragments]** de cada vez. Não é possível usar ambas as opções simultaneamente.
   > * Você pode usar o **[!UICONTROL Use existing adaptive form fragments]** somente com PDF forms não interativos. Outros tipos de formulário ainda não são compatíveis.
   > * Você só pode usar fragmentos ou fragmentos não vinculados a um esquema JSON com o Serviço de conversão automatizada. Não use fragmentos XFA. Fragmentos XFA não são compatíveis.


   * Selecione o **[!UICONTROL Auto-detect multi-column layout of input forms]** para manter o layout do formulário de origem para telas grandes, como desktops e laptops. A opção é útil para preservar o layout de várias colunas de formulários de origem. Por exemplo, quando um PDF de origem tem um layout de duas colunas, o serviço gera um formulário adaptável de saída com um layout de duas colunas para telas grandes e um layout de coluna única para dispositivos de tela pequena, como telefones celulares. O recurso tem alguns problemas conhecidos com a estrutura do schema da fonte de dados. Para obter detalhes, consulte o [problemas conhecidos](known-issues.md) artigo 10. o
   * Por padrão, o serviço cria um painel de nível superior separado para cada página de um formulário PDF. Agora, você pode usar o **[!UICONTROL Auto-detect logical sections]** opção para não criar painéis no nível da página (painéis baseados em números de página) e criar apenas painéis lógicos. Ele também agrupa os campos que não pertencem a nenhuma seção com a seção lógica anterior e agrupa os campos de uma seção lógica espalhados por duas páginas adjacentes em uma única seção lógica. Por exemplo, se alguns campos de uma seção lógica estiverem no final da página um e alguns estiverem no início da página dois, todos esses campos serão agrupados em uma única seção lógica.

      >[!NOTE]
      > Você precisa do pacote de conectores 1.1.38 ou superior para usar o  **[!UICONTROL Auto-detect logical sections]** recurso.


* (Somente AEM Forms as a Cloud Service) A variável [Conversão automática de seções em fragmentos] se aplica a PDF forms com mais de 15 páginas. Ele converte as seções de nível superior detectadas em fragmentos. Ele também permite o carregamento lento para todos os fragmentos criados. Ajuda a melhorar a velocidade de renderização de formulários convertidos e facilita o carregamento de formulários grandes no editor de formulários adaptável.

   >[!NOTE]
   > Não use o modelo de layout responsivo ao usar a opção Conversão automática de seções em fragmentos .
   > Use o editor de revisão e correção para mesclar pequenos painéis em um grande. Ajuda a reduzir o número de fragmentos no formulário adaptável convertido.
   > Se você enfrentar a exceção &quot;muitas chamadas&quot;,
   >
   > * reestruturar o formulário para criar uma hierarquia simplificada
   > * [aumente o valor do parâmetro sling.max.calls]para um número alto o suficiente até que a exceção desapareça.
   > * [aumentar o tamanho do cache](https://experienceleague.adobe.com/docs/experience-manager-65/forms/install-aem-forms/configure-aem-forms/configure-adaptive-forms-cache.html). O erro ocorre se o formulário for muito complexo, tiver um grande número de tabelas e uma estrutura hierárquica de vários níveis.


1. Tocar **[!UICONTROL Start Conversion]**. A Conversão é iniciada. O progresso da conversão é exibido na pasta ou no formulário até que a conversão esteja em andamento. A mensagem é substituída por outra mensagem de status (Convertido, Parcialmente Convertido ou Falha de Conversão) após a conversão ser concluída. Um email de status também é enviado no endereço de email configurado após a conclusão da conversão:

   * Em uma conversão bem-sucedida, o formulário adaptável convertido e o schema relacionado são baixados para o caminho especificado na variável **[!UICONTROL Basic]** da caixa de diálogo de conversão. Os fragmentos de formulário e o esquema correspondente são baixados somente se a opção Extrair fragmento estiver selecionada antes de iniciar a conversão.
   * Em uma conversão com falha, a variável **[!UICONTROL Conversion Failed]** será exibida se todos os formulários de entrada falharem na conversão ou a variável **[!UICONTROL Partially Failed]** será exibida quando apenas alguns de todos os formulários de entrada falharem na conversão. Um email de status é enviado no [endereço de email configurado](configure-service.md#configureemailnotification) e um erro é registrado no arquivo error.log.

   Se um formulário PDF baseado em XFA for convertido em um formulário adaptável, o serviço de conversão associará automaticamente o formulário PDF ao formulário adaptável convertido como o modelo Documento de registro. Após a conversão, você pode abrir as propriedades do formulário adaptável para exibir o modelo de Documento de registro na **[!UICONTROL Document of Record Template Configuration]** seção de **[!UICONTROL Form Model]** guia . </br>

   O serviço de conversão carrega automaticamente o formulário PDF para o formulário adaptável convertido como o modelo Documento de registro somente se você habilitar o **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Automated Forms Conversion Configuration]** > **[!UICONTROL Properties of selected configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Generate Document of Record]** opção.

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
   >Se o processo de conversão levar mais de 60 minutos e o formulário PDF ainda não for convertido em um formulário adaptável, crie uma pasta na instância do AEM Forms, faça o upload do formulário PDF para a pasta recém-criada e reinicie a conversão.

## Revisar e corrigir os formulários convertidos {#review-and-correct-the-converted-forms}

Os formulários do mundo real têm requisitos complexos de captura de dados. Quando a conversão automática estiver concluída, os clientes poderão revisar a qualidade de conversão do formulário e fazer as atualizações necessárias no formulário. A AEM Forms fornece uma [revisar e corrigir](review-correct-ui-edited.md) para fazer as alterações necessárias. Ele permite melhorar a identificação automatizada de campos de formulário e converter campos identificados de um tipo para outro. Por exemplo, é possível ajudar a identificar o layout de duas colunas de um formulário e alterar um campo identificado automaticamente como botão de opção para vários campos de opções.
