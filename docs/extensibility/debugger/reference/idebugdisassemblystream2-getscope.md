---
title: IDebugDisassemblyStream2::GetScope |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugDisassemblyStream2::GetScope
helpviewer_keywords:
- IDebugDisassemblyStream2::GetScope
ms.assetid: 71c6e632-642a-42d8-a995-77e4ac190a5b
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: fcfd474c1f10887fd30356fe444476428c263fe0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugdisassemblystream2getscope"></a>IDebugDisassemblyStream2::GetScope
取得反組譯碼資料流的範圍。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetScope(   
   DISASSEMBLY_STREAM_SCOPE* pdwScope  
);  
```  
  
```csharp  
int GetScope(   
   out enum_ DISASSEMBLY_STREAM_SCOPE pdwScope  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pdwScope`  
 [out]傳回值，從[DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)列舉，描述這個反組譯碼資料流的範圍。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 反組譯碼的範圍可能是函式或整個模組，例如。  
  
## <a name="see-also"></a>請參閱  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)