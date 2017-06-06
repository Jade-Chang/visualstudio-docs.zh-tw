---
title: "偵錯混合模式應用程式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "呼叫堆疊視窗"
  - "呼叫堆疊視窗, 混合模式偵錯"
  - "偵錯 [Visual Studio], 混合模式"
  - "偵錯 Managed 程式碼, 混合程式碼"
  - "混合模式偵錯"
  - "混合模式偵錯, 呼叫堆疊"
  - "混合模式偵錯, 屬性評估"
ms.assetid: 60e34477-ae4e-48c7-9093-3e37f72e1bc3
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# 偵錯混合模式應用程式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

混合模式應用程式是指任何組合了機器碼 \(C\+\+\) 和 Managed 程式碼 \(例如在通用語言執行平台執行的 Visual Basic、Visual C\# 或 C\+\+\) 的應用程式。  在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中，偵錯混合模式應用程式是個極為平常的動作；這和偵錯單一模式應用程式大致上相同。  但是仍然要考慮一些特殊情況。  
  
## 在混合模式偵錯中啟用 C\+\+ 編輯後繼續  
  
-   若要在 Visual Studio 2013 中使用 C\+\+ 的「編輯後繼續」，您必須還原成舊版偵錯引擎。  請參閱 Microsoft Application Lifecycle Management 部落格上的[在 Visual Studio 2013 中切換成 Managed 相容性模式](http://blogs.msdn.com/b/visualstudioalm/archive/2013/10/16/switching-to-managed-compatibility-mode-in-visual-studio-2013.aspx) \(英文\)。  
  
## 混合模式應用程式的屬性評估  
 在混合模式應用程式中，偵錯工具所進行的屬性評估是一種極耗資源的作業。  如此一來，像逐步執行之類的偵錯作業就會顯得相當慢。  如需詳細資訊，請參閱[逐步執行程式碼](http://msdn.microsoft.com/zh-tw/8791dac9-64d1-4bb9-b59e-8d59af1833f9)。  如果您在混合模式偵錯的效能非常低，可以考慮關閉偵錯視窗的屬性評估。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選取 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
#### 若要關閉屬性評估  
  
1.  在 \[**工具**\] 功能表上選擇 \[**選項**\]。  
  
2.  在 \[**選項**\] 對話方塊中，開啟 \[**偵錯**\] 資料夾，並選取 \[**一般**\] 分類。  
  
3.  清除 \[**啟用屬性評估及其他隱含函式呼叫**\] 核取方塊。  
  
 因為原生呼叫堆疊和 Managed 呼叫堆疊有所不同，偵錯工具無法一直為混合模式提供完整呼叫堆疊。  當機器碼呼叫 Managed 程式碼時，您可能會發現某些不一樣的地方。  如需詳細資訊，請參閱[呼叫堆疊視窗內的混合程式碼和遺失的資訊](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md)。  
  
## 請參閱  
 [偵錯 Managed 程式碼](../debugger/debugging-managed-code.md)