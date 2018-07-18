---
title: IDebugCustomAttributeQuery2::GetCustomAttributeByName |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
helpviewer_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
ms.assetid: 7428dfeb-8929-41b2-9b99-cb343a86c02d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b61cb7304f6fed3e2f3da55b94450c58bfc53334
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31109671"
---
# <a name="idebugcustomattributequery2getcustomattributebyname"></a>IDebugCustomAttributeQuery2::GetCustomAttributeByName
取得指定的自訂屬性名稱的自訂屬性位元組。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetCustomAttributeByName(   
   LPCOLESTR pszCustomAttributeName,  
   BYTE*     ppBlob,  
   DWORD*    pdwLen  
);  
```  
  
```csharp  
int GetCustomAttributeByName(  
   [In] string        pszCustomAttributeName,   
   [In, Out] byte[]   ppBlob,   
   [In, Out] ref uint pdwLen  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pszCustomAttributeName`  
 [in]字串，包含要尋找的自訂屬性的名稱。  
  
 `ppBlob`  
 [in、 out]陣列，其中已填入的自訂屬性的位元組。  
  
 `pdwLen`  
 [in、 out]指定要傳回的位元組數目上限`ppBlob`陣列並傳回實際寫入至陣列的位元組數目。  
  
## <a name="return-value"></a>傳回值  
 如果成功的話，會傳回 S_OK，或傳回 S_FALSE，如果自訂屬性不存在。 反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 設定`ppBlob`參數為 null 的值，傳回的數字屬性可用位元組。 配置陣列，然後將陣列中的傳送`ppBlob`參數。  
  
 屬性代表自訂屬性的未經處理資料。  
  
 如果`ppBlob`和`pdwLen`參數已設為 null 的值，這個方法可用來判斷是否只存在於自訂屬性。 簡單的替代方案，不過，是呼叫[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)方法。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)   
 [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)