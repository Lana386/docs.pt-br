---
title: Interface ICorProfilerInfo3
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3
helpviewer_keywords:
- ICorProfilerInfo3 interface [.NET Framework profiling]
ms.assetid: 044a262f-0fa7-485d-b0c1-64cdc359c654
topic_type:
- apiref
ms.openlocfilehash: c3642154ba5f9798f59ca8fc49cb848d7e2f73c7
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862224"
---
# <a name="icorprofilerinfo3-interface"></a>Interface ICorProfilerInfo3
Fornece métodos que os profileres de código usam para se comunicar com o Common Language Runtime (CLR) para controlar o monitoramento de eventos e solicitar informações. A interface `ICorProfilerInfo3` é uma extensão da interface [ICorProfilerInfo2](icorprofilerinfo2-interface.md) . Ele fornece novos métodos com suporte no .NET Framework 4 e em versões posteriores.  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md)|Retorna um enumerador para todas as funções previamente compiladas por JIT.|  
|[Método EnumModules](icorprofilerinfo3-enummodules-method.md)|Retorna um enumerador que fornece métodos para iterar em sequência por meio de uma coleção de módulos gerenciados que são carregados no aplicativo.|  
|[Método GetAppDomainsContainingModule](icorprofilerinfo3-getappdomainscontainingmodule-method.md)|Obtém os identificadores dos domínios de aplicativo nos quais o módulo fornecido foi carregado.|  
|[Método GetFunctionEnter3Info](icorprofilerinfo3-getfunctionenter3info-method.md)|Fornece o quadro de pilha e as informações de argumento da função que está sendo relatada para o criador de perfil pela função [FunctionEnter3WithInfo](functionenter3withinfo-function.md) ; pode ser chamado somente durante o retorno de chamada `FunctionEnter3WithInfo`.|  
|[Método GetFunctionLeave3Info](icorprofilerinfo3-getfunctionleave3info-method.md)|Fornece o quadro de pilha e o valor de retorno da função que está sendo relatada ao criador de perfil pela função de [função FunctionLeave3WithInfo](functionleave3withinfo-function.md) ; pode ser chamado somente durante o retorno de chamada `FunctionLeave3WithInfo`.|  
|[Método GetFunctionTailcall3Info](icorprofilerinfo3-getfunctiontailcall3info-method.md)|Fornece o registro de ativação da função que está sendo relatado para o criador de perfil pela função [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) ; pode ser chamado somente durante o retorno de chamada `FunctionTailcall3WithInfo`.|  
|[Método GetModuleInfo2](icorprofilerinfo3-getmoduleinfo2-method.md)|Dada uma ID de módulo, retorna o nome do arquivo do módulo, a ID do assembly pai do módulo e um bitmask que descreve as propriedades do módulo.|  
|[Método GetRuntimeInformation](icorprofilerinfo3-getruntimeinformation-method.md)|Fornece informações de versão sobre o tempo de execução cujo perfil está sendo criado.|  
|[Método GetStringLayout2](icorprofilerinfo3-getstringlayout2-method.md)|Obtém informações sobre o layout de um objeto de cadeia de caracteres.|  
|[Método GetThreadStaticAddress2](icorprofilerinfo3-getthreadstaticaddress2-method.md)|Obtém o endereço do campo de thread estático especificado que está no escopo do thread e do domínio do aplicativo especificados.|  
|[Método RequestProfilerDetach](icorprofilerinfo3-requestprofilerdetach-method.md)|Instrui o tempo de execução para desanexar o criador de perfil.|  
|[Método SetEnterLeaveFunctionHooks3](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)|Especifica as funções implementadas pelo criador de perfil que serão chamadas nas funções [FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md)e [FunctionTailcall3](functiontailcall3-function.md) .|  
|[Método SetEnterLeaveFunctionHooks3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)|Especifica as funções implementadas pelo criador de perfil que serão chamadas nos ganchos [FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md)e [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) das funções gerenciadas.|  
|[Método SetFunctionIDMapper2](icorprofilerinfo3-setfunctionidmapper2-method.md)|Especifica a função implementada pelo criador de perfil que será chamada para mapear valores de `FunctionID` para valores alternativos, que são passados para os ganchos de entrada/saída da função do criador de perfil. Esse método estende [ICorProfilerInfo:: SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md) com um parâmetro que os profileres podem usar para fazer a ambiguidade entre os tempos de execução.|  
  
## <a name="remarks"></a>Comentários  
 O CLR implementa os métodos da interface `ICorProfilerInfo3` usando o modelo de thread livre. Cada método retorna um HRESULT para indicar êxito ou falha. Para obter uma lista de possíveis códigos de retorno, consulte o arquivo CorError. h.  
  
 O CLR passa uma interface `ICorProfilerInfo3` para cada criador de perfil de código durante a inicialização, usando a implementação do criador de perfil do método [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) ou [ICorProfilerCallback3:: InitializeForAttach](icorprofilercallback3-initializeforattach-method.md) . Um criador de perfil de código pode então chamar os métodos de `ICorProfilerInfo3` para obter informações sobre o código gerenciado que está sendo executado sob o controle do CLR.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interfaces de criação de perfil](profiling-interfaces.md)
- [Interface ICorProfilerInfo](icorprofilerinfo-interface.md)
