---
title: JsEnableRuntimeExecution 函式 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- jsrt/JsEnableRuntimeExecution
helpviewer_keywords:
- JsEnableRuntimeExecution function
ms.assetid: daa2036b-aef6-497d-a8ce-5a006b6ed13f
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ad54fb76aec1bf6c1a7f53aa64192807cf0361c2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24567878"
---
# <a name="jsenableruntimeexecution-function"></a>JsEnableRuntimeExecution 函式
指令碼可在執行階段中執行。  
  
## <a name="syntax"></a>語法  
  
```  
STDAPI_(JsErrorCode) JsEnableRuntimeExecution(  
   _In_ JsRuntimeHandle runtime  
);  
```  
  
#### <a name="parameters"></a>參數  
 `runtime`  
 要啟用的執行階段。  
  
## <a name="return-value"></a>傳回值  
 如果作業成功，則為 `JsNoError` 碼，否則為失敗碼。  
  
## <a name="remarks"></a>備註  
 無法在已啟用指令碼執行的執行階段中啟用指令碼執行。  
  
## <a name="requirements"></a>需求  
 **標頭：** jsrt.h  
  
## <a name="see-also"></a>另請參閱  
 [參考資料 (JavaScript 執行階段)](../chakra-hosting/reference-javascript-runtime.md)