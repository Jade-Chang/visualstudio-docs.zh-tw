---
title: "將類型移到相符的檔案-重構 (C#) |Microsoft 文件"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40f58c34-c50f-4297-91b2-2e243380dcc9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9fa5a15f9c8e688c973594309efbfa6cb5d10e8b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="move-a-type-to-a-matching-file-in-c"></a>將類型移到 C# 中的比對的檔案 #
**項目：**可讓您選取的類型移至具有相同名稱的個別檔案。

**當：**您想要區隔的相同檔案中有多個類別、 結構、 介面、 等等。  

**原因：**將多個型別放在相同的檔案可讓容易找到這些類型。  將類型移至具有相同名稱的檔案，程式碼變得更容易閱讀和您更輕鬆地瀏覽。

**如何：**

1. 反白顯示，或將文字指標放置要移動之類型的名稱：

   ![反白顯示的程式碼](media/movetype_highlight.png)

1. 接下來，執行下列其中一項：
   * **鍵盤**
     * 按**Ctrl +。** 觸發程序**快速控制項目及重構**功能表，然後選取**類型移至*TypeName*.cs**從預覽視窗快顯視窗，其中*TypeName*是您所選取的類型名稱。
   * **滑鼠**
     * 以滑鼠右鍵按一下程式碼中，選取**快速控制項目及重構**功能表，然後選取**類型移至*TypeName*.cs**從預覽視窗快顯視窗，其中*TypeName*是您所選取的類型名稱。

   型別將會立即移至具有該名稱在您的方案內新的檔案。

   ![Inline 結果](media/movetype_result.png)

## <a name="see-also"></a>另請參閱  
[重構 (C#)](../refactoring-csharp.md)