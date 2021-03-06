---
title: Método ICorDebugStepper::SetUnmappedStopMask
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.SetUnmappedStopMask
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::SetUnmappedStopMask
helpviewer_keywords:
- ICorDebugStepper::SetUnmappedStopMask method [.NET Framework debugging]
- SetUnmappedStopMask method [.NET Framework debugging]
ms.assetid: b1211981-e90c-4e05-8def-fa18d85ad9ab
topic_type:
- apiref
ms.openlocfilehash: ff393b119c349e34898b781c3185cc82f2dba11f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137560"
---
# <a name="icordebugsteppersetunmappedstopmask-method"></a>Método ICorDebugStepper::SetUnmappedStopMask
Define um valor que especifica o tipo de código não mapeado no qual a execução será interrompida.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetUnmappedStopMask (  
    [in] CorDebugUnmappedStop   mask  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `mask`  
 no Um valor da Enumeração CorDebugUnmappedStop que especifica o tipo de código não mapeado no qual o depurador irá parar a execução.  
  
 O valor padrão é STOP_OTHER_UNMAPPED. O valor STOP_UNMANAGED é válido somente com depuração de interoperabilidade.  
  
## <a name="remarks"></a>Comentários  
 Quando o depurador encontra uma compilação JIT (just-in-time) que não tem mapeamento correspondente à MSIL (Microsoft Intermediate Language), ele interrompe a execução se o sinalizador que especifica esse tipo de código não mapeado tiver sido definido; caso contrário, a etapa continuará de forma transparente.  
  
 Se o depurador não usar um stepper para inserir um método, ele não irá necessariamente passar por código não mapeado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
