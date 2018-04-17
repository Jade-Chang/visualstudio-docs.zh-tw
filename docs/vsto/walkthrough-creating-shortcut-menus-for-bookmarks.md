---
title: 逐步解說： 建立書籤的捷徑功能表 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- context menus, Word
- Bookmark control, events
- shortcut menus, Word
- menus, creating in Office applications
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6d54d23330c6d5fab836f168a291b15b90379117
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-creating-shortcut-menus-for-bookmarks"></a>逐步解說：建立書籤的快速鍵功能表
  本逐步解說示範如何建立快顯功能表<xref:Microsoft.Office.Tools.Word.Bookmark>Word 的文件層級自訂中的控制項。 當使用者以滑鼠右鍵按一下書籤中的文字時，快顯功能表隨即出現，並提供用來格式化文字的使用者選項。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 這個逐步解說將說明下列工作：  
  
-   [建立專案](#BKMK_CreateProject)。  
  
-   [將文字和書籤加入至文件](#BKMK_addtextandbookmarks)。  
  
-   [將命令加入至快顯功能表](#BKMK_AddCmndsShortMenu)。  
  
-   [格式化文字方塊中的書籤](#BKMK_formattextbkmk)。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] 或 [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]  
  
##  <a name="BKMK_CreateProject"></a> 建立專案  
 第一個步驟是在 Visual Studio 中建立的 Word 文件專案。  
  
#### <a name="to-create-a-new-project"></a>建立新的專案  
  
-   建立具有名稱的 Word 文件專案**我的書籤快顯功能表**。 在精靈中，選取**建立新的文件**。 如需詳細資訊，請參閱 [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
     Visual Studio 設計工具中開啟新的 Word 文件，並將**我的書籤快顯功能表**專案加入**方案總管 中**。  
  
##  <a name="BKMK_addtextandbookmarks"></a> 將文字和書籤加入至文件  
 文件中加入一些文字，然後加入兩個重疊書籤。  
  
#### <a name="to-add-text-to-your-document"></a>將文字加入文件  
  
-   在文件出現在專案設計工具中，輸入下列文字。  
  
     **這是您以滑鼠右鍵按一下書籤中的文字時，建立快顯功能表的範例。**  
  
#### <a name="to-add-a-bookmark-control-to-your-document"></a>若要加入書籤控制項加入文件  
  
1.  在**工具箱**，從**Word 控制項**索引標籤，拖曳<xref:Microsoft.Office.Tools.Word.Bookmark>控制項加入文件。  
  
     **加入書籤控制項** 對話方塊隨即出現。  
  
2.  選取 「 建立快顯功能表文字上按一下滑鼠右鍵 」 的文字，然後按一下 **確定**。  
  
     `bookmark1` 會加入至文件。  
  
3.  加入另一個<xref:Microsoft.Office.Tools.Word.Bookmark>控制字組 」 以滑鼠右鍵按一下書籤中的文字 」。  
  
     `bookmark2` 會加入至文件。  
  
    > [!NOTE]  
    >  「 以滑鼠右鍵按一下文字 」 會在這兩字`bookmark1`和`bookmark2`。  
  
 當在設計階段加入文件書籤<xref:Microsoft.Office.Tools.Word.Bookmark>建立控制項。 您可以針對數個事件書籤的程式。 您可以撰寫程式碼<xref:Microsoft.Office.Tools.Word.Bookmark.BeforeRightClick>事件的書籤，以便當使用者按一下滑鼠右鍵在書籤，文字會出現捷徑功能表。  
  
##  <a name="BKMK_AddCmndsShortMenu"></a> 將命令加入至快顯功能表  
 將按鈕加入到文件上按一下滑鼠右鍵時出現的捷徑功能表。  
  
#### <a name="to-add-commands-to-a-shortcut-menu"></a>若要將命令加入快顯功能表  
  
1.  新增**功能區 XML**項目加入專案。 如需詳細資訊，請參閱 [如何：開始自定義功能區](../vsto/how-to-get-started-customizing-the-ribbon.md)。  
  
2.  在**方案總管 中**，選取**ThisDocument.cs**或**ThisDocument.vb**。  
  
3.  在功能表列上選擇 [檢視] 、[程式碼] 。  
  
     **ThisDocument**類別隨即開啟 程式碼編輯器。  
  
4.  將下列程式碼加入**ThisDocument**類別。 此程式碼會覆寫 CreateRibbonExtensibilityObject 方法，而此功能區 XML 類別傳回 Office 應用程式。  
  
     [!code-csharp[Trin_Word_Document_Menus#1](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#1)]
     [!code-vb[Trin_Word_Document_Menus#1](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb#1)]  
  
5.  在方案總管 中選取功能區 XML 檔案。 根據預設，功能區 XML 檔名為 Ribbon1.xml。  
  
6.  在功能表列上選擇 [檢視] 、[程式碼] 。  
  
     功能區 XML 檔案隨即在程式碼編輯器中開啟。  
  
7.  在程式碼編輯器中，會取代下列程式碼中的功能區 XML 檔案的內容。  
  
    ```  
    <?xml version="1.0" encoding="UTF-8"?>  
    <customUI xmlns="http://schemas.microsoft.com/office/2009/07/customui" onLoad="Ribbon_Load">  
      <contextMenus>  
        <contextMenu idMso="ContextMenuText">  
          <button id="BoldButton" label="Bold" onAction="ButtonClick"          
               getVisible="GetVisible" />  
          <button id="ItalicButton" label="Italic" onAction="ButtonClick"   
              getVisible="GetVisible"/>  
        </contextMenu>  
      </contextMenus>  
    </customUI>  
    ```  
  
     此程式碼會將兩個按鈕加入至文件上按一下滑鼠右鍵時出現的捷徑功能表。  
  
8.  在**方案總管] 中**，以滑鼠右鍵按一下`ThisDocument`，然後按一下 [**檢視程式碼**。  
  
9. 宣告下列變數和書籤變數類別層級。  
  
     [!code-csharp[Trin_Word_Document_Menus#2](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#2)]
     [!code-vb[Trin_Word_Document_Menus#2](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb#2)]  
  
10. 在**方案總管 中**，選取功能區程式碼檔案。 根據預設，功能區程式碼檔名為**Ribbon1.cs**或**Ribbon1.vb**。  
  
11. 在功能表列上選擇 [檢視] 、[程式碼] 。  
  
     功能區程式碼檔案隨即在程式碼編輯器中開啟。  
  
12. 在功能區程式碼檔案中，加入下列方法。 這是您已加入文件的捷徑功能表的兩個按鈕的回呼方法。 這個方法會決定這些按鈕是否出現快速鍵功能表中。 只有當您以滑鼠右鍵按一下書籤內的文字，則會出現粗體和斜體按鈕。  
  
     [!code-csharp[Trin_Word_Document_Menus#5](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/ribbon1.cs#5)]
     [!code-vb[Trin_Word_Document_Menus#5](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/ribbon1.vb#5)]  
  
##  <a name="BKMK_formattextbkmk"></a> 格式化文字方塊中的書籤  
  
#### <a name="to-format-the-text-in-the-bookmark"></a>若要格式化文字方塊中的書籤  
  
1.  在功能區程式碼檔案中，加入`ButtonClick`事件處理常式，將格式套用至書籤。  
  
     [!code-csharp[Trin_Word_Document_Menus#6](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/ribbon1.cs#6)]
     [!code-vb[Trin_Word_Document_Menus#6](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/ribbon1.vb#6)]  
  
2.  **方案總管 中**，選取**ThisDocument.cs**或**ThisDocument.vb**。  
  
3.  在功能表列上選擇 [檢視] 、[程式碼] 。  
  
     **ThisDocument**類別隨即開啟 程式碼編輯器。  
  
4.  將下列程式碼加入**ThisDocument**類別。  
  
     [!code-csharp[Trin_Word_Document_Menus#3](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#3)]
     [!code-vb[Trin_Word_Document_Menus#3](../vsto/codesnippet/VisualBasic/trin_word_document_menus.vb/thisdocument.vb#3)]  
  
    > [!NOTE]  
    >  您必須撰寫程式碼以處理重疊書籤的情況。 如果沒有這樣做，依預設，程式碼會呼叫選取範圍中的所有書籤。  
  
5.  在 C# 中，您必須加入書籤控制項的事件處理常式<xref:Microsoft.Office.Tools.Word.Document.Startup>事件。 如需建立事件處理常式的詳細資訊，請參閱[How to： 在 Office 專案中建立事件處理常式](../vsto/how-to-create-event-handlers-in-office-projects.md)。  
  
     [!code-csharp[Trin_Word_Document_Menus#4](../vsto/codesnippet/CSharp/trin_word_document_menus.cs/thisdocument.cs#4)]  
  
## <a name="testing-the-application"></a>測試應用程式  
 測試文件，以確認書籤中的文字上按一下滑鼠右鍵捷徑功能表中會出現粗體和斜體功能表項目，且已正確格式化的文字。  
  
#### <a name="to-test-your-document"></a>測試文件  
  
1.  請按 F5 執行您的專案。  
  
2.  在第一個書籤中，按一下滑鼠右鍵，然後按一下**粗體**。  
  
3.  確認所有的文字中`bookmark1`格式化為粗體。  
  
4.  以滑鼠右鍵按一下的文字個重疊書籤，然後按一下 **斜體**。  
  
5.  確認所有的文字中`bookmark2`是斜體、 和中只有部分中的文字`bookmark1`重疊`bookmark2`為斜體。  
  
## <a name="next-steps"></a>後續步驟  
 接著可以執行下列一些工作：  
  
-   撰寫程式碼來回應在 Excel 中的主控制項的事件。 如需詳細資訊，請參閱 [逐步解說：針對 NamedRange 控制項的事件進行程式設計](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)。  
  
-   使用核取方塊變更格式書籤中。 如需詳細資訊，請參閱[逐步解說： 變更文件格式使用核取方塊控制項](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md)。  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說使用 Word](../vsto/walkthroughs-using-word.md)   
 [Office UI 自訂](../vsto/office-ui-customization.md)   
 [使用擴充物件自動化 Word](../vsto/automating-word-by-using-extended-objects.md)   
 [書籤控制項](../vsto/bookmark-control.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
  
  