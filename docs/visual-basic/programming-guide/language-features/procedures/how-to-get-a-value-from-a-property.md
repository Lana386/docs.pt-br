---
title: Como obter um valor a partir de uma propriedade
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: 3954423e-6ab7-4a4c-b55c-a8d27be47891
ms.openlocfilehash: 85512d4311d3e731a2c4e129d6a01f9b3273b333
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74339823"
---
# <a name="how-to-get-a-value-from-a-property-visual-basic"></a>Como obter um valor a partir de uma propriedade (Visual Basic)
Você recupera o valor de uma propriedade, incluindo o nome da propriedade em uma expressão.  
  
 O procedimento de `Get` da propriedade recupera o valor, mas você não o chama explicitamente por nome. Você usa a propriedade da mesma forma como usaria uma variável. Visual Basic faz as chamadas para os procedimentos da propriedade.  
  
### <a name="to-retrieve-a-value-from-a-property"></a>Para recuperar um valor de uma propriedade  
  
1. Use o nome da propriedade em uma expressão da mesma maneira que usaria um nome de variável. Você pode usar uma propriedade em qualquer lugar em que possa usar uma variável ou uma constante.  
  
     - ou -  
  
     Use o nome da propriedade após o sinal de igual (`=`) em uma instrução de atribuição.  
  
     O exemplo a seguir lê o valor da Propriedade Visual Basic `Now`, chamando implicitamente seu procedimento de `Get`.  
  
     [!code-vb[VbVbalrDateProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDateProperties/VB/Module1.vb#4)]  
  
2. Se a propriedade usar argumentos, siga o nome da propriedade com parênteses para colocar a lista de argumentos. Se não houver argumentos, você pode opcionalmente omitir os parênteses.  
  
3. Coloque os argumentos na lista de argumentos dentro dos parênteses, separados por vírgulas. Certifique-se de fornecer os argumentos na mesma ordem em que a propriedade define os parâmetros correspondentes.  
  
 O valor da propriedade participa da expressão, assim como uma variável ou constante, ou é armazenado na variável ou propriedade no lado esquerdo da instrução de atribuição.  
  
## <a name="see-also"></a>Consulte também

- [Procedimentos](./index.md)
- [Procedimentos de Propriedade](./property-procedures.md)
- [Parâmetros e Argumentos de Procedimento](./procedure-parameters-and-arguments.md)
- [Instrução Property](../../../../visual-basic/language-reference/statements/property-statement.md)
- [Diferenças entre propriedades e variáveis no Visual Basic](./differences-between-properties-and-variables.md)
- [Como criar uma propriedade](./how-to-create-a-property.md)
- [Como declarar uma propriedade com níveis de acesso mistos](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Como chamar um procedimento de propriedade](./how-to-call-a-property-procedure.md)
- [Como: declarar e chamar uma propriedade padrão no Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Como inserir um valor em uma propriedade](./how-to-put-a-value-in-a-property.md)
