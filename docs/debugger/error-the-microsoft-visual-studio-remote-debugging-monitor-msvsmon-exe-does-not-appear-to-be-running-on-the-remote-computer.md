---
title: "錯誤：Microsoft Visual Studio 遠端偵錯監視 (MSVSMON.EXE) 似乎沒有在遠端電腦上執行。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.server_machine_no_default"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 86db9931-50e3-4095-b161-802ed8ef39c9
caps.latest.revision: 21
caps.handback.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 錯誤：Microsoft Visual Studio 遠端偵錯監視 (MSVSMON.EXE) 似乎沒有在遠端電腦上執行。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

這個錯誤訊息表示 Visual Studio 無法在遠端電腦上找到正確的 Visual Studio 遠端偵錯監視執行個體。 必須安裝 Visual Studio 遠端偵錯監視，才能執行遠端偵錯。 如需下載和設定遠端偵錯工具的相關資訊，請參閱[在裝置上設定遠端工具](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md)。  
  
> [!IMPORTANT]
>  如果您確信收到這則訊息是因為產品錯誤，請向 Visual Studio 報告這個問題：[傳送笑臉](../Topic/Visual%20Studio%20Send%20a%20Smile%20Instructions.md)。 如果您需要更多協助，請參閱[告訴我們](../ide/talk-to-us.md)與 Microsoft 連絡。  
  
## 我在 Visual Studio 2010 或更早版本中偵錯時收到這則訊息  
 如果您使用的 Visual Studio 版本是 Visual Studio 2010 或更早版本，在未啟用檔案或印表機共用時，也可能會收到這個錯誤。若要深入了解這個問題，請參閱本文件的 Visual Studio 2010 版本：[錯誤：Microsoft Visual Studio 遠端偵錯監視 \(MSVSMON.EXE\) 似乎沒有在遠端電腦上執行。\- Visual Studio 2010](https://msdn.microsoft.com/en-us/library/ms164726\(v=vs.100\).aspx)  
  
## 我在本機偵錯時收到這則訊息  
 如果您是在本機偵錯時收到這則訊息，可能要歸責於您的防毒軟體或協力廠商防火牆。 Visual Studio 是 32 位元的應用程式，所以使用 64 位元版本的遠端偵錯工具偵錯 64 位元的應用程式。 這兩種處理序使用本機電腦內的區域網路進行通訊。 雖然沒有流量離開電腦，但協力廠商的安全性軟體很可能會封鎖通訊。  
  
 下列章節會列出一些之所以可能收到這則訊息的其他原因，以及修正問題的可行作法。  
  
## 找不到遠端電腦  
 請嘗試 [ping](https://technet.microsoft.com/en-us/library/ee624059\(v=ws.10\).aspx) 遠端電腦。 如果它不回覆 ping，遠端工具將無法連線。 請嘗試重新啟動遠端電腦，另確定它的網路設定正確。  
  
## 遠端偵錯工具的版本與 Visual Studio 版本不相符  
 您在本機執行的 Visual Studio 版本必須符合遠端電腦執行的遠端偵錯監視版本。 若要修正這個問題，請下載並安裝相符的遠端偵錯監視版本。 請移至[下載中心](http://www.microsoft.com/en-us/download)，尋找正確的遠端偵錯工具版本。  
  
## 本機和遠端電腦的驗證模式不同  
 本機和遠端電腦必須使用相同的驗證模式。 若要修正此問題，請確定兩部電腦使用相同的驗證模式。 如需驗證模式的詳細資訊，請參閱 [Windows 驗證概觀](https://technet.microsoft.com/en-us/library/hh831472.aspx)。  
  
## 遠端偵錯工具在不同的使用者帳戶下執行  
 您可以使用下列方式的其中之一解決這個問題：  
  
-   您可以停止遠端偵錯工具，再以使用的本機電腦帳戶重新啟動它。  
  
-   您可以從命令列使用 **\/allow \<使用者名稱\>** 參數: `msvsmon /allow <username@computer>` 啟動遠端偵錯工具。  
  
-   您可以將使用者加入遠端偵錯工具的權限 \(在遠端偵錯工具視窗：\[工具\] \/ \[權限\]\)。  
  
-   如果無法使用前述步驟中的方法，您可以允許任何使用者執行遠端偵錯。 在遠端偵錯工具視窗中，移至 \[工具\] \/ \[選項\] 對話方塊。 當您選取 \[無驗證\] 時，可以接著選取 \[允許任何使用者執行偵錯\]。 不過，您應該只有在沒有任何選擇或在私人網路上，才使用這個選項。  
  
## 遠端電腦上的防火牆不允許連入連線至遠端偵錯工具  
 Visual Studio 電腦上的防火牆和遠端電腦上的防火牆必須設定為允許 Visual Studio 和遠端偵錯工具之間的通訊。 如需遠端偵錯工具所用連接埠的相關資訊，請參閱[遠端偵錯工具連接埠指派](../debugger/remote-debugger-port-assignments.md)。 如需設定 Windows 防火牆的相關資訊，請參閱[設定 Windows 防火牆進行遠端偵錯](../debugger/configure-the-windows-firewall-for-remote-debugging.md)。  
  
## 防毒軟體封鎖連線  
 Windows 防毒軟體允許遠端偵錯工具連接，但某些協力廠商的防毒軟體可能會封鎖它們。 請檢查防毒軟體文件以了解如何允許這些連線。  
  
## 網路安全性原則封鎖了遠端電腦與 Visual Studio 之間的通訊  
 檢閱您的網路安全性確定它沒有封鎖通訊。 如需 Windows 網路安全性原則的詳細資訊，請參閱[安全性管理](https://msdn.microsoft.com/en-us/library/windows/desktop/ms721855\(v=vs.85\).aspx)。  
  
## 網路太忙碌無法支援遠端偵錯  
 您可能需要在別的時間執行遠端偵錯，或重新排定其他時間的網路工作。  
  
## 詳細的說明  
 若要取得遠端偵錯工具的詳細說明，包括命令列參數，請在瀏覽器中開啟下列內容：  
  
 **res:\/\/C:\\Program%20Files\\Microsoft%20Visual%20Studio%2014.0\\Common7\\IDE\\Remote%20Debugger\\x64\\msvsmon.exe\/help.htm**  
  
## 請參閱  
 [遠端偵錯錯誤和疑難排解](../debugger/remote-debugging-errors-and-troubleshooting.md)