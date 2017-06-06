---
title: "逐步解說：在執行階段於 VSTO 增益集專案中，將控制項加入工作表中"
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
  - "增益集 [Visual Studio 中的 Office 程式開發], 加入控制項"
  - "應用程式層級增益集 [Visual Studio 中的 Office 程式開發], 加入控制項"
  - "控制項 [Visual Studio 中的 Office 程式開發], 在執行階段加入至工作表"
  - "工作表, 在執行階段加入控制項"
ms.assetid: 4f68677a-4789-4564-b229-02e2d4031a5f
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# 逐步解說：在執行階段於 VSTO 增益集專案中，將控制項加入工作表中
  您可以使用 Excel VSTO 增益集，將控制項加入任何開啟的工作表中。  本逐步解說將示範如何使用功能區，讓使用者將 <xref:Microsoft.Office.Tools.Excel.Controls.Button>、<xref:Microsoft.Office.Tools.Excel.NamedRange> 及 <xref:Microsoft.Office.Tools.Excel.ListObject> 加入工作表。  如需詳細資訊，請參閱[在執行階段將控制項加入至 Office 文件](../vsto/adding-controls-to-office-documents-at-run-time.md)。  
  
 **適用對象：**本主題資訊適用於 Excel 的 VSTO 增益集專案。  如需詳細資訊，請參閱＜[依 Office 應用程式和專案類型提供的功能](../vsto/features-available-by-office-application-and-project-type.md)＞。  
  
 這個逐步解說將說明下列工作：  
  
-   提供可將控制項加入工作表的使用者介面 \(UI\)。  
  
-   將控制項加入工作表。  
  
-   移除工作表的控制項。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Excel  
  
## 建立新的 Excel VSTO 增益集專案  
 請從建立新的 Excel VSTO 增益集專案開始。  
  
#### 若要建立新的 Excel VSTO 增益集專案  
  
1.  在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中，建立名為 ExcelDynamicControls 的 Excel VSTO 增益集專案。  如需詳細資訊，請參閱[如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
2.  加入 **Microsoft.Office.Tools.Excel.v4.0.Utilities.dll** 組件的參考。  本逐步解說稍後會需要用到此參考，以透過程式設計的方式將 Windows Form 控制項加入工作表。  
  
## 提供可將控制項加入工作表的 UI  
 將自訂索引標籤加入 Excel 功能區。  使用者可以選取索引標籤上的核取方塊，將控制項加入工作表。  
  
#### 若要提供可將控制項加入工作表的 UI  
  
1.  在 \[專案\] 功能表中，按一下 \[加入新項目\]。  
  
2.  選取 \[加入新項目\] 對話方塊中的 \[功能區 \(視覺化設計工具\)\]，然後按一下 \[加入\]。  
  
     **Ribbon1.cs** 或 **Ribbon1.vb** 檔案會在功能區設計工具中開啟，並顯示預設索引標籤和群組。  
  
3.  從 \[工具箱\] 的 \[Office 功能區控制項\] 索引標籤，將 CheckBox 控制項拖曳至 \[group1\]。  
  
4.  按一下 \[CheckBox1\] 予以選取。  
  
5.  在 \[屬性\] 視窗中變更下列屬性。  
  
    |屬性|值|  
    |--------|-------|  
    |**名稱**|按鈕|  
    |**標籤**|按鈕|  
  
6.  將第二個核取方塊加入 \[group1\]，然後變更下列屬性。  
  
    |屬性|值|  
    |--------|-------|  
    |**名稱**|NamedRange|  
    |**標籤**|NamedRange|  
  
7.  將第二個核取方塊加入 \[group1\]，然後變更下列屬性。  
  
    |屬性|值|  
    |--------|-------|  
    |**名稱**|ListObject|  
    |**標籤**|ListObject|  
  
## 將控制項加入工作表  
 您只能將 Managed 控制項加入做為容器的主項目。  因為 VSTO 增益集專案會使用任何開啟的工作表，所以 VSTO 增益集會將工作表轉換為主項目後，或取得現有主項目，再加入控制項。  將程式碼加入每個控制項的 Click 事件處理常式，以根據開啟的工作表，產生 <xref:Microsoft.Office.Tools.Excel.Worksheet> 主項目。  然後，將 <xref:Microsoft.Office.Tools.Excel.Controls.Button>、<xref:Microsoft.Office.Tools.Excel.NamedRange> 和 <xref:Microsoft.Office.Tools.Excel.ListObject> 加入工作表中目前選取的範圍。  
  
#### 若要將控制項加入工作表  
  
1.  在功能區設計工具中，按兩下 \[Button\]。  
  
     在程式碼編輯器中，隨即開啟 \[Button\] 核取方塊的 <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> 事件處理常式。  
  
2.  以下列程式碼取代 `Button_Click` 事件處理常式。  
  
     此程式碼會使用 `GetVstoObject` 方法來取得代表活頁簿中第一個工作表的主項目，然後將 <xref:Microsoft.Office.Tools.Excel.Controls.Button> 控制項加入目前選取的儲存格。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/Ribbon1.cs#2)]
     [!code-vb[Trin_Excel_Dynamic_Controls#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/Ribbon1.vb#2)]  
  
3.  在 \[方案總管\] 中，選取 Ribbon1.cs 或 Ribbon1.vb。  
  
4.  在 \[檢視\] 功能表中，按一下 \[設計工具\]。  
  
5.  在功能區設計工具中，按兩下 \[NamedRange\]。  
  
6.  以下列程式碼取代 `NamedRange_Click` 事件處理常式。  
  
     此程式碼會使用 `GetVstoObject` 方法來取得代表活頁簿中第一個工作表的主項目，然後為目前選取的儲存格定義 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/Ribbon1.cs#3)]
     [!code-vb[Trin_Excel_Dynamic_Controls#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/Ribbon1.vb#3)]  
  
7.  在功能區設計工具中，按兩下 \[ListObject\]。  
  
8.  以下列程式碼取代 `ListObject_Click` 事件處理常式。  
  
     此程式碼會使用 `GetVstoObject` 方法來取得代表活頁簿中第一個工作表的主項目，然後為目前選取的儲存格定義 <xref:Microsoft.Office.Tools.Excel.ListObject>。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/Ribbon1.cs#4)]
     [!code-vb[Trin_Excel_Dynamic_Controls#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/Ribbon1.vb#4)]  
  
9. 在功能區程式碼檔的頂端加入下列陳述式。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/Ribbon1.cs#1)]
     [!code-vb[Trin_Excel_Dynamic_Controls#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/Ribbon1.vb#1)]  
  
## 移除工作表的控制項  
 當工作表儲存和關閉時，都不會保存控制項。  您應該在儲存工作表之前，以程式設計方式移除所有產生的 Windows Form 控制項，否則該活頁簿下次開啟時，只會顯示控制項的外框。  請將程式碼加入 <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> 事件，以便從產生之主項目的控制項集合移除 Windows Form 控制項。  如需詳細資訊，請參閱[在 Office 文件中保存動態控制項](../vsto/persisting-dynamic-controls-in-office-documents.md)。  
  
#### 若要移除工作表的控制項  
  
1.  在 \[方案總管\] 中，選取 ThisAddIn.cs 或 ThisAddIn.vb。  
  
2.  在 \[檢視\] 功能表上，按一下 \[程式碼\]。  
  
3.  將下列方法加入 ThisAddin 類別。  此程式碼會取得活頁簿中的第一個工作表，然後使用 `HasVstoObject` 方法檢查工作表是否具有產生的工作表物件。  如果產生的工作表物件具有控制項，程式碼便會取得該工作表物件，並逐一查看控制項集合，同時移除控制項。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#6)]
     [!code-vb[Trin_Excel_Dynamic_Controls#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/ThisAddIn.vb#6)]  
  
4.  在 C\# 中，您必須建立 <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> 事件的事件處理常式。  您可以將這個程式碼放入 `ThisAddIn_Startup` 方法中。  如需建立事件處理常式的詳細資訊，請參閱[如何：在 Office 專案中建立事件處理常式](../vsto/how-to-create-event-handlers-in-office-projects.md)。  以下列程式碼取代 `ThisAddIn_Startup` 方法。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#5)]  
  
## 測試方案  
 從功能區上的自訂索引標籤選取控制項，將此控制項加入工作表。  當您儲存工作表時，這些控制項將會被移除。  
  
#### 若要測試方案  
  
1.  請按 F5 執行您的專案。  
  
2.  選取 Sheet1 中的任何儲存格。  
  
3.  按一下 \[增益集\] 索引標籤。  
  
4.  在 \[group1\] 群組中，按一下 \[Button\]。  
  
     按鈕隨即出現在選取的儲存格中。  
  
5.  選取 Sheet1 中的其他儲存格。  
  
6.  在 \[group1\] 群組中，按一下 \[NamedRange\]。  
  
     隨即定義選定儲存格的已命名範圍。  
  
7.  選取 Sheet1 中的一連串儲存格。  
  
8.  在 \[group1\] 群組中，按一下 \[ListObject\]。  
  
     隨即加入選定儲存格的清單物件。  
  
9. 儲存工作表。  
  
     您加入 Sheet1 的控制項將不再出現。  
  
## 後續步驟  
 您可以透過下列主題，進一步了解 Excel VSTO 增益集專案：  
  
-   若要深入了解如何將控制項儲存至工作表，請參閱 [Office 程式開發範例和逐步解說](../vsto/office-development-samples-and-walkthroughs.md)中的＜Excel VSTO 增益集動態控制項範例＞。  
  
## 請參閱  
 [Excel 方案](../vsto/excel-solutions.md)   
 [Office 文件上的 Windows Forms 控制項概觀](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Office 文件上的控制項](../vsto/controls-on-office-documents.md)   
 [NamedRange 控制項](../vsto/namedrange-control.md)   
 [ListObject 控制項](../vsto/listobject-control.md)  
  
  