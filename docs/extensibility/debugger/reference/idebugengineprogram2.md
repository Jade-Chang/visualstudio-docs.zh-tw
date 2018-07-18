---
title: IDebugEngineProgram2 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngineProgram2
helpviewer_keywords:
- IDebugEngineProgram2 interface
ms.assetid: 151003a9-2e4d-4acf-9f4d-365dfa6b9596
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ff075605371d39f9d3ff04df01c7022c52e809ef
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31112219"
---
# <a name="idebugengineprogram2"></a>IDebugEngineProgram2
這個介面會提供多執行緒偵錯支援。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugEngineProgram2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 偵錯引擎實作這個介面來支援多個執行緒同時進行偵錯。 實作的相同物件上實作此介面[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)介面。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 使用[QueryInterface](/cpp/atl/queryinterface)獲得從這個介面`IDebugProgram2`介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugEngineProgram2`。  
  
|方法|描述|  
|------------|-----------------|  
|[Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)|停止執行此程式中的所有執行緒。|  
|[WatchForThreadStep](../../../extensibility/debugger/reference/idebugengineprogram2-watchforthreadstep.md)|監看是否正在執行 （或停止觀賞執行） 在給定的執行緒上發生。|  
|[WatchForExpressionEvaluationOnThread](../../../extensibility/debugger/reference/idebugengineprogram2-watchforexpressionevaluationonthread.md)|允許 （或不允許），在給定的執行緒上發生，即使程式停止的運算式評估。|  
  
## <a name="remarks"></a>備註  
 Visual Studio 會呼叫這個介面，以回應[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)事件，並設定的 「 執行緒逐步監看式 」 和 「 監看式運算式評估在執行緒的"狀態的程式。 [停止](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)每當呼叫程式會停止，則這個方法可讓程式有機會終止所有的執行緒。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)