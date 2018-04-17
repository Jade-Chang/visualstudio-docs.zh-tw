---
title: IDebugEngine2::SetLocale |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugEngine2::SetLocale
helpviewer_keywords:
- IDebugEngine2::SetLocale
ms.assetid: cd0d2cf1-2aac-43da-a830-4bb3d696c219
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: e007080f7c959b3667a95890babc819c6bba17f8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugengine2setlocale"></a>IDebugEngine2::SetLocale
設定偵錯引擎 (DE) 的地區設定。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetLocale(   
   WORD wLangID  
);  
```  
  
```csharp  
int SetLocale(   
   ushort wLangID  
);  
```  
  
#### <a name="parameters"></a>參數  
 `wLangID`  
 [in]指定的語言地區設定。 例如，1033 代表英文。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 工作階段的偵錯管理員 (SDM) 傳播 IDE 的地區設定，以便正確當地語系化 DE 所傳回的字串會呼叫這個方法。  
  
## <a name="see-also"></a>請參閱  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)