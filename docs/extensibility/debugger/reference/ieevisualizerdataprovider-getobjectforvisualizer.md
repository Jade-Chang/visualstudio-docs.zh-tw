---
title: IEEVisualizerDataProvider::GetObjectForVisualizer |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEEVisualizerDataProvider::GetObjectForVisualizer
helpviewer_keywords:
- IEEVisualizerDataProvider::GetObjectForVisualizer method
ms.assetid: bd5376fc-13b4-40b7-9a5d-7ba8289f1b24
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 7fd08179f02b6a08d29eebe12f914434ff0ec873
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ieevisualizerdataprovidergetobjectforvisualizer"></a>IEEVisualizerDataProvider::GetObjectForVisualizer
這個方法會取得代表這個視覺化檢視的物件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetObjectForVisualizer(  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int GetObjectForVisualizer(  
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppObject`  
 [out]這個視覺化檢視所要表示的物件  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 `GetObjectForVisualizer`被允許傳回物件的快取的版本。 如果呼叫端想要確定物件是最新狀態，然後它會呼叫[GetNewObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)。  
  
## <a name="see-also"></a>請參閱  
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [GetNewObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)