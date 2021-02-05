---
title: 'Práticas recomendadas e considerações '
description: NÃO PUBLICAR
seo-description: NÃO PUBLICAR
page-status-flag: never-activated
uuid: c2821264-39e2-44f8-b234-835c46f33fd5
topic-tags: introduction
discoiquuid: b786e40a-202e-4e17-a2f5-1f77c46538c2
privatebeta: true
index: false
translation-type: tm+mt
source-git-commit: b2d29c22a275f2dc6a82593cf5e441c8da0bba13
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 7%

---


# Práticas recomendadas e considerações {#do-not-publish-best-practices-and-considerations}

<!--
[DO NOT PUBLISH]
-->

O serviço de Conversão automatizada da AEM Forms converte um formulário PDF em um formulário adaptável. O serviço usa inteligência artificial e algoritmos de aprendizado de máquina para entender o layout e os campos do formulário de origem. Cada serviço de aprendizado de máquina aprende continuamente a partir de dados de origem e produz uma saída aprimorada com cada churn. Estes serviços aprendem com a experiência como os humanos.

O serviço de automated forms conversion é treinado em um grande conjunto de formulários. Ela identifica facilmente os campos em um formulário de origem e produz formulários adaptáveis. No entanto, há alguns campos e estilos em PDF forms que são facilmente visíveis para o olho humano, mas difíceis de entender para o serviço. O serviço pode atribuir tipos de campos ou painéis diferentes dos aplicáveis a alguns campos ou estilos. Todos esses padrões de campo e estilo estão listados abaixo.

O serviço start a identificação e atribuição de campos ou painéis corretos a esses padrões à medida que continua aprendendo com os dados de origem. Por enquanto, você pode usar o editor [Revisar e corrigir](review-correct-ui-edited.md) para corrigir esses problemas. Antes de o start corrigir os problemas ou ler mais detalhadamente, familiarize-se com [componentes de formulário adaptáveis](https://helpx.adobe.com/experience-manager/6-5/forms/using/introduction-forms-authoring.html).

## Geral {#general}

<table border="1" cellpadding="1" cellspacing="0" style="border-collapse: separate; border-spacing: 0px;" width="100%"> 
 <tbody>
  <tr>
   <td width="30%">Padrões e resolução conhecidos</td> 
   <td width="70%">Exemplo</td> 
  </tr>
   <td><p><strong>Padrão</strong></p> <p>O serviço não converte PDF forms preenchidos em formulários adaptáveis.</p> <p> </p> <p><strong>Resolução</strong></p> <p>Use formulários adaptativos vazios.</p> </td> 
   <td style="text-align: left;"><img src="assets/pre-filled-form.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>Padrão</strong></p> <p>O serviço não consegue reconhecer o texto e os campos num formulário denso.</p> <p> </p> <p><strong>Resolução</strong></p> <p>Aumente a largura entre o texto e os campos de um formulário denso antes de iniciar a conversão.</p> </td> 
   <td style="text-align: left;"><img src="assets/dense%20form.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>Padrão</strong></p> <p>O serviço não suporta formulários digitalizados.</p> <p> </p> <p><strong>Resolução</strong></p> <p>Não use formulários digitalizados. </p> </td> 
   <td><img src="assets/scanned-form.jpg" /></td> 
  </tr>
  <tr>
   <td><p><strong>Padrão</strong></p> <p>O serviço não extrai imagens e texto em imagens. </p> <p> </p> <p><strong>Resolução</strong></p> <p>Adicione manualmente imagens ou texto a formulários convertidos.</p> </td> 
   <td><img src="assets/image-in-adaptive-form.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>Padrão</strong></p> <p>Tabelas com limites e bordas pontilhados ou não claros não são convertidas.</p> <p><strong>Resolução</strong></p> <p>Use tabelas com limites e bordas claramente explícitos. suportado.</p> </td> 
   <td><img src="assets/border-less-tables.png" /></td> 
  </tr>
 </tbody>
</table>

## Grupo de Escolha {#choice-group}

<table border="1" cellpadding="1" cellspacing="0" width="100%"> 
 <tbody>
  <tr>
   <td width="30%">Padrão</td> 
   <td width="70%">Exemplo</td> 
  </tr>
  <tr>
   <td><p><strong>Padrão</strong></p> <p>As opções de grupo de opções com formas diferentes de caixa ou círculo não são convertidas em componentes de formulário adaptáveis correspondentes. </p> <p> </p> <p><strong>Resolução</strong></p> <p>Altere as formas das opções de escolha para caixa ou círculo ou use o Editor de revisão e correção para identificar as formas.</p> </td> 
   <td><img src="assets/shaded-box-patterns.png" /> </td> 
  </tr>
 </tbody>
</table>

## Campos de formulário {#form-fields}

<table border="1" cellpadding="1" cellspacing="0" width="100%"> 
 <tbody>
  <tr>
   <td width="30%">Padrão</td> 
   <td width="70%">Exemplo</td> 
  </tr>
  <tr>
   <td width="25%"><p><strong>Padrão</strong></p> <p>O serviço não identifica campos sem bordas claras.</p> <p> </p> <p><strong>Resolução</strong></p> <p>Use o Editor de revisão e correção para identificar esses campos.</p> <p> </p> <p> </p> </td> 
   <td width="50%"><br /> <img src="assets/fields-without-clear-borders.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>Padrão</strong></p> <p>O serviço deixa alguns campos de formulário com legendas na parte inferior ou direita não identificadas.</p> <p> </p> <p><strong>Resolução</strong></p> <p>Usar o Editor de revisão e correção para identificar esses campos</p> </td> 
   <td><br /> <img src="assets/forms-with-clear-borders-scale.png" /><br /> </td> 
  </tr>
  <tr>
   <td><p><strong>Padrão</strong></p> <p>O serviço mescla ou atribui um tipo errado a alguns campos de formulário que são colocados muito próximos uns dos outros ou não têm bordas claras. </p> <p> </p> <p><strong>Resolução</strong></p> <p>Use o Editor de revisão e correção para identificar esses campos.</p> </td> 
   <td><img src="assets/forms-with-fields-placed-nearby.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>Padrão</strong></p> <p>O serviço pode falhar ao reconhecer campos com legendas distantes ou uma linha pontilhada entre a legenda e o campo de entrada.</p> <p> </p> <p><strong>Resolução</strong></p> <p>Use campos de formulários com limites claros ou use o Editor de revisão e correção para corrigir esses problemas.</p> </td> 
   <td><img src="assets/form-fields-with-far-away-captions.png" /></td> 
  </tr>
 </tbody>
</table>

## Listas {#lists}

<table border="1" cellpadding="1" cellspacing="0" width="100%"> 
 <tbody>
  <tr>
   <td width="30%">Padrão</td> 
   <td width="70%">Exemplo</td> 
  </tr>
  <tr>
   <td><p><strong>Padrão</strong></p> <p>Listas que contêm campos de formulário são mescladas ou não são convertidas em componentes de formulário adaptáveis correspondentes</p> <p><strong>Resolução</strong></p> <p>Use campos de formulários com limites claros ou use o Editor de revisão e correção para corrigir esses problemas.</p> </td> 
   <td><img src="assets/lists-with-fields.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>Padrão</strong></p> <p>O serviço pode deixar algumas listas aninhadas não identificadas</p> <p> </p> <p><strong>Resolução</strong></p> <p>Use o Editor de revisão e correção para corrigir esses problemas.</p> </td> 
   <td><img src="assets/nested-lists.png" /> </td> 
  </tr>
  <tr>
   <td><p><strong>Padrão</strong></p> <p>O serviço mescla algumas listas que contêm grupos de opções entre si</p> <p><strong>Resolução</strong></p> <p>Use o Editor de revisão e correção para corrigir esses problemas.</p> </td> 
   <td><img src="assets/lists-containing-choice-groups.png" /> </td> 
  </tr>
 </tbody>
</table>

<!--
Comment Type: draft

<h3>Choice groups</h3>
-->

<!--
Comment Type: draft

<ul>
<li>Lists with form fields, nested lists, and nested choice groups are not supported.</li>
<li>Form fields with captions at bottom or right are not supported.</li>
<li>Form fiields without bordes are not supported.</li>
<li>Hidden form fields are not supported.</li>
<li>Button in PDF forms are not converted to adaptive form buttons.<br /> </li>
<li>Tables with clear explicit boundaries and borders are supported.</li>
<li>Fields with far away captions are not supported.<br /> </li>
<li>Choice groups with only box or circle shaped selectors are supported. </li>
</ul>
-->

