---
title: Introdução
description: 'Acelere a conversão de formulários impressos em formulários adaptáveis '
translation-type: tm+mt
source-git-commit: ef5789dabccc65dcf988b9424b435aa036017691

---


# Introdução {#introduction-to-automated-forms-conversion-service}

O serviço de Conversão de formulários automatizados ajuda a acelerar a digitalização e a modernização da experiência de captura de dados por meio da conversão automatizada de formulários PDF em formulários adaptáveis. O serviço, desenvolvido pelo Adobe Sensei, converte automaticamente seus formulários PDF em formulários adaptáveis compatíveis com dispositivos, responsivos e baseados em HTML5. Ao aproveitar os investimentos existentes em PDF Forms e XFA, o serviço também aplica validações, estilo e layout apropriados aos campos de formulário adaptáveis durante a conversão. O serviço ajuda:

* Salve o esforço manual necessário para converter formulários impressos em formulários adaptáveis
* Aplica padrões e validações apropriadas durante a conversão
* Gerar documento de registro durante a conversão
* Agrupar campos que ocorrem com frequência em fragmentos de formulário reutilizáveis
* Habilita o Adobe Analytics durante a conversão

![É simples. Você só nos fornece as fontes e deixa tudo para nós. Nós lhe daremos belas formas adaptativas. É claro que você vai se preocupar com o resultado para sua satisfação. ](assets/pdf-to-adaptive-form-gitx50.gif)

## Integração {#onboarding}

O serviço está disponível gratuitamente para clientes de termo no local do AEM 6.5 Forms e clientes corporativos do Adobe Managed Service. Você pode entrar em contato com a equipe de vendas da Adobe ou com seu representante da Adobe para solicitar acesso ao serviço.

A Adobe habilita o acesso para sua organização e fornece os privilégios necessários à pessoa designada como administrador em sua organização. O administrador pode conceder acesso aos desenvolvedores (usuários) do AEM Forms de sua organização para se conectar ao serviço. Consulte [Configurar o serviço](configure-service.md) de Conversão de formulários automatizados para obter detalhes.

## Formulários e idiomas PDF suportados {#supported-languages-and-pdf-forms}

O serviço oferece suporte a formulários PDF não interativos, formulários criados com o Adobe Acrobat conhecidos como AcroForms e baseados em XFA criados com o AEM Forms ou o Adobe LiveCycle.

O serviço pode converter somente formulários em inglês em formulários adaptáveis. Você pode traduzir os formulários adaptativos gerados para outro idioma usando o fluxo de trabalho [de tradução do](https://helpx.adobe.com/experience-manager/6-5/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.html)AEM.

## Fluxo de trabalho de conversão {#conversion-workflow}

O serviço de conversão de formulários automatizada é executado na Adobe Cloud. Você conecta sua instância do AEM ao serviço, carrega formulários na instância do AEM e inicia a conversão. O processo de conversão completo está conforme listado abaixo:

![Fluxo de trabalho](assets/conversion-workflow.png)

### 1.Configurar o ambiente {#set-up-the-environment}

O serviço de conversão de formulários automatizada é executado na Adobe Cloud. [Configure a conta de E/S da Adobe de sua organização e conecte sua instância](configure-service.md) de AEM local ao serviço de conversão em execução na Adobe Cloud.

### 2.Converter formulários PDF em formulários adaptáveis {#use-the-conversion-service}

Depois que o ambiente do AEM Forms for configurado, para converter formulários PDF em formulários adaptáveis, [carregue formulários](convert-existing-forms-to-adaptive-forms.md) PDF na instância do AEM e [inicie a conversão](convert-existing-forms-to-adaptive-forms.md#run-the-conversion). Antes de carregar os formulários, considere o seguinte:

* Não carregue os formulários protegidos. O serviço não converte formulários protegidos por senha e criptografados.
* Não carregue formulários digitalizados, coloridos, em idioma diferente do inglês e preenchidos. Esses formulários não são suportados.
* Não carregue formulários PDF com espaços no nome do arquivo.
* Não carregue portfólios [PDF](https://helpx.adobe.com/acrobat/using/overview-pdf-portfolios.html). O serviço não converte um Portfólio PDF em formulários adaptáveis.
* Faça as alterações sugeridas em formulários PDF descritas no artigo [Práticas recomendadas e considerações](styles-and-pattern-considerations-and-best-practices.md) .
* Leia o artigo Problemas [](known-issues.md) conhecidos para evitar armadilhas.

### 3. Revisar formulários convertidos {#review-converted-forms}

Os formulários do mundo real podem ter requisitos complexos de captura de dados em termos de layout de campo, nomeação ou sugestões implícitas que podem não ser capturadas com precisão pela lógica de detecção baseada em AI/ML. Quando a conversão automatizada estiver concluída, você poderá usar o editor [](review-correct-ui-edited.md) Revisar e corrigir para revisar o formulário convertido e fazer as atualizações necessárias e gerar uma saída aprimorada mais próxima à experiência desejada. Depois de fazer as alterações necessárias, envie o formulário novamente para conversão.

O tempo necessário para a conversão automática depende de uma variedade de fatores, como tamanho do formulário de entrada, complexidade do formulário, empréstimo na fila de processamento do serviço. O usuário é notificado regularmente sobre o progresso por meio do indicador de status na pasta/arquivo. Quando a conversão for concluída, uma notificação por email também será enviada para o endereço de email configurado.
