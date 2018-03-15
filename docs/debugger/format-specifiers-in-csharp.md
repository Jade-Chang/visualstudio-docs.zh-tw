---
title: "格式規範，在偵錯工具 (C#) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- expressions [C#], formatting values
- variables [debugger], watch variable symbols
- symbols, watch variable formatting
- QuickWatch dialog box, using format specifiers
- specifiers, watch variable format
- QuickWatch dialog box, format specifiers in C#
- specifiers
- watch variable symbols
- Watch window, format specifiers in C#
- format specifiers, debugger
- debugger, format specifiers recognized by
ms.assetid: 345c8589-5f36-4d34-a58c-e56271687dd6
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: fee9e4c355c83ae44cf6147084c95a3b213bce5a
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2018
---
# <a name="format-specifiers-in-c-in-the-visual-studio-debugger"></a>C# 中的格式規範，在 Visual Studio 偵錯工具
您可以使用格式規範變更在 **監看式** 視窗中顯示值的格式。 您也可以使用中的格式規範**即時運算**視窗中，**命令**視窗，請在[追蹤點](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints)，甚至來源視窗中。 如果暫停在這些視窗中的某個運算式上，結果則會顯示在 DataTip (資料提示方塊)。 DataTip (資料提示方塊) 會反映 DataTip 顯示中的格式規範。  
  
 如要使用格式規範，請輸入運算式且後面加上逗號。 在逗號後面加上適當的規範。  
  
## <a name="using-format-specifiers"></a>使用格式規範  
 如果您有下列程式碼：  
  
```csharp  
{  
        int my_var1 = 0x0065;  
        int my_var2 = 0x0066;  
        int my_var3 = 0x0067;  
}  
```  
  
 新增`my_var1`監看式視窗變數 (偵錯時，**偵錯 > Windows > 監看式 > 監看式 1**) 並將顯示設定為十六進位 (在**監看式**視窗中，以滑鼠右鍵按一下變數和選取**十六進位顯示**)。 現在 **監看式** 視窗顯示它包含了值 0x0065。 若希望以十進位整數、非十六進位整數表示這個值，請在 [名稱] 欄位的變數名稱後面，加入十進位格式規範： **, d**。 [值] 欄位現在會顯示十進位值 101  
  
 ![WatchFormatCSharp](../debugger/media/watchformatcsharp.png "WatchFormatCSharp")  
  
## <a name="format-specifiers"></a>格式規範  
 下表說明偵錯工具可辨識的 C# 格式規範。  
  
|指定名稱|格式|原始的監看值|顯示|  
|---------------|------------|--------------------------|--------------|  
|ac|強制評估運算式。 在隱含評估屬性和隱含函式呼叫關閉時，這就會很有用。|訊息 「 隱含函式評估已關閉使用者 」|\<value>|  
|d|十進位整數|0x0065|101|  
|動態|使用動態檢視顯示指定的物件|顯示物件所有成員，包括動態檢視|只顯示動態檢視|  
|h|十六進位整數|61541|0x0000F065|  
|nq|沒有引號的字串|"My String"|My String|  
|隱藏|顯示所有公用及非公用成員|顯示公用成員|顯示所有成員|  
|raw|以項目在原始項目節點中出現的形式顯示該項目。 只有在 Proxy 物件上有效。|字典\<T >|字典的未經處理檢視\<T >|  
|結果|搭配實作 IEnumerable 或 IEnumerable 類型的變數\<T >，通常是在查詢運算式的結果。 只顯示包含查詢結果的成員。|顯示所有成員。|顯示符合查詢條件的成員。|  
  
## <a name="see-also"></a>請參閱  
 [監看式和快速監看式視窗](../debugger/watch-and-quickwatch-windows.md)   
 [[自動變數] 和 [區域變數] 視窗](../debugger/autos-and-locals-windows.md)
