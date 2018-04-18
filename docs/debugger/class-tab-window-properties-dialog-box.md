---
title: 類別索引標籤，視窗屬性對話方塊 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: reference
helpviewer_keywords:
- Window Properties dialog box, Class Tab
ms.assetid: eaec9f07-d580-436d-934d-76c4e59439aa
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 573eb3f9cbcaedddc67524e81b2508df2112de04
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="class-tab-window-properties-dialog-box"></a>視窗屬性對話方塊、類別索引標籤
使用**類別**索引標籤，以顯示在選取的視窗類別資訊。 若要顯示[視窗屬性對話方塊](../debugger/window-properties-dialog-box.md)，焦點移至[視窗檢視](../debugger/windows-view.md)視窗。 在樹狀目錄中，選取視窗中的任何節點，然後選擇 **屬性**從**檢視**功能表。  
  
 下列設定都適用於**類別** 索引標籤：  
  
|進入|描述|  
|-----------|-----------------|  
|**類別名稱**|此視窗類別名稱 （或序數）。|  
|**類別樣式**|類別樣式代碼的組合。|  
|**類別位元組**|此視窗類別相關聯的應用程式特定資料。|  
|**類別元素**|此類別所傳回 atom **RegisterClass**呼叫。|  
|**執行個體控制代碼**|註冊類別之模組的執行個體控制代碼。 執行個體控制代碼不是唯一的。|  
|**視窗位元組**|與這個類別的每個視窗相關聯的額外位元組數目。 這些位元組的意義取決於應用程式。 展開清單方塊，請參閱 DWORD 格式中的位元組值。|  
|**視窗程序**|目前的位址**WndProc**適用於這個類別的 windows 函式。 這不同於**視窗程序**上**一般**索引標籤上，如果視窗子類別化。|  
|**功能表名稱**|這個類別 （如果有任何功能表 「 無 」） 的 windows 與相關聯的主功能表的名稱。|  
|**圖示的控制代碼**|這個類別 （如果有任何圖示 「 無 」） 的 windows 與相關聯的圖示的控制代碼。|  
|**資料指標控制代碼**|這個類別 （如果有任何資料指標 「 無 」） 的 windows 與相關聯的游標控制代碼。|  
|**背景筆刷**|這個類別，或其中一個預先定義 COLOR_ * 色彩繪製視窗背景 （如果有任何筆刷 「 無 」） 的 windows 與相關聯的背景筆刷的控制代碼。|