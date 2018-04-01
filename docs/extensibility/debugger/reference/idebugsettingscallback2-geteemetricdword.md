---
title: IDebugSettingsCallback2::GetEEMetricDword |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugSettingsCallback2::GetEEMetricDword
ms.assetid: c5f8f417-0ef0-4fd0-a779-b0a8ead4effe
caps.latest.revision: 9
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 3cc688bad18e1adad8376168ac306518c5747d0e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugsettingscallback2geteemetricdword"></a>IDebugSettingsCallback2::GetEEMetricDword
擷取值，對應至指定的運算式評估工具度量。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetEEMetricDword(  
   REFGUID guidLang,  
   REFGUID guidVendor,  
   LPCWSTR pszMetric,  
   DWORD*  pdwValue  
);  
```  
  
```csharp  
private int GetEEMetricDword(  
   ref Guid guidLang,  
   ref Guid guidVendor,  
   string   pszMetric,  
   out uint pdwValue  
);  
```  
  
#### <a name="parameters"></a>參數  
 `guidLang`  
 [in]程式設計語言的唯一識別碼。  
  
 `guidVendor`  
 [in]廠商的唯一識別碼。  
  
 `pszMetric`  
 [in]標準的名稱。  
  
 `pdwValue`  
 [out]傳回度量的字串之對應值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>請參閱  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)