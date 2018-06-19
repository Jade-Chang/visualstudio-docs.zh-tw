---
title: IDebugBreakpointErrorEvent2 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBreakpointErrorEvent2
helpviewer_keywords:
- IDebugBreakpointErrorEvent2
ms.assetid: adee79df-8db5-4510-a7df-c50f4dbf5e35
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6f7cd8bdb5e8a36539807970958efda8f152e5c1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31103938"
---
# <a name="idebugbreakpointerrorevent2"></a>IDebugBreakpointErrorEvent2
這個介面會告知工作階段的偵錯管理員 (SDM) 的暫止中斷點無法繫結到載入的程式，可能是因為警告或錯誤。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugBreakpointErrorEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 DE 實作這個介面做為其支援中斷點的一部分。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須實作此介面為相同的物件上 (SDM 使用[QueryInterface](/cpp/atl/queryinterface)存取`IDebugEvent2`介面)。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 建立裝置和暫止中斷點無法繫結至偵錯程式時所傳送此事件的物件。 事件會使用傳送[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)它附加到正在偵錯程式時，SDM 所提供的回呼函式。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugBreakpointErrorEvent2`。  
  
|方法|描述|  
|------------|-----------------|  
|[GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)|取得[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)描述警告或錯誤的介面。|  
  
## <a name="remarks"></a>備註  
 每當中斷點繫結時，就會傳送事件到 SDM。 如果中斷點無法繫結，`IDebugBreakpointErrorEvent2`傳送，否則[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)傳送。  
  
 例如，暫止中斷點具有相關聯的條件失敗時要剖析或評估，警告會傳送暫止中斷點不能繫結在這個階段。 如果不有尚未載入中斷點的程式碼，也可能會發生。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)