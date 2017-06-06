---
title: "錯誤清單視窗 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ErrorList
helpviewer_keywords:
- Task List
- build errors
- Error List window
- errors [Visual Studio], Error List window
ms.assetid: b7f6d45a-733b-4ad8-bc2f-737a37509e56
caps.latest.revision: 32
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 11c0b7e3bf572aa99610acf6b218cccf360ed7ba
ms.lasthandoff: 02/22/2017

---
# <a name="error-list-window"></a>錯誤清單視窗
> [!NOTE]
>  錯誤清單會顯示特定錯誤訊息的相關資訊。 您可以從 [輸出] 視窗複製錯誤碼或錯誤字串文字。 若要顯示 [輸出] 視窗，請按下 Ctrl+Alt+O。 請參閱[輸出視窗](../../ide/reference/output-window.md)。  
  
 您可以使用 [錯誤清單] 視窗，更快速地開發應用程式。 例如，您可以進行下列工作：  
  
-   於撰寫程式碼時，顯示發生的錯誤、警告和訊息。  
  
-   尋找 IntelliSense 標記的語法錯誤。  
  
-   套用企業樣板原則時，尋找部署錯誤、特定靜態分析錯誤與偵測到的錯誤。  
  
-   按兩下任何錯誤訊息項目開啟發生問題的檔案，然後移動到錯誤的位置。  
  
-   篩選已顯示的項目，以及每個項目所要顯示的資訊欄位。  
  
-   搜尋特定詞彙，以及將搜尋範圍限制在目前的專案或文件。  
  
 若要顯示 [錯誤清單]，請按一下 [檢視]/[錯誤清單]，或按 **CTRL+\\+E**。  
  
 您可以選擇 [錯誤]、[警告] 和 [訊息] 索引標籤來查看不同的層級資訊。  
  
 若要排序清單，請按一下任何資料行標頭。 若要以另一個資料行來重新排序，請按住 SHIFT 鍵，然後按一下其他的資料行標頭。 若要選取要顯示和隱藏的資料行，請從捷徑功能表中選擇 [顯示行]。 若要變更已顯示的資料行順序，請將任一資料行標頭拖曳到左邊或右邊。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與此處所描述的不同。 如果要變更設定，請按一下 [工具]/[匯入和匯出設定]。 如需詳細資訊，請參閱 [Visual Studio 中的自訂開發設定](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## <a name="error-list-filters"></a>錯誤清單篩選條件  
 在兩個下拉式方塊中有兩種篩選型別，一個位於工具列的右邊，一個位於工具列的左邊。 位於工具列左邊的下拉式清單會指定一組可使用的程式碼檔案 ([整個解決方案]、[開啟的文件]、[目前專案] 和 [目前文件])。  
  
 您可以限制搜尋範圍，以分析和處理錯誤群組。 例如，您可以專注於阻礙專案編譯的核心錯誤。 範圍選項包含：  
  
1.  **開啟的文件**：顯示開啟文件的錯誤、警告和訊息。  
  
2.  **目前專案**：顯示**編輯器**中目前選取之文件的專案，或方案總管中選取之專案的錯誤、警告和訊息。  
  
    > [!NOTE]
    >  如果目前選取的文件專案不同於方案總管中選取的專案，則會變更錯誤、警告和訊息的篩選清單。  
  
3.  **目前文件**：顯示**編輯器**或方案總管中目前選取之文件的錯誤、警告和訊息。  
  
 如果搜尋結果目前有套用篩選條件，篩選條件名稱會顯示在 [錯誤清單] 標題列中。 [錯誤]、[警告] 和 [訊息] 按鈕即會顯示目前出現的已篩選項目數和項目總數；例如，按鈕會顯示「x，共 Y 項錯誤」。 如果未套用任何篩選條件，標題列只顯示「錯誤清單」。  
  
 位於工具列右邊的清單會指定是否要從組建 (從建置作業所產生的錯誤) 顯示錯誤，或從 IntelliSense (執行組建之前偵測到的錯誤) 顯示錯誤，或同時從兩者顯示錯誤。  
  
## <a name="search"></a>搜尋  
 您可以使用 [錯誤清單] 工具列右邊的 [搜尋錯誤清單] 文字方塊，從錯誤清單中找出特定錯誤。 您可以在錯誤清單中任何可見的資料行上搜尋，而搜尋結果永遠是依據有排序優先順序的資料行排序，而不是依據套用的查詢或篩選條件。 當 [錯誤清單] 顯示時，如果您選擇 **Esc** 鍵，則可以清除搜尋詞彙和篩選的搜尋結果。 您也可以按一下文字方塊右邊的 **X** 將它清除。  
  
## <a name="save"></a>儲存  
 您可以複製錯誤清單並將它儲存到檔案。 選取您要複製的錯誤，以滑鼠右鍵按一下選取範圍，然後在操作功能表中選取 [複製]。 然後您可以將錯誤貼至檔案。 如果您將錯誤貼至 Excel 試算表，欄位會顯示為不同的資料行。  
  
## <a name="ui-element-list"></a>UI 項目清單  
 嚴重性  
 會顯示不同類型的 [錯誤清單] 項目 ([錯誤]、[訊息]、[警告]、[警告 (使用中)] 和 [警告 (非使用中)])。  
  
 程式碼  
 會顯示錯誤碼。  
  
 說明  
 會顯示項目的文字。  
  
 專案  
 會顯示目前專案的名稱。  
  
 檔案  
 會顯示檔案名稱。  
  
 線  
 會顯示發生錯誤的行。