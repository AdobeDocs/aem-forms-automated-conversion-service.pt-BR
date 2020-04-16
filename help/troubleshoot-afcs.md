---
title: 'Solução de problemas do serviço de conversão de formulários automatizado '
seo-title: 'Solução de problemas do serviço de conversão de formulários automatizado (AFCS) '
description: 'Problemas comuns do AFCS e suas soluções '
seo-description: Problemas comuns do AFCS e suas soluções
contentOwner: khsingh
topic-tags: forms
translation-type: tm+mt
source-git-commit: 638d2adec39a4ecba335ae7bdebebd8bf9ab2274

---


# Solução de problemas do serviço de conversão de formulários automatizado


O artigo fornece informações sobre problemas de instalação, configuração e administração que podem surgir em um ambiente de produção do Automated Forms Conversion Service. O documento também fornece etapas básicas de solução de problemas e explicações para mensagens de erro comuns.

## Erros comuns {#commonerrors}

| Erro | Exemplo |
|--- |--- |
| **Mensagem** de erro <br> O cabeçalho do token de acesso não está disponível. <br><br>**Razão **pela qual<br>um administrador criou várias configurações IMS ou a configuração IMS não consegue acessar o serviço AFCS na Adobe Cloud.<br><br>**Resolução** Se houver várias configurações, exclua todas as configurações e <br> crie uma nova configuração [](configure-service.md#obtainpubliccertificates). <br> Se houver uma única configuração, use **[!UICONTROL Health Check]** para [verificar a conectividade](configure-service.md#createintegrationoption). | ![O cabeçalho do token de acesso não está disponível](assets/invalid-ims-configuration.png) |
| **Mensagem** de erro <br> Não é possível se conectar ao serviço.  <br><br>**Motivo **<br>pelo qual o URL de serviço incorreto ou nenhum URL de serviço é mencionado nos serviços em nuvem do serviço de conversão de formulários automatizados.<br><br>**URL** <br> do [serviço de correção de resolução](configure-service.md#configure-the-cloud-service) nos serviços da Creative Cloud do serviço de conversão de formulários automatizada. | ![Não é possível ligar ao serviço.](assets/wrong-endpoint-configured.png) |
| **Mensagem** de erro <br> Não é possível se conectar ao serviço.  <br><br>**Motivo **<br>pelo qual o URL de serviço incorreto ou nenhum URL de serviço é mencionado nos serviços em nuvem do serviço de conversão de formulários automatizados.<br><br>**URL** <br> do [serviço de correção de resolução](configure-service.md#configure-the-cloud-service) nos serviços da Creative Cloud do serviço de conversão de formulários automatizada. | ![Não é possível ligar ao serviço.](assets/wrong-endpoint-configured.png) |
