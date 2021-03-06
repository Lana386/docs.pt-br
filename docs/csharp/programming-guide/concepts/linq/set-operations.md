---
title: Operações de conjunto (C#)
ms.date: 07/20/2015
ms.assetid: 7c589367-ef8f-4161-9050-642c47e6bf63
ms.openlocfilehash: 44a145a625b5e2e16d2469b20f8cfda1858560a2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167927"
---
# <a name="set-operations-c"></a>Operações de conjunto (C#)
As operações de conjunto na LINQ referem-se a operações de consulta que geram um conjunto de resultados baseado na presença ou ausência de elementos equivalentes dentro da mesma ou de coleções (ou conjuntos) separadas.  
  
 Os métodos de operador de consulta padrão que executam operações de conjunto estão listados na seção a seguir.  
  
## <a name="methods"></a>Métodos  
  
|Nome do método|Descrição|Sintaxe de expressão de consulta C#|Mais informações|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Distinct|Remove os valores duplicados de uma coleção.|Não aplicável.|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|  
|Except|Retorna a diferença de conjunto, que significa os elementos de uma coleção que não aparecem em uma segunda coleção.|Não aplicável.|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|  
|Intersect|Retorna a interseção de conjunto, o que significa os elementos que aparecem em cada uma das duas coleções.|Não aplicável.|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|  
|Union|Retorna a união de conjunto, o que significa os elementos únicos que aparecem em qualquer uma das duas coleções.|Não aplicável.|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|  
  
## <a name="comparison-of-set-operations"></a>Comparação de operações de conjuntos  
  
### <a name="distinct"></a>Distinct  
 O exemplo a seguir mostra <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> o comportamento do método em uma seqüência de caracteres. A sequência retornada contém os elementos exclusivos da sequência de entrada.  
  
 ![Gráfico mostrando o comportamento de Distinct&#40;&#41;.](./media/set-operations/distinct-method-behavior.png)  

 [!code-csharp-interactive[Distinct](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#1)]
  
### <a name="except"></a>Except  
 O exemplo a seguir <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>mostra o comportamento de . A sequência retornada contém apenas os elementos da primeira sequência de entrada que não estão na segunda sequência de entrada.  
  
 ![Gráfico mostrando a ação de Except&#40;&#41;.](./media/set-operations/except-behavior-graphic.png "Mostra o comportamento da Except.")  
  
[!code-csharp-interactive[Except](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#2)]

### <a name="intersect"></a>Intersect  
 O exemplo a seguir <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>mostra o comportamento de . A sequência retornada contém os elementos que são comuns a ambas as sequências de entrada.  
  
 ![Gráfico mostrando a interseção de duas sequências.](./media/set-operations/intersection-two-sequences.png)  

[!code-csharp-interactive[Intersect](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#3)]

### <a name="union"></a>Union  
 O exemplo a seguir mostra uma operação sindical em duas sequências de caracteres. A sequência retornada contém os elementos exclusivos das duas sequências de entrada.  
  
 ![Gráfico mostrando a união de duas sequências.](./media/set-operations/union-operation-two-sequences.png)  

[!code-csharp-interactive[Union](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#4)]

## <a name="see-also"></a>Confira também

- <xref:System.Linq>
- [Visão geral de operadores de consulta padrão (C#)](./standard-query-operators-overview.md)
- [Como combinar e comparar coleções de strings (LINQ) (C#)](./how-to-combine-and-compare-string-collections-linq.md)
- [Como encontrar a diferença de conjunto entre duas listas (LINQ) (C#)](./how-to-find-the-set-difference-between-two-lists-linq.md)
