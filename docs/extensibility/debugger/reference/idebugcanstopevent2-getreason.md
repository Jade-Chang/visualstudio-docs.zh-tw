---
title: IDebugCanStopEvent2::GetReason |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCanStopEvent2::GetReason
helpviewer_keywords:
- IDebugCanStopEvent2::GetReason
ms.assetid: f5de31ca-7b8d-4029-9cf9-ba860ac66af6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4c0eaefee714467084898182b338ceda63ebdc0f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31101985"
---
# <a name="idebugcanstopevent2getreason"></a>IDebugCanStopEvent2::GetReason
取得為什麼偵錯引擎 (DE) 想要停止的原因。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetReason(   
   CANSTOP_REASON* pcr  
);  
```  
  
```csharp  
int GetReason(   
   out enum_CANSTOP_REASON pcr  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pcr`  
 [out]傳回值，從[CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)列舉，描述這個事件的原因。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 通常會呼叫這個方法之前[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)方法，讓呼叫端可以決定是否要傳遞非零 (`TRUE`) 至`IDebugCanStopEvent2::CanStop`方法。  
  
 可以停止的原因是`CANSTOP_ENTRYPOINT`，這表示 DE 已達到的進入點，或`CANSTOP_STEPIN`，這表示 DE 已逐步執行函式。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)   
 [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)