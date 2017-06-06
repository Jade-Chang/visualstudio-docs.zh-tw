---
title: "指令碼偵錯的限制 | Microsoft Docs"
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
helpviewer_keywords: 
  - "ASPX 中斷點對應, 限制"
  - "中斷點對應, 限制"
  - "指令碼偵錯, 限制"
ms.assetid: 280eead5-693c-47af-967f-dfe9d23f84db
caps.latest.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 22
---
# 指令碼偵錯的限制
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 支援用戶端指令碼偵錯，但受限於本主題所述的限制。  
  
## 用戶端指令碼的中斷點對應限制  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 可讓您在執行階段轉換為用戶端的伺服器端 ASPX 或 HTML 檔中設定中斷點。  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 會將伺服器端檔案的中斷點對應到用戶端檔案中對應的中斷點，但會有下列限制：  
  
-   中斷點必須在 `<script>` 區塊內部設定。  內嵌指令碼或 `<% %>` 區塊內的中斷點無法對應。  
  
-   頁面的瀏覽器 URL 必須包含頁面名稱。  例如，http:\/\/microsoft.com\/default.apsx。  中斷點對應無法辨識來自像是 http:\/\/microsoft.com 這類位址到預設頁面的重新導向。  
  
-   中斷點必須在瀏覽器 URL 中指定的頁面中設定，而不是在 ASPX 控制項 \(ascx\) 檔、主版頁面或該頁面包含的其他檔案中設定。  在所包含頁面中設定的中斷點無法對應。  
  
-   在 `<script defer=true>` 區塊內設定的中斷點無法對應。  
  
-   位於在 `<script id="">` 區塊中設定中斷點，中斷點對應會忽略 `id` 屬性。  
  
## 中斷點對應和重複的程式行  
 為了要在伺服器端和用戶端指令碼中找到對應位置，中斷點對應演算法會檢查每一行的程式碼。  演算法會假設每一行都是唯一的。  如果有兩行以上包含相同的程式碼，而且您已在其中一個重複的程式行上設定中斷點，則中斷點對應演算法可能會在用戶端檔案中選取錯誤的重複項目。  為了避免這種情況發生，請在您設定中斷點的程式行上加入註解。  例如：  
  
```  
i++ ;  
i ++; // I added a comment, so this line is now unique  
i ++;  
```