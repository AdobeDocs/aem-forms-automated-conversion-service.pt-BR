---
title: Introdução ao serviço de conversão automática de formulários (AFCS)
description: Acelere a conversão de formulários impressos em formulários adaptáveis
solution: Experience Manager Forms
feature: Adaptive Forms, Foundation Components
topic: Administration
topic-tags: forms
role: Admin, Developer
level: Beginner, Intermediate
exl-id: edabeac8-cd66-48ca-a99f-9643a1c184cf
source-git-commit: 23d441d19dea63382f0a0024b4682d5bd0eaa63c
workflow-type: tm+mt
source-wordcount: '739'
ht-degree: 53%

---

# Serviço de conversão automática de formulários (AFCS) {#introduction-to-automated-forms-conversion-service}

O serviço de conversão automática de formulários (AFCS) ajuda a acelerar a digitalização e a modernização de experiências de captura de dados por meio da conversão automatizada do PDF forms em formulários adaptáveis. O serviço, desenvolvido pelo Adobe Sensei, converte automaticamente seus formulários PDF em formulários adaptáveis compatíveis com dispositivos responsivos e baseados em HTML5. Ao aproveitar os investimentos existentes em formulários PDF e XFA, o serviço também aplica validações, estilo e layout apropriados aos campos de formulário adaptáveis durante a conversão. O serviço ajuda a:

* Poupar o esforço manual necessário para converter formulários impressos em formulários adaptáveis
* Aplicar padrões e validações apropriadas durante a conversão
* Gerar documento de registro durante a conversão
* Agrupar campos comuns em fragmentos de formulário reutilizáveis
* Habilitar o Adobe Analytics durante a conversão

![É simples. Você nos fornece as fontes e deixa tudo com a gente. Nós lhe fornecemos lindos formulários adaptáveis. Você sempre pode remexer no resultado para sua satisfação. &#x200B;](assets/pdf-to-adaptive-form-gitx50.gif)

## Integração {#onboarding}

O serviço está disponível gratuitamente para clientes de vigência no local do AEM 6.5 Forms e AEM 6.5 LTS Forms e clientes corporativos do Adobe Managed Service. Você pode entrar em contato com a equipe de vendas da Adobe ou com seu representante da Adobe para solicitar acesso ao serviço. O serviço também está disponível gratuitamente e pré-ativado para clientes do AEM Forms as a Cloud Service.

A Adobe habilita o acesso para sua organização e fornece os privilégios necessários à pessoa designada como administrador em sua organização. O administrador pode conceder acesso aos desenvolvedores (usuários) do AEM Forms de sua organização para se conectar ao serviço. Consulte [Configurar o serviço de conversão automática de formulários](configure-service.md) para obter detalhes.

## PDF forms e idiomas compatíveis {#supported-languages-and-pdf-forms}

O serviço oferece suporte a formulários PDF não interativos, formulários criados com o Adobe Acrobat conhecidos como AcroForms e baseados em XFA criados com o AEM Forms ou o Adobe LiveCycle.

O serviço também oferece suporte ao PDF forms habilitado para Adobe Sign. Se o formulário PDF de origem tiver marcas de texto do Adobe Sign, o serviço preserva todas as informações relacionadas ao Adobe Sign durante a conversão e associa as informações do assinante presentes no PDF de origem aos campos de formulário adaptáveis correspondentes. O recurso está disponível apenas para AcroForms.

O serviço pode converter formulários em inglês, francês, alemão, espanhol, italiano e português em formulários adaptáveis. Você também pode traduzir os formulários adaptáveis gerados para outro idioma usando o [fluxo de trabalho de tradução do AEM](https://helpx.adobe.com/br/experience-manager/6-5/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.html).

## Fluxo de trabalho de conversão  {#conversion-workflow}

O serviço de conversão automática de formulários (AFCS) é executado na Adobe Cloud. Você conecta sua instância do AEM ao serviço, carrega formulários na instância do AEM e inicia a conversão. O processo de conversão completo é realizado conforme listado abaixo:

![Fluxo de trabalho](assets/conversion-workflow.png)

### &#x200B;1. Configurar o ambiente {#set-up-the-environment}

O serviço de conversão automática de formulários (AFCS) é executado na Adobe Cloud. [Configure a conta do Adobe I/O de sua organização e conecte sua instância do AEM local](configure-service.md) ao serviço de conversão em execução na Adobe Cloud. Para o AEM 6.5 e o AEM 6.5 LTS, você deve habilitar os Componentes principais do formulário adaptável se usar modelos e temas baseados em Componentes principais; consulte [Configurar o serviço](configure-service.md#referencepackage).

### &#x200B;2. Converter o PDF forms em formulários adaptáveis {#use-the-conversion-service}

Depois que o ambiente do AEM Forms for configurado, para converter formulários PDF em formulários adaptáveis, [carregue formulários PDF](convert-existing-forms-to-adaptive-forms.md) na sua instância do AEM e [inicie a conversão](convert-existing-forms-to-adaptive-forms.md#run-the-conversion). Antes de carregar os formulários, considere o seguinte:

* Não carregue os formulários protegidos. O serviço não converte formulários protegidos por senha e criptografados.
* Não carregue formulários digitalizados, coloridos e preenchidos em nenhum idioma além de inglês, francês, alemão, espanhol, italiano e português. Tais formas não são suportados.
* Não carregue formulários PDF com espaços no nome do arquivo.
* Não carregue [portfólios em PDF](https://helpx.adobe.com/br/acrobat/using/overview-pdf-portfolios.html). O serviço não converte um PDF Portfolio em um formulário adaptável.
* Faça as alterações sugeridas nos formulários PDF descritas no artigo [Práticas recomendadas e considerações](styles-and-pattern-considerations-and-best-practices.md).
* Leia o artigo [Problemas conhecidos](known-issues.md) para evitar armadilhas.

### &#x200B;3. Revisar formulários convertidos {#review-converted-forms}

Os formulários do mundo real podem ter requisitos complexos de captura de dados em termos de layout de campo, nomenclatura ou sugestões implícitas que podem não ser capturadas com precisão pela lógica de detecção baseada em AI/ML. Quando a conversão automática estiver concluída, você poderá usar o [editor de Revisar e corrigir](review-correct-ui-edited.md) para revisar o formulário convertido e fazer as atualizações necessárias e gerar uma saída aprimorada mais próxima à experiência desejada. Depois de fazer as alterações necessárias, envie o formulário novamente para conversão.

O tempo necessário para a conversão automática depende de vários fatores, como tamanho do formulário de entrada, complexidade do formulário, empréstimo na fila de processamento do serviço. O usuário é notificado regularmente sobre o progresso através do indicador de status na pasta/arquivo. Quando a conversão for concluída, uma notificação por e-mail também será enviada para o endereço de e-mail configurado.

