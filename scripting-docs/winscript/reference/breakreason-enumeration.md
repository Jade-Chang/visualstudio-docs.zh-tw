---
title: BREAKREASON 列舉 |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- BREAKREASON
apilocation:
- scrobj.dll
helpviewer_keywords:
- BREAKREASON enumeration
ms.assetid: bde07ede-2f9b-4fa2-affc-f9405683f5f7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bf1baa8b627df50db33cbd86302ce06e80c1cf34
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641018"
---
# <a name="breakreason-enumeration"></a>BREAKREASON 列舉
指出造成中斷的原因。  
  
## <a name="syntax"></a>語法  
  
```  
typedef enum tagBREAKREASON {  
   BREAKREASON_STEP,  
   BREAKREASON_BREAKPOINT,  
   BREAKREASON_DEBUGGER_BLOCK,  
   BREAKREASON_HOST_INITIATED,  
   BREAKREASON_LANGUAGE_INITIATED,  
   BREAKREASON_DEBUGGER_HALT,  
   BREAKREASON_ERROR,  
   BREAKREASON_JIT  
} BREAKREASON;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|BREAKREASON_STEP|語言引擎是逐步執行模式。|  
|BREAKREASON_BREAKPOINT|語言引擎發現明確的中斷點。|  
|BREAKREASON_DEBUGGER_BLOCK|語言引擎遇到另一個執行緒上的偵錯工具區塊。|  
|BREAKREASON_HOST_INITIATED|主應用程式要求中斷。|  
|BREAKREASON_LANGUAGE_INITIATED|語言引擎要求中斷。|  
|BREAKREASON_DEBUGGER_HALT|偵錯工具 IDE 要求中斷。|  
|BREAKREASON_ERROR|執行錯誤造成中斷的原因。|  
|BREAKREASON_JIT|JIT 偵錯啟動所造成。|  
  
## <a name="see-also"></a>另請參閱  
 [動態指令碼偵錯工具的常數、列舉和結構](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)