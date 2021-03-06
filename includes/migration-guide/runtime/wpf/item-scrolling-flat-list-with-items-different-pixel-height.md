---
ms.openlocfilehash: 3a82822aae281ea7e873ba649f05b1d68686ec69
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "70997542"
---
### <a name="item-scrolling-a-flat-list-with-items-of-different-pixel-height"></a>Rolagem de itens em uma lista simples de itens com diferentes alturas em pixels

|   |   |
|---|---|
|Detalhes|Quando um <xref:System.Windows.Controls.ItemsControl?displayProperty=name> exibe uma coleção usando virtualização (<code>IsVirtualizing=true</code>) e rolagem de itens (<code>ScrollUnit=Item</code>) e quando o controle rola para exibir um item cuja altura em pixels é diferente de seus vizinhos, o <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=name> itera em todos os itens na coleção. A ui não responde durante esta iteração; se a coleção é grande, isso pode ser percebido como um enforcamento. A iteração ocorre em outras circunstâncias, mesmo em versões anteriores do .NET Framework. Por exemplo, isso ocorre na rolagem de pixels (<code>ScrollUnit=Pixel</code>) ao encontrar um item com uma altura de pixels diferente e na rolagem de itens de dados hierárquicos (como em um <xref:System.Windows.Controls.TreeView?displayProperty=name> ou um <xref:System.Windows.Controls.ItemsControl?displayProperty=name> com o agrupamento habilitado) ao encontrar um item com um número de itens descendentes diferentes de seus vizinhos. Para o caso em que há rolagem de itens e diferentes alturas em pixels, a iteração foi introduzida no .NET Framework 4.6.1 para corrigir bugs no layout de dados hierárquicos.  Ela não será necessária se os dados forem simples (sem hierarquia) e, nesse caso, ela não ocorre no .NET Framework 4.6.2.|
|Sugestão|Se a iteração ocorrer no .NET Framework 4.6.1, mas não nas versões anteriores, ou seja, se o <xref:System.Windows.Controls.ItemsControl?displayProperty=name> for uma lista plana de rolagem de item com itens de alturas em pixels diferentes, haverá duas soluções:<ol><li>Instalar o .NET Framework 4.6.2.</li><li>Instalar o hotfix HR 1605 para o .NET Framework 4.6.1.</li></ol>|
|Escopo|Secundária|
|Versão|4.6.1|
|Type|Runtime|
|APIs afetadas|<ul><li><xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=nameWithType></li></ul>|
