---
title: "如何：比較程式碼剖析工具資料檔案 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vsperf.choosediffbinaries"
helpviewer_keywords: 
  - "分析工具結果檔案, 如何比較"
  - "程式碼剖析工具, 如何比較分析工具結果檔案"
ms.assetid: 1905b45d-c6b3-43c8-87b1-1aee734f37f9
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# 如何：比較程式碼剖析工具資料檔案
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以建立差異比對 \("Diff"\) 報告或檢視，以比較兩個不同的分析工具 \(Profiler\) 資料檔案 \(.vsp 或 .vsps\) 的結果。  差異比較會顯示兩個程式碼剖析工作階段之間的效能差異、效能衰退和改善。  
  
 差異比對報告會顯示資料的資料表檢視。  資料表中則顯示相較於基準的差異或變化。  計算的方法是找出舊的值 \(也就是基準值\) 以及新的分析結果值兩者之間的差異。  
  
 分析工具資料的比較基準可以是程式碼中的函式、應用程式中的模組、程式行、指定指標 \(IP\) 以及型別。  
  
 您可以設定臨界值，藉以減少雜訊，並依指定的量篩選出資料表檢視中尚未變更的任何資料。  
  
### 在效能總管中建立專案的比較檔案檢視  
  
1.  在 \[**效能總管**\] 中的 \[**報告**\] 底下，選取要用來當做比較基準值的 .vsp 或 .vsps 報告檔。  
  
2.  選取要比較的 .vsp 或 .vsps 報告檔。  
  
3.  以滑鼠右鍵按一下其中一個已選取的檔案，然後按一下 \[**比較報告**\]。  
  
### 若要比較值  
  
1.  在 \[報告檢視\] 視窗中選取 \[**比較報告**\] 索引標籤。  
  
2.  在 \[**資料表**\] 下拉式清單中，選取要比較的函式或模組。  
  
3.  在 \[**資料行**\] 下拉式清單中，選取要比較的值。  
  
4.  \(選擇性\) 在 \[**臨界值**\] 中輸入值。  
  
5.  按一下 \[**套用**\]。  
  
### 若要比較報告檔  
  
1.  在 \[**分析** \] 功能表上，選取 \[**比較效能報告**\]。  
  
2.  在 \[**選取要進行比較的分析檔案**\] 視窗中，瀏覽並選取 \[**基準檔案**\] 分析檔案 \(.vsp 或 .vsps\) 和 \[**比較檔案**\] \(.vsp or .vsps\)。  
  
3.  按一下 \[**確定**\]。