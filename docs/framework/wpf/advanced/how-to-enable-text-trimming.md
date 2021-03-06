---
title: 'Como: Habilitar filtragem de texto'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [WPF], trimming
- documents [WPF], trimming text
- trimming text [WPF]
ms.assetid: dd8c9191-d2be-45fd-9fb4-3c75b65578c5
ms.openlocfilehash: 25fff566868e792004a915fee195485c4a1f385f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61776087"
---
# <a name="how-to-enable-text-trimming"></a>Como: Habilitar filtragem de texto

Este exemplo demonstra o uso e efeitos dos valores disponíveis no <xref:System.Windows.TextTrimming> enumeração.

## <a name="example"></a>Exemplo

O exemplo a seguir define uma <xref:System.Windows.Controls.TextBlock> elemento com o <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> conjunto de atributos.

[!code-xaml[TextTrimmingSnippets#_TextTrimmingXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTrimmingSnippets/CSharp/Window1.xaml#_texttrimmingxaml)]

Configuração correspondente <xref:System.Windows.TextTrimming> propriedade no código é demonstrada abaixo.

[!code-csharp[TextTrimmingSnippets#_TextTrimmingSetTextTrimming](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTrimmingSnippets/CSharp/Window1.xaml.cs#_texttrimmingsettexttrimming)]
[!code-vb[TextTrimmingSnippets#_TextTrimmingSetTextTrimming](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextTrimmingSnippets/VisualBasic/Window1.xaml.vb#_texttrimmingsettexttrimming)]

Existem atualmente três opções para cortar texto: **CharacterEllipsis**, **WordEllipsis**, e **None**.

Quando <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> é definido como **CharacterEllipsis**, texto é cortado e continuado com uma elipse no caractere mais próximo à borda de corte.  Essa configuração tende a cortar o texto para se ajustar mais bem ao limite de corte, mas pode resultar em palavras parcialmente cortadas.  A figura a seguir mostra o efeito dessa configuração em um <xref:System.Windows.Controls.TextBlock> semelhante àquele definido acima.

![Exemplo: TextTrimming.CharacterEllipsis](./media/texttrimming-character.png "TextTrimming_Character")

Quando <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> é definido como **WordEllipsis**, texto é cortado e continuado com uma elipse no final da primeira palavra completa mais próxima à borda de corte.  Essa configuração não mostrará palavras parcialmente cortadas, mas tende a não cortar o texto tão próximo à borda de corte quanto o **CharacterEllipsis** configuração.  A figura a seguir mostra o efeito dessa configuração no <xref:System.Windows.Controls.TextBlock> definido acima.

![Exemplo: TextTrimming.WordEllipsis](./media/texttrimming-word.png "TextTrimming_Word")

Quando <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> é definido como **None**, nenhuma quebra de texto é realizada.  Nesse caso, o texto é simplesmente recortado para o limite do contêiner de texto pai.  A figura a seguir mostra o efeito dessa configuração em um <xref:System.Windows.Controls.TextBlock> semelhante àquele definido acima.

![Exemplo: TextTrimming.None](./media/texttrimming-none.png "TextTrimming_None")
