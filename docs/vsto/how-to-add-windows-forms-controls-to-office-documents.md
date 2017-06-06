---
title: "如何：將 Windows Form 控制項加入至 Office 文件"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "控制項 [Visual Studio 中的 Office 程式開發], Windows Form 控制項"
  - "文件 [Visual Studio 中的 Office 程式開發], Windows Form 控制項"
  - "Office 文件 [Visual Studio 中的 Office 程式開發], Windows Form 控制項"
  - "Windows Form 控制項 [Visual Studio 中的 Office 程式開發], 加入"
ms.assetid: 4d188ad2-8e17-4eb0-8422-2ff56c683e3d
caps.latest.revision: 54
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# 如何：將 Windows Form 控制項加入至 Office 文件
  您可以在文件層級專案的設計階段中，將 Windows Form 控制項加入 Microsoft Office Excel 和 Microsoft Office Word 文件。  您可以在文件層級自訂和 VSTO 增益集的執行階段中，加入控制項。  例如，您可以將 <xref:Microsoft.Office.Tools.Excel.Controls.ComboBox> 控制項加入工作表，讓使用者可以從選項清單中進行選取。  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
 本主題將說明下列工作：  
  
-   [在設計階段加入控制項](#designtime)  
  
-   [在文件層級專案中的執行階段加入控制項](#runtimedoclevel)  
  
-   [在 VSTO 增益集中的執行階段加入控制項](#runtimeaddin)  
  
 ![視訊的連結](../vsto/media/playvideo.png "視訊的連結") 如需相關的影片示範，請參閱[如何：在執行階段將控制項加入文件介面？](http://go.microsoft.com/fwlink/?LinkId=132782)  
  
##  <a name="designtime"></a> 在設計階段加入控制項  
 您可以用幾種方式，透過文件層級專案，於設計階段將 Windows Form 控制項加入文件。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
#### 若要將 Windows Form 控制項拖曳至文件  
  
1.  在 Visual Studio 中建立或開啟 Excel 活頁簿專案或 Word 文件專案，如此才能在設計工具中看到文件。  如需建立專案的詳細資訊，請參閱[如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
2.  在 \[工具箱\] 的 \[通用控制項\] 索引標籤中，按一下要加入的控制項，並將其拖曳到文件。  
  
    > [!NOTE]  
    >  在 Excel 中選取控制項時，您會在 \[資料編輯列\] 看到 **\=EMBED\("WinForms.Control.Host",""\)** 。  這個文字是必要的，不應該刪除。  
  
#### 若要將 Windows Form 控制項拖曳至文件  
  
1.  在 Visual Studio 中建立或開啟 Excel 活頁簿專案或 Word 文件專案，如此才能在設計工具中看到文件。  如需建立專案的詳細資訊，請參閱[如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
2.  在 \[工具箱\] 的 \[通用控制項\] 索引標籤中，按一下要加入的控制項。  
  
3.  在文件上，在您希望成為控制項左上角的位置按一下，然後拖曳到希望成為控制項右下角的位置。  
  
     控制項會依指定的位置和大小加入文件。  
  
    > [!NOTE]  
    >  在 Excel 中選取控制項時，您會在 \[資料編輯列\] 看到 **\=EMBED\("WinForms.Control.Host",""\)** 。  這個文字是必要的，不應該刪除。  
  
#### 若要按一下控制項，將 Windows Form 控制項加入文件  
  
1.  在 Visual Studio 中建立或開啟 Excel 活頁簿專案或 Word 文件專案，如此才能在設計工具中看到文件。  如需建立專案的詳細資訊，請參閱[如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
2.  在 \[工具箱\] 的 \[通用控制項\] 索引標籤中，按一下要加入的控制項。  
  
3.  在文件中，按一下要加入控制項的位置。  
  
     控制項會依預設大小加入文件。  
  
    > [!NOTE]  
    >  在 Excel 中選取控制項時，您會在 \[資料編輯列\] 看到 **\=EMBED\("WinForms.Control.Host",""\)** 。  這個文字是必要的，不應該刪除。  
  
#### 若要按兩下控制項，將 Windows Form 控制項加入文件  
  
1.  在 Visual Studio 中建立或開啟 Excel 活頁簿專案或 Word 文件專案，如此才能在設計工具中看到文件。  如需建立專案的詳細資訊，請參閱[如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
2.  在 \[工具箱\] 的 \[通用控制項\] 索引標籤中，按兩下要加入的控制項。  
  
     控制項會加入文件或現用窗格的中央位置。  
  
    > [!NOTE]  
    >  在 Excel 中選取控制項時，您會在 \[資料編輯列\] 看到 **\=EMBED\("WinForms.Control.Host",""\)** 。  這個文字是必要的，不應該刪除。  
  
#### 若要按下 ENTER 鍵，將 Windows Form 控制項加入文件  
  
1.  在 Visual Studio 中建立或開啟 Excel 活頁簿專案或 Word 文件專案，如此才能在設計工具中看到文件。  如需建立專案的詳細資訊，請參閱[如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
2.  在 \[工具箱\] 的 \[通用控制項\] 索引標籤中，按一下要加入的控制項，然後按下 ENTER 鍵。  
  
     控制項會加入文件或現用窗格的中央位置。  
  
    > [!NOTE]  
    >  在 Excel 中選取控制項時，您會在 \[資料編輯列\] 看到 **\=EMBED\("WinForms.Control.Host",""\)** 。  這個文字是必要的，不應該刪除。  
  
##  <a name="runtimedoclevel"></a> 在文件層級專案中的執行階段加入控制項  
 您可以透過程式設計的方式，在執行階段將 Windows Form 控制項加入文件。  在 Word 中，請使用 `ThisDocument` 類別之 <xref:Microsoft.Office.Tools.Word.DocumentBase.Controls%2A> 屬性的方法。  在 Excel 中，請使用 `Sheet`*n* 類別之 <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Controls%2A> 屬性的方法。  每個方法都有數個多載，可讓您以不同方式指定控制項的位置。  
  
 當您在執行階段將 Windows Form 控制項加入文件時，若關閉文件，文件不會保存該控制項。  您可以在下一次開啟文件時重新建立該控制項。  如需詳細資訊，請參閱[在執行階段將控制項加入至 Office 文件](../vsto/adding-controls-to-office-documents-at-run-time.md)。  
  
#### 若要在執行階段加入 Windows Form 控制項  
  
1.  使用名為 Add\<*控制項類別*\> 的方法 \(其中 \<*控制項類別*\> 是您要加入的 Windows Form 控制項類別名稱，例如 <xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A>\)。  
  
     下列程式碼範例示範如何透過 Excel 文件層級專案，將 <xref:Microsoft.Office.Tools.Excel.Controls.Button> 加入 `Sheet1` 的 \[C5\] 儲存格。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#4)]  
  
##  <a name="runtimeaddin"></a> 在 VSTO 增益集中的執行階段加入控制項  
 您可以透過程式設計的方式，在執行階段將 Windows Form 控制項加入任何開啟的文件。  首先，請依據開啟的文件或工作表，產生一個主項目。  然後，在 Word 中使用新主項目之 <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> 屬性的方法。  在 Excel 中，則使用新主項目之 <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> 屬性的方法。  每個方法都有數個多載，可讓您以不同方式指定控制項的位置。  
  
 當您在執行階段將 Windows Form 控制項加入文件時，若關閉文件，文件不會保存該控制項。  您可以在下一次開啟文件時重新建立該控制項。  如需詳細資訊，請參閱[在執行階段將控制項加入至 Office 文件](../vsto/adding-controls-to-office-documents-at-run-time.md)。  
  
 如需在 VSTO 增益集專案中產生主項目的詳細資訊，請參閱[在 VSTO 增益集的執行階段中擴充 Word 文件和 Excel 活頁簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)。  
  
#### 若要在執行階段加入 Windows Form 控制項  
  
1.  使用名為 Add\<*控制項類別*\> 的方法 \(其中 \<*控制項類別*\> 是您要加入的 Windows Form 控制項類別名稱，例如 <xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A>\)。  
  
    > [!NOTE]  
    >  在目標為 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本的 VSTO 增益集專案中，您必須加入 Microsoft.Office.Tools.Excel.v4.0.Utilities.dll 或 Microsoft.Office.Tools.Word.v4.0.Utilities.dll 組件的參考，才能存取 Add\<*控制項類別*\> 方法。  
  
     下列程式碼範例示範如何使用 Word VSTO 增益集，將 <xref:Microsoft.Office.Tools.Word.Controls.Button> 加入現用文件的第一個段落。  
  
     [!code-csharp[Trin_WordAddInDynamicControls#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#7)]
     [!code-vb[Trin_WordAddInDynamicControls#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#7)]  
  
## 請參閱  
 [Office 文件上的 Windows Forms 控制項概觀](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [在執行階段將控制項加入至 Office 文件](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [如何：在工作表儲存格中調整控制項的大小](../vsto/how-to-resize-controls-within-worksheet-cells.md)   
 [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)  
  
  