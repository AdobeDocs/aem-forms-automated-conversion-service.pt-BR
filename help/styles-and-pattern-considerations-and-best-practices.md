---
title: 'Práticas recomendadas e considerações '
seo-title: 'Práticas recomendadas e considerações '
description: Práticas recomendadas e considerações para o serviço de conversão de formulários automatizada
seo-description: Lista de estilos e padrões em formulários PDF de origem que o serviço de conversão de formulários automatizados tem dificuldade de identificar
uuid: e24773a2-be14-4184-a168-48aa976d459a
topic-tags: introduction
discoiquuid: 79f2026e-73a5-4bd1-b041-d1399b4ad23e
translation-type: tm+mt
source-git-commit: 0f413a8bc0bb444b6faaddaf32f84f36e38438a5

---


# Práticas recomendadas e padrões complexos conhecidos {#Best-practices-and-considerations2}

Este documento fornece orientações e recomendações que podem beneficiar os administradores, autores e desenvolvedores de formulários ao trabalhar com o serviço de Conversão de formulários automatizados. Ele discute as práticas recomendadas, desde a preparação de formulários de origem até a correção de padrões complexos que exigem algum esforço extra para a conversão automatizada. Essas práticas recomendadas contribuem coletivamente para o desempenho geral e a saída do serviço de Conversão de formulários automatizados.

## Práticas recomendadas

O serviço de conversão converte formulários PDF disponíveis na instância do AEM Forms em formulários adaptáveis. Você pode carregar todos os formulários PDF de uma vez ou em fases, conforme necessário. Antes de carregar os formulários, considere o seguinte:

* Mantenha o número de formulários em uma pasta menor que 15 e mantenha o número total de páginas em uma pasta menor que 50.
* Mantenha o tamanho da pasta com menos de 10 MB. Não mantenha formulários em uma subpasta.
* Mantenha o número de páginas em um formulário menor que 15.
* Não carregue os formulários protegidos. O serviço não converte formulários protegidos por senha e protegidos.
* Não carregue os portfólios [PDF](https://helpx.adobe.com/acrobat/using/overview-pdf-portfolios.html). O serviço não converte um Portfólio PDF em formulários adaptáveis.
* Não carregue formulários digitalizados, coloridos, em idioma diferente do inglês e preenchidos. Esses formulários não são suportados.
* Não carregue formulários de origem com espaços no nome do arquivo. Remova o espaço do nome do arquivo antes de fazer upload dos formulários.
* Use modelos de formulário adaptáveis para especificar cabeçalho e rodapé para o formulário adaptável de saída. O serviço ignora o cabeçalho-rodapé dos documentos PDF de origem e usa o cabeçalho-rodapé especificado no modelo de formulário adaptável.

## Conheça padrões complexos

O serviço de conversão automatizada do AEM Forms usa algoritmos de inteligência artificial e aprendizado de máquina para entender o layout e os campos do formulário de origem. Cada serviço de aprendizado de máquina aprende continuamente a partir de dados de origem e produz uma saída aprimorada com cada churn. Estes serviços aprendem com a experiência como os humanos.

O serviço de Conversão de formulários automatizada é treinado em um grande conjunto de formulários. Ela identifica facilmente os campos em um formulário de origem e produz formulários adaptáveis. Entretanto, há alguns campos e estilos em formulários PDF que são facilmente visíveis para o olho humano, mas difíceis de entender para o serviço. O serviço pode atribuir tipos de campos ou painéis diferentes dos aplicáveis a alguns campos ou estilos. Todos esses padrões de campo e estilo estão listados abaixo.

O serviço começaria a identificar e atribuir campos ou painéis corretos a esses padrões à medida que continuava aprendendo com os dados de origem. Por enquanto, você pode usar o editor [Revisar e Corrigir](review-correct-ui-edited.md) para corrigir esses problemas. Antes de começar a corrigir os problemas ou a ler mais detalhadamente, familiarize-se com os componentes [de formulário](https://helpx.adobe.com/experience-manager/6-5/forms/using/introduction-forms-authoring.html)adaptáveis.

### Padrões gerais {#general}

| Padrão | Resolução |
|--- |--- |
| **O Serviço de padrão** <br> não converte formulários PDF coloridos em formulários adaptáveis. <br><br>**Resolução **<br>Use formulários PDF em preto-e-branco ou em tons de cinza. | ![Formulário colorido](assets/best-practice-coloured-forms.png) |
| **O** Serviço de padrão <br>não converte formulários PDF preenchidos em formulários adaptáveis. <br><br>**Resolução **<br>Use formulários adaptativos vazios. | ![Formulário preenchido](assets/best-practice-filled-forms.png) |
| **O** Serviço de padrão <br>pode falhar ao reconhecer texto e campos em um formulário denso. <br><br>**Resolução **<br>Aumenta a largura entre o texto e os campos de um formulário denso antes de iniciar a conversão. |  |
| **O** Serviço de padrão <br>não suporta formulários digitalizados. <br><br>**Resolução **<br>Não use formulários digitalizados. | ![Formulário digitalizado](assets/scanned-forms.png) |
| **O** Serviço de padrão <br>não extrai imagens e texto em imagens. <br><br>**Resolução **<br>Adiciona manualmente imagens ou texto a formulários convertidos. | ![Imagem com formulário de texto](assets/best-practice-image-with-text.png) |
| **As** tabelas padrão <br>com limites e bordas pontilhados ou não claros não são convertidas. <br><br>**Resolução **<br>Use tabelas com limites e bordas explícitos. suportado. | ![Formulário de tabela não limpo](assets/best-practice-table-dotted-non-clear.png) |
| **Padrão** <br> O formulário adaptável não suporta texto vertical pronto para uso. Portanto, o serviço não converte o texto vertical para o texto correspondente dos Formulários adaptáveis. <br><br>**Resolução **<br>Use o editor de formulário adaptável para adicionar texto vertical, se necessário. | ![Formulário de tabela não limpo](assets/vertical-text.png) |



### Grupo de escolha {#choice-group}

| Padrão | Resolução |
|--- |--- |
| **Opções de grupo de escolha de padrão** <br> com formas diferentes de caixa ou círculo não são convertidas em componentes de formulário adaptáveis correspondentes. <br><br>**Resolução **<br>Altere as opções de escolha para caixa ou círculo ou use o Editor de revisão e correção para identificar as formas. | ![Campos de escolha ](assets/best-practice-choice-group-options.png) |

### Form fields {#form-fields}

| Padrão | Resolução |
|--- |--- |
| **O Serviço de Padrão** <br> não identifica campos sem bordas claras. <br><br>**Resolução **<br>Use o editor Revisão e Correção para identificar esses campos. | ![campos com limites não claros](assets/best-practice-fields-without-clear-borders.png) |
| **O Serviço de padrão** <br> pode não identificar alguns campos de formulário de grupo de escolha com legendas na parte inferior ou direita de um formulário. <br><br>**Resolução **<br>Use o Editor de revisão e correção para identificar esses campos | ![Campos de escolha](assets/best-practice-caption-bottom-right.png) |
| **O Serviço de padrão** <br> mescla ou atribui um tipo errado a alguns campos de formulário que são colocados muito próximos uns dos outros ou não têm bordas claras. <br><br>**Resolução **<br>Use o editor Revisão e Correção para identificar esses campos. | ![Campos de escolha](assets/best-practice-placed-very-near.png) |
| **O Serviço de padrão** <br> pode falhar ao reconhecer campos com legendas distantes ou uma linha pontilhada entre a legenda e o campo de entrada. <br><br>**Resolução **<br>Use campos de formulários com limites claros ou use o Editor de revisão e correção para corrigir esses problemas. | ![Campos distantes ou linha pontilhada entre o campo de legenda](assets/best-practice-far-away-captions-or-a-dotted-line.png) |

### Listas {#lists}

| Padrão | Resolução |
|--- |--- |
| **As** listas de padrões <br>que contêm campos de formulário são mescladas ou não são convertidas em componentes de formulário adaptáveis correspondentes <br><br>**Resolução **<br>Use campos de formulários com limites claros ou use o Editor de revisões e correções para corrigir esses problemas. | ![listas que contêm grupos de opções](assets/best-practice-lists-containing-form-fields.png) |
| **O** Serviço de padrão <br>pode deixar algumas listas aninhadas sem identificação <br><br>**Resolução **<br>Use o editor de Revisão e Correção para corrigir esses problemas. | ![listas que contêm grupos de opções](assets/best-practice-nested-lists.png) |
| **O Serviço de padrão** <br> mescla algumas listas que contêm grupos de opções entre si <br><br>****<br>Use o Editor de revisão e correção para corrigir esses problemas. | ![listas que contêm grupos de opções](assets/best-practice-check-box-in-table-cells.png) |

<!--
Comment Type: draft

<h3>Choice groups</h3>
-->

<!--
Comment Type: draft

<ul>
<li>Lists with form fields, nested lists, and nested choice groups are not supported.</li>
<li>Form fields with captions at bottom or right are not supported.</li>
<li>Form fields without borders are not supported.</li>
<li>Hidden form fields are not supported.</li>
<li>Button in PDF forms are not converted to adaptive form buttons.<br /> </li>
<li>Tables with clear explicit boundaries and borders are supported.</li>
<li>Fields with far away captions are not supported.<br /> </li>
<li>Choice groups with only box or circle shaped selectors are supported. </li>
</ul>
-->
