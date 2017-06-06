---
title: "錯誤：請確認目標電腦上的 DNS 設定都正確 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.callback_dns_failed"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 2d364caf-73af-4186-bf9b-af186331cbe8
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# 錯誤：請確認目標電腦上的 DNS 設定都正確
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可能會在嘗試進行遠端偵錯時，得到下列錯誤訊息：  
  
```  
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Ensure that DNS is correctly configured on the target computer.  
```  
  
 當目標電腦無法解析 Visual Studio 偵錯工具主機電腦的名稱時，便會發生這個錯誤。  請檢查目標電腦上的 DNS 設定。  
  
-   如需檢視在 Windows 8.1、Vista、Windows 7、Windows Server 2012、Windows Server 2008 或 Windows Server 2008 R2 上 DNS 的設定資訊，請執行下列作業：在 \[開始\] 功能表上，選擇 \[說明及支援\]，然後搜尋 \[變更 TCP\/IP\] 設定。  
  
-   如需詳細資訊，請移至 [Microsoft Windows 網站](http://go.microsoft.com/fwlink/?LinkId=252720)並搜尋 \[變更 TCP\/IP\] 設定。  
  
 如果無法解決 DNS 問題，您可以嘗試用其他帳戶執行 \[遠端偵錯工具\]。  只有在您使用本機系統或網路服務帳戶執行 \[遠端偵錯工具\] 時，才會發生這個錯誤。  如果是以其他帳戶執行 \[遠端偵錯工具\]，就可以使用不需要 DNS 的 NTLM 驗證。  。  如需相關程序，請參閱[錯誤：目標電腦上的 Visual Studio 遠端偵錯工具服務無法連回這部電腦](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md)。