---
title: Novidades? Notas de versão - Serviço de conversão de formulários automatizado
description: 'Saiba mais sobre os recursos mais recentes e o erro corrigido do serviço de conversão de formulários automatizado '
translation-type: tm+mt
source-git-commit: 01dfd20951314017d47713bfb1a2a5f2d563f434

---


# Serviço de conversão de formulários automatizado: Notas de versão

O serviço de conversão de formulários automatizado recebe melhorias continuamente. Para se manter atualizado com os desenvolvimentos mais recentes, visite esta página regularmente. Esta página fornece informações sobre:

* Versões mais recentes
* Novos recursos
* Correções de erros
* Funcionalidade obsoleta
* Instruções especiais
* Planos futuros para alterações

Esta página é atualizada mensalmente, portanto, volte a ela regularmente.

## 20 de março de 2020 (AFC-2020.03.1)

### Novidades

**Detectar automaticamente seções lógicas em um formulário**

Por padrão, o serviço cria um painel de nível superior separado para cada página de um formulário PDF de entrada. Agora, você pode selecionar a **[!UICONTROL Auto-detect logical sections]** opção para remover a noção de criar um painel de nível superior separado para cada página do PDF e detectar automaticamente seções lógicas. Os campos relacionados de um formulário aos grupos de serviço em uma seção lógica. Por exemplo, todos os campos relacionados ao endereço de faturamento são agrupados em uma seção e todos os campos relacionados ao endereço de entrega são agrupados em uma seção diferente. O serviço também cria um painel de nível superior separado para cada seção lógica detectada automaticamente.

### O que foi melhorado

**Melhorias na detecção de listas**

O serviço agora é mais eficiente na detecção de listas com marcadores e numeradas. Agora, ele pode detectar facilmente listas de vários níveis.

### Instruções especiais

**Instalar o pacote Automated Forms Conversion Service Connector**

Você precisa do pacote do conector 1.1.38 ou superior para usar os recursos e as melhorias mais recentes fornecidos na versão AFC-2020.03.1. Você pode baixar o pacote do conector do Compartilhamento [de pacotes do](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/servicepack/fd/AEM-Forms-6.5.4.0-WIN)AEM.

Se você já tiver um ambiente de serviço de Conversão de formulários automatizados em funcionamento, para usar os recursos mais recentes do serviço de conversão, instale o service pack mais recente, o pacote complementar AEM Forms mais recente e o pacote de conector mais recente na ordem mencionada. Para obter instruções detalhadas, consulte o artigo [Configurar o serviço](configure-service.md) de Conversão de formulários automatizados.
