---
title: Gerar documento de registro durante a conversão
seo-title: Gerar documento de registro durante a conversão
description: Caminhos recomendados para gerar um DoR com base no tipo de formulários de origem usados para conversão.
seo-description: Caminhos recomendados para gerar um DoR com base no tipo de formulários de origem usados para conversão.
page-status-flag: never-activated
uuid: 7f0f5bf3-21be-449a-b23e-5946a9fd7ed4
contentOwner: khsingh
discoiquuid: 75f6e6bc-7636-4b40-919c-8b20a6ccbb1f
translation-type: tm+mt
source-git-commit: 640d72d7961ef0c2393bf0ae6745d918e388a056
workflow-type: tm+mt
source-wordcount: '878'
ht-degree: 3%

---


# Fluxos de trabalho recomendados para habilitar a geração de documentos de registro para formulários adaptáveis {#recommended-workflows-dor-generation}

O Documento de registro (DoR) permite que você mantenha um registro das informações fornecidas e enviadas em um formulário adaptável para que possa consultá-lo posteriormente.
O DoR usa um modelo base para definir seu layout. Você pode gerar um DoR usando um modelo padrão ou associando qualquer outro modelo ao formulário adaptável.

![Documento de registro gerado](assets/document_of_record.gif)

Para obter mais informações sobre como gerar um DoR, consulte [Gerar Documento de Registro para formulários adaptáveis](https://helpx.adobe.com/experience-manager/6-5/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.html).

O [serviço de Automated forms conversion](../help/introduction.md) converte os seguintes formulários de origem em formulários adaptáveis:

* pdf forms não interativos
* Acro Forms
* PDF forms baseados em XFA

Com base no formulário de origem usado para conversão, é possível gerar um DoR usando:

* um modelo padrão
* o formulário de origem como modelo - se você selecionar essa opção, o serviço de conversão associará automaticamente o formulário de origem ao formulário adaptável convertido como modelo DoR.
* associar qualquer outro modelo ao formulário adaptativo convertido

A tabela a seguir ilustra um exemplo de como o modelo DoR usado afeta o layout do DoR gerado:

<table> 
 <tbody>
 <tr>
  <td><p><strong>Formulário fonte</strong></p></td>
  <td><p><strong>DoR gerado</strong></p></td> 
   </tr>
  <tr>
   <td><img src="assets/source_xdp_updated.png"/></td>
   <td><p>Se você usar o modelo padrão para gerar DoR:</br><img src="assets/source_form_default_updated.png"/></td>
   </tr>
   <tr>
   <td></td>
   <td><p>Se você usar o formulário de origem como modelo para gerar DoR:</br></p><img src="assets/source_form_dor_updated.png"/></td>
   </tr>
  </tbody>
</table>

Conforme ilustrado na tabela, se você usar o formulário de origem como modelo, o DoR manterá o layout do formulário de origem.
Este artigo descreve os caminhos recomendados para gerar um DoR com base nos três tipos de formulários de origem.

<table> 
 <tbody> 
  <tr> 
   <th><strong>Formulário fonte</strong></th> 
   <th><strong>Métodos para gerar DoR</strong></th> 
  </tr> 
  <tr> 
   <td><p>PDF forms não interativos</p></td> 
   <td> 
    <ul> 
     <li><a href="#generate-document-of-record-using-cloud-configuration">Ative a geração DoR antes da conversão de formulário adaptável para gerar DoR usando um modelo padrão</a></li> 
     <li><a href="#edit-adaptive-form-properties-generate-document-of-record">Edite as propriedades de formulário adaptável após a conversão de formulário adaptável para ativar a geração DoR usando o padrão ou qualquer outro modelo de formulário</a></li> 
    </ul> </td> 
  </tr>
  <tr> 
   <td><p>PDF forms baseados em Forms ou XFA</p></td> 
   <td> 
    <ul> 
     <li><a href="#use-input-form-as-template-to-generate-document-of-record">Ative a geração DoR antes da conversão de formulário adaptável para gerar DoR usando o formulário de origem como modelo</a></li> 
     <li><a href="#edit-adaptive-form-properties-to-generate-document-of-record">Edite as propriedades de formulário adaptáveis após a conversão de formulário adaptável para ativar a geração DoR usando o modelo padrão, o formulário de origem como modelo ou qualquer outro modelo de formulário</a></li> 
    </ul> </td> 
  </tr>    
 </tbody> 
</table>

## Gerar Documento de Registro para PDF forms não interativos {#generate-document-of-record-non-interactive-pdf}

Se você estiver usando um formulário PDF não interativo como o formulário de origem para o serviço de Automated forms conversion, é possível:

* ativar a geração DoR antes da conversão de formulário adaptável para gerar DoR usando um modelo padrão
* ou edite as propriedades adaptáveis do formulário após a conversão adaptável do formulário para ativar a geração DoR usando o padrão ou qualquer outro modelo de formulário

### Ative a geração DoR antes da conversão para gerar DoR usando o modelo padrão {#generate-document-of-record-using-cloud-configuration}

1. Selecione **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Automated Forms Conversion Configuration]** > Propriedades da configuração de nuvem usada para conversão > opção **[!UICONTROL Advanced]** > **[!UICONTROL Generate Document of Record]**.

   ![Gerar Documento de Registro usando a configuração da nuvem](assets/generate_dor_cloud_config.gif)

1. Toque em **[!UICONTROL Save & Close]** para salvar as configurações.

1. [Execute a conversão](../help/convert-existing-forms-to-adaptive-forms.md). Certifique-se de usar a configuração de nuvem editada na etapa 1 dessas instruções.
Ao enviar o formulário adaptativo convertido, o DoR é gerado automaticamente usando o modelo padrão.

### Edite as propriedades de formulário adaptável após a conversão para ativar a geração Do {#edit-adaptive-form-properties-generate-document-of-record}

Se você não ativar a geração DoR antes de converter o formulário de origem em um formulário adaptável, ainda será possível fazê-lo após a conversão.

1. [Execute a ](../help/convert-existing-forms-to-adaptive-forms.md) conversão no formulário PDF não interativo para gerar um formulário adaptável.

1. Selecione o formulário adaptável na pasta **[!UICONTROL output]** e toque em **[!UICONTROL Properties]**.

1. Na guia **[!UICONTROL Form Model]**, expanda a seção **[!UICONTROL Document of Record Template Configuration]** e selecione **[!UICONTROL Generate Document of Record]**.

   ![Gerar documento de registro](assets/generate_dor_af_properties.png)

1. Toque em **[!UICONTROL Save & Close]** para salvar as configurações.

Ao enviar o formulário adaptativo convertido, o DoR é gerado automaticamente usando o modelo padrão. Se quiser associar qualquer outro modelo DoR ao formulário adaptativo convertido, selecione a opção **[!UICONTROL Associate form template as the Document of Record template]**.

## Gerar Documento de Registro para PDF forms baseados no Acro Forms ou XFA {#generate-document-of-record-acroform-xfaform}

Se você estiver usando um formulário PDF baseado em Acro Form ou XFA como o formulário de origem para o serviço de Automated forms conversion, é possível:

* ativar a geração DoR antes da conversão de formulário adaptável para gerar DoR usando o formulário de origem como modelo

* ou edite as propriedades adaptáveis do formulário após a conversão adaptável do formulário para ativar a geração DoR usando o modelo padrão, o formulário de origem como modelo ou qualquer outro modelo de formulário

### Ative a geração DoR antes da conversão para gerar DoR usando o modelo de formulário de origem {#use-input-form-as-template-to-generate-document-of-record}

1. Selecione **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Automated Forms Conversion Configuration]** > Propriedades da configuração de nuvem usada para conversão > opção **[!UICONTROL Advanced]** > **[!UICONTROL Generate Document of Record]**.

1. Toque em **[!UICONTROL Save & Close]** para salvar as configurações.

1. [Execute a conversão](../help/convert-existing-forms-to-adaptive-forms.md). Certifique-se de usar a configuração de nuvem editada na etapa 1 dessas instruções.
O serviço de conversão associa automaticamente o formulário Acro Form ou PDF baseado em XFA ao formulário adaptável convertido como modelo DoR.
É possível abrir as propriedades de formulário adaptável para visualização do modelo DoR na seção **[!UICONTROL Document of Record Template Configuration]** da guia **[!UICONTROL Form Model]**.

   ![Editar propriedades de formulário adaptáveis para gerar o Documento de Registro](assets/generate_dor_af_properties_xdp_acro.png)

   Ao enviar o formulário adaptativo convertido, o DoR é gerado automaticamente usando o modelo de formulário de origem.

### Edite as propriedades de formulário adaptável após a conversão para ativar a geração Do {#edit-adaptive-form-properties-to-generate-document-of-record}

1. [Execute a ](../help/convert-existing-forms-to-adaptive-forms.md) conversão no formulário PDF não interativo para gerar um formulário adaptável.

1. Selecione o formulário adaptável na pasta **[!UICONTROL output]** e toque em **[!UICONTROL Properties]**.

1. Na guia **[!UICONTROL Form Model]**, expanda a seção **[!UICONTROL Document of Record Template Configuration]** e selecione **[!UICONTROL Generate Document of Record]** para ativar a geração DoR usando o modelo padrão.
Você também pode selecionar a opção **[!UICONTROL Associate form template as the Document of Record template]** e selecionar o modelo para ativar a geração DoR usando o modelo de formulário de origem ou qualquer outro modelo de formulário.

1. Toque em **[!UICONTROL Save & Close]** para salvar as configurações.
