---
title: Problemas conhecidos
seo-title: Known Issues
description: problemas conhecidos e limitações do Automated forms conversion Service
seo-description: Before you begin using AEM Forms Automated Forms Conversion service, learn about the known issues and limitations of the service
uuid: b1dc661b-ccd3-457f-acbb-4bd25db86e1e
topic-tags: introduction
discoiquuid: 9cd2363c-47a0-46e9-98cd-1fe088b9cd6e
exl-id: 35f59e02-e38e-473a-94c8-123e0a85ac8e
source-git-commit: 47261710e6616c27c210ac53bffcc2387a06ea7a
workflow-type: tm+mt
source-wordcount: '794'
ht-degree: 1%

---

# Problemas conhecidos e limitações {#known-issues-limitations}

Antes de começar a usar o serviço AEM Forms Automated forms conversion, analise os seguintes problemas conhecidos e limitações:

## Problemas conhecidos {#known-issues}

* A pasta que contém formulários para conversão não deve ter mais de 15 formulários e 50 páginas no total. O tamanho da pasta de origem não deve exceder 10 MB. Não crie subpastas na pasta de origem.
* Alguns objetos de formulário são facilmente visíveis no olho humano, mas são [difíceis de identificar para o serviço](styles-and-pattern-considerations-and-best-practices.md). Use [Revisar e corrigir o editor](review-correct-ui-edited.md) para identificar e converter esses objetos de formulário.
* Editor de revisão e correção:

   * Não tem ação de desfazer. O botão Salvar salva as alterações permanentemente.
   * Não suporta painéis repetíveis para formulários baseados em XFA.
   * Se você modificar uma lista em uma tabela usando o editor Revisar e corrigir, a largura da linha não se ajusta automaticamente e o texto pode se estender até a próxima linha da tabela.
   * O recurso **[!UICONTROL Auto-detect multi-column layout from input forms]** não funciona com o editor Revisar e corrigir e Fragmentos de formulário.
   * A assinatura do Scribble criada com o editor de Revisar e corrigir falha ao carregar para formulários adaptáveis publicados.


* Para formulários baseados em XFA:
   * A extração de fragmentos de um formulário baseado em XFA não é suportada.
   * Não há suporte para scripts XFA. Por exemplo, scripts para gerar valores automaticamente para um componente suspenso.
   * O metamodelo não funciona para o grupo de opções
   * A opção Grupos de opções com um único caractere não é identificada
   * Quando o documento de origem é um XFA dinâmico (.XDP) e [define o comportamento das propriedades do XFA em um formulário adaptável](https://helpx.adobe.com/experience-manager/6-5/forms/using/xfa-api-supported-in-adaptive-form.html#supportedxfaelementsandtheirmappinginadaptiveformsbr), a propriedade presence do documento de origem não é respeitada. Por exemplo, um campo no documento de origem é marcado como oculto e um script torna o campo visível, então o campo permanece visível no formulário adaptável de saída.

* Quando você usa a opção **Use input AcroForm como Document of Record (DoR) para formulários adaptáveis gerados**, considere o seguinte:

<table>
    <tr>
        <td>O vínculo e os dados são perdidos para campos de texto composto. Um campo de texto composto tem várias caixas de texto alinhadas entre si. Por exemplo, em um AcroForm, um número de cartão de crédito é dividido em várias caixas de texto e cada caixa de texto tem um vínculo separado. Quando o AcroForm é convertido em formulário adaptável, o formulário adaptável convertido tem um único vínculo para todas as caixas de texto. Como solução, antes de converter um AcroForm em formulário adaptável, modifique o AcroForm para usar uma única caixa de texto para aceitar números de cartão de crédito.</td>
        <td><img  src="assets/creditCard_Composite.png"/>                                                            </td>
    </tr>
    <tr>
        <td>O vínculo e os dados são perdidos para campos de data compostos. Um campo de data composto é composto por três campos diferentes. Por exemplo, um campo de data de nascimento em um AcroForm é dividido em três campos separados. O formulário adaptável fornece um componente seletor de datas pronto para uso. Para usar o componente seletor de datas do formulário adaptável enquanto mantém o vínculo do AcroForm, antes de converter um AcroForm em um formulário adaptável, modifique o AcroForm para usar um campo de data único.</td>
        <td><img  src="assets/CompositeDateField.png"/></td>
    </tr>
    <tr>
        <td>Se o tamanho das caixas de seleção for maior que o texto que o acompanha, então as caixas de seleção não são detectadas e o vínculo no AcroForm é perdido. Modifique o AcroForm para tornar o tamanho das caixas de seleção menor que o texto que o acompanha.</td>
        <td><img  src="assets/large-text-box.png"/><br/><img  src="assets/small-text-box.png"/></td>
    </tr>
    <tr>
        <td>Se os campos de entrada não estiverem alinhados ao campo de texto correspondente, o campo de entrada não será detectado.  </td>
        <td><img  src="assets/non-alingned-fields.png"/></td>
    </tr>
    <tr >
        <td>O serviço converte todas as caixas de seleção de um AcroForm em grupos de escolha separados. Grupos de opções separados são criados para preservar vínculos com o AcroForm. Não mescle grupos de opções no formulário adaptável. Isso levará à perda de vínculos. Se você unir os grupos de opções, converta o formulário novamente para recuperar os vínculos perdidos. </td>
        <td></td>
    </tr>
    <tr >
        <td>Os limites de algumas tabelas são estendidos para fora da página no documento de registro gerado automaticamente (DoR). </td>
        <td></td>
    </tr>
</table>

## Limitações           {#limitations}

* Não há suporte para PDF forms com layout dinâmico complexo, campos com contorno pontilhado ou campos preenchidos.
* Imagens e texto dentro das imagens não são identificados. Adicionar manualmente imagens a formulários convertidos.
* Documentos XDP de arte não são suportados.
* PDF forms maiores que 15 páginas não são compatíveis.
* Documentos criptografados, protegidos por senha e protegidos não são convertidos. Remova a criptografia ou as senhas antes de executar a conversão.
* Tabelas complexas como tabelas sem bordas, tabelas aninhadas e tabelas com valores de espaço reservado não são suportadas. Use o editor de formulário adaptável para adicionar ou modificar tabelas complexas, após a conversão. Somente tabelas simples, com campos vazios, cabeçalhos adequados e limites de limpeza são compatíveis.
* O serviço converte somente formulários em inglês, francês, alemão, espanhol, italiano e português em formulários adaptáveis. Você pode traduzir formulários adaptáveis convertidos para outro idioma usando [AEM fluxo de trabalho de tradução](https://helpx.adobe.com/br/experience-manager/6-5/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.html).
* AEM 6.4 O Forms não oferece suporte à detecção automática do layout de várias colunas de formulários de entrada.
* As informações codificadas com cores no formulário PDF de origem não são transferidas para o formulário adaptável.
* As cores do formulário PDF de origem não são transferidas para temas de formulário adaptável.
* Os PDF forms coloridos são tratados como formulários em tons de cinza e os campos são detectados adequadamente.
