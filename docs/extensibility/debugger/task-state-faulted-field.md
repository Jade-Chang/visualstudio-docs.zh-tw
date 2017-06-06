---
title: "TASK_STATE_FAULTED 欄位 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "TASK_STATE_FAULTED] 欄位中，工作類別 [.NET Framework 偵錯引擎]"
ms.assetid: ced826ae-09a9-4acf-af00-a2343d396bb8
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# TASK_STATE_FAULTED 欄位
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

工作因未處理的例外狀況而完成。  
  
 **命名空間︰** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **組件︰** mscorlib （在 mscorlib.dll\)  
  
 因為您無法從.NET Framework 來存取這個內部成員，下列語法提供通用中繼語言 \(CIL\)。  
  
## 語法  
  
```  
.field static assembly literal int32 TASK_STATE_FAULTED = int32(0x00400000)  
```  
  
## 備註  
 如果 [m\_stateFlags](../../extensibility/debugger/m-stateflags-field.md) 欄位包含此值， <xref:System.Threading.Tasks.Task.Status%2A> 屬性會傳回 <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>。  
  
## 請參閱  
 [工作類別](../../extensibility/debugger/task-class-internal-members.md)