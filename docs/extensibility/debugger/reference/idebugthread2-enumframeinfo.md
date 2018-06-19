---
title: IDebugThread2::EnumFrameInfo |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugThread2::EnumFrameInfo
helpviewer_keywords:
- IDebugThread2::EnumFrameInfo
ms.assetid: 17914a71-10ea-4b6f-8982-e364f87dca53
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4781533d533228e07b4268f5c92b662cf7cda122
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31120536"
---
# <a name="idebugthread2enumframeinfo"></a>IDebugThread2::EnumFrameInfo
擷取這個執行緒的堆疊框架的清單。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumFrameInfo (   
   FRAMEINFO_FLAGS        dwFieldSpec,  
   UINT                   nRadix,  
   IEnumDebugFrameInfo2** ppEnum  
);  
```  
  
```csharp  
int EnumFrameInfo (   
   enum_FRAMEINFO_FLAGS     dwFieldSpec,  
   uint                     nRadix,  
   out IEnumDebugFrameInfo2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwFieldSpec`  
 [in]從旗標的組合[FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)列舉，指定的哪些欄位[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)結構會填入。指定`FIF_FUNCNAME_FORMAT`格式化成單一字串的函式名稱的旗標。  
  
 `nRadix`  
 [in]格式化數字資訊列舉值中的使用的基數。  
  
 `ppEnum`  
 [out]傳回[IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)物件，其中包含一份[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)結構描述的堆疊框架。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 執行緒的框架會先列舉目前框架與最舊的框架上一次列舉列舉順序。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)   
 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)