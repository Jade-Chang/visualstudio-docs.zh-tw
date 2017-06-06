---
title: "如何：從主控制項中使用資料更新資料來源"
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
  - "文件 [Visual Studio 中的 Office 程式開發]，資料來源更新"
  - "資料 [Visual Studio 中的 Office 程式開發]，從文件更新資料來源"
  - "主控制項 [Visual Studio 中的 Office 程式開發]，資料來源更新"
  - "Office 文件 [Visual Studio 中的 Office 程式開發]，資料來源"
ms.assetid: b91025af-1eaa-44ee-88f2-71ecaa7a0440
caps.latest.revision: 53
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 52
---
# 如何：從主控制項中使用資料更新資料來源
  您可以將主控制項繫結至資料來源，並以在控制項中對資料所做的變更來更新資料來源。 這個程序包含兩個主要步驟：  
  
1.  以控制項中修改的資料更新記憶體內部資料來源。 一般而言，記憶體內部資料來源是 <xref:System.Data.DataSet>、<xref:System.Data.DataTable> 或其他一些資料物件。  
  
2.  以記憶體內部資料來源中變更的資料更新資料庫。 只有在資料來源已連接到 SQL Server 或 Microsoft Office Access 資料庫等後端資料庫時才適用。  
  
 如需主控制項和資料繫結的詳細資訊，請參閱[主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)和[將資料繫結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)。  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## 更新記憶體內部資料來源  
 根據預設，啟用簡單資料繫結的主控制項 \(Word 文件上的內容控制項或 Excel 工作表上的具名範圍控制項\)，不會將資料變更儲存至記憶體內部資料來源。 也就是說，當使用者變更主控制項中的值，並接著移動離開該控制項時，這個控制項中的新值並不會自動儲存至資料來源。  
  
 若要將資料儲存至資料來源，您可以撰寫可在執行階段回應特定事件而更新資料來源的程式碼，或是將控制項設定為只要控制項中的值一變更就自動更新資料來源。  
  
 您不需要將 <xref:Microsoft.Office.Tools.Excel.ListObject> 變更儲存至記憶體內部資料來源。 當您將 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項繫結至資料時，<xref:Microsoft.Office.Tools.Excel.ListObject> 控制項會自動將變更儲存至記憶體內部資料來源，而不需要其他程式碼。  
  
#### 在執行階段更新記憶體內部資料來源  
  
-   呼叫 <xref:System.Windows.Forms.Binding> 物件的 <xref:System.Windows.Forms.Binding.WriteValue%2A> 方法，將控制項繫結至資料來源。  
  
     下列範例會將對 Excel 工作表上 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項所做的變更儲存至資料來源。 這個範例假設您有名為 `namedRange1` 的 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項，而且控制項的 <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> 屬性已繫結至資料來源中的欄位。  
  
     [!code-csharp[Trin_VstcoreDataExcel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreDataExcel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#1)]  
  
### 自動更新記憶體內部資料來源  
 您也可以設定控制項，讓它自動更新記憶體內部資料來源。 在文件層級專案中，您可以使用程式碼或設計工具來執行這項作業。 在 VSTO 增益集專案中，您必須使用程式碼。  
  
##### 使用程式碼將控制項設定為自動更新記憶體內部資料來源  
  
1.  使用 <xref:System.Windows.Forms.Binding> 物件的 System.Windows.Forms.DataSourceUpdateMode.OnPropertyChanged  模式，將控制項繫結至資料來源。 您可以使用兩種選項來更新資料來源：  
  
    -   若要在驗證控制項時更新資料來源，請將這個屬性設定為 System.Windows.Forms.DataSourceUpdateMode.OnValidation。  
  
    -   若要在控制項的資料繫結屬性值變更時更新資料來源，請將這個屬性設定為 System.Windows.Forms.DataSourceUpdateMode.OnPropertyChanged。  
  
        > [!NOTE]  
        >  System.Windows.Forms.DataSourceUpdateMode.OnPropertyChanged 選項不適用於 Word 主控制項，因為 Word 不提供文件變更或控制項變更通知。 不過，這個選項可用於 Word 文件上的 Windows Form 控制項。  
  
     下列範例會將 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項設定為只要控制項中的值一變更就自動更新資料來源。 這個範例假設您有名為 `namedRange1` 的 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項，而且控制項的 <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> 屬性已繫結至資料來源中的欄位。  
  
     [!code-csharp[Trin_VstcoreDataExcel#19](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreDataExcel#19](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#19)]  
  
##### 使用設計工具將控制項設定為自動更新記憶體內部資料來源  
  
1.  在 Visual Studio 中，以設計工具開啟 Word 文件或 Excel 活頁簿。  
  
2.  按一下您要自動更新資料來源的控制項。  
  
3.  在 \[屬性\] 視窗中，展開 \[\(DataBindings\)\] 屬性。  
  
4.  按一下 \[\(進階\)\] 屬性旁的省略符號按鈕 \(![VisualStudioEllipsesButton 螢幕擷取畫面](../vsto/media/vbellipsesbutton.png "VisualStudioEllipsesButton 螢幕擷取畫面")\)。  
  
5.  在 \[格式化與進階繫結\] 對話方塊中，按一下 \[資料來源更新模式\] 下拉式清單，然後選取下列其中一個值：  
  
    -   若要在驗證控制項時更新資料來源，請選取 \[OnValidation\]。  
  
    -   若要在控制項的資料繫結屬性值變更時更新資料來源，請選取 \[OnPropertyChanged\]。  
  
        > [!NOTE]  
        >  \[OnPropertyChanged\] 選項不適用於 Word 主控制項，因為 Word 不提供文件變更或控制項變更通知。 不過，這個選項可用於 Word 文件上的 Windows Form 控制項。  
  
6.  關閉 \[格式化與進階繫結\] 對話方塊。  
  
## 更新資料庫  
 如果資料庫與記憶體內部資料來源相關聯，您必須以對資料來源所做的變更來更新資料庫。 如需更新資料庫的詳細資訊，請參閱[儲存資料集中的資料](../Topic/Saving%20data%20back%20to%20the%20database.md)和[如何：使用 TableAdapter 更新資料](../data-tools/update-data-by-using-a-tableadapter.md)。  
  
#### 若要更新資料庫  
  
1.  呼叫控制項之 <xref:System.Windows.Forms.BindingSource> 的 <xref:System.Windows.Forms.BindingSource.EndEdit%2A> 方法。  
  
     當您在設計階段將資料繫結控制項加入文件或活頁簿時，會自動產生 <xref:System.Windows.Forms.BindingSource>。<xref:System.Windows.Forms.BindingSource> 會將控制項連接到專案中的具類型資料集。 如需詳細資訊，請參閱[BindingSource 元件概觀](http://msdn.microsoft.com/library/be838caf-fcb0-4b68-827f-58b2c04b747f)。  
  
     下列程式碼範例假設您的專案包含名為 `customersBindingSource` 的 <xref:System.Windows.Forms.BindingSource> 。  
  
     [!code-csharp[Trin_VstcoreDataExcel#20](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#20)]
     [!code-vb[Trin_VstcoreDataExcel#20](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#20)]  
  
2.  呼叫您專案中所產生之 TableAdapter 的 `Update` 方法。  
  
     當您在設計階段將資料繫結控制項加入文件或活頁簿時，會自動產生 TableAdapter。TableAdapter 會將您專案中的具類型資料集連接到資料庫。 如需詳細資訊，請參閱[TableAdapter 概觀](/visual-studio/data-tools/tableadapter-overview)。  
  
     下列程式碼範例假設您已連接到 Northwind 資料庫中的 Customers 資料表，而且您的專案包含名為 `customersTableAdapter` 的 TableAdapter 和名為 `northwindDataSet` 的具類型資料集。  
  
     [!code-csharp[Trin_VstcoreDataExcel#21](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#21)]
     [!code-vb[Trin_VstcoreDataExcel#21](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#21)]  
  
## 請參閱  
 [將資料繫結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [儲存資料集中的資料](../Topic/Saving%20data%20back%20to%20the%20database.md)   
 [如何：使用 TableAdapter 更新資料](../data-tools/update-data-by-using-a-tableadapter.md)   
 [如何：在工作表中捲動資料庫記錄](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)   
 [如何：將資料庫的資料填入工作表](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [如何：將物件的資料填入文件](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [如何：將資料庫的資料填入文件](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [如何：將服務的資料填入文件](../vsto/how-to-populate-documents-with-data-from-services.md)  
  
  