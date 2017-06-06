---
title: "為變數 &#39;&lt;變數名稱&gt;&#39; 指派值之前，已用參考方式傳遞該變數 | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc42030"
  - "BC42030"
helpviewer_keywords: 
  - "BC42030"
ms.assetid: 8f1aae99-f032-4fdf-b6dc-3360cc5b94de
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 為變數 &#39;&lt;變數名稱&gt;&#39; 指派值之前，已用參考方式傳遞該變數
為變數 '\<變數名稱\>' 指派值之前，已用參考方式傳遞該變數。 可能會在執行階段產生 null 參考例外狀況。  
  
 程序呼叫在為變數指派任何值之前，將變數當做引數傳遞至 `ByRef` 參數。  
  
 如果變數從未獲派值，則會持有其資料類型的預設值。 若是參考資料類型，該預設值為 [Nothing](/dotnet/visual-basic/language-reference/nothing)。 在某些情況下，讀取具有 `Nothing` 值的參考變數可能會導致 <xref:System.NullReferenceException>。  
  
 將引數傳遞至程序 `ByRef` 會將引數的基礎變數公開給程序進行可能的修改。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱[在 Visual Basic 中設定警告](../ide/configuring-warnings-in-visual-basic.md)。  
  
 **錯誤 ID︰**BC42030  
  
### 更正這個錯誤  
  
-   如果不論變數是否已持有值，都想讓程序透過 `ByRef` 引數將值指派給變數，則不需要採取任何動作。  
  
-   如果程序中的邏輯在為引數指派任何值之前讀取引數，而且變數屬於實值類型，請確定程序邏輯並非取決於變數是否持有其預設值。  
  
-   如果程序中的邏輯在為引數指派任何值之前讀取引數，而且變數屬於參考類型，請確定程序邏輯可以處理 `Nothing` 值。 例如，它可以使用 [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement) 來攔截 <xref:System.NullReferenceException>。  
  
## 請參閱  
 [Dim Statement](/dotnet/visual-basic/language-reference/statements/dim-statement)   
 [Value Types and Reference Types](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)   
 [Passing Arguments by Value and by Reference](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference)   
 [ByRef](/dotnet/visual-basic/language-reference/modifiers/byref)   
 [變數宣告](/dotnet/visual-basic/programming-guide/language-features/variables/variable-declaration)   
 [為變數進行疑難排解](/dotnet/visual-basic/programming-guide/language-features/variables/troubleshooting-variables)