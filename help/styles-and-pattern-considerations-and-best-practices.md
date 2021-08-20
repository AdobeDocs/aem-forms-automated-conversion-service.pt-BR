---
title: 'Práticas recomendadas e considerações '
seo-title: 'Práticas recomendadas e considerações '
description: Práticas recomendadas e considerações para o serviço Automated forms conversion
seo-description: Lista de estilos e padrões em PDF forms de origem que o serviço Automated forms conversion tem dificuldade de identificar
uuid: e24773a2-be14-4184-a168-48aa976d459a
topic-tags: introduction
discoiquuid: 79f2026e-73a5-4bd1-b041-d1399b4ad23e
exl-id: 9ada091a-e7c6-40e9-8196-c568f598fc2a
source-git-commit: 65b0d6f6568ce7915b1a8bd85981bead967d869c
workflow-type: tm+mt
source-wordcount: '1267'
ht-degree: 3%

---

# Práticas recomendadas e padrões complexos conhecidos {#Best-practices-and-considerations2}

Este documento fornece diretrizes e recomendações que podem ser beneficiadas pelo administrador, autores e desenvolvedores de formulários ao trabalhar com [!DNL Automated Forms Conversion service]. Ele discute as práticas recomendadas desde a preparação de formulários de origem até a correção de padrões complexos que exigem algum esforço extra para a conversão automatizada. Essas práticas recomendadas contribuem coletivamente para o desempenho e a saída gerais do [!DNL Automated Forms Conversion service].

## Práticas recomendadas

O serviço de conversão converte PDF forms disponíveis na instância AEM [!DNL Forms] em formulários adaptáveis. As práticas recomendadas listadas abaixo ajudam a melhorar a velocidade e a precisão da conversão. Além disso, essas práticas recomendadas ajudam a economizar tempo gasto em atividades de conversão.

### Antes de fazer upload da fonte

Você pode fazer upload de todas as PDF forms de uma só vez ou em fases, conforme necessário. Antes de carregar os formulários, considere o seguinte:

* Mantenha o número de formulários em uma pasta menor que 15 e mantenha o número total de páginas em uma pasta menor que 50.
* Mantenha o tamanho da pasta menor que 10 MB. Não conserve formulários em uma subpasta.
* Mantenha o número de páginas em um formulário menor que 15.
* Organize documentos de origem em um lote de 8 a 15 documentos. Mantenha formulários de origem com Fragmentos de formulário adaptável comuns em um único lote.
* Não carregue os formulários protegidos. O serviço não converte formulários protegidos por senha.
* Não carregue o [PDF Portfolio](https://helpx.adobe.com/br/acrobat/using/overview-pdf-portfolios.html). O serviço não converte um Portfolio PDF em um formulário adaptável.
* Não carregue formulários digitalizados, preenchidos e em qualquer idioma diferente de inglês, francês, alemão e espanhol. Tais formas não são suportados.
* Não carregue formulários de origem com espaços no nome do arquivo. Remova o espaço do nome do arquivo antes de fazer upload dos formulários.

Ao usar um formulário XDP para conversão, execute as seguintes etapas antes de fazer upload dos formulários XPD de origem:

* Analise o formulário XDP e corrija problemas visuais. Certifique-se de que o documento de origem use os controles e estruturas pretendidos. Por exemplo, o formulário de origem pode ter caixas de seleção em vez de botões de opção para uma única seleção. Altere as caixas de seleção para botões de opção para produzir um formulário adaptável com componentes pretendidos.
* [Adicione vínculos ao ](http://www.adobe.com/go/learn_aemforms_designer_65) formulário XDP antes de iniciar a conversão. Quando os vínculos estão disponíveis no formulário XDP de origem, o serviço aplica automaticamente vínculos aos campos de formulário adaptáveis correspondentes durante a conversão. Ele economiza o tempo necessário para aplicar manualmente os vínculos.
* [Adicione ](https://helpx.adobe.com/sign/using/text-tag.html) tags Adobe Sign ao arquivo XDP. O serviço converte automaticamente as tags Adobe Sign em campos de formulário adaptáveis correspondentes. O Adaptive Forms suporta um número limitado de campos Adobe Sign. Para obter a lista completa de campos compatíveis, consulte a documentação [Usando Adobe Sign em um formulário adaptável](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/working-with-adobe-sign.html?lang=en).
* Se possível, converta tabelas complexas em documentos XDP em tabelas simples. Uma tabela com campos de formulário em células de tabela, células de tamanho desigual, células expandidas de linha ou coluna, células unidas, bordas parciais ou nenhuma borda visível é considerada uma tabela complexa. Um quadro com qualquer um dos itens acima mencionados é considerado um quadro complexo.
<!-- * Use sub-forms in XDP documents to create panels in adaptive forms. Service converts each sub-form to one or more adaptive form panels during conversion. -->

### Antes de iniciar a conversão

* Criar modelos de formulário adaptáveis. Os modelos ajudam a especificar uma estrutura uniforme para os formulários de sua organização ou departamento.
* Especifique o cabeçalho e o rodapé nos modelos de formulário adaptáveis. O serviço ignora o cabeçalho-rodapé dos documentos de origem e usa o cabeçalho-rodapé especificado no modelo de formulário adaptável.
* Crie temas de formulário adaptáveis. Os temas ajudam a fornecer uma aparência uniforme às formas de sua organização ou departamento.
* Configure o Modelo de dados de formulário para salvar e recuperar de uma fonte de dados. Crie e configure serviços de leitura e gravação para o Modelo de dados de formulário.
* Crie Fragmentos de formulário adaptáveis e configure o serviço para usar os Fragmentos de formulário adaptáveis.
* Prepare modelos de fluxo de trabalho comuns para os formulários que exigem automação de processos de negócios.
* Configure o Adobe Analytics, se necessário


## Conhecer padrões complexos

AEM [!DNL Forms Automated Conversion service] usa inteligência artificial e algoritmos de aprendizado de máquina para entender o layout e os campos do formulário de origem. Cada serviço de aprendizado de máquina aprende continuamente a partir de dados de origem e produz uma saída aprimorada com cada churn. Esses serviços aprendem com a experiência como humanos.

[!DNL Automated Forms Conversion service] O é treinado em um grande conjunto de formulários. Ele identifica facilmente os campos em um formulário de origem e produz formulários adaptáveis. No entanto, há alguns campos e estilos em PDF forms que são facilmente visíveis para o olho humano, mas difíceis de entender para o serviço. O serviço pode atribuir diferentes tipos de campos ou painéis aplicáveis a alguns campos ou estilos. Todos esses padrões de campo e estilo estão listados abaixo.

O serviço começaria a identificar e atribuir campos ou painéis corretos a esses padrões, pois continuaria aprendendo com os dados de origem. Por enquanto, você pode usar o editor [Revisar e corrigir](review-correct-ui-edited.md) para corrigir esses problemas. Antes de começar a corrigir os problemas ou a ler mais, familiarize-se com [componentes de formulário adaptáveis](https://helpx.adobe.com/experience-manager/6-5/forms/using/introduction-forms-authoring.html).

### Padrões gerais {#general}

| Padrão | Exemplo |
|--- |--- |
| **** <br>O PatternService não converte PDF forms preenchidas em um formulário adaptável. <br><br>**** <br>SoluçãoUse formulários adaptáveis vazios. | ![Formulário preenchido](assets/best-practice-filled-forms.png) |
| **** <br>O PatternService pode falhar ao reconhecer o texto e os campos em um formulário denso. <br><br>**** <br> SoluçãoAumenta a largura entre o texto e os campos de um formulário denso antes de iniciar a conversão. |  |
| **** <br>O PatternService não oferece suporte a formulários digitalizados. <br><br>**** <br>SoluçãoNão use formulários digitalizados. | ![Formulário digitalizado](assets/scanned-forms.png) |
| **** <br>O StandardService não extrai imagens e texto em imagens. <br><br>**** <br> SoluçãoAdicionar imagens ou texto manualmente a formulários convertidos. | ![Imagem com formulário de texto](assets/best-practice-image-with-text.png) |
| **** <br>As tabelas padrão com limites e bordas pontilhados ou não claros não são convertidas. <br><br>**** <br>SoluçãoUse tabelas com limites e limites explícitos claros. suportado. | ![Formulário de tabela não-claro](assets/best-practice-table-dotted-non-clear.png) |
| **** <br> PadrãoOs formulários adaptáveis não suportam texto vertical pronto para uso. Portanto, o serviço não converte o texto vertical para o texto Adaptive Forms correspondente. <br><br>**** <br> SoluçãoUse o editor de formulário adaptável para adicionar texto vertical, se necessário. | ![Formulário de tabela não-claro](assets/vertical-text.png) |



### Grupo de opções  {#choice-group}

| Padrão | Resolução |
|--- |--- |
| **** <br> Opções de grupo de escolha de padrão com formas diferentes de caixa ou círculo não são convertidas em componentes de formulário adaptáveis correspondentes. <br><br>**** <br> SoluçãoAltere as opções de escolha para caixa ou círculo ou use o editor Revisar e corrigir para identificar as formas. | ![Campos de escolha  ](assets/best-practice-choice-group-options.png) |

### Campos de formulário {#form-fields}

| Padrão | Resolução |
|--- |--- |
| **** <br> O PatternService não identifica campos sem bordas claras. <br><br>**** <br> SoluçãoUse o editor de Revisão e Correção para identificar esses campos. | ![campos com limites não claros](assets/best-practice-fields-without-clear-borders.png) |
| **** <br> O StandardService pode não identificar alguns campos de formulário de grupo de escolha com legendas no lado inferior ou direito de um formulário. <br><br>**** <br> SoluçãoUse o editor de Revisão e Correção para identificar esses campos | ![Campos de escolha](assets/best-practice-caption-bottom-right.png) |
| **** <br> O PatternService mescla ou atribui um tipo errado a alguns campos de formulário que são colocados muito próximos uns dos outros ou que não têm bordas claras. <br><br>**** <br> SoluçãoUse o editor de Revisão e Correção para identificar esses campos. | ![Campos de escolha](assets/best-practice-placed-very-near.png) |
| **** <br> O StandardService pode falhar ao reconhecer campos com legendas distantes ou uma linha pontilhada entre a legenda e o campo de entrada. <br><br>**** <br> SoluçãoUse campos de formulários com limites claros ou use o editor Revisar e corrigir para corrigir esses problemas. | ![Campos distantes ou linha pontilhada entre o campo da legenda](assets/best-practice-far-away-captions-or-a-dotted-line.png) |

### Listas {#lists}

| Padrão | Resolução |
|--- |--- |
| **** <br>Listas de padrões que contêm campos de formulário são mescladas ou não convertidas em componentes de formulário adaptáveis correspondentes  <br><br>**** <br>ResoluçãoUse campos de formulários com limites claros ou use o editor de Revisar e corrigir para corrigir esses problemas. | ![listas contendo grupos de escolha](assets/best-practice-lists-containing-form-fields.png) |
| **** <br>O Serviço de padrões pode deixar algumas listas aninhadas  <br><br>**** <br> com resolução não identificada. Use o editor de revisão e correção para corrigir esses problemas. | ![listas contendo grupos de escolha](assets/best-practice-nested-lists.png) |
| **** <br> O PatternService mescla algumas listas contendo grupos de opções entre si  <br><br>**** <br> SoluçãoUse Revisar e Corrigir editor para corrigir esses problemas. | ![listas contendo grupos de escolha](assets/best-practice-check-box-in-table-cells.png) |

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
