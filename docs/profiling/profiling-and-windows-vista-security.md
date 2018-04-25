---
title: 分析和 Windows Vista 安全性 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,security
- performance tools, security
ms.assetid: 842112fc-b886-4801-8cd7-a25b314b0393
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6f03c5d6a7afec1010653c6e4a66a3770573ea5e
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="profiling-and-windows-vista-security"></a>分析和 Windows Vista 安全性
依據電腦系統管理員提供的 [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)] 使用者存取權限設定，個別使用者可能具有安全性權限可以在該電腦上分析處理序。 下列範例説明各使用者之間可能存在的差異：  
  
-   當系統管理員設定了要啟動的驅動程式和服務時，某些使用者可以存取進階的程式碼剖析功能。  
  
-   網域使用者只能存取取樣程式碼剖析。  
  
-   某些使用者可以拒絕其他所有使用者存取程式碼剖析。  
  
 如需詳細資訊，請參閱 [VSPerfCmd](../profiling/vsperfcmd.md) 中的 ADMIN 選項。  
  
## <a name="cross-session-profiling"></a>跨工作階段進行程式碼剖析  
 「跨工作階段進行程式碼剖析」是指能夠分析在不同登入工作階段中執行的處理序。 例如，大部分服務是在工作階段 0 中執行，而使用者無法直接在工作階段 0 中執行。 使用 [效能總管] 工具列上的 [附加至處理序] 按鈕或 VSPerfCmd 命令列工具的 /attach 選項，您就可以分析不同登入工作階段中的大部分處理序。  
  
 您透過設定跨處理序進行程式碼剖析可見性選項，就可以看到處理序清單。 當您按一下 [附加至處理序] 後，隨即顯示的 [附加至處理序] 視窗中，會提供這些選項：  
  
-   **顯示所有使用者的處理序**  
  
     未選取此選項時，清單只會顯示目前使用者所擁有的處理序。 選取 [顯示所有使用者的處理序] 時，清單才會顯示所有使用者的處理序。  
  
-   **顯示所有工作階段中的處理序**  
  
     未選取此選項時，清單會顯示目前工作階段中的處理序。 選取此選項時，清單才會顯示所有工作階段中的處理序。  
  
## <a name="see-also"></a>請參閱  
 [概觀](../profiling/overviews-performance-tools.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [ 如何：附加至執行中處理序](http://msdn.microsoft.com/en-us/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4)