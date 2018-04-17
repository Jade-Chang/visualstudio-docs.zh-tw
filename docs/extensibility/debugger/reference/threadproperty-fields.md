---
title: THREADPROPERTY_FIELDS |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- THREADPROPERTY_FIELDS
helpviewer_keywords:
- THREADPROPERTY_FIELDS enumeration
ms.assetid: 5b88acb9-03ea-4c29-a788-f0087dccbe23
caps.latest.revision: 11
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 9ff443fc655c18600ff90536d6e7ee5b8aa1ab7f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="threadpropertyfields"></a>THREADPROPERTY_FIELDS
指定要擷取執行緒的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
enum enum_THREADPROPERTY_FIELDS {   
   TPF_ID           = 0x0001,  
   TPF_SUSPENDCOUNT = 0x0002,  
   TPF_STATE        = 0x0004,  
   TPF_PRIORITY     = 0x0008,  
   TPF_NAME         = 0x0010,  
   TPF_LOCATION     = 0x0020,  
   TPF_ALLFIELDS    = 0xffffffff  
};  
typedef DWORD THREADPROPERTY_FIELDS;  
```  
  
```csharp  
public enum enum_THREADPROPERTY_FIELDS {   
   TPF_ID           = 0x0001,  
   TPF_SUSPENDCOUNT = 0x0002,  
   TPF_STATE        = 0x0004,  
   TPF_PRIORITY     = 0x0008,  
   TPF_NAME         = 0x0010,  
   TPF_LOCATION     = 0x0020,  
   TPF_ALLFIELDS    = 0xffffffff  
};  
```  
  
## <a name="members"></a>成員  
 TPF_ID  
 初始化/使用`dwThreadId`欄位[THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)結構。  
  
 TPF_SUSPENDCOUNT  
 初始化/使用`dwSuspendCount`欄位`THREADPROPERTIE`結構。  
  
 TPF_STATE  
 初始化/使用`dwThreadState`欄位`THREADPROPERTIE`結構。  
  
 TPF_PRIORITY  
 初始化/使用`bstrPriority`欄位`THREADPROPERTIE`結構。  
  
 TPF_NAME  
 初始化/使用`bstrName`欄位`THREADPROPERTIE`結構。  
  
 TPF_LOCATION  
 初始化/使用`bstrLocation`欄位`THREADPROPERTIE`結構。  
  
 TPF_ALLFIELDS  
 指定所有欄位。  
  
## <a name="remarks"></a>備註  
 這些值會傳遞做為引數[GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)方法，以表示的哪些欄位[THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)結構會進行初始化。  
  
 這些值也會在`dwFields`隸屬`THREADPROPERTIES`結構，以指出哪些欄位是使用且有效。  
  
 這些旗標可能會合併使用位元`OR`。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)