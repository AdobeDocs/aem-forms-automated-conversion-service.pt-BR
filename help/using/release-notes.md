---
title: Novidades? Notas de versão - Serviço de conversão automática de formulários
description: Saiba mais sobre os recursos mais recentes e o erro corrigido do serviço de conversão automática de formulários
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Administration
topic-tags: forms
role: Admin, Developer
level: Beginner, Intermediate
exl-id: fccafbc9-28c1-4736-922c-24d675b25213
TQID: https://experienceleague.adobe.com/5c2zcJqsjOyH--SIp-DbEyQtflWnBy67-ja0BZY8aC8
product_v2: id: e8f6de9b-cf88-4405-8d10-15efa08c230eid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2: id: d49d6117-dd89-469c-a774-cc96b7eee433
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2: id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 0be767cc3d09331ea7a61c114a11bb0354b5f4ad
workflow-type: tm+mt
source-wordcount: 496
ht-degree: 51%

---

# Notas de versão

O Serviço de conversão automática de formulários recebe melhorias continuamente. Para se manter atualizado com os últimos desenvolvimentos, visite esta página regularmente. Esta página fornece informações sobre:

* Acesso antecipado
* Versões mais recentes
* Novos recursos
* melhorias
* Correções de erros
* Funcionalidade obsoleta
* Instruções especiais
* Futuros planos de alterações

## 24 de fevereiro de 2022 (AFC-2022.02.0) {#feb-2022}

* Recurso adicionado para [converter automaticamente seções em fragmentos](convert-existing-forms-to-adaptive-forms.md) para ajudar a melhorar a velocidade de renderização de formulários convertidos e facilitar o carregamento de formulários grandes no editor de formulários adaptáveis.

## 29 de agosto de 2021 (AFC-2021.08.0) {#aug-2021}

* Adição da capacidade de converter PDF forms em italiano e português para um formulário adaptável.

## 29 de julho de 2021 (AFC-2021.07.2) {#july-2021}

* Adição da capacidade de converter um formulário do PDF em francês, alemão e espanhol em um formulário adaptável.

## 24 de junho de 2021 (AFC-2021.06.2) {#june-2021}

### O que foi melhorado {#june-2021-improvements}

Precisão aprimorada para detectar automaticamente seções lógicas nos formulários de origem e convertê-las em painéis de formulários adaptáveis correspondentes.

## 3 de março de 2021 (AFC-2021.02.2) {#mar-2021}

### O que foi melhorado {#march-2021-improvements}

Melhorias na organização do conteúdo do formulário em grupos de opções e campos ao converter um formulário de origem em um formulário adaptável.

## 02 de fevereiro de 2021 (AFC-2021.01.2) {#feb-2021}

### O que foi melhorado {#feb-2021-improvements}

Melhorias na organização do conteúdo do formulário em painéis e geração de títulos para painéis ao converter um formulário de origem em um formulário adaptável.

## 16 de julho de 2020 (AFC-2020.07.2) {#jul-2020}

### Novidades {#whats-new-jul-2020-}

Adicionado suporte para converter PDF forms coloridos em formulários adaptáveis.

### O que foi melhorado {#jul-2020-improvements}

Melhorias na conversão automática de campos de texto, formulário e grupo de opções para os componentes de formulário adaptáveis correspondentes.

## 20 de março de 2020 (AFC-2020.03.1) {#mar-2020}

### Acesso antecipado {#early-access}

**Detectar automaticamente seções lógicas em um formulário**

Por padrão, o serviço cria um painel de nível superior separado para cada página de um formulário PDF. Agora, você pode usar a opção **[!UICONTROL Auto-detect logical sections]** para soltar painéis no nível da página (painéis baseados em números de página) e criar apenas painéis lógicos. Ele também agrupa os campos que não pertencem a nenhuma seção com a seção lógica anterior e agrupa os campos de uma seção lógica espalhados por duas páginas adjacentes em uma única seção lógica. Por exemplo, se alguns campos de uma seção lógica estiverem no final da página um e alguns estiverem no início da página dois, todos esses campos serão agrupados em uma única seção lógica.

### O que foi melhorado {#mar-2020-improvements}

**Melhorias na detecção de listas**

O serviço agora é mais eficiente na detecção de listas com marcadores e numeradas.

### Instruções especiais {#special-instructions}

**Instalar o pacote de conectores do Serviço de conversão automática de formulários**

Você precisa do pacote de conectores 1.1.38 ou superior para usar os recursos e as melhorias mais recentes fornecidos na versão AFC-2020.03.1.

Se você já tiver em execução um ambiente do serviço de Conversão automática de formulários (AEM 6.5 ou AEM 6.5 LTS), para usar os recursos mais recentes do serviço de conversão, instale o service pack mais recente, o pacote complementar mais recente do AEM Forms e o pacote de conectores mais recente na ordem mencionada. Para o AEM Forms as a Cloud Service, as atualizações são fornecidas automaticamente. Para obter instruções detalhadas, consulte o artigo [Configurar o Serviço de conversão automática de formulários](configure-service.md).

