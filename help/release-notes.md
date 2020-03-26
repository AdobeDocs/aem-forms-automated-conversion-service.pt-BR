---
title: Novidades? Notas de versão - Serviço de conversão de formulários automatizado
description: 'Saiba mais sobre os recursos mais recentes e o erro corrigido do serviço de conversão de formulários automatizado '
translation-type: tm+mt
source-git-commit: dc17dfcb331df6144b8a7ce3c9c9d840b1182a95

---


# Serviço de conversão de formulários automatizado: Notas de versão

O serviço de conversão de formulários automatizado recebe melhorias continuamente. Para se manter atualizado com os desenvolvimentos mais recentes, visite esta página regularmente. Esta página fornece informações sobre:

* Acesso antecipado
* Versões mais recentes
* Novos recursos
* melhorias
* Correções de erros
* Funcionalidade obsoleta
* Instruções especiais
* Futuros planos para mudanças

## 20 de março de 2020 (AFC-2020.03.1)

### Acesso antecipado

**Detectar automaticamente seções lógicas em um formulário**

A versão AFC-2020.03.1 fornece acesso antecipado ao **[!UICONTROL Auto-detect logical sections]** recurso.

Por padrão, o serviço cria um painel de nível superior separado para cada página de um formulário PDF. Agora, você pode usar a **[!UICONTROL Auto-detect logical sections]** opção para soltar painéis de nível de página (painéis baseados em número de página) e criar apenas painéis lógicos.  Ele também pausa os campos que não pertencem a nenhuma seção com seção lógica anterior e os campos de uma seção lógica espalhados por duas páginas adjacentes em uma única seção lógica. Por exemplo, se alguns campos de uma seção lógica estiverem no final da página um e alguns estiverem no início da página dois, todos esses campos serão agrupados em uma única seção lógica.

É necessário o pacote do conector 1.1.38 ou superior para usar o **[!UICONTROL Auto-detect logical sections]** recurso. Você pode baixar o pacote do conector do Compartilhamento [de pacotes do](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/featurepack/AFCS-Connector-2020.03.1)AEM.

### O que foi melhorado

**Melhorias na detecção de listas**

O serviço agora é mais eficiente na detecção de listas com marcadores e numeradas.