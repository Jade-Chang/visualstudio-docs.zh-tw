---
title: IDebugArrayObject::GetDimensions |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugArrayObject::GetDimensions
helpviewer_keywords:
- IDebugArrayObject::GetDimensions method
ms.assetid: 113e0aff-9028-49d6-b104-9fe7be4772d7
caps.latest.revision: 9
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 0e5297019470fe8f3fe314d542013850eab7f1e9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugarrayobjectgetdimensions"></a>IDebugArrayObject::GetDimensions
取得陣列維度。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetDimensions(   
   DWORD dwCount,  
   DWORD dwDimensions[]  
);  
```  
  
```csharp  
int GetDimensions(  
   [In] uint    dwCount,   
   [Out] uint[] dwDimensions  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwCount`  
 [in]要擷取的維度數目。  
  
 `dwDimensions`  
 [in、 out]陣列，其中已填入每個維度大小。 `dwCount`指定的大小上限`dwDimensions`陣列。  
  
## <a name="return-value"></a>傳回值  
 如果成功，會傳回 S_OK;反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 多維陣列可以具有不同的大小，針對每個維度。 例如，假設三維陣列`myarray[3][2][6]`，這個方法會傳回 3、 2 和 6`dwDimensions`參數的順序。  
  
## <a name="see-also"></a>請參閱  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)