---
title: IDebugProgram2::Execute |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::Execute
helpviewer_keywords:
- IDebugProgram2::Execute
ms.assetid: f7205ce8-0ac6-4fcd-b6ec-b720b4fcaccf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f7f4e26a5c892e1c796a2b6e2f9371898db21f68
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogram2execute"></a>IDebugProgram2::Execute
會繼續執行此程式從已停止的狀態。 清除任何先前的執行狀態 （例如步驟），並在程式啟動重新執行。  
  
> [!NOTE]
>  這個方法已被取代。 使用[Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md)方法改為。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Execute(  
   void  
);  
```  
  
```csharp  
int Execute();  
```  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 當使用者開始從某些其他程式的執行緒處於停止狀態時執行時，在這個程式會呼叫這個方法。 當使用者選取時，也會呼叫這個方法**啟動**命令**偵錯**在 IDE 中的功能表。 這個方法的實作可能會只要呼叫[繼續](../../../extensibility/debugger/reference/idebugthread2-resume.md)程式中目前的執行緒上的方法。  
  
> [!WARNING]
>  不會停止事件或直接 （同步） 事件，以傳送[事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)時處理這個呼叫，否則偵錯工具可能會停止回應。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)