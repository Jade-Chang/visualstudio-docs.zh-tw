---
title: IDebugReference2::GetReferenceInfo |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugReference2::GetReferenceInfo
helpviewer_keywords:
- IDebugReference2::GetReferenceInfo
ms.assetid: ae611714-f114-4cf2-b5bb-37461e6ff289
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: a656b7eb2bc848d023cbd88a44e0ab7c80c88d01
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugreference2getreferenceinfo"></a>IDebugReference2::GetReferenceInfo
取得[DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)結構描述的參考。 保留供未來使用。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetReferenceInfo (   
   DEBUGREF_INFO_FLAGS   dwFields,  
   DWORD                 nRadix,  
   DWORD                 dwTimeout,  
   IDebugReference2**    rgpArgs,  
   DWORD                 dwArgCount,  
   DEBUG_REFERENCE_INFO* pReferenceInfo  
);  
```  
  
```csharp  
int GetReferenceInfo (   
   enum_DEBUGREF_INFO_FLAGS  dwFields,  
   uint                      nRadix,  
   uint                      dwTimeout,  
   IDebugReference2[]        rgpArgs,  
   uint                      dwArgCount,  
   DEBUG_REFERENCE_INFO[]    pReferenceInfo  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwFields`  
 [in]從旗標的組合[DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)列舉，可決定要中填寫欄位[DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)結構。  
  
 `nRadix`  
 [in]要用於格式化數字的任何資訊基數。  
  
 `dwTimeout`  
 [in]最大時間 （毫秒），從這個方法返回之前等候。 使用`INFINITE`無限期地等待。  
  
 `rgpArgs`  
 [in]陣列[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)物件。 保留供未來使用。設定為 null 的值。  
  
 `dwArgCount`  
 [in]中的參考引數數目`rgpArgs`陣列。 保留供未來使用。設定為 0。  
  
 `pReferenceInfo`  
 [out]A [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)填入這些屬性描述的結構。  
  
## <a name="return-value"></a>傳回值  
 一律傳回 `E_NOTIMPL`。  
  
## <a name="see-also"></a>請參閱  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)