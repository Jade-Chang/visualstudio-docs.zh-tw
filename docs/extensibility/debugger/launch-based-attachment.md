---
title: 啟動時附加 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- debug engines, attaching to programs
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 518a3f804298df6c0af98a6e5d2a6d851b645aee
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2018
ms.locfileid: "39231700"
---
# <a name="launch-based-attachment"></a>啟動時附加
啟動時附加至程式便會自動的。 當裝載程式的處理序由 SDM 啟動時，啟動時附加會遵循的路徑類似於手動附件方法。 如需資訊，請參閱[附加至程式](../../extensibility/debugger/attaching-to-the-program.md)。  
  
## <a name="the-attaching-process"></a>附加的處理程序  
 主要差異在於下列事件的順序**附加**呼叫，如下所示：  
  
1.  傳送**IDebugEngineCreateEvent2** SDM 事件物件。 如需詳細資訊，請參閱 <<c0> [ 將事件傳送](../../extensibility/debugger/sending-events.md)。  
  
2.  呼叫`IDebugProgram2::GetProgramId`方法**IDebugProgram2**介面傳遞給**附加**方法。  
  
3.  傳送**IDebugProgramCreateEvent2**通知 SDM 事件物件的本機**IDebugProgram2**以 DE 代表程式建立物件。  
  
4.  傳送[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)事件物件，以通知 SDM 啟動的處理序會建立一個新的執行緒。  
  
## <a name="see-also"></a>另請參閱  
 [傳送所需的事件](../../extensibility/debugger/sending-the-required-events.md)   
 [啟用要偵錯程式](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)