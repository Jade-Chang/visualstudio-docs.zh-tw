---
title: "如何：自訂捲軸以追蹤程式碼 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a9ebe7ec-4b6f-4ba2-a79e-80fab3db485b
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# 如何：自訂捲軸以追蹤程式碼
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在處理冗長的程式碼檔案時，很難記住所有內容。  您可以自訂程式碼視窗的捲軸，讓您得以鳥瞰程式碼中的所有狀況。  
  
### 在捲軸上顯示註解  
  
1.  您可以設定捲軸，以顯示程式碼的變更、中斷點、錯誤及書籤。  
  
     開啟 \[捲軸\] 選項頁面 \(\[工具\]、\[選項\]、\[文字編輯器\]。**\[所有語言\]** 或特定語言，或是在 \[快速啟動\] 視窗中輸入捲軸。  
  
2.  選取 \[在垂直捲軸上顯示註釋\]，然後選取想要查看的註釋。  \(\[標記\] 選項包含中斷點及書籤。\)  
  
3.  現在試試看。  開啟一個大型的程式碼檔案，在檔案中改掉幾個地方的內容。  捲軸會顯示出您改動過的內容，因此如果您改掉了不該更動的東西，可以將變更還原。  
  
     以下是在搜尋字串之後，捲軸呈現的外觀。  請注意，會出現該字串的所有出現處。  
  
     ![搜尋字串之後的捲軸。](../ide/media/enhancedscrollbarsearch.png "EnhancedScrollbarSearch")  
  
     以下是取代字串所有出現處之後的捲軸外觀。  您馬上就能看到此作業造成一些問題。  
  
     ![以錯誤的字串來取代之後的捲軸](../ide/media/enhancedscrollbarreplace.png "EnhancedScrollbarReplace")  
  
### 設定捲軸的顯示模式  
  
1.  捲軸有兩種模式：捲軸模式 \(預設值\) 和地圖模式。  捲軸模式只會在捲軸上顯示註釋指標。  在地圖模式中，程式碼行會呈現在捲軸上。  您可以選擇程式碼行的寬度，以及當您將指標放在程式碼行上方時，是否要顯示指標下的程式碼。  當您按一下捲軸上的某個位置時，游標會移至程式碼中的該位置。  摺疊的區域會以不同的陰影標出；按兩下該陰影區域即可展開。  
  
     在 \[捲軸\] 選項頁面上，選取 \[垂直捲軸使用捲軸模式\] 或 \[垂直捲軸使用地圖模式\]。  您可以在 \[原始檔概觀\] 下拉式清單中選擇寬度。  
  
     啟用地圖模式且寬度設定為 \[中\] 時，搜尋範例的外觀如下：  
  
     ![地圖模式中的捲軸](../ide/media/enhancedscrollbar.png "EnhancedScrollbar")  
  
2.  如果您在地圖模式中的捲軸上，想要一邊上下移動游標，一邊預覽程式碼時，請選取 \[顯示預覽工具提示\] 選項。  其外觀如下：  
  
     ![包含工具提示的捲軸](../ide/media/enhancedscrollbarsearchtooltip.png "EnhancedScrollbarSearchTooltip")  
  
     如果您想要保留地圖模式的捲動行為與預覽工具提示，但不想看到原始程式碼概觀，可以將 \[原始檔概觀\] 設為 \[關閉\]。