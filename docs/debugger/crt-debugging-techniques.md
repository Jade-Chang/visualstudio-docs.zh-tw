---
title: "CRT 偵錯技術 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.runtime.debugging"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "CRT, 偵錯"
  - "偵錯 [C++], CRT 偵錯支援"
  - "偵錯 [CRT]"
ms.assetid: 9be561f6-14a8-44ff-925d-d911d5b8e6ff
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# CRT 偵錯技術
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

如果您要偵錯的程式使用 C 執行階段程式庫，可以使用這些偵錯技術。  
  
## 在本節中  
 [CRT 偵錯程式庫操作](../debugger/crt-debug-library-use.md)  
 描述由 C 執行階段程式庫提供的偵錯支援，並提供存取這些工具的指示。  
  
 [報告巨集](../debugger/macros-for-reporting.md)  
 提供 **\_RPTn** 和 **\_RPTFn** 巨集 \(定義於 CRTDBG.H\) 的相關資訊，這些巨集取代偵錯時使用的 `printf` 陳述式。  
  
 [堆積配置函式的偵錯版本](../debugger/debug-versions-of-heap-allocation-functions.md)  
 討論堆積配置函式的特殊偵錯版本，包括：CRT 對應呼叫的方式、明確呼叫他們的優點、如何避免轉換、追蹤用戶端區塊中不同的配置類型，以及未定義 \_DEBUG 的結果。  
  
 [CRT 偵錯堆積詳細資料](../debugger/crt-debug-heap-details.md)  
 提供記憶體管理和偵錯堆積、偵錯堆積上的區塊類型、使用偵錯堆積、回報函式的堆積狀態和追蹤堆積配置要求的連結。  
  
 [撰寫偵錯攔截函式](../debugger/debug-hook-function-writing.md)  
 列出以下主題的連結：用戶端區塊攔截函式、配置攔截函式，配置攔截與 CRT 記憶體配置，以及報告攔截函式。  
  
 [使用 CRT 程式庫尋找記憶體遺漏](../debugger/finding-memory-leaks-using-the-crt-library.md)  
 說明使用偵錯工具和 C 執行階段程式庫來偵錯和找出記憶體流失問題的技術。  
  
## 相關章節  
 [偵錯機器碼](../debugger/debugging-native-code.md)  
 討論 C 和 C\+\+ 應用程式的一些常見偵錯問題和技術。  
  
 [偵錯工具安全性](../debugger/debugger-security.md)  
 提供更安全偵錯的建議事項。