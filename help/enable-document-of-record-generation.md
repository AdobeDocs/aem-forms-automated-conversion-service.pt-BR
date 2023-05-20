---
title: Gerar documento de registro durante a conversão
seo-title: Generate Document of Record during conversion
description: Caminhos recomendados para gerar uma DoR com base no tipo de formulários de origem usados para conversão.
seo-description: Recommended paths to generate a DoR based on the type of source forms used for conversion.
page-status-flag: never-activated
uuid: 7f0f5bf3-21be-449a-b23e-5946a9fd7ed4
contentOwner: khsingh
discoiquuid: 75f6e6bc-7636-4b40-919c-8b20a6ccbb1f
exl-id: c24313cd-2b9b-4209-9505-a8e14d8dc530
source-git-commit: 1a3f79925f25dcc7dbe007f6e634f6e3a742bf72
workflow-type: tm+mt
source-wordcount: '856'
ht-degree: 2%

---

# Fluxos de trabalho recomendados para habilitar a geração de documentos de registro para formulários adaptáveis {#recommended-workflows-dor-generation}

O Documento de registro (DoR) permite manter um registro das informações fornecidas e submetê-las em um formulário adaptável para que você possa consultá-las posteriormente.
O DoR usa um modelo base para definir seu layout. Você pode gerar uma DoR usando um modelo padrão ou associando qualquer outro modelo ao formulário adaptável.

![Documento de registro gerado](assets/document_of_record.gif)

Para obter mais informações sobre como gerar uma DoR, consulte [Gerar documento de registro para formulários adaptáveis](https://helpx.adobe.com/experience-manager/6-5/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.html).

A variável [serviço Automated forms conversion](../help/introduction.md) converte os seguintes formulários de origem em formulários adaptáveis:

* PDF forms não interativos
* Acro Forms
* PDF forms baseado em XFA

Com base no formulário de origem usado para conversão, é possível gerar uma DoR usando:

* um template padrão
* o formulário de origem como modelo - Se você selecionar essa opção, o serviço de conversão associará automaticamente o formulário de origem ao formulário adaptável convertido como o modelo DoR.
* associar qualquer outro modelo ao formulário adaptável convertido

A tabela a seguir ilustra um exemplo de como o modelo DoR usado afeta o layout do DoR gerado:

<table> 
 <tbody>
 <tr>
  <td><p><strong>Formulário de origem</strong></p></td>
  <td><p><strong>DoR gerado</strong></p></td> 
   </tr>
  <tr>
   <td><img src="assets/source_xdp_updated.png"/></td>
   <td><p>Se você usar o template padrão para gerar DoR:</br><img src="assets/source_form_default_updated.png"/></td>
   </tr>
   <tr>
   <td></td>
   <td><p>Se você usar o formulário de origem como modelo para gerar DoR:</br></p><img src="assets/source_form_dor_updated.png"/></td>
   </tr>
  </tbody>
</table>

Conforme ilustrado na tabela, se você usar o formulário de origem como modelo, o DoR manterá o layout do formulário de origem.
Este artigo descreve os caminhos recomendados para gerar uma DoR com base nos três tipos de formulários de origem.

<table> 
 <tbody> 
  <tr> 
   <th><strong>Formulário de origem</strong></th> 
   <th><strong>Métodos para gerar DoR</strong></th> 
  </tr> 
  <tr> 
   <td><p>PDF forms não interativos</p></td> 
   <td> 
    <ul> 
     <li><a href="#generate-document-of-record-using-cloud-configuration">Habilite a geração de DoR antes da conversão do formulário adaptável para gerar DoR usando um modelo padrão</a></li> 
     <li><a href="#edit-adaptive-form-properties-generate-document-of-record">Editar propriedades do formulário adaptável após a conversão do formulário adaptável para habilitar a geração de DoR usando o padrão ou qualquer outro modelo de formulário</a></li> 
    </ul> </td> 
  </tr>
  <tr> 
   <td><p>PDF forms baseados no Acro Forms ou XFA</p></td> 
   <td> 
    <ul> 
     <li><a href="#use-input-form-as-template-to-generate-document-of-record">Habilite a geração de DoR antes da conversão do formulário adaptável para gerar DoR usando o formulário de origem como modelo</a></li> 
     <li><a href="#edit-adaptive-form-properties-to-generate-document-of-record">Edite as propriedades do formulário adaptável após a conversão do formulário adaptável para habilitar a geração de DoR usando o modelo padrão, o formulário de origem como modelo ou qualquer outro modelo de formulário</a></li> 
    </ul> </td> 
  </tr>    
 </tbody> 
</table>

## Gerar documento de registro para PDF forms não interativos {#generate-document-of-record-non-interactive-pdf}

Se você estiver usando um formulário PDF não interativo como o formulário de origem para o serviço Automated forms conversion, é possível:

* habilite a geração de DoR antes da conversão do formulário adaptável para gerar DoR usando um modelo padrão
* ou edite as propriedades do formulário adaptável após a conversão do formulário adaptável para habilitar a geração de DoR usando o padrão ou qualquer outro modelo de formulário

### Habilitar geração de DoR antes da conversão para gerar DoR usando o modelo padrão {#generate-document-of-record-using-cloud-configuration}

1. Selecionar **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Automated Forms Conversion Configuration]** > Propriedades da configuração da nuvem usadas para conversão > **[!UICONTROL Advanced]** > **[!UICONTROL Generate Document of Record]** opção.

   ![Gerar documento de registro usando a configuração na nuvem](assets/generate_dor_cloud_config.gif)

1. Toque **[!UICONTROL Save & Close]** para salvar as configurações.

1. [Executar a conversão](../help/convert-existing-forms-to-adaptive-forms.md). Certifique-se de usar a configuração de nuvem editada na etapa 1 dessas instruções.
Ao enviar o formulário adaptável convertido, o DoR é gerado automaticamente usando o modelo padrão.

### Editar propriedades do formulário adaptável após a conversão para habilitar a geração de DoR {#edit-adaptive-form-properties-generate-document-of-record}

Se você não habilitar a geração de DoR antes de converter o formulário de origem em um formulário adaptável, ainda poderá fazer isso após a conversão.

1. [Executar a conversão](../help/convert-existing-forms-to-adaptive-forms.md) no formulário PDF não interativo para gerar um formulário adaptável.

1. Selecione o formulário adaptável no **[!UICONTROL output]** pasta e toque em **[!UICONTROL Properties]**.

1. No **[!UICONTROL Form Model]** , expanda a **[!UICONTROL Document of Record Template Configuration]** e selecione **[!UICONTROL Generate Document of Record]**.

   ![Gerar documento de registro](assets/generate_dor_af_properties.png)

1. Toque **[!UICONTROL Save & Close]** para salvar as configurações.

Ao enviar o formulário adaptável convertido, o DoR é gerado automaticamente usando o modelo padrão. Se quiser associar outro modelo DoR ao formulário adaptável convertido, selecione **[!UICONTROL Associate form template as the Document of Record template]** opção.

## Gerar documento de registro para PDF forms baseados no Acro Forms ou XFA {#generate-document-of-record-acroform-xfaform}

Se você estiver usando um formulário Acro Form ou PDF baseado em XFA como o formulário de origem do serviço do Automated forms conversion, será possível:

* habilite a geração de DoR antes da conversão do formulário adaptável para gerar DoR usando o formulário de origem como modelo

* ou edite as propriedades do formulário adaptável após a conversão do formulário adaptável para habilitar a geração de DoR usando o modelo padrão, o formulário de origem como modelo ou qualquer outro modelo de formulário

### Habilite a geração de DoR antes da conversão para gerar DoR usando o modelo de formulário de origem {#use-input-form-as-template-to-generate-document-of-record}

1. Selecionar **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Automated Forms Conversion Configuration]** > Propriedades da configuração da nuvem usadas para conversão > **[!UICONTROL Advanced]** > **[!UICONTROL Generate Document of Record]** opção.

1. Toque **[!UICONTROL Save & Close]** para salvar as configurações.

1. [Executar a conversão](../help/convert-existing-forms-to-adaptive-forms.md). Certifique-se de usar a configuração de nuvem editada na etapa 1 dessas instruções.
O serviço de conversão associa automaticamente o formulário Acro Form ou o formulário PDF baseado em XFA ao formulário adaptável convertido como o modelo DoR.
É possível abrir as propriedades do formulário adaptável para exibir o modelo DoR na **[!UICONTROL Document of Record Template Configuration]** seção de **[!UICONTROL Form Model]** guia.

   ![Editar propriedades do formulário adaptável para gerar o Documento de registro](assets/generate_dor_af_properties_xdp_acro.png)

   Ao enviar o formulário adaptável convertido, o DoR é gerado automaticamente usando o modelo de formulário de origem.

### Editar propriedades do formulário adaptável após a conversão para habilitar a geração de DoR {#edit-adaptive-form-properties-to-generate-document-of-record}

1. [Executar a conversão](../help/convert-existing-forms-to-adaptive-forms.md) no formulário PDF não interativo para gerar um formulário adaptável.

1. Selecione o formulário adaptável no **[!UICONTROL output]** pasta e toque em **[!UICONTROL Properties]**.

1. No **[!UICONTROL Form Model]** , expanda a **[!UICONTROL Document of Record Template Configuration]** e selecione **[!UICONTROL Generate Document of Record]** para habilitar a geração de DoR usando o template padrão.
Você também pode selecionar a variável **[!UICONTROL Associate form template as the Document of Record template]** e selecione o template para habilitar a geração de DoR usando o template de formulário de origem ou qualquer outro template de formulário.

1. Toque **[!UICONTROL Save & Close]** para salvar as configurações.
