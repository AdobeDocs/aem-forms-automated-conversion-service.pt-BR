---
title: Novidades? Notas de versão - Serviço de conversão de formulários automatizado
description: 'Saiba mais sobre os recursos mais recentes e o erro corrigido do serviço de conversão de formulários automatizado '
translation-type: tm+mt
source-git-commit: c0ca850a0a1e82e34364766601011d6367b218ac

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

Por padrão, o serviço cria um painel de nível superior separado para cada página de um formulário PDF. Agora, você pode usar a **[!UICONTROL Auto-detect logical sections]** opção para soltar painéis de nível de página (painéis baseados em números de página) e criar apenas painéis lógicos. Também associa os campos que não pertencem a nenhuma seção com a seção lógica anterior e os campos de uma seção lógica espalhados por duas páginas adjacentes em uma única seção lógica. Por exemplo, se alguns campos de uma seção lógica estiverem no final da página um e alguns estiverem no início da página dois, todos esses campos serão agrupados em uma única seção lógica.

### O que foi melhorado

**Melhorias na detecção de listas**

O serviço agora é mais eficiente na detecção de listas com marcadores e numeradas.

### Instruções especiais

**Instalar o pacote Automated Forms Conversion Service Connector**

Você precisa do pacote do conector 1.1.38 ou superior para usar os recursos e as melhorias mais recentes fornecidos na versão AFC-2020.03.1. Você pode baixar o pacote do conector do Compartilhamento [de pacotes do](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/featurepack/AFCS-Connector-2020.03.1)AEM.

Se você já tiver um ambiente de serviço de Conversão de formulários automatizada para usar os recursos mais recentes do serviço de conversão, instale o service pack mais recente, o pacote complementar mais recente do AEM Forms e o pacote de conector mais recente na ordem mencionada. Para obter instruções detalhadas, consulte o artigo [Configurar o serviço](configure-service.md) de Conversão de formulários automatizados.