---
title: IDebugExceptionEvent2::CanPassToDebuggee |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f0ffea7be736cbf6d04c368ba6124d0faf22be61
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugexceptionevent2canpasstodebuggee"></a>IDebugExceptionEvent2::CanPassToDebuggee
決定偵錯引擎 (DE) 支援將此例外狀況傳遞至偵錯時就會繼續執行程式的選項。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CanPassToDebuggee(  
   void  
);  
```  
  
```csharp  
int CanPassToDebuggee();  
```  
  
## <a name="return-value"></a>傳回值  
 傳回`S_OK`（例外狀況可以傳遞至程式） 或`S_FALSE`（無法傳遞的例外狀況）。  
  
## <a name="remarks"></a>備註  
 DE 必須傳遞至偵錯工具的預設動作。 IDE，可能會收到[IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)事件和呼叫[繼續](../../../extensibility/debugger/reference/idebugprocess3-continue.md)方法，而不需呼叫`CanPassToDebuggee`方法。 因此，DE 應該或未傳遞例外狀況的預設案例。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)