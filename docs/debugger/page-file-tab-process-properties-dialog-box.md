---
title: 分頁檔索引標籤程序屬性對話方塊、 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: daf41a06-8a55-48f6-95f5-49a8416bd308
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 624be76badf8d57b060198c2ee910ead17b5efcb
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
ms.locfileid: "31472964"
---
# <a name="page-file-tab-process-properties-dialog-box"></a>處理序屬性對話方塊、分頁檔索引標籤
使用**分頁檔**檢查分頁檔的程序 索引標籤。 若要顯示[處理序屬性對話方塊](../debugger/process-properties-dialog-box.md)，焦點移至[處理序檢視](../debugger/processes-view.md)視窗。 在樹狀目錄中，選取任何處理序節點，然後選擇 **屬性**從**檢視**功能表。  
  
 下列設定都適用於**分頁檔** 索引標籤：  
  
|進入|描述|  
|-----------|-----------------|  
|**分頁檔位元組**|目前此處理序正在使用中的分頁檔的頁面數目。 分頁檔會儲存資料的處理序使用，但不是包含其他檔案中的頁面。 分頁檔由所有處理程序，並在分頁檔的空間不足可能會導致錯誤，而其他處理序正在執行。|  
|**尖峰分頁檔位元組**|此程序已使用分頁檔案中頁面的數目上限。|  
|**分頁錯誤**|此程序中執行之執行緒的分頁錯誤數目。 當執行緒參照不在其工作集主記憶體中的虛擬記憶體分頁時，就會發生分頁錯誤。 因此，頁面將不會擷取從磁碟如果它在待命清單上，因此在主記憶體，或如果它正由另一個使用共用分頁處理。|