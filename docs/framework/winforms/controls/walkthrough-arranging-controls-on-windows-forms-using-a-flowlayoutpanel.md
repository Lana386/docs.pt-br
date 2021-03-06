---
title: Organizar controles usando o FlowLayoutPanel
ms.date: 03/30/2017
helpviewer_keywords:
- FlowLayoutPanel control [Windows Forms], walkthroughs
- Windows Forms controls, arranging
- controls [Windows Forms], arranging with FlowLayoutPanel
- layout [Windows Forms], walkthroughs
ms.assetid: a1744323-0316-49c2-992e-ebfc0a976b85
ms.openlocfilehash: 6df0a910ee346f319fbee835e5e632808630a99e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745407"
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel"></a>Explicação passo a passo: organizando controles no Windows Forms utilizando um FlowLayoutPanel

Alguns aplicativos exigem um formulário com um layout que se organiza adequadamente à medida que o formulário é redimensionado ou conforme o tamanho do conteúdo é alterado. Quando você precisar de um layout dinâmico e não quiser manipular <xref:System.Windows.Forms.Control.Layout> eventos explicitamente em seu código, considere o uso de um painel de layout.

O controle de <xref:System.Windows.Forms.FlowLayoutPanel> e o controle de <xref:System.Windows.Forms.TableLayoutPanel> fornecem maneiras intuitivas de organizar controles em seu formulário. Ambos fornecem uma capacidade automática e configurável de controlar as posições relativas dos controles filho contidos neles e ambos oferecem recursos de layout dinâmico em tempo de execução, para que eles possam redimensionar e reposicionar os controles filho conforme as dimensões do formulário pai se alteram. Os painéis de layout podem ser aninhados em painéis de layout, para permitir a realização de interfaces do usuário sofisticadas.

O <xref:System.Windows.Forms.TableLayoutPanel> organiza seu conteúdo em uma grade, fornecendo uma funcionalidade semelhante ao elemento HTML \<tabela >. Suas células são organizadas em linhas e colunas, que podem ter diferentes tamanhos. Para obter mais informações, consulte [Passo a passo: organizando controles nos Windows Forms usando um TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).

O <xref:System.Windows.Forms.FlowLayoutPanel> organiza seu conteúdo em uma direção de fluxo específica: horizontal ou vertical. Seu conteúdo pode ser encapsulado de uma linha à outra ou de uma coluna à próxima. Como alternativa, seu conteúdo pode ser recortado, em vez de encapsulado. As tarefas ilustradas neste passo a passo incluem:

- Criação de um projeto dos Windows Forms

- Organizando controles horizontalmente e verticalmente

- Alterando a direção do fluxo

- Inserindo quebras de fluxo

- Organizando controles usando preenchimento e margens

- Inserindo controles ao clicar duas vezes neles na caixa de ferramentas

- Inserindo um controle ao desenhar seu contorno

- Inserindo controles usando o sinal de interpolação

- Reatribuição de controles existentes a um pai diferente

Quando terminar, você terá uma compreensão da função desempenhada por esses recursos de layout importantes.

## <a name="create-the-project"></a>Criar o projeto

1. No Visual Studio, crie um projeto de aplicativo baseado no Windows chamado "FlowLayoutPanelExample" **(arquivo** > **novo** > **projeto** > **Visual C#**  ou **Visual Basic** > área de **trabalho clássica** > Windows Forms **aplicativo**).

2. Selecione o formulário no **Designer de Formulários**.

## <a name="arranging-controls-horizontally-and-vertically"></a>Organizando controles horizontalmente e verticalmente
 O controle <xref:System.Windows.Forms.FlowLayoutPanel> permite colocar controles em linhas ou colunas sem exigir que você especifique precisamente a posição de cada controle individual.

 O controle de <xref:System.Windows.Forms.FlowLayoutPanel> pode redimensionar ou refluir seus controles filho à medida que as dimensões do formulário pai são alteradas.

### <a name="to-arrange-controls-horizontally-and-vertically-using-a-flowlayoutpanel"></a>Para organizar controles horizontalmente e verticalmente usando um FlowLayoutPanel

1. Arraste um controle de <xref:System.Windows.Forms.FlowLayoutPanel> da **caixa de ferramentas** para seu formulário.

2. Arraste um controle de <xref:System.Windows.Forms.Button> da **caixa de ferramentas** para a <xref:System.Windows.Forms.FlowLayoutPanel>. Observe que ele é movido automaticamente para o canto superior esquerdo do controle de <xref:System.Windows.Forms.FlowLayoutPanel>.

3. Arraste outro controle de <xref:System.Windows.Forms.Button> da **caixa de ferramentas** para a <xref:System.Windows.Forms.FlowLayoutPanel>. Observe que o controle de <xref:System.Windows.Forms.Button> é movido automaticamente para uma posição ao lado do primeiro controle de <xref:System.Windows.Forms.Button>. Se o <xref:System.Windows.Forms.FlowLayoutPanel> for muito estreito para ajustar os dois controles na mesma linha, o novo controle de <xref:System.Windows.Forms.Button> será automaticamente movido para a próxima linha.

4. Arraste vários controles mais <xref:System.Windows.Forms.Button> da **caixa de ferramentas** para a <xref:System.Windows.Forms.FlowLayoutPanel>. Continue colocando os controles de <xref:System.Windows.Forms.Button> até que um passe para a próxima linha.

5. Altere o valor da propriedade <xref:System.Windows.Forms.FlowLayoutPanel> do controle <xref:System.Windows.Forms.FlowLayoutPanel.WrapContents%2A> para `false`. Observe que os controles filho não fluem mais para a próxima linha. Em vez disso, eles são movidos para a primeira linha e recortados.

6. Altere o valor da propriedade <xref:System.Windows.Forms.FlowLayoutPanel> do controle <xref:System.Windows.Forms.FlowLayoutPanel.WrapContents%2A> para `true`. Observe que os controles filho quebram novamente para a próxima linha.

7. Diminua a largura do controle de <xref:System.Windows.Forms.FlowLayoutPanel> até que todos os controles de <xref:System.Windows.Forms.Button> sejam movidos para a primeira coluna.

8. Aumente a largura do controle de <xref:System.Windows.Forms.FlowLayoutPanel> até que todos os controles de <xref:System.Windows.Forms.Button> sejam movidos para a primeira linha. Você pode precisar redimensionar o formulário para acomodar a largura maior.

## <a name="changing-flow-direction"></a>Alterando a direção do fluxo
 A propriedade <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> permite que você altere a direção na qual os controles são organizados. Você pode organizar os controles filho da esquerda para a direita, da direita para a esquerda, de cima para baixo ou de baixo para cima.

### <a name="to-change-the-flow-direction-in-a-flowlayoutpanel"></a>Para alterar a direção do fluxo em um FlowLayoutPanel

1. Altere o valor da propriedade <xref:System.Windows.Forms.FlowLayoutPanel> do controle <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> para <xref:System.Windows.Forms.FlowDirection.TopDown>. Observe que os controles filho são reorganizados em uma ou mais colunas, dependendo da altura do controle.

2. Redimensione o <xref:System.Windows.Forms.FlowLayoutPanel> para que sua altura seja menor que a coluna de controles de <xref:System.Windows.Forms.Button>. Observe que o <xref:System.Windows.Forms.FlowLayoutPanel> reorganiza os controles filho para fluir para a próxima coluna. Continue a diminuir a altura e observe que os controles filho fluem para colunas consecutivas. Altere o valor da propriedade <xref:System.Windows.Forms.FlowLayoutPanel> do controle <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> para <xref:System.Windows.Forms.FlowDirection.RightToLeft>. Observe que as posições dos controles filho são revertidas. Observe o layout quando você altera o valor da propriedade <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> para <xref:System.Windows.Forms.FlowDirection.BottomUp>.

## <a name="inserting-flow-breaks"></a>Inserindo quebras de fluxo
 O controle <xref:System.Windows.Forms.FlowLayoutPanel> fornece uma propriedade FlowBreak para seus controles filho. Definir o valor da propriedade FlowBreak como `true` faz com que o controle de <xref:System.Windows.Forms.FlowLayoutPanel> pare de dispor os controles na direção do fluxo atual e seja quebrado para a próxima linha ou coluna.

### <a name="to-insert-flow-breaks"></a>Para inserir quebras de fluxo

1. Altere o valor da propriedade <xref:System.Windows.Forms.FlowLayoutPanel> do controle <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> para <xref:System.Windows.Forms.FlowDirection.TopDown>.

2. Selecione um dos controles de <xref:System.Windows.Forms.Button> no meio da coluna mais à esquerda.

3. Defina o valor da propriedade FlowBreak do controle de <xref:System.Windows.Forms.Button> como `true`. Observe que a coluna está quebrada e os controles que seguem o fluxo de controle de <xref:System.Windows.Forms.Button> selecionado para a próxima coluna. Defina o valor da propriedade FlowBreak do controle de <xref:System.Windows.Forms.Button> como `false` para retornar ao comportamento original.

## <a name="positioning-controls-using-docking-and-anchoring"></a>Posicionando controles usando encaixe e ancoragem
 Os comportamentos de encaixe e ancoragem dos controles filho diferem dos comportamentos em outras caixas de controles. O encaixe e a ancoragem são relativos ao maior controle na direção do fluxo.

### <a name="to-position-controls-using-docking-and-anchoring"></a>Para posicionar controles usando encaixe e ancoragem

1. Aumente o tamanho do <xref:System.Windows.Forms.FlowLayoutPanel> até que os controles de <xref:System.Windows.Forms.Button> sejam todos organizados em uma coluna.

2. Selecione o controle de <xref:System.Windows.Forms.Button> superior. Aumente sua largura para que seja aproximadamente duas vezes mais largas que os outros controles de <xref:System.Windows.Forms.Button>.

3. Selecione o segundo controle de <xref:System.Windows.Forms.Button>. Altere o valor de sua propriedade <xref:System.Windows.Forms.Control.Anchor%2A> para <xref:System.Windows.Forms.AnchorStyles.Right>. Observe que ele é movido de forma que sua borda direita seja alinhada com a primeira borda direita do controle de <xref:System.Windows.Forms.Button>.

4. Altere o valor de sua propriedade <xref:System.Windows.Forms.Control.Anchor%2A> para <xref:System.Windows.Forms.AnchorStyles.Right> e <xref:System.Windows.Forms.AnchorStyles.Left>. Observe que ele é dimensionado para a mesma largura que o primeiro controle de <xref:System.Windows.Forms.Button>.

5. Selecione o terceiro controle de <xref:System.Windows.Forms.Button>. Altere o valor de sua propriedade <xref:System.Windows.Forms.Control.Dock%2A> para <xref:System.Windows.Forms.DockStyle.Fill>. Observe que ele é dimensionado para a mesma largura que o primeiro controle de <xref:System.Windows.Forms.Button>.

## <a name="arranging-controls-using-padding-and-margins"></a>Organizando controles usando preenchimento e margens
 Você também pode organizar controles em seu controle de <xref:System.Windows.Forms.FlowLayoutPanel> alterando as propriedades <xref:System.Windows.Forms.Control.Padding%2A> e <xref:System.Windows.Forms.Control.Margin%2A>.

 A propriedade <xref:System.Windows.Forms.Control.Padding%2A> permite controlar o posicionamento de controles dentro de uma célula de controle de <xref:System.Windows.Forms.FlowLayoutPanel>. Especifica o espaçamento entre os controles filho e a borda do controle de <xref:System.Windows.Forms.FlowLayoutPanel>.

 A propriedade <xref:System.Windows.Forms.Control.Margin%2A> permite controlar o espaçamento entre os controles.

### <a name="to-arrange-controls-using-the-padding-and-margin-properties"></a>Para organizar controles usando as propriedades de preenchimento e margem

1. Altere o valor da propriedade <xref:System.Windows.Forms.FlowLayoutPanel> do controle <xref:System.Windows.Forms.Control.Dock%2A> para <xref:System.Windows.Forms.DockStyle.Fill>. Se o formulário for grande o suficiente, os controles de <xref:System.Windows.Forms.Button> serão movidos para a primeira coluna do controle de <xref:System.Windows.Forms.FlowLayoutPanel>.

2. Altere o valor da propriedade <xref:System.Windows.Forms.Control.Padding%2A> do controle de <xref:System.Windows.Forms.FlowLayoutPanel> expandindo a entrada <xref:System.Windows.Forms.Control.Padding%2A> na janela **Propriedades** e definindo a propriedade <xref:System.Windows.Forms.Padding.All%2A> como **20**. Para obter mais informações, consulte [Passo a passo: definindo o layout de controles dos Windows Forms com preenchimento, margens e a propriedade AutoSize](windows-forms-controls-padding-autosize.md). Observe que os controles filho são movidos para o centro do controle de <xref:System.Windows.Forms.FlowLayoutPanel>. O maior valor para a propriedade <xref:System.Windows.Forms.Control.Padding%2A> empurra os controles filho para longe das bordas do controle de <xref:System.Windows.Forms.FlowLayoutPanel>.

3. Selecione todos os controles de <xref:System.Windows.Forms.Button> na <xref:System.Windows.Forms.FlowLayoutPanel> e defina o valor da propriedade <xref:System.Windows.Forms.Control.Margin%2A> como **20**. Observe que o espaçamento entre os controles de <xref:System.Windows.Forms.Button> aumenta, para que eles sejam mais bem movidos. Talvez seja necessário redimensionar o controle de <xref:System.Windows.Forms.FlowLayoutPanel> para que seja maior para ver todos os controles filho.

## <a name="inserting-controls-by-double-clicking-them-in-the-toolbox"></a>Inserindo controles ao clicar duas vezes neles na caixa de ferramentas
 Você pode preencher o controle de <xref:System.Windows.Forms.FlowLayoutPanel> clicando duas vezes em controles na **caixa de ferramentas**.

### <a name="to-insert-controls-by-double-clicking-in-the-toolbox"></a>Para inserir controles clicando duas vezes na caixa de ferramentas

1. Clique duas vezes no ícone de controle de <xref:System.Windows.Forms.Button> na **caixa de ferramentas**. Observe que um novo controle de <xref:System.Windows.Forms.Button> aparece no controle de <xref:System.Windows.Forms.FlowLayoutPanel>.

2. Clique duas vezes em vários outros controles na **Caixa de ferramentas**. Observe que os novos controles aparecem sucessivamente no controle de <xref:System.Windows.Forms.FlowLayoutPanel>.

## <a name="inserting-a-control-by-drawing-its-outline"></a>Inserindo um controle ao desenhar seu contorno
 Você pode inserir um controle em um controle de <xref:System.Windows.Forms.FlowLayoutPanel> e especificar seu tamanho, desenhando seu contorno em uma célula.

### <a name="to-insert-a-control-by-drawing-its-outline"></a>Para inserir um controle desenhando seu contorno

1. Na **caixa de ferramentas**, clique no ícone controle de <xref:System.Windows.Forms.Button>. Não o arraste para o formulário.

2. Mova o ponteiro do mouse sobre o controle de <xref:System.Windows.Forms.FlowLayoutPanel>. Observe que o ponteiro muda para um cruz com o ícone de controle de <xref:System.Windows.Forms.Button> anexado.

3. Clique e mantenha o botão do mouse pressionado.

4. Arraste o ponteiro do mouse para desenhar a estrutura de tópicos do controle de <xref:System.Windows.Forms.Button>. Quando estiver satisfeito com o tamanho, solte o botão do mouse. Observe que o controle de <xref:System.Windows.Forms.Button> é criado no próximo local aberto do controle de <xref:System.Windows.Forms.FlowLayoutPanel>.

## <a name="inserting-controls-using-the-insertion-bar"></a>Inserindo controles usando a barra de inserção
 Você pode inserir controles em uma posição específica em um controle de <xref:System.Windows.Forms.FlowLayoutPanel>. Quando você arrasta um controle para a área do cliente do controle de <xref:System.Windows.Forms.FlowLayoutPanel>, uma barra de inserção é exibida para indicar onde o controle será inserido.

### <a name="to-insert-a-control-using-the-caret"></a>Para inserir um controle usando o sinal de interpolação

1. Arraste um controle de <xref:System.Windows.Forms.Button> da **caixa de ferramentas** para o controle de <xref:System.Windows.Forms.FlowLayoutPanel> e aponte para o espaço entre dois controles de <xref:System.Windows.Forms.Button>. Observe que uma barra de inserção é desenhada, indicando onde o <xref:System.Windows.Forms.Button> será colocado quando for descartado para o controle de <xref:System.Windows.Forms.FlowLayoutPanel>. Antes de descartar o novo controle de <xref:System.Windows.Forms.Button> no controle de <xref:System.Windows.Forms.FlowLayoutPanel>, mova o ponteiro do mouse para observar como a barra de inserção se move.

2. Descarte o novo controle de <xref:System.Windows.Forms.Button> no controle de <xref:System.Windows.Forms.FlowLayoutPanel>. Observe que o novo controle de <xref:System.Windows.Forms.Button> não está alinhado com os outros, porque sua propriedade <xref:System.Windows.Forms.Control.Margin%2A> tem um valor diferente.

## <a name="reassigning-existing-controls-to-a-different-parent"></a>Reatribuição de controles existentes a um pai diferente
 Você pode atribuir controles que existem no formulário a um novo controle de <xref:System.Windows.Forms.FlowLayoutPanel>.

### <a name="to-reparent-existing-controls"></a>Para reassociar os controles existentes

1. Arraste três controles de <xref:System.Windows.Forms.Button> da **caixa de ferramentas** para o formulário. Posicione-os próximo entre si, mas deixe-os desalinhados.

2. Na **caixa de ferramentas**, clique no ícone controle de <xref:System.Windows.Forms.FlowLayoutPanel>. Não o arraste para o formulário.

3. Mova o ponteiro do mouse para perto dos três <xref:System.Windows.Forms.Button> controles. Observe que o ponteiro muda para um cruz com o ícone de controle de <xref:System.Windows.Forms.FlowLayoutPanel> anexado.

4. Clique e mantenha o botão do mouse pressionado.

5. Arraste o ponteiro do mouse para desenhar a estrutura de tópicos do controle de <xref:System.Windows.Forms.FlowLayoutPanel>. Desenhe a estrutura de tópicos em torno dos três controles de <xref:System.Windows.Forms.Button>.

6. Solte o botão do mouse. Observe que os três controles de <xref:System.Windows.Forms.Button> são inseridos no controle de <xref:System.Windows.Forms.FlowLayoutPanel>.

## <a name="next-steps"></a>{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}
 Você pode obter um layout complexo usando uma combinação de controles e painéis de layout. Sugestões para exploração adicional incluem:

- Redimensione um dos controles de <xref:System.Windows.Forms.Button> para um tamanho maior e observe o efeito no layout.

- Os painéis de layout podem conter outros painéis de layout. Experimente soltar um controle de <xref:System.Windows.Forms.TableLayoutPanel> no controle existente.

- Encaixe o controle de <xref:System.Windows.Forms.FlowLayoutPanel> no formulário pai. Redimensione o formulário e observe o efeito no layout.

- Defina a propriedade <xref:System.Windows.Forms.Control.Visible%2A> de um dos controles como `false` e observe como o <xref:System.Windows.Forms.FlowLayoutPanel> reflui em resposta.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [Passo a passo: organizando controles nos Windows Forms usando um TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Passo a passo: organizando controles nos Windows Forms usando linhas de alinhamento](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [Visão geral da propriedade AutoSize](autosize-property-overview.md)
- [Como encaixar controles nos Windows Forms](how-to-dock-controls-on-windows-forms.md)
- [Como ancorar controles nos Windows Forms](how-to-anchor-controls-on-windows-forms.md)
- [Instruções passo a passo: projetando controles do Windows Forms com preenchimento, margens e a propriedade AutoSize](windows-forms-controls-padding-autosize.md)
