---
ms.openlocfilehash: 6c1740df66ead271afa5f97dc125587810946bc6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "66379650"
---
### <a name="flowdocument-may-show-an-extra-line-of-text"></a>FlowDocument pode mostrar uma linha extra de texto

|   |   |
|---|---|
|Detalhes|Em alguns casos, um elemento <xref:System.Windows.Documents.FlowDocument> exibirá uma linha de texto extra ao ser executado no .NET Framework 4.5, em comparação a como ele foi exibido quando executado no .NET Framework 4.0. Não conhecemos casos em que a alteração fez com que qualquer texto fosse exibido de forma inadequada ou ilegível, mas textos omitidos de uma exibição de <xref:System.Windows.Documents.FlowDocument> podem aparecer.|
|Sugestão|Em alguns casos, diminuir a propriedade PageHeight do elemento de exibição em 1 pode restaurar o número anterior de linhas exibidas.|
|Escopo|Microsoft Edge|
|Versão|4.5|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Windows.Documents.FlowDocument.%23ctor?displayProperty=nameWithType></li><li><xref:System.Windows.Documents.FlowDocument.%23ctor(System.Windows.Documents.Block)?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.FlowDocumentReader.%23ctor?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.FlowDocumentPageViewer.%23ctor?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.Primitives.DocumentPageView.%23ctor?displayProperty=nameWithType></li></ul>|
