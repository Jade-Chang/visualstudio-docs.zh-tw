---
title: IDebugCoreServer3::EnableAutoAttach |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugCoreServer3::EnableAutoAttach
helpviewer_keywords:
- IDebugCoreServer3::EnableAutoAttach
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
caps.latest.revision: 9
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: d0b7fbfc1d7c3d9d4ab5214e8c0c5518c6dad5cb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugcoreserver3enableautoattach"></a>IDebugCoreServer3::EnableAutoAttach
可讓自動附加指定的偵錯引擎。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnableAutoAttach(  
   GUID*     rgguidSpecificEngines,  
   DWORD     celtSpecificEngines,  
   LPCOLESTR pszStartPageUrl,  
   BSTR*     pbstrSessionId  
);  
```  
  
```csharp  
int EnableAutoAttach(  
   Guid[]     rgguidSpecificEngines,  
   uint       celtSpecificEngines,  
   string     pszStartPageUrl,  
   out string pbstrSessionId  
);  
```  
  
#### <a name="parameters"></a>參數  
 `rgguidSpecificEngines`  
 [in]陣列的每個偵錯引擎將標示為自動附加的 Guid。  
  
 `celtSpecificEngines`  
 [in]中指定的引擎數`rgguidSpecificEngines`。  
  
 `pszStartPageUrl`  
 [in]要使用自動附加時的起始 URL。  
  
 `pbstrSessionID`  
 [out]已自動附加的工作階段識別碼。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則會傳回錯誤碼。 一個錯誤碼是`E_AUTO_ATTACH_NOT_REGISTERED`，表示尚未註冊 auto-attach class factory。  
  
## <a name="remarks"></a>備註  
 使用指定的 URL 相關聯的程式啟動時，將指定的偵錯引擎會自動啟動，並附加。  
  
## <a name="see-also"></a>請參閱  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)