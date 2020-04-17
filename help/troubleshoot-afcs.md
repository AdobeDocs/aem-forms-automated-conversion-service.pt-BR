---
title: 'Solução de problemas do serviço de conversão de formulários automatizado '
seo-title: 'Solução de problemas do serviço de conversão de formulários automatizado (AFCS) '
description: 'Problemas comuns do AFCS e suas soluções '
seo-description: Problemas comuns do AFCS e suas soluções
contentOwner: khsingh
topic-tags: forms
translation-type: tm+mt
source-git-commit: 3a82102feffa7fc618dc37c9a745c254a46a0700

---


# Solução de problemas do serviço de conversão de formulários automatizado


<!--The article provides information on installation, configuration and administration issues that may arise in an Automated Forms Conversion Service production environment. --> The document  provides basic troubleshooting steps for common errors.

## Erros comuns {#commonerrors}

| Erro | Exemplo |
|--- |--- |
| **Mensagem** de erro <br> O cabeçalho do token de acesso não está disponível. <br><br> **Razão** pela qual <br> um administrador criou várias configurações IMS ou a configuração IMS não consegue acessar o serviço AFCS na Adobe Cloud. <br><br>**Resolução **Se houver várias configurações, exclua todas as configurações e<br>crie uma nova configuração[](configure-service.md#obtainpubliccertificates).<br>Se houver uma única configuração, use a Verificação** de **integridade para[verificar a conectividade](configure-service.md#createintegrationoption). | ![O cabeçalho do token de acesso não está disponível](assets/invalid-ims-configurations.png) |
| **Mensagem** de erro <br> Não é possível se conectar ao serviço.  <br><br>**Motivo **<br>pelo qual o URL de serviço incorreto ou nenhum URL de serviço é mencionado nos serviços em nuvem do serviço de conversão de formulários automatizados.<br><br>**URL** <br> do [serviço de correção de resolução](configure-service.md#configure-the-cloud-service) nos serviços da Creative Cloud do serviço de conversão de formulários automatizada. | ![Não é possível ligar ao serviço.](assets/wrong-service-url-configured.png) |

| Erro | Exemplo |
|--- |--- |
| **Mensagem** de erro <br> O serviço não pôde converter o formulário.  <br><br>**Por **<br>que problemas de conectividade com a rede estão relacionados, o serviço está inativo devido à manutenção programada ou falha na Adobe Cloud.<br><br>**Resolução** <br> Resolva problemas de conectividade de rede no seu extremo e verifique o status do serviço em https://status.adobe.com/ para uma interrupção planejada ou não planejada. | ![Não é possível ligar ao serviço.](assets/service-failure.png) |
| **Mensagem** <br> de erroO número de páginas é superior a 15.  <br><br>**Motivo **<br>O formulário de origem tem mais de 15 páginas.<br><br>**Resolução** <br> Use o Adobe Acrobat para dividir formulários com mais de 15 páginas. Reduza o número de páginas em um formulário para menos de 15. | ![Não é possível ligar ao serviço.](assets/number-of-pages.png) |
| **Mensagem** <br> de erroO número de arquivos é superior a 15.  <br><br>**Motivo **<br>A pasta contém mais de 15 formulários.<br><br>**Resolução**<br> Coloque o número de formulários em uma pasta igual ou inferior a 15. Traga o número total de páginas em uma pasta menor que 50. Ajuste o tamanho da pasta para menos de 10 MB. Não mantenha formulários em uma subpasta. Organize formulários de origem em um lote de 8 a 15 formulários. | ![Não é possível ligar ao serviço.](assets/number-of-pages.png) |
| **Mensagem** <br> de erroO formato de arquivo de origem não é suportado.  <br><br>**Motivo **<br>A pasta que contém formulários de origem tem alguns arquivos não suportados.<br><br>**Resolução** <br> O serviço suporta apenas arquivos .xdp e .pdf. Remova os arquivos com qualquer outra extensão da pasta e execute a conversão. | ![Não é possível ligar ao serviço.](assets/unsupported-file-formats.png) |
| **Formulários de mensagem** de erro <br> digitalizados não são suportados.  <br><br>**Motivo **<br>O formulário PDF contém apenas imagens digitalizadas do formulário e não contém nenhuma estrutura de conteúdo.<br><br>**Resolução** <br> O serviço não suporta a conversão de formulários digitalizados ou de uma imagem de um formulário para um formulário pronto para uso adaptável. No entanto, você usa o Adobe Acrobat para converter a imagem de um formulário em um formulário PDF. Em seguida, use o serviço para converter o Formulário PDF em um formulário adaptável. Sempre use uma imagem de alta qualidade do formulário para conversão no Acrobat. Melhora a qualidade da conversão. | ![Não é possível ligar ao serviço.](assets/scanned-forms-error.png) |
| **O formulário PDF criptografado por mensagem** <br> de erro não é suportado.  <br><br>**Motivo **<br>A pasta contém formulários PDF criptografados.<br><br>**Resolução** <br> O serviço não suporta a conversão de um formulário PDF criptografado em um formulário adaptável. Remova a criptografia, carregue o formulário não criptografado e execute a conversão. | ![Não é possível ligar ao serviço.](assets/secured-pdf-form.png) |
| **Mensagem** de erro <br> Não é possível analisar o schema JSON meta-model.  <br><br>**Motivo **para que<br>o schema JSON fornecido ao serviço não esteja corretamente formatado, contenha caracteres inválidos ou utilize sintaxe inválida para mapear componentes.<br><br>**Resolução**<br> Verifique a formatação do arquivo JSON. Você pode usar qualquer validador JSON online para verificar a formatação e a estrutura do schema. Consulte [Estender o artigo de meta-modelo](extending-the-default-meta-model.md) padrão para obter informações sobre a sintaxe meta-modelo. | ![Não é possível ligar ao serviço.](assets/invalid-meta-model-schema.png) |

<!--

<table>
<thead>
<tr>
<th>Error</th>
<th>Example</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>Error Message</strong> <p> The access token header is not available. </p><br><strong>Reason</strong> <br> An administrator has created multiple IMS configurations or IMS configuration is not able to reach AFCS service on Adobe Cloud. <br><br><strong>Resolution</strong> <br> If there are multiple configurations, delete all the configurations and <a href="configure-service.md#obtainpubliccertificates">create a new configuration</a>. <br> If there is a single configuration, use <strong> Health Check </strong> to <a href="configure-service.md#createintegrationoption">check connectivity</a>.</td>
<td><img alt="The access token header is not available" src="assets/invalid-ims-configuration.png" /></td>
</tr>
<tr>
<td><strong>Error Message</strong> <br> Unable to connect to the service.  <br><br><strong>Reason</strong> <br> Incorrect service URL or no service URL is mentioned in Automated Forms Conversion Service cloud services. <br><br><strong>Resolution</strong> <br> Correct <a href="configure-service.md#configure-the-cloud-service">Service URL</a> in Automated Forms Conversion Service Cloud services.</td>
<td><img alt="Unable to connect to the service." src="assets/wrong-endpoint-configured.png" /></td>
</tr>
<tr>
<td><strong>Error Message</strong> <br> The service failed to convert the form.  <br><br><strong>Reason</strong> <br> Network connectivity issues at your end, the service is down due to scheduled maintenance, or outage on Adobe Cloud. <br><br><strong>Resolution</strong> <br> Resolve network connectivity issues at your end and check the status of the service on <a href="https://status.adobe.com/">https://status.adobe.com/</a> for a planned or unplanned outage.</td>
<td><img alt="The service failed to convert the form." src="assets/service-failure.png" /></td>
</tr>
<tr>
<td><strong>Error Message</strong> <br> The number of pages is more than 15.  <br><br><strong>Reason</strong> <br> The source form is more than 15 pages long.  <br><br><strong>Resolution</strong> <br> Use Adobe Acrobat to split forms with more than 15 pages. Bring the number of pages in a form to less than 15.</td>
<td><img alt="The number of pages is more than 15." src="assets/number-of-pages.png" /></td>
</tr>
<tr>
<td><strong>Error Message</strong> <br> The number of files is more than 15.  <br><br><strong>Reason</strong> <br>  The folder contains more than 15 forms. <br><br><strong>Resolution</strong> <br> Bring the number of forms in a folder to less than or equal to 15. Bring the total number of pages in a folder less than 50. Bring the size of the folder to less than 10 MB. Do not keep forms in a sub-folder. Organize source forms into a batch of 8-15 forms.</td>
<td><img alt="The number of files is more than 15." src="assets/number-of-pages.png" /></td>
</tr>
<tr>
<td><strong>Error Message</strong> <br> The source file format is not supported.  <br><br><strong>Reason</strong> <br> The folder containing source forms have some unsupported files. <br><br><strong>Resolution</strong> <br> The service supports only .xdp and .pdf files. Remove files with any other extension from the folder and run the conversion.</td>
<td><img alt="The source file format is not supported." src="assets/unsupported-file-formats.png" /></td>
</tr>
<tr>
<td><strong>Error Message</strong> <br> Scanned forms are not supported.  <br><br><strong>Reason</strong> <br> The PDF form contains only scanned images of the form and contains no content structure. <br><br><strong>Resolution</strong> <br> The service does not support converting scanned forms or an image of a form to an adaptive out-of-the-box. However, you use Adobe Acrobat to convert the image of a form to a PDF Form. Then, use the service to convert the PDF Form to an adaptive form. Always use a high-quality image of the form for conversion in Acrobat. It improves the quality of the conversion.</td>
<td><img alt="Scanned forms are not supported." src="assets/scanned-forms-error.png" /></td>
</tr>
<tr>
<td><strong>Error Message</strong> <br> Encrypted PDF form is not supported.  <br><br><strong>Reason</strong> <br> The folder contains encrypted PDF forms. <br><br><strong>Resolution</strong> <br> The service does not support converting an encrypted PDF form to an adaptive form. Remove the encryption, upload the non-encrypted form, and run the conversion.</td>
<td><img alt="Encrypted PDF form is not supported." src="assets/secured-pdf-form.png" /></td>
</tr>
<tr>
<td><strong>Error Message</strong> <br> Unable to parse meta-model JSON schema.  <br><br><strong>Reason</strong> <br> The JSON schema supplied to the service is not properly formatted, contains invalid characters, or uses invalid syntax to map components.  <br><br><strong>Resolution</strong> <br> Check the formatting of the JSON file. You can use any online JSON validator to check the formatting and structure of the schema. See, <a href="extending-the-default-meta-model.md">Extend the default meta-model</a> article for information on meta-model syntax.</td>
<td><img alt="Unable to parse meta-model JSON schema" src="assets/invalid-meta-model-schema.png" /></td>
</tr>
</tbody>
</table>
-->