---
title: IDebugMemoryContext2::GetInfo |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugMemoryContext2::GetInfo
helpviewer_keywords:
- GetInfo method
- IDebugMemoryContext2::GetInfo method
ms.assetid: 08c7f091-1816-4d64-8834-f9ecaac5c58d
caps.latest.revision: 13
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: ff035004831f8efa6e378b2ddf85251699c66c18
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugmemorycontext2getinfo"></a>IDebugMemoryContext2::GetInfo
擷取[CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)結構描述內容。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetInfo(   
   CONTEXT_INFO_FIELDS dwFields,  
   CONTEXT_INFO*       pInfo  
);  
```  
  
```csharp  
int GetInfo(  
   enum_CONTEXT_INFO_FIELDS dwFields,   
   CONTEXT_INFO[]           pinfo  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwFields`  
 [in]從旗標的組合[CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)列舉型別，以指出哪些欄位的[CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)結構要填滿。  
  
 `pInfo`  
 [in、 out]`CONTEXT_INFO`會自動填入的結構。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>請參閱  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)   
 [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)   
 [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)