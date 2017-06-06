---
title: "ResumeProfile | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ResumeProfile"
ms.assetid: 876f145b-ec07-4240-ade6-4f6e44baadce
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# ResumeProfile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`ResumeProfile` 方法會遞減指定之分析層級的暫停\/繼續計數器。  
  
## 語法  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI ResumeProfile(  
                       PROFILE_CONTROL_LEVEL Level,   
                       unsigned int dwId);  
```  
  
#### 參數  
 `Level`  
  
 表示可套用效能資料集合的設定檔層級。  下列 **PROFILE\_CONTROL\_LEVEL** 列舉程式可用來表示可套用效能資料集合之三個層級中的一個層級：  
  
|Enumerator|描述|  
|----------------|--------|  
|PROFILE\_GLOBALLEVEL|全域層級設定會影響程式碼剖析回合中的所有處理序和執行緒。|  
|PROFILE\_PROCESSLEVEL|處理序層級設定會影響屬於指定之處理序的一部分的所有執行緒。|  
|PROFILE\_THREADLEVEL|執行緒分析層級設定會影響指定的執行緒。|  
  
 `dwId`  
  
 由系統產生的處理序或執行緒識別項。  
  
## 屬性值\/傳回值  
 此函式會使用 **PROFILE\_COMMAND\_STATUS** 列舉型別來表示成功或失敗。  傳回值可以是下列其中之一：  
  
|Enumerator|描述|  
|----------------|--------|  
|PROFILE\_ERROR\_ID\_NOEXIST|分析項目 ID 不存在。|  
|PROFILE\_ERROR\_LEVEL\_NOEXIST|所指定的分析層級不存在。|  
|PROFILE\_ERROR\_MODE\_NEVER|當呼叫函式時，分析模式是設定為 NEVER。|  
|PROFILE\_ERROR\_NOT\_YET\_IMPLEMENTED|尚未實作分析函式呼叫、分析層級，或呼叫與層級的組合。|  
|PROFILE\_OK|呼叫成功。|  
  
## 備註  
 暫停\/繼續計數器的初始值為 0。  SuspendProfile 的每一個呼叫都會將 1 加到暫停\/繼續計數，每個 ResumeProfile 的呼叫則會減 1。  
  
 當暫停\/繼續計數大於 0 時，該層級的暫停\/繼續狀態會為 OFF。  當計數小於或等於 0 時，暫停\/繼續狀態會為 ON。  
  
 當 Start\/Stop 狀態和 Suspend\/Resume 狀態兩者都為 ON 時，此層級的分析狀態就會是 ON。  對於要分析的執行緒，該執行緒的全域、處理序和執行緒層級狀態都必須為 ON。  
  
## .NET Framework 對等用法  
 Microsoft.VisualStudio.Profiler.dll  
  
## 功能資訊  
 標頭：在 VSPerf.h 中宣告  
  
 匯入程式庫: VSPerf.lib  
  
## 範例  
 下列範例將說明 ResumeProfile 函式。  此範例假設已針對由 [PROFILE\_CURRENTID](../profiling/profile-currentid.md) 所識別的同一執行緒或處理序呼叫 SuspendProfile 方法。  
  
```  
void ExerciseResumeProfile()  
{  
    // The initial value of the Suspend/Resume counter is 0.   
    // Each call to SuspendProfile adds 1 to the Suspend/Resume   
    // count; each call to ResumeProfile subtracts 1.   
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Declare enumeration to hold result of call to ResumeProfile  
    PROFILE_COMMAND_STATUS profileResult;  
  
    profileResult = ResumeProfile(  
        PROFILE_GLOBALLEVEL,  
        PROFILE_CURRENTID);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("ResumeProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, profileResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## 請參閱  
 [Visual Studio 分析工具 API 參考 \(原生\)](../profiling/visual-studio-profiler-api-reference-native.md)