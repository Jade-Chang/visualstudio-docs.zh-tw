---
title: 尋找和取代文字
ms.date: 05/07/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.find
- vs.findreplacecontrol
- vs.findreplace.findsymbol
- vs.findreplace.symbol
- findresultswindow
- vs.findreplace.quickreplace
- vs.findsymbol
- vs.findinfiles
- vs.findresults1
- vs,findsymbolwindow
- vs.findreplace.quickfind
- vs.lookin
- vs.replace
helpviewer_keywords:
- text searches
- Replace in Files dialog box
- Find in Files dialog box
- text searches, finding and replacing text
- text, finding and replacing
- find and replace
- find text
- replace text
ms.assetid: a62545c3-1570-4d12-99fb-a82607eb35a1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7051b90dde45965b76e8a9e08b33b5326ff2848c
ms.sourcegitcommit: 56018fb1f52f17bf35ae2ce71c50c763486e6173
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33106748"
---
# <a name="find-and-replace-text"></a>尋找和取代文字

您可以在 Visual Studio 編輯器中使用[尋找和取代](#find-and-replace-control)或[檔案中尋找/取代](#find-in-files-and-replace-in-files)來尋找和使用文字。

> [!TIP]
> 如果您要重新命名程式碼符號 (例如變數和方法)，比起使用尋找和取代，最好是*[重構](../ide/reference/rename.md)* 它們。 重構是智慧型功能，可了解範圍，而尋找和取代則會盲目地取代所有執行個體。

尋找和取代功能位在編輯器的某些其他文字型視窗 (例如 [尋找結果] 視窗)、設計工具視窗 (例如 XAML 設計工具和 Windows Form 設計工具)，以及工具視窗中。

您可以將搜尋範圍設為目前文件、目前方案或一組自訂的資料夾。 您也可以指定一組副檔名來搜尋多個檔案。 請使用 .NET [規則運算式](../ide/using-regular-expressions-in-visual-studio.md)來自訂搜尋語法。

> [!TIP]
> [尋找/命令](../ide/find-command-box.md)方塊可提供作為工具列控制項，但預設為不可見。 若要顯示 [尋找/命令] 方塊，請選取 [標準] 工具列上的 [新增或移除按鈕]，然後選取 [尋找]。

## <a name="find-and-replace-control"></a>尋找和取代控制項

[尋找和取代] 控制項會出現在程式碼編輯器視窗的右上角。 [尋找和取代] 控制項會立即反白顯示目前文件中每個出現的指定搜尋字串。 您可以選擇搜尋控制項上的 [找下一個] 按鈕或 [找上一個] 按鈕，以從第一個出現位置巡覽至另一個出現位置。

![尋找和取代控制項](media/find-and-replace-box.png)

您可以選擇 [尋找] 文字方塊旁的按鈕，以存取取代選項。 若要一次執行一個取代，請選擇 [取代] 文字方塊旁的 [取代下一個] 按鈕。 若要取代所有相符項目，請選擇 [全部取代] 按鈕。

若要變更相符項目的醒目提示色彩，請選擇 [工具] 功能表，並選取 [選項]，然後選擇 [環境]，再選取 [字型和色彩]。 在 [顯示設定] 清單中，選取 [文字編輯器]，然後在 [顯示項目] 清單中選取 [尋找醒目提示 (副檔名)]。

### <a name="search-tool-windows"></a>搜尋工具視窗

您可以選取 [編輯] > [尋找和取代] 或按 **Ctrl+F**，以使用程式碼或文字視窗中的 [尋找] 控制項 (例如 [輸出] 視窗和 [尋找結果] 視窗)。

部分工具視窗中也提供 [尋找] 控制項的版本。 例如，您可以在搜尋方塊中輸入文字，以篩選 [工具箱] 視窗中的控制項清單。 可讓您搜尋其內容的其他工具視窗包含 [方案總管]、[屬性] 視窗和 [Team Explorer]。

## <a name="find-in-files-and-replace-in-files"></a>檔案中尋找和檔案中取代

[檔案中尋找/取代] 的運作方式與 [尋找和取代] 控制項類似，不同之處在於您可以定義搜尋範圍。 您不只可以在編輯器中搜尋目前開啟的檔案，還可以搜尋所有開啟的文件、整個方案、目前專案以及選取的資料夾集。 您也可以依副檔名進行搜尋。 若要存取 [檔案中尋找/取代] 對話方塊，請選取 [編輯] 功能表上的 [尋找和取代] 或按 **Ctrl+Shift+F**。

![檔案中尋找對話方塊](media/find-in-files-box.png)

### <a name="find-results"></a>尋找結果

當您選擇 [全部尋找] 時，會開啟 [尋找結果] 視窗，並列出您搜尋的相符項目。 在清單中選取結果會顯示相關聯的檔案，並反白顯示相符項目。 如果尚未開啟檔案進行編輯，則會在索引標籤牆右側的預覽索引標籤中開啟它。 您可以使用 [尋找] 控制項來搜尋 [尋找結果] 清單。

### <a name="create-custom-search-folder-sets"></a>建立自訂搜尋資料夾集

您可以選擇 [查詢] 方塊旁的 [選擇搜尋資料夾] 按鈕 (看起來就像 **...**)，來定義搜尋範圍。 在 [選擇搜尋資料夾] 對話方塊中，您可以指定一組要搜尋的資料夾，並且可以儲存規格，以在稍後重複使用。

> [!TIP]
> 如果遠端電腦的磁碟機已對應至本機電腦，您可以指定遠端電腦上要搜尋的資料夾。

### <a name="create-custom-component-sets"></a>建立自訂元件集

您可以選擇 [查詢] 方塊旁的 [編輯自訂元件集] 按鈕，將元件集定義為搜尋範圍。 您可以指定已安裝的 .NET 或 COM 元件、解決方案中所含的 Visual Studio 專案，或者任何組件或類型庫 (*.dll*、*.tlb*、*.olb*、*.exe* 或 *.ocx*)。 若要搜尋參考，請選取 [查詢參考] 方塊。

## <a name="see-also"></a>另請參閱

- [在 Visual Studio 中使用規則運算式](../ide/using-regular-expressions-in-visual-studio.md)
- [在 Visual Studio 中重構程式碼](../ide/refactoring-in-visual-studio.md)