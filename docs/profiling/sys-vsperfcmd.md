---
title: "Sys (VSPerfCmd) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 294a6f9e-b49f-4c83-b322-5ac5411b66fb
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Sys (VSPerfCmd)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSPerfCmd.exe **Sys** 選項會將取樣的程式碼剖析事件設定為系統呼叫事件 \(從程式碼剖析應用程式對作業系統的函式呼叫\)，並且選擇性地變更取樣間隔中預設為 10 的系統呼叫數目。  
  
 **Sys** 只能在也包含 **Launch** 或 **Attach** 選項的命令列中使用。  
  
 根據預設，程式碼剖析工具取樣事件是設定為處理器時脈週期，且取樣間隔設定為 10,000,000。  **Timer**、**PF**、**Sys** 和 **Counter** 選項可讓您設定取樣事件和取樣間隔。  **GC** 選項會在每個配置和記憶體回收事件時收集 .NET 記憶體資料。  在命令列上只能指定這些選項的其中一個。  
  
 取樣事件和取樣間隔只能在包含 **Launch** 或 **Attach** 選項的第一個命令列中設定。  
  
## 語法  
  
```  
VSPerfCmd.exe {/Launch:AppName|Attach:PID} /Sys[:Events] [Options]  
```  
  
#### 參數  
 `Events`  
 指定取樣間隔中系統呼叫事件數目的整數值。  如果未指定 `Events`，則間隔會設定為 10。  
  
## 必要選項  
 **Sys** 需要下列其中一個選項。  
  
 **Launch:** `AppName`  
 啟動程式碼剖析工具以及 `AppName` 所指定的應用程式。  
  
 **Attach:** `PID`  
 將程式碼剖析工具附加至 `PID` 指定的處理序。  
  
## 無效的選項  
 下列選項無法在與 **Sys** 相同的命令列上指定。  
  
 **PF**\[**:**`Events`\]  
 將取樣事件設定為分頁錯誤，並且選擇性地將取樣間隔設定為 `Events`。  預設的 PF 間隔為 10。  
  
 **Timer**\[**:**`Cycles`\]  
 將取樣事件設定為處理器時脈週期，並且選擇性地將取樣間隔設定為 `Cycles`。  預設 Timer 間隔為 10,000,000。  
  
 **Counter:** `Name`\[`,Reload`\[`,FriendlyName`\]\]  
 將取樣事件設定為 `Name` 所指定的 CPU 效能計數器，並將取樣間隔設定為 `Reload`。  
  
 **GC**\[**:**{**Allocation**&#124;**Lifetime**}\]  
 收集 .NET 記憶體資料。  根據預設 \(**Allocation**\)，資料會於每次記憶體配置事件收集。  已指定 **Lifetime** 參數時，也會在每個記憶體回收事件時收集資料。  
  
## 範例  
 這個範例示範如何將程式碼剖析工具取樣事件設定為系統呼叫，以及如何將取樣間隔設定為每個樣本 20 次呼叫。  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Sys:20  
```  
  
## 請參閱  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [對獨立應用程式進行程式碼剖析](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [為 ASP.NET Web 應用程式進行程式碼剖析](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [對服務進行程式碼剖析](../profiling/command-line-profiling-of-services.md)