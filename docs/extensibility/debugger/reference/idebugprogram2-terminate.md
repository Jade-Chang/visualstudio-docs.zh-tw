---
title: IDebugProgram2::Terminate |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgram2::Terminate
helpviewer_keywords:
- IDebugProgram2::Terminate
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
caps.latest.revision: 8
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: fea9b99fc597a75e93392b14fe40a1be87072602
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogram2terminate"></a>IDebugProgram2::Terminate
結束程式。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Terminate(   
   void   
);  
```  
  
```csharp  
int Terminate();  
```  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 程式可能的話，會終止並從處理序; 卸載否則，偵錯引擎 (DE) 會執行任何必要的清除作業。  
  
 這個方法或[Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) IDE，通常是在回應停止偵錯的所有使用者所呼叫方法。 這個方法的實作應該在理想情況下，終止處理序內的程式。 如果不可行，DE 應該阻止程式執行此程序更多，並執行任何必要的清除。 如果`IDebugProcess2::Terminate`IDE 所呼叫方法，整個程序將會終止一段時間之後`IDebugProgram2::Terminate`方法呼叫。  
  
## <a name="see-also"></a>請參閱  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [終止](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)