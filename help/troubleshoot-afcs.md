---
title: 'Solução de problemas do serviço de conversão de formulários automatizado '
seo-title: 'Solução de problemas do serviço de conversão de formulários automatizado (AFCS) '
description: 'Problemas comuns do AFCS e suas soluções '
seo-description: Problemas comuns do AFCS e suas soluções
contentOwner: khsingh
topic-tags: forms
translation-type: tm+mt
source-git-commit: 4b9f3f4fe3b3901cb99c9374ff40e8f49855237f

---


# Solução de problemas do serviço de conversão de formulários automatizado


O artigo fornece informações sobre problemas de instalação, configuração e administração que podem surgir em um ambiente de produção do Automated Forms Conversion Service. O documento também fornece etapas básicas de solução de problemas e explicações para mensagens de erro comuns.

## Erros comuns {#commonerrors}

| Erro | Exemplo |
|--- |--- |
| **Mensagem** de erro <br> O cabeçalho do token de acesso não está disponível. <br><br>**Razão **pela qual<br>um administrador criou várias configurações IMS ou a configuração IMS não consegue acessar o serviço AFCS na Adobe Cloud.<br><br>**Resolução** Se houver várias configurações, exclua todas as configurações e <br> crie uma nova configuração [](configure-service.md#obtainpubliccertificates). <br> Se houver uma única configuração, use **[!UICONTROL Health Check]** para [verificar a conectividade](configure-service.md#createintegrationoption). | ![O cabeçalho do token de acesso não está disponível](assets/invalid-ims-configuration.png) |
| **Mensagem** de erro <br> Não é possível se conectar ao serviço.  <br><br>**Motivo **<br>pelo qual o URL de serviço incorreto ou nenhum URL de serviço é mencionado nos serviços em nuvem do serviço de conversão de formulários automatizados.<br><br>**URL** <br> do [serviço de correção de resolução](configure-service.md#configure-the-cloud-service) nos serviços da Creative Cloud do serviço de conversão de formulários automatizada. | ![Não é possível ligar ao serviço.](assets/wrong-endpoint-configured.png) |
| **Mensagem** de erro <br> O serviço não pôde converter o formulário.  <br><br>**Motivo **<br>pelo qual os problemas de conectividade da rede no seu fim ou serviço estão inativos devido à manutenção ou interrupção programadas na Adobe Cloud.<br><br>**Resolução** <br> Resolva problemas de conectividade de rede no seu extremo e verifique o status do serviço em https://status.adobe.com/ para uma interrupção planejada ou não planejada. | ![Não é possível ligar ao serviço.](assets/service-failure.png) |
| **Mensagem** <br> de erroO número de páginas é superior a 15.  <br><br>**Motivo **<br>A pasta que contém formulários XDP e PDF de origem tem mais de 15 arquivos.<br><br>**Resolução**<br> Coloque o número de formulários em uma pasta igual ou inferior a 15. Traga o número total de páginas em uma pasta menor que 50. Ajuste o tamanho da pasta para menos de 10 MB. Não mantenha formulários em uma subpasta. Organize documentos de origem em um lote de 8 a 15 documentos. | ![Não é possível ligar ao serviço.](assets/number-of-pages.png) |
| **Mensagem** <br> de erroO formato de arquivo de origem não é suportado.  <br><br>**Motivo **<br>A pasta que contém formulários de origem tem alguns arquivos não suportados.<br><br>**Resolução** <br> O serviço suporta apenas arquivos .xdp e .pdf. Remova os arquivos com qualquer outra extensão da pasta e execute a conversão. | ![Não é possível ligar ao serviço.](assets/unsupported-file-formats.png) |
| **Formulários de mensagem** de erro <br> digitalizados não são suportados.  <br><br>**Motivo **<br>O formulário PDF contém apenas a imagem digitalizada do formulário e não contém nenhuma estrutura de conteúdo.<br><br>**Resolução** <br> O serviço não suporta a conversão de formulários digitalizados ou de uma imagem de um formulário para um formulário pronto para uso adaptável. No entanto, você usa o Adobe Acrobat para converter a imagem de um formulário em um formulário PDF. Em seguida, use o serviço para converter o Formulário PDF em um formulário adaptável. Sempre use uma imagem de alta qualidade do formulário para conversão no Acrobat. Melhora a qualidade da conversão. | ![Não é possível ligar ao serviço.](assets/scanned-forms-error.png) |