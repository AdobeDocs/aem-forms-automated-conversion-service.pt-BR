---
title: Novidades? Notas de versão - Serviço de conversão automática de formulários
description: 'Saiba mais sobre os recursos mais recentes e o erro corrigido do serviço de conversão automática de formulários '
translation-type: tm+mt
source-git-commit: 5031050795a558795c151e9f3c26a16736566adf
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 100%

---


# Notas de versão

O Serviço de conversão automática de formulários recebe melhorias continuamente. Para se manter atualizado com os desenvolvimentos mais recentes, visite esta página regularmente. Esta página fornece informações sobre:

* Acesso antecipado
* Versões mais recentes
* Novos recursos
* melhorias
* Correções de erros
* Funcionalidade obsoleta
* Instruções especiais
* Futuros planos de alterações

## 20 de março de 2020 (AFC-2020.03.1)

### Acesso antecipado

**Detectar automaticamente seções lógicas em um formulário**

Por padrão, o serviço cria um painel de nível superior separado para cada página de um formulário PDF. Agora, você pode usar a opção **[!UICONTROL Auto-detect logical sections]** para soltar painéis no nível da página (painéis baseados em números de página) e criar apenas painéis lógicos. Ele também agrupa os campos que não pertencem a nenhuma seção com a seção lógica anterior e agrupa os campos de uma seção lógica espalhados por duas páginas adjacentes em uma única seção lógica. Por exemplo, se alguns campos de uma seção lógica estiverem no final da página um e alguns estiverem no início da página dois, todos esses campos serão agrupados em uma única seção lógica.

### O que foi melhorado

**Melhorias na detecção de listas**

O serviço agora é mais eficiente na detecção de listas com marcadores e numeradas.

### Instruções especiais

**Instalar o pacote de conectores do Serviço de conversão automática de formulários**

Você precisa do pacote de conectores 1.1.38 ou superior para usar os recursos e as melhorias mais recentes fornecidos na versão AFC-2020.03.1. Você pode baixar o pacote de conectores no [Compartilhamento de pacotes do AEM](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/featurepack/AFCS-Connector-2020.03.1).

Se você já tiver em execução um ambiente do Serviço de conversão automática de formulários, para usar os recursos mais recentes do serviço de conversão, instale o service pack mais recente, o pacote complementar mais recente do AEM Forms e o pacote de conectores mais recente na ordem mencionada. Para obter instruções detalhadas, consulte o artigo [Configurar o Serviço de conversão automática de formulários](configure-service.md).