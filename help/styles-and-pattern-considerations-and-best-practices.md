---
title: 'Práticas recomendadas e considerações '
seo-title: 'Práticas recomendadas e considerações '
description: Práticas recomendadas e considerações para o serviço Automated Forms Conversion
seo-description: Lista de estilos e padrões em PDF forms de origem que o serviço Automatizado de Conversão Forms encontra dificuldades para identificar
uuid: e24773a2-be14-4184-a168-48aa976d459a
topic-tags: introduction
discoiquuid: 79f2026e-73a5-4bd1-b041-d1399b4ad23e
translation-type: tm+mt
source-git-commit: e2298422e0af9b1c678e7604be3efb6da377d7dd
workflow-type: tm+mt
source-wordcount: '1259'
ht-degree: 3%

---


# Práticas recomendadas e padrões complexos conhecidos {#Best-practices-and-considerations2}

Este documento fornece orientações e recomendações que podem ser beneficiadas pelo administrador, autores e desenvolvedores de formulários ao trabalhar com [!DNL Automated Forms Conversion service]. Ele discute as práticas recomendadas, desde a preparação de formulários de origem até a correção de padrões complexos que exigem algum esforço extra para a conversão automatizada. Essas práticas recomendadas contribuem coletivamente para o desempenho e a produção geral do [!DNL Automated Forms Conversion service].

## Práticas recomendadas

O serviço de conversão converte PDF forms disponíveis na sua [!DNL Forms] instância AEM em formulários adaptáveis. As práticas recomendadas listadas abaixo ajudam você a melhorar a velocidade e a precisão de conversão. Além disso, essas práticas recomendadas ajudam você a economizar tempo gasto em atividades de conversão.

### Antes de fazer upload da fonte

Você pode fazer upload de todas as PDF forms de uma só vez ou em fases, conforme necessário. Antes de carregar os formulários, considere o seguinte:

* Mantenha o número de formulários em uma pasta menor que 15 e mantenha o número total de páginas em uma pasta menor que 50.
* Mantenha o tamanho da pasta com menos de 10 MB. Não conserve formulários em uma subpasta.
* Mantenha o número de páginas em um formulário menor que 15.
* Organize documentos de origem em um lote de 8 a 15 documentos. Mantenha formulários de origem com Fragmentos de formulário adaptáveis comuns em um único lote.
* Não carregue os formulários protegidos. O serviço não converte formulários protegidos por senha e protegidos.
* Do not upload the [PDF Portfolios](https://helpx.adobe.com/br/acrobat/using/overview-pdf-portfolios.html). O serviço não converte um Portfolio PDF em um formulário adaptável.
* Não carregue formulários digitalizados, em idioma diferente do inglês e preenchidos. Tais formas não são suportados.
* Não carregue formulários de origem com espaços no nome do arquivo. Remova o espaço do nome do arquivo antes de fazer upload dos formulários.

Ao usar um formulário XDP para conversão, execute as seguintes etapas antes de carregar os formulários XPD de origem:

* Analise o formulário XDP e corrija problemas visuais. Verifique se o documento de origem usa os controles e estruturas desejados. Por exemplo, o formulário de origem pode ter caixas de seleção em vez de botões de opção para uma única seleção. Altere as caixas de seleção para botões de opção para produzir um formulário adaptável com os componentes desejados.
* [Adicione vínculos ao formulário](http://www.adobe.com/go/learn_aemforms_designer_65) XDP antes de iniciar a conversão. Quando os vínculos estão disponíveis no formulário XDP de origem, o serviço aplica automaticamente vínculos aos campos de formulário adaptáveis correspondentes durante a conversão. Ele economiza o tempo necessário para aplicar manualmente os vínculos.
* [Adicione tags](https://helpx.adobe.com/sign/using/text-tag.html) do Adobe Sign ao arquivo XDP. O serviço converte automaticamente as tags Adobe Sign em campos de formulário adaptáveis correspondentes. A Forms adaptativa suporta um número limitado de campos Adobe Sign. Para obter a lista completa dos campos suportados, consulte [Uso do Adobe Sign em uma documentação de formulário](https://docs.adobe.com/content/help/en/experience-manager-65/forms/adaptive-forms-advanced-authoring/working-with-adobe-sign.html) adaptável.
* Converta tabelas complexas em documentos XDP em tabelas simples, se possível. Uma tabela com campos de formulário em células de tabela, células de tamanho irregular, células expandidas de linha ou coluna, células unidas, bordas parciais ou nenhuma borda visível é considerada uma tabela complexa. Um quadro com qualquer um dos itens acima mencionados é considerado um quadro complexo.
<!-- * Use sub-forms in XDP documents to create panels in adaptive forms. Service converts each sub-form to one or more adaptive form panels during conversion. -->

### Antes de start da conversão

* Crie modelos de formulário adaptáveis. Os modelos ajudam a especificar uma estrutura uniforme para os formulários de sua organização ou departamento.
* Especifique o cabeçalho e o rodapé nos modelos de formulário adaptável. O serviço ignora o cabeçalho-rodapé dos documentos de origem e usa o cabeçalho-rodapé especificado no modelo de formulário adaptável.
* Crie temas de formulário adaptáveis. Os temas ajudam a fornecer uma aparência uniforme aos formulários de sua organização ou departamento.
* Configure o Modelo de dados de formulário para salvar e recuperar de uma fonte de dados. Crie e configure serviços de leitura e gravação para o Modelo de dados de formulário.
* Crie Fragmentos de formulário adaptáveis e configure o serviço para usar seus Fragmentos de formulário adaptáveis.
* Prepare modelos de fluxo de trabalho comuns para os formulários que exigem automação de processos de negócios.
* Configure o Adobe Analytics, se necessário


## Conheça padrões complexos

AEM [!DNL Forms Automated Conversion service] usa inteligência artificial e algoritmos de aprendizado de máquina para entender o layout e os campos do formulário de origem. Cada serviço de aprendizado de máquina aprende continuamente a partir de dados de origem e produz uma saída aprimorada com cada churn. Estes serviços aprendem com a experiência como os humanos.

[!DNL Automated Forms Conversion service] é treinada em um grande conjunto de formulários. Ela identifica facilmente os campos em um formulário de origem e produz formulários adaptáveis. No entanto, há alguns campos e estilos em PDF forms que são facilmente visíveis para o olho humano, mas difíceis de entender para o serviço. O serviço pode atribuir diferentes tipos de campos ou painéis aplicáveis a alguns campos ou estilos. Todos esses padrões de campo e estilo estão listados abaixo.

O serviço start a identificação e atribuição de campos ou painéis corretos a esses padrões à medida que continua aprendendo com os dados de origem. Por enquanto, você pode usar o editor [Revisar e Corrigir](review-correct-ui-edited.md) para corrigir esses problemas. Antes de o start corrigir os problemas ou ler mais detalhadamente, familiarize-se com os componentes [de formulário](https://helpx.adobe.com/experience-manager/6-5/forms/using/introduction-forms-authoring.html)adaptáveis.

### Padrões gerais {#general}

| Padrão | Exemplo |
|--- |--- |
| **O** Serviço de padrão <br>não converte PDF forms preenchidos em formulários adaptáveis. <br><br>**Resolução** <br>Use formulários adaptativos vazios. | ![Formulário preenchido](assets/best-practice-filled-forms.png) |
| **O** Serviço de padrão <br>pode falhar ao reconhecer texto e campos em um formulário denso. <br><br>**Resolução**<br> Aumenta a largura entre o texto e os campos de um formulário denso antes de iniciar a conversão. |  |
| **O** Serviço de padrão <br>não suporta formulários digitalizados. <br><br>**Resolução** <br>Não use formulários digitalizados. | ![Formulário digitalizado](assets/scanned-forms.png) |
| **O** Serviço de padrão <br>não extrai imagens e texto em imagens. <br><br>**Resolução**<br> Adiciona manualmente imagens ou texto a formulários convertidos. | ![Imagem com formulário de texto](assets/best-practice-image-with-text.png) |
| **As** tabelas padrão <br>com limites e bordas pontilhados ou não claros não são convertidas. <br><br>**Resolução** <br>Use tabelas com limites e bordas explícitos. suportado. | ![Formulário de tabela não limpo](assets/best-practice-table-dotted-non-clear.png) |
| **Padrão** Os formulários adaptáveis não são compatíveis com o texto vertical pronto para uso <br> . Portanto, o serviço não converte o texto vertical para o texto Adaptive Forms correspondente. <br><br>**Resolução** <br> Use o editor de formulário adaptável para adicionar texto vertical, se necessário. | ![Formulário de tabela não limpo](assets/vertical-text.png) |



### Grupo de escolha  {#choice-group}

| Padrão | Resolução |
|--- |--- |
| **Opções de grupo de escolha de padrão** <br> com formas diferentes de caixa ou círculo não são convertidas em componentes de formulário adaptáveis correspondentes. <br><br>**Resolução**<br> Altere as opções de escolha para caixa ou círculo ou use o Editor de revisão e correção para identificar as formas. | ![Campos de escolha ](assets/best-practice-choice-group-options.png) |

### Form fields {#form-fields}

| Padrão | Resolução |
|--- |--- |
| **O Serviço de Padrão** <br> não identifica campos sem bordas claras. <br><br>**Resolução**<br> Use o editor Revisão e Correção para identificar esses campos. | ![campos com limites não claros](assets/best-practice-fields-without-clear-borders.png) |
| **O Serviço de padrão** <br> pode não identificar alguns campos de formulário de grupo de escolha com legendas na parte inferior ou direita de um formulário. <br><br>**Resolução**<br> Use o Editor de revisão e correção para identificar esses campos | ![Campos de escolha](assets/best-practice-caption-bottom-right.png) |
| **O Serviço de padrão** <br> mescla ou atribui um tipo errado a alguns campos de formulário que são colocados muito próximos uns dos outros ou que não têm bordas claras. <br><br>**Resolução**<br> Use o editor Revisão e Correção para identificar esses campos. | ![Campos de escolha](assets/best-practice-placed-very-near.png) |
| **O Serviço de padrão** <br> pode falhar ao reconhecer campos com legendas distantes ou uma linha pontilhada entre a legenda e o campo de entrada. <br><br>**Resolução**<br> Use campos de formulários com limites claros ou use o Editor de revisão e correção para corrigir esses problemas. | ![Campos distantes ou linha pontilhada entre o campo de legenda](assets/best-practice-far-away-captions-or-a-dotted-line.png) |

### Listas {#lists}

| Padrão | Resolução |
|--- |--- |
| **As** Listas padrão <br>que contêm campos de formulário são mescladas ou não convertidas em componentes de formulário adaptáveis correspondentes <br><br>**Resolução** <br>Use campos de formulários com limites claros ou use o Editor de revisão e correção para corrigir esses problemas. | ![listas que contêm grupos de escolha](assets/best-practice-lists-containing-form-fields.png) |
| **O** Serviço de padrão <br>pode deixar algumas listas aninhadas sem identificação <br><br>**Resolução** <br> Use o editor de Revisão e Correção para corrigir esses problemas. | ![listas que contêm grupos de escolha](assets/best-practice-nested-lists.png) |
| **O Serviço de padrão** <br> mescla algumas listas que contêm grupos de opções entre si <br><br>**** <br> Use o Editor de revisão e correção para corrigir esses problemas. | ![listas que contêm grupos de escolha](assets/best-practice-check-box-in-table-cells.png) |

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
