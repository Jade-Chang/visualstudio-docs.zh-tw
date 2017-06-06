---
title: "How to: Create Inheritance Between Types (Class Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.classdesigner.inheritanceline"
helpviewer_keywords: 
  - "inheritance, relationship defining"
  - "relationships, defining inheritance"
ms.assetid: 3786a21c-8022-4bf5-9d13-740fd354e93c
caps.latest.revision: 30
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 30
---
# How to: Create Inheritance Between Types (Class Designer)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

若要使用 \[類別設計工具\] 在類別圖上建立兩個類型之間的繼承關係，請將基底類型連接至其衍生類型或其他類型。  您可以建立兩個類別之間的繼承關係、一個類別和一個介面之間的繼承關係，或兩個介面之間的繼承關係。  
  
### 建立兩個類型之間的繼承  
  
1.  從 \[方案總管\] 的專案中開啟類別圖 \(.cd\) 檔。  
  
     如果您還沒有類別圖，請先建立類別圖。  請參閱 [How to: Add Class Diagrams to Projects \(Class Designer\)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)。  
  
2.  在 \[工具箱\] 的 \[類別設計工具\] 下，按一下 \[繼承\]。  
  
3.  在類別圖上，繪製所需類型之間的繼承線，從下列各項開始：  
  
    -   衍生類別到基底類別  
  
    -   實作中的類別到已實作的介面  
  
    -   擴充中的介面到已擴充的介面  
  
4.  \(選擇性\) 如果您有泛型類型的衍生類型，請按一下繼承線。  在 \[屬性\] 視窗中，將 \[類型引數\] 屬性設定為符合泛型類型所需的類型。  
  
    > [!NOTE]
    >  如果父抽象類別至少包含一個抽象成員，則所有抽象成員都會實作為非抽象繼承類別。  請參閱 [Implementing Abstract Base Classes](../ide/refactoring-classes-and-types-class-designer.md#ImplementingAbstractBaseClasses)。  
    >   
    >  雖然您可以視覺化現有的泛型類型，不過無法建立新的泛型類型。  您也無法變更現有泛型類型的類型參數。  
  
## 請參閱  
 [繼承](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)   
 [Inheritance Basics](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)   
 [How to: View Inheritance Between Types \(Class Designer\)](../ide/how-to-view-inheritance-between-types-class-designer.md)   
 [Visual C\+\+ Classes in Class Designer](../ide/visual-cpp-classes-in-class-designer.md)