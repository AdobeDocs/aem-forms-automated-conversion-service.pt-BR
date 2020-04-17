---
title: 'Solução de problemas do serviço de conversão de formulários automatizado '
seo-title: 'Solução de problemas do serviço de conversão de formulários automatizado (AFCS) '
description: 'Problemas comuns do AFCS e suas soluções '
seo-description: Problemas comuns do AFCS e suas soluções
contentOwner: khsingh
topic-tags: forms
translation-type: tm+mt
source-git-commit: 0af626e21a0c3d6a7d3c339c0b87179b048092d3

---


# Solução de problemas do serviço de conversão de formulários automatizado


<!--The article provides information on installation, configuration and administration issues that may arise in an Automated Forms Conversion Service production environment. --> The document  provides basic troubleshooting steps for common errors.

## Erros comuns {#commonerrors}

<table>
<thead>
<tr>
<th>Erro</th>
<th>Exemplo</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>Mensagem</strong> de erro <br> O cabeçalho do token de acesso não está disponível. <br><br><strong>Razão</strong> pela qual <br> um administrador criou várias configurações IMS ou a configuração IMS não consegue acessar o serviço AFCS na Adobe Cloud. <br><br><strong>Resolução</strong> Se houver várias configurações, exclua todas as configurações e <br> crie uma nova configuração <a href="configure-service.md#obtainpubliccertificates"></a>. <br> Se houver uma única configuração, use a <strong> Verificação de integridade </strong> para <a href="configure-service.md#createintegrationoption">verificar a conectividade</a>.</td>
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
