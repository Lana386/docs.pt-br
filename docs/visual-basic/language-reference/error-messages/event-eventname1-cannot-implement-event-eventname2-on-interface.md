---
title: O evento '<eventname1>' não pode implementar o evento '<eventname2>' na interface '<interface>' porque seus tipos delegados '<delegate1>' e '<delegate2>' não correspondem.
ms.date: 07/20/2015
f1_keywords:
- vbc31423
- bc31423
helpviewer_keywords:
- BC31423
ms.assetid: 2e754b66-5836-48ff-9697-b9c0d7085f18
ms.openlocfilehash: d6b85124b4408df532623f7c14a76e936ea28572
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625537"
---
# <a name="event-eventname1-cannot-implement-event-eventname2-on-interface-interface-because-their-delegate-types-delegate1-and-delegate2-do-not-match"></a>Evento '\<eventname1 >' não pode implementar o evento '\<eventname2 >' na interface '\<interface >' porque seus tipos delegados\<delegate1 >' e '\<delegate2 >' não coincidem
Visual Basic não pode implementar um evento porque o tipo de delegado do evento não corresponde ao tipo de delegado do evento na interface. Esse erro pode ocorrer quando você define vários eventos em uma interface e, em seguida, tentar implementá-los junto com o mesmo evento. Um evento pode implementar dois ou mais eventos apenas se todos os eventos são declarados usando a `As` sintaxe e especifique o mesmo tipo de delegado.  
  
 **ID do erro:** BC31423  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Implemente os eventos separadamente.  
  
     —ou—  
  
- Defina os eventos na interface usando o `As` sintaxe e especifique o mesmo tipo de delegado.  
  
## <a name="see-also"></a>Consulte também

- [Instrução Event](../../../visual-basic/language-reference/statements/event-statement.md)
- [Instrução Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [Eventos](../../../visual-basic/programming-guide/language-features/events/index.md)
