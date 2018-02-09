---
title: "Visual Studio R 工具中的變數總管 | Microsoft Docs"
description: "Visual Studio 中的 [變數總管] 會顯示目前 R 工作階段中指定範圍內的所有變數。"
ms.custom: 
ms.date: 01/24/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: 
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- data-science
ms.openlocfilehash: 1d766d3ad6a48a46c3f781b8a87e5f388de93e74
ms.sourcegitcommit: ba29e4d37db92ec784d4acf9c6e120cf0ea677e9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2018
---
# <a name="variable-explorer"></a>變數總管

使用 [R 工具] > [Windows] > [變數總管] (如果曾使用 [R 工具] > [資料科學設定] 則為 Ctrl+8) 開啟的 [變數總管] 視窗，會在目前的 R 工作階段中顯示指定範圍內的所有變數。 例如，如果您要開啟變數總管，並在[互動視窗](interactive-repl-for-r-in-visual-studio.md)中輸入下列行：

```R
x <- 42
y <- 43
n <- c(1,2,3,5,8,13)
```

變數總管視窗會隨即出現，如下所示︰

![Visual Studio 中的變數總管視窗](media/variable-explorer-window.png)

如已在工作階段中定義了更複雜的 R 資料框架，您可以巡覽資料。 例如，在執行 `cars <- mtcars` 之後，您可以展開變數總管中的不同節點來巡覽資料集︰

![變數總管的展開檢視](media/variable-explorer-expanded-results.png)

若要刪除變數，請以滑鼠右鍵按一下並選取 [刪除]，或選取變數，然後按 Delete 鍵。

您也可以使用累加搜尋，在資料框架中搜尋觀察值。 首先，展開您要搜尋之資料框架中的節點，然後在搜尋方塊中輸入搜尋字詞。

## <a name="details-table-view"></a>詳細 (資料表) 檢視

因為資料通常是表格式的，所以您可以選取放大鏡圖示或以滑鼠右鍵按一下選取 [顯示詳細資料]，將任何複雜的資料類型當成個別的資料表檢視。

![變數總管表格檢視](media/variable-explorer-table-view.png)

按一下資料行標題按資料行排序資料 (輪換遞增和遞減)。 按住 Shift 鍵並按一下其他資料行，將這些資料行也新增至排序。 按一下資料行但不按 Shift 鍵會傳回單一資料行排序。

您按下的資料行標題順序會決定執行的排序順序。 例如，用 Shift 鍵按一下 **cyl** 資料行，然後用 Shift 鍵按兩下 **mpg** 資料行，清單會依汽缸遞增、每加侖英哩數遞減排序︰

![依兩個資料行排序的資料表格檢視。](media/variable-explorer-table-view-sorting.png)

因為變數總管和表格檢視使用不同的 Visual Studio 視窗，所以您可以依自己心意排列它們進行並存工作。 如需一般指示，請參閱[在 Visual Studio 中自訂視窗版面配置](../ide/customizing-window-layouts-in-visual-studio.md)。

## <a name="open-in-excel-or-other-csv-capable-application"></a>在 Excel (或其他可使用 CSV 的應用程式) 中開啟

如需進一步的操作和分析，將工作階段變數匯出成 CSV 通常很有用。 使用變數總管中每個節點旁邊的小型 Excel 圖示 (![Excel 匯出圖示](media/variable-explorer-excel-icon.png))，或以滑鼠右鍵按一下項目，然後選取 [在 CSV 應用程式中開啟]，即可匯出。 選取圖示會將資料寫入 `%userprofile%\Documents\RTVS_CSV_Exports` 資料夾的新 CSV 檔案並啟動該檔案，這會在任何與 `.csv` 延伸模組建立關聯的應用程式中開啟檔案。

## <a name="scopes"></a>範圍

變數總管預設會開啟至全域範圍。 您可以從視窗頂端的下拉式清單中選取套件，切換到套件範圍。

![顯示套件範圍的變數總管](media/variable-explorer-package-scopes.png)

您也可以在於偵錯工具中斷點處停止時，切換到函式範圍 (請注意，變數總管不會自動切換至被偵錯的程式碼函式範圍)︰

![在偵錯期間顯示資料框架的變數總管](media/variable-explorer-as-locals-window.png)

當您逐步執行偵錯工具的程式碼時，例如在函式中顯示區域變數，變數總管會自動變更函式範圍。

## <a name="importing-data-into-variable-explorer"></a>將資料匯入變數總管

變數總管工具列上的兩個命令，也可以透過 [R 工具] > [資料] 功能表取得，將外部 CSV 資料集匯入 R 工作階段︰[將資料集從 Web URL 匯入 R 工作階段] 和 [將資料集從文字檔匯入 R 工作階段]。 

一旦找到要匯入的 CSV 檔案，Visual Studio 就會顯示 [匯入資料集] 對話方塊，您可在此選擇如何控制該資料檔案的剖析方式 (也就是欄位分隔符號為何以及如何處理引號)。 您也可以預覽匯入的資料框架和原始資料檔案：

![匯入資料集對話方塊](media/variable-explorer-import-dataset-dialog.png)
