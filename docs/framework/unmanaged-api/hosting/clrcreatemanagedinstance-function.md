---
title: Função ClrCreateManagedInstance
ms.date: 03/30/2017
api_name:
- ClrCreateManagedInstance
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- ClrCreateManagedInstance
helpviewer_keywords:
- ClrCreateManagedInstance function [.NET Framework hosting]
ms.assetid: 58ba42c0-4857-43bf-a039-73a4dc6544c2
topic_type:
- apiref
ms.openlocfilehash: 7fbe0cf3e93d75749fa3f463f3f97dbd1bfe27a0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176533"
---
# <a name="clrcreatemanagedinstance-function"></a>Função ClrCreateManagedInstance
Cria uma instância do tipo gerenciado especificado.  
  
 Esta função foi depreciada no Quadro .NET 4. Use a ativação COM para criar uma instância do tipo gerenciado ou usar a hospedagem (consulte [Interfaces de hospedagem CLR adicionadas no .NET Framework 4 e 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
STDAPI ClrCreateManagedInstance (  
    [in]  LPCWSTR  pTypeName,
    [in]  REFIID   riid,
    [out] void     **ppObject  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `pTypeName`  
 [em] Um ponteiro para o nome do tipo de ocorrência que está sendo solicitado.  
  
 `riid`  
 [em] O `IID` tipo de ocorrência que está sendo solicitado.  
  
 `ppObject`  
 [fora] Um ponteiro para um ponteiro para uma instância do tipo gerenciado que foi solicitado pelo chamador.  
  
## <a name="remarks"></a>Comentários  
 O tempo de execução do idioma comum já deve ser carregado em um processo. Por exemplo, ele pode ser carregado usando uma chamada para a `ClrCreateManagedInstance` função [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) antes que a função seja chamada. Se o tempo de execução não estiver carregado, `ClrCreateManagedInstance` primeiro tente carregar v1.0.3705 do tempo de execução. Se isso falhar, ele tentará carregar a versão mais recente do tempo de execução.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** Mscoree.dll  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Funções de hospedagem CLR reprovadas](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
- [Hospedagem](../../../../docs/framework/unmanaged-api/hosting/index.md)
