---
title: Não é possível chamar a função friend no objeto que não é uma instância da classe de definição
ms.date: 07/20/2015
f1_keywords:
- vbrID97
ms.assetid: b9d821f0-8565-4f15-bb35-184789c69662
ms.openlocfilehash: a227e5761bacc36c0682844a833e70c34582a5d3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64622600"
---
# <a name="cannot-call-friend-function-on-object-which-is-not-an-instance-of-defining-class"></a>Não é possível chamar a função friend no objeto que não é uma instância da classe de definição
Ou você tentou chamar as `Friend` procedimento de uma classe, ou você tentou acessar um `Friend` propriedade ou método entre processos ou entre threads. Um `Friend` procedimento pode ser chamado de um módulo de fora da classe, mas é parte do projeto no qual a classe é definida.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Certifique-se de que você estiver chamando ou acessando o procedimento a partir de um módulo que faz parte do projeto no qual a classe é definida.  
  
## <a name="see-also"></a>Consulte também

- [Friend](../../visual-basic/language-reference/modifiers/friend.md)
