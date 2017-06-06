---
title: "進階安全性設定對話方塊 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.err.debug_in_zone_no_hostproc"
  - "vs.err.debug_in_zone_no_hostproc:11310"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "[進階安全性設定] 對話方塊"
ms.assetid: 2e7aefe9-6d20-4f3e-b257-aee1ebcc6f5d
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# 進階安全性設定對話方塊
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

這個對話方塊可讓您指定與區域中的偵錯相關的安全性設定。  
  
 若要存取此對話方塊，請選取 \[**方案總管**\] 中的專案節點，然後按一下 \[**專案**\] 功能表上的 \[**屬性**\]。  當 \[**專案設計工具**\] 出現時，請按一下 \[**安全性**\] 索引標籤。  在 \[**安全性**\] 頁中，依序選取 \[**啟用 ClickOnce 安全性設定**\] 和 \[**這是部分信任的應用程式**\]，然後按一下 \[**進階**\]。  
  
## UIElement 清單  
 **以選取的使用權限集合對此應用程式進行偵錯**  
 如果您選取這個核取方塊，則在偵錯時會使用 \[**安全性**\] 頁面上所選取的使用權限集合。  根據預設，這個選項是選取的。  
  
 為了可以在安全性區域 \(Security Zone\) 中進行偵錯，必須啟用這個選項以及 \[**啟用 Visual Studio 裝載處理序**\] 選項 \(可以在 \[**專案設計工具**\] 的 \[**偵錯**\] 頁面上找到\)。  
  
 如果是 WPF Web 瀏覽器應用程式專案，\[**以選取的使用權限集合對此應用程式進行偵錯**\] 選項為核取且停用。  
  
 **允許應用程式存取它的來源網站**  
 如果您選取這個核取方塊，可以讓應用程式存取發行它的網站或伺服器共用。  根據預設，這個選項是選取的。  
  
 **將下列 URL 視為此應用程式的下載位置來進行偵錯**  
 如果要讓應用程式存取對應於您在 \[**發行**\] 頁面上所指定的 \[**安裝 URL**\] 網站或伺服器共用，請在此處輸入該 URL。  這個選項只有在選取 \[**允許應用程式存取它的來源網站**\] 時才能使用。  
  
## 請參閱  
 [專案設計工具、安全性頁](../../ide/reference/security-page-project-designer.md)