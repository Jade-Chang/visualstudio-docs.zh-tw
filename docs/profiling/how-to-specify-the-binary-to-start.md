---
title: "如何：指定要啟動的二進位檔 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.property.itemlaunch"
helpviewer_keywords: 
  - "分析工具, 啟動"
  - "效能工具, 啟動"
  - "效能工作階段, 啟動"
ms.assetid: ba77fcf4-8d78-49f1-b8f3-7dd0acf84306
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# 如何：指定要啟動的二進位檔
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

若要剖析二進位檔 \(如 DLL\)，您必須在 \[**\<目標\> 屬性頁**\] 對話方塊中輸入資訊。  這項資訊會指示 DLL 專案可以在何處找到呼叫的應用程式。  
  
 **需求**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
### 若要指定要啟動的可執行檔  
  
1.  在 \[**效能總管**\] 中，以滑鼠右鍵按一下目標二進位檔，然後按一下 \[**屬性**\]。  
  
2.  在 \[**屬性頁**\] 對話方塊中，按一下 \[**啟動**\] 屬性。  
  
3.  選取 \[**覆寫專案屬性**\] 核取方塊。  
  
4.  在 \[**要啟動的可執行檔**\] 文字方塊中，指定檔案位置。  
  
5.  在 \[**引數**\] 文字方塊中，指定啟動應用程式所需的引數。  
  
6.  在 \[**工作目錄**\] 文字方塊中，指定目錄位置。  
  
7.  按一下 \[**確定**\]。  
  
## 請參閱  
 [設定效能工作階段](../profiling/configuring-performance-sessions.md)