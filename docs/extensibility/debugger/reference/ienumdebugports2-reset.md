---
title: IEnumDebugPorts2::Reset |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEnumDebugPorts2::Reset
helpviewer_keywords:
- IEnumDebugPorts2::Reset
ms.assetid: 67da406c-eadb-421e-ae12-e26e9866f262
caps.latest.revision: 9
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: fdcf2fbe5349b4f404a8b1d8ad71f754a759230f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ienumdebugports2reset"></a>IEnumDebugPorts2::Reset
將列舉重設第一個項目。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Reset(  
   void  
);  
```  
  
```csharp  
int Reset();  
```  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 呼叫這個方法是下, 一次呼叫之後[下一步](../../../extensibility/debugger/reference/ienumdebugports2-next.md)方法會傳回第一個元素的列舉型別。  
  
## <a name="see-also"></a>請參閱  
 [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)