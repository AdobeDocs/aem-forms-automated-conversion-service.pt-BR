---
title: 'Solução de problemas do serviço de conversão de formulários automatizado '
seo-title: 'Solução de problemas do serviço de conversão de formulários automatizado (AFCS) '
description: 'Problemas comuns do AFCS e suas soluções '
seo-description: Problemas comuns do AFCS e suas soluções
contentOwner: khsingh
topic-tags: forms
translation-type: tm+mt
source-git-commit: 56e4696c0372223e0b27f1c313382a2a637b6db1

---


# Solução de problemas do serviço de conversão de formulários automatizado


<!--The article provides information on installation, configuration and administration issues that may arise in an Automated Forms Conversion Service production environment. --> The document  provides basic troubleshooting steps for common errors.

## Erros comuns {#commonerrors}
<!--
|Error|Example|
|--- |--- |
|**Error Message** <br> The access token header is not available. <br><br>**Reason** <br> An administrator has created multiple IMS configurations or IMS configuration is not able to reach AFCS service on Adobe Cloud. <br><br>**Resolution** <br> If there are multiple configurations, delete all the configurations and [create a new configuration](configure-service.md#obtainpubliccertificates). <br> If there is a single configuration, use **[!UICONTROL Health Check]** to [check connectivity](configure-service.md#createintegrationoption).|![The access token header is not available](assets/invalid-ims-configuration.png)|
|**Error Message** <br> Unable to connect to the service.  <br><br>**Reason** <br> Incorrect service URL or no service URL is mentioned in Automated Forms Conversion Service cloud services. <br><br>**Resolution** <br> Correct [Service URL](configure-service.md#configure-the-cloud-service) in Automated Forms Conversion Service Cloud services.|![Unable to connect to the service.](assets/wrong-endpoint-configured.png)|
|**Error Message** <br> The service failed to convert the form.  <br><br>**Reason** <br> Network connectivity issues at your end, the service is down due to scheduled maintenance, or outage on Adobe Cloud. <br><br>**Resolution** <br> Resolve network connectivity issues at your end and check the status of the service on https://status.adobe.com/ for a planned or unplanned outage.|![Unable to connect to the service.](assets/service-failure.png)|
|**Error Message** <br> The number of pages is more than 15.  <br><br>**Reason** <br> The source form is more than 15 pages long.  <br><br>**Resolution** <br> Use Adobe Acrobat to split forms with more than 15 pages. Bring the number of pages in a form to less than 15. |![Unable to connect to the service.](assets/number-of-pages.png)|
|**Error Message** <br> The number of files is more than 15.  <br><br>**Reason** <br>  The folder contains more than 15 forms. <br><br>**Resolution** <br> Bring the number of forms in a folder to less than or equal to 15. Bring the total number of pages in a folder less than 50. Bring the size of the folder to less than 10 MB. Do not keep forms in a sub-folder. Organize source forms into a batch of 8-15 forms. |![Unable to connect to the service.](assets/number-of-pages.png)|
|**Error Message** <br> The source file format is not supported.  <br><br>**Reason** <br> The folder containing source forms have some unsupported files. <br><br>**Resolution** <br> The service supports only .xdp and .pdf files. Remove files with any other extension from the folder and run the conversion. |![Unable to connect to the service.](assets/unsupported-file-formats.png)|
|**Error Message** <br> Scanned forms are not supported.  <br><br>**Reason** <br> The PDF form contains only scanned images of the form and contains no content structure. <br><br>**Resolution** <br> The service does not support converting scanned forms or an image of a form to an adaptive out-of-the-box. However, you use Adobe Acrobat to convert the image of a form to a PDF Form. Then, use the service to convert the PDF Form to an adaptive form. Always use a high-quality image of the form for conversion in Acrobat. It improves the quality of the conversion. |![Unable to connect to the service.](assets/scanned-forms-error.png)|
|**Error Message** <br> Encrypted PDF form is not supported.  <br><br>**Reason** <br> The folder contains encrypted PDF forms. <br><br>**Resolution** <br> The service does not support converting an encrypted PDF form to an adaptive form. Remove the encryption, upload the non-encrypted form, and run the conversion. |![Unable to connect to the service.](assets/secured-pdf-form.png)|
|**Error Message** <br> Unable to parse meta-model JSON schema.  <br><br>**Reason** <br> The JSON schema supplied to the service is not properly formatted, contains invalid characters, or uses invalid syntax to map components.  <br><br>**Resolution** <br> Check the formatting of the JSON file. You can use any online JSON validator to check the formatting and structure of the schema. See, [Extend the default meta-model](extending-the-default-meta-model.md) article for information on meta-model syntax. |![Unable to connect to the service.](assets/invalid-meta-model-schema.png)| -->

<table>
<thead>
<tr>
<th>Erro</th>
<th>Exemplo</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>Mensagem</strong> de erro <br> O cabeçalho do token de acesso não está disponível. <br><br><strong>Razão</strong> pela qual <br> um administrador criou várias configurações IMS ou a configuração IMS não consegue acessar o serviço AFCS na Adobe Cloud. <br><br><strong>Resolução</strong> Se houver várias configurações, exclua todas as configurações e <br> crie uma nova configuração <a href="configure-service.md#obtainpubliccertificates"></a>. <br> Se houver uma única configuração, use <strong>[!UICONTROL Health Check]</strong> para <a href="configure-service.md#createintegrationoption">verificar a conectividade</a>.</td>
<td><img alt="O cabeçalho do token de acesso não está disponível" src="assets/invalid-ims-configuration.png" /></td>
</tr>
<tr>
<td><strong>Mensagem</strong> de erro <br> Não é possível se conectar ao serviço.  <br><br><strong>Motivo</strong> <br> pelo qual o URL de serviço incorreto ou nenhum URL de serviço é mencionado nos serviços em nuvem do serviço de conversão de formulários automatizados. <br><br><strong>URL</strong> <br> do <a href="configure-service.md#configure-the-cloud-service">serviço de correção de resolução</a> nos serviços da Creative Cloud do serviço de conversão de formulários automatizada.</td>
<td><img alt="Não é possível ligar ao serviço." src="assets/wrong-endpoint-configured.png" /></td>
</tr>
<tr>
<td><strong>Mensagem</strong> de erro <br> O serviço não pôde converter o formulário.  <br><br><strong>Por</strong> <br> que problemas de conectividade com a rede estão relacionados, o serviço está inativo devido à manutenção programada ou falha na Adobe Cloud. <br><br><strong>Resolução</strong> <br> Resolva problemas de conectividade de rede no seu extremo e verifique o status do serviço em <a href="https://status.adobe.com/">https://status.adobe.com/</a> para uma interrupção planejada ou não.</td>
<td><img alt="O serviço não pôde converter o formulário." src="assets/service-failure.png" /></td>
</tr>
<tr>
<td><strong>Mensagem</strong> <br> de erroO número de páginas é superior a 15.  <br><br><strong>Motivo</strong><br> O formulário de origem tem mais de 15 páginas.  <br><br><strong>Resolução</strong> <br> Use o Adobe Acrobat para dividir formulários com mais de 15 páginas. Reduza o número de páginas em um formulário para menos de 15.</td>
<td><img alt="O número de páginas é superior a 15." src="assets/number-of-pages.png" /></td>
</tr>
<tr>
<td><strong>Mensagem</strong> <br> de erroO número de arquivos é superior a 15.  <br><br><strong>Motivo</strong><br> A pasta contém mais de 15 formulários. <br><br><strong>Resolução</strong><br> Coloque o número de formulários em uma pasta igual ou inferior a 15. Traga o número total de páginas em uma pasta menor que 50. Ajuste o tamanho da pasta para menos de 10 MB. Não mantenha formulários em uma subpasta. Organize formulários de origem em um lote de 8 a 15 formulários.</td>
<td><img alt="O número de arquivos é superior a 15." src="assets/number-of-pages.png" /></td>
</tr>
<tr>
<td><strong>Mensagem</strong> <br> de erroO formato de arquivo de origem não é suportado.  <br><br><strong>Motivo</strong> <br> A pasta que contém formulários de origem tem alguns arquivos não suportados. <br><br><strong>Resolução</strong> <br> O serviço suporta apenas arquivos .xdp e .pdf. Remova os arquivos com qualquer outra extensão da pasta e execute a conversão.</td>
<td><img alt="O formato de arquivo de origem não é suportado." src="assets/unsupported-file-formats.png" /></td>
</tr>
<tr>
<td><strong>Formulários de mensagem</strong> de erro <br> digitalizados não são suportados.  <br><br><strong>Motivo</strong> <br> O formulário PDF contém apenas imagens digitalizadas do formulário e não contém nenhuma estrutura de conteúdo. <br><br><strong>Resolução</strong> <br> O serviço não suporta a conversão de formulários digitalizados ou de uma imagem de um formulário para um formulário pronto para uso adaptável. No entanto, você usa o Adobe Acrobat para converter a imagem de um formulário em um formulário PDF. Em seguida, use o serviço para converter o Formulário PDF em um formulário adaptável. Sempre use uma imagem de alta qualidade do formulário para conversão no Acrobat. Melhora a qualidade da conversão.</td>
<td><img alt="Formulários digitalizados não são suportados." src="assets/scanned-forms-error.png" /></td>
</tr>
<tr>
<td><strong>O formulário PDF criptografado por mensagem</strong> <br> de erro não é suportado.  <br><br><strong>Motivo</strong><br> A pasta contém formulários PDF criptografados. <br><br><strong>Resolução</strong> <br> O serviço não suporta a conversão de um formulário PDF criptografado em um formulário adaptável. Remova a criptografia, carregue o formulário não criptografado e execute a conversão.</td>
<td><img alt="O formulário PDF criptografado não é suportado." src="assets/secured-pdf-form.png" /></td>
</tr>
<tr>
<td><strong>Mensagem</strong> de erro <br> Não é possível analisar o schema JSON meta-model.  <br><br><strong>Motivo</strong> para que <br> o schema JSON fornecido ao serviço não esteja corretamente formatado, contenha caracteres inválidos ou utilize sintaxe inválida para mapear componentes.  <br><br><strong>Resolução</strong><br> Verifique a formatação do arquivo JSON. Você pode usar qualquer validador JSON online para verificar a formatação e a estrutura do schema. Consulte <a href="extending-the-default-meta-model.md">Estender o artigo de meta-modelo</a> padrão para obter informações sobre a sintaxe meta-modelo.</td>
<td><img alt="Não é possível analisar o schema JSON meta-model" src="assets/invalid-meta-model-schema.png" /></td>
</tr>
</tbody>
</table>
