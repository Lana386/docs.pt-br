---
title: Método ISymUnmanagedDocument::GetURL
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetURL
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetURL
helpviewer_keywords:
- GetURL method [.NET Framework debugging]
- ISymUnmanagedDocument::GetURL method [.NET Framework debugging]
ms.assetid: 60600178-c2b5-4cab-b3a5-f0f61acebaf1
topic_type:
- apiref
ms.openlocfilehash: 134a89d62a0fc455a9579de1e577103f1fe6abcf
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449127"
---
# <a name="isymunmanageddocumentgeturl-method"></a>Método ISymUnmanagedDocument::GetURL
Retorna o Uniform Resource Locator (URL) deste documento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetURL(  
    [in]  ULONG32  cchUrl,  
    [out] ULONG32  *pcchUrl,  
    [out, size_is(cchUrl), length_is(*pcchUrl)] WCHAR szUrl[]);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `cchUrl`  
 no O tamanho, em caracteres, do buffer de `szURL`.  
  
 `pcchUrl`  
 fora Um ponteiro para uma variável que recebe o tamanho da URL, incluindo a terminação nula.  
  
 `szUrl`  
 fora O buffer que contém a URL.  
  
## <a name="return-value"></a>Valor retornado  
 S_OK se o método tiver sucesso; caso contrário, um código de erro.  
  
## <a name="see-also"></a>Consulte também

- [Interface ISymUnmanagedDocument](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
