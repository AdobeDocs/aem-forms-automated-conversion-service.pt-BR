---
title: Solução de problemas do serviço de conversão automática de formulários (AFCS)
description: Problemas comuns do AFCS e suas soluções
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Administration
topic-tags: forms
role: Admin, Developer
level: Beginner, Intermediate
contentOwner: khsingh
exl-id: e8406ed9-37f5-4f26-be97-ad042f9ca57c
source-git-commit: c2392932d1e29876f7a11bd856e770b8f7ce3181
workflow-type: tm+mt
source-wordcount: '655'
ht-degree: 85%

---

# Solução de problemas do serviço de conversão automática de formulários (AFCS)

O documento fornece etapas básicas de solução de problemas para erros comuns.

<!--The article provides information on installation, configuration and administration issues that may arise in an Automated Forms Conversion Service production environment. -->

## Erros comuns {#commonerrors}

| Erro | Exemplo |
|--- |--- |
| **Mensagem de erro** <br> O cabeçalho do token de acesso não está disponível. <br><br> **Motivo** <br> Um administrador criou várias configurações do IMS ou a configuração do IMS não pode acessar o serviço AFCS na Adobe Cloud. <br><br>**Solução** <br> Se houver várias configurações, exclua todas as configurações e [crie uma nova configuração](configure-service.md#obtainpubliccertificates). <br> Se houver uma única configuração, use a **Verificação de integridade** para [verificar a conectividade](configure-service.md#createintegrationoption). | ![O cabeçalho do token de acesso não está disponível](assets/invalid-ims-configurations.png) |
| **Mensagem de erro** <br> Não é possível conectar ao serviço.  <br><br>**Motivo** <br> Um URL de serviço incorreto ou nenhum URL de serviço é mencionado nos serviços em nuvem do Serviço de Automated forms conversion (AFCS). <br><br>**Resolução** <br> Correto [URL do serviço](configure-service.md#configure-the-cloud-service) no Automated forms conversion Service (AFCS) Cloud services. | ![Não é possível se conectar ao serviço.](assets/wrong-service-url-configured.png) |
| **Mensagem de erro** <br> O serviço falhou ao converter o formulário.  <br><br>**Motivo** <br> Problemas de conectividade de rede da sua parte, o serviço está inativo devido à manutenção agendada ou interrupção no Adobe Cloud. <br><br>**Solução** <br> Resolva os problemas de conectividade de rede da sua parte e verifique o status do serviço em https://status.adobe.com/ para consultar se há uma interrupção planejada ou não planejada. | ![Não é possível se conectar ao serviço.](assets/conversion-failure.png) |
| **Mensagem de erro** <br> O número de páginas é superior a 15.  <br><br>**Motivo** <br> O formulário de origem tem mais de 15 páginas.  <br><br>**Solução** <br> Use o Adobe Acrobat para dividir os formulários com mais de 15 páginas. Reduza o número de páginas em um formulário para menos de 15. | ![Não é possível se conectar ao serviço.](assets/number-of-pages.png) |
| **Mensagem de erro** <br> O número de arquivos é superior a 15.  <br><br>**Motivo** <br>  A pasta contém mais de 15 formulários. <br><br>**Solução** <br>Coloque o número de formulários em uma pasta igual ou inferior a 15. Reduza o número total de páginas em uma pasta menos de 50. Ajuste o tamanho da pasta para menos de 10 MB. Não conserve formulários em uma subpasta. Organize formulários de origem em um lote de 8 a 15 formulários. | ![Não é possível se conectar ao serviço.](assets/number-of-pages.png) |
| **Mensagem de erro** <br> O formato do arquivo de origem não é suportado.  <br><br>**Motivo** <br> A pasta que contém formulários de origem tem alguns arquivos não suportados. <br><br>**Solução** <br> O serviço suporta apenas arquivos .xdp e .pdf. Remova os arquivos com qualquer outra extensão da pasta e execute a conversão. | ![Não é possível se conectar ao serviço.](assets/unsupported-file-formats.png) |
| **Mensagem de erro** <br> Formulários digitalizados não são suportados.  <br><br>**Motivo** <br> O formulário PDF contém apenas imagens digitalizadas do formulário e não contém nenhuma estrutura de conteúdo. <br><br>**Solução** <br> O serviço não oferece suporte à conversão de formulários digitalizados ou de uma imagem de um formulário para um formulário pronto para uso adaptável. No entanto, você usa o Adobe Acrobat para converter a imagem de um formulário em um formulário PDF. Em seguida, use o serviço para converter o formulário PDF em um formulário adaptável. Sempre use uma imagem de alta qualidade do formulário para conversão no Acrobat. Melhora a qualidade da conversão. | ![Não é possível se conectar ao serviço.](assets/scanned-forms-error.png) |
| **Mensagem de erro** <br> Formulários PDF criptografados não são suportados.  <br><br>**Motivo** <br> A pasta contém formulários PDF criptografados. <br><br>**Solução** <br> O serviço não oferece suporte à conversão de formulários PDF criptografados em formulários adaptáveis. Remova a criptografia, carregue o formulário não criptografado e execute a conversão. | ![Não é possível se conectar ao serviço.](assets/secured-pdf-form.png) |
| **Mensagem de erro** <br> Não é possível analisar o esquema JSON do metamodelo.  <br><br>**Motivo** <br> O esquema JSON fornecido para o serviço não está formatado corretamente, contém caracteres inválidos ou usa sintaxe inválida para mapear componentes.  <br><br>**Solução**<br> Verifique a formatação do arquivo JSON. Você pode usar qualquer validador JSON online para verificar a formatação e a estrutura do esquema. Consulte o artigo [Ampliar o metamodelo padrão](extending-the-default-meta-model.md) para obter informações sobre a sintaxe do metamodelo. | ![Não é possível se conectar ao serviço.](assets/invalid-meta-model-schema.png) |
| **Erro (somente ambientes locais)** <br> A variável **[!UICONTROL Source Language]** A opção não lista o idioma correto de um Formulário adaptável. <br><br>**Motivo** <br> A propriedade jcr:language do formulário adaptável não está definida corretamente.  <br><br>**Resolução** <br> Abra o CRX-DE lite, acesse `/content/forms/af/`, abra o `jcr:content` e defina o valor do nó para o idioma correto. Para obter a lista de idiomas compatíveis, consulte [Adicionar suporte de localização para localidades sem suporte](https://experienceleague.adobe.com/docs/experience-manager-65/forms/manage-administer-aem-forms/supporting-new-language-localization.html#add-localization-support-for-non-supported-locales). | ![Não é possível se conectar ao serviço.](assets/aem-forms-translation-project-language-unavailable.png) |

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
<td><strong>Error Message</strong> <br> Unable to connect to the service.  <br><br><strong>Reason</strong> <br> Incorrect service URL or no service URL is mentioned in Automated Forms Conversion Service (AFCS) cloud services. <br><br><strong>Resolution</strong> <br> Correct <a href="configure-service.md#configure-the-cloud-service">Service URL</a> in Automated Forms Conversion Service (AFCS) Cloud services.</td>
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
