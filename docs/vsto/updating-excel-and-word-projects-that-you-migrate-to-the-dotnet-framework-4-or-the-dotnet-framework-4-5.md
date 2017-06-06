---
title: "更新您要移轉至 .NET Framework 4 或 .NET Framework 4.5 的 Excel 和 Word 專案 | Microsoft Docs"
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
  - "Office 專案 [Visual Studio 中的 Office 程式開發]，移轉至 .NET Framework 4"
ms.assetid: 282c8876-fd49-462e-875b-4a0a79ad951c
caps.latest.revision: 25
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# 更新您要移轉至 .NET Framework 4 或 .NET Framework 4.5 的 Excel 和 Word 專案
  如果您有使用下列任何功能的 Excel 或 Word 專案，當目標 Framework 變更為 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本時，即必須修改程式碼：  
  
-   [GetVstoObject 和 HasVstoObject 方法](#GetVstoObject)  
  
-   [文件層級專案中之產生的類別](#generatedclasses)  
  
-   [文件上的 Windows Form 控制項](#winforms)  
  
-   [Word 內容控制項事件](#ccevents)  
  
-   [OLEObject 和 OLEControl 類別](#ole)  
  
-   [Controls.Item\(Object\) 屬性](#itemproperty)  
  
-   [衍生自 CollectionBase 的集合](#collections)  
  
 您也必須從重新指向 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本的 Excel 專案中，移除 Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute 以及對 Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy 類別的參考。 Visual Studio 不會為您移除這個屬性或類別參考。  
  
## 從 Excel 專案中移除 ExcelLocale1033 屬性  
 已從 Visual Studio 2010 Tools for Office Runtime 用於以 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本為目標之解決方案的部分移除 Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute。[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 和更新版本中的 Common Language Runtime \(CLR\) 會一律將地區設定 ID 1033 傳遞給 Excel 物件模型，而您也無法再使用這個屬性停用此行為。 如需詳細資訊，請參閱[Excel 方案的全球化與當地語系化](../vsto/globalization-and-localization-of-excel-solutions.md)。  
  
#### 移除 ExcelLocale1033Attribute  
  
1.  請使用在 Visual Studio 中開啟的專案，開啟 \[方案總管\]。  
  
2.  在 \[屬性\] 節點 \(C\#\) 或 \[我的專案\] 節點 \(Visual Basic\) 下，按兩下 AssemblyInfo 程式碼檔，以在程式碼編輯器中加以開啟。  
  
    > [!NOTE]  
    >  在 Visual Basic 專案中，您必須按一下 \[方案總管\] 中的 \[顯示所有檔案\] 按鈕，才能查看 AssemblyInfo 程式碼檔。  
  
3.  找出 Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute，並將它從檔案移除或加以註解化。  
  
    ```vb  
    <Assembly: ExcelLocale1033Proxy(True)>  
    ```  
  
    ```csharp  
    [assembly: ExcelLocale1033Proxy(true)]  
    ```  
  
## 移除 ExcelLocal1033Proxy 類別的參考  
 使用 Microsoft Visual Studio 2005 Tools for Microsoft Office System 所建立的專案，使用 Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy 類別具現化 Excel <xref:Microsoft.Office.Interop.Excel.Application> 物件。 已從 Visual Studio 2010 Tools for Office Runtime 用於以 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本為目標之解決方案的部分移除這個類別。 因此，您必須移除或註解化參考此類別的程式碼行。  
  
#### 移除 ExcelLocal1033Proxy 類別的參考  
  
1.  請在 Visual Studio 中開啟專案，再開啟 \[方案總管\]。  
  
2.  在 \[方案總管\] 中，開啟 ThisAddin.cs \(C\#\) 或 ThisAddin.vb \(Visual Basic\) 的捷徑功能表，然後選擇 \[檢視程式碼\]。  
  
3.  在程式碼編輯器的 `VSTO generated code` 區域中，移除或註解化下列程式碼行。  
  
    ```vb  
    Me.Application = CType(Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy.Wrap(GetType(Excel.Application), Me.Application), Excel.Application)  
  
    ```  
  
    ```csharp  
    this.Application = (Excel.Application)Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy.Wrap(typeof(Excel.Application), this.Application);  
  
    ```  
  
##  <a name="GetVstoObject"></a> 更新使用 GetVstoObject 和 HasVstoObject 方法的程式碼  
 在以 .NET Framework 3.5 為目標的專案中，GetVstoObject 或 HasVstoObject 方法在專案下列其中一個原生物件上可用為擴充方法：<xref:Microsoft.Office.Interop.Word.Document>、<xref:Microsoft.Office.Interop.Excel.Workbook>、<xref:Microsoft.Office.Interop.Excel.Worksheet> 或 <xref:Microsoft.Office.Interop.Excel.ListObject>。 當您呼叫這些方法時，不需要傳遞參數。 下列程式碼範例示範如何在以 .NET Framework 3.5 為目標的 Word VSTO 增益集中使用 GetVstoObject 方法。  
  
```vb  
Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _ Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject()  
```  
  
```csharp  
Microsoft.Office.Tools.Word.Document vstoDocument = Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject();  
```  
  
 在以 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本為目標的專案中，您必須修改程式碼，以下列方式之一存取這些方法：  
  
-   您仍然可以在後列物件上存取這些方法當成擴充方法：<xref:Microsoft.Office.Interop.Word.Document>、<xref:Microsoft.Office.Interop.Excel.Workbook>、<xref:Microsoft.Office.Interop.Excel.Worksheet> 或 <xref:Microsoft.Office.Interop.Excel.ListObject> 物件。 不過，您現在必須將 Globals.Factory 屬性傳回的物件傳遞給這些方法。  
  
    ```vb  
    Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _ Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject(Globals.Factory)  
    ```  
  
    ```csharp  
    Microsoft.Office.Tools.Word.Document vstoDocument = Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject(Globals.Factory);  
    ```  
  
-   或者，您可以存取位於 Globals.Factory 屬性傳回之物件上的這些方法。 當您以這種方式存取這些方法時，您必須將想要擴充的原生物件傳遞給方法。  
  
    ```vb  
    Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _ Globals.Factory.GetVstoObject(Globals.ThisAddIn.Application.ActiveDocument)  
    ```  
  
    ```csharp  
    Microsoft.Office.Tools.Word.Document vstoDocument = Globals.Factory.GetVstoObject(Globals.ThisAddIn.Application.ActiveDocument);  
    ```  
  
 如需詳細資訊，請參閱[在 VSTO 增益集的執行階段中擴充 Word 文件和 Excel 活頁簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)。  
  
##  <a name="generatedclasses"></a> 在文件層級專案中更新使用產生的類別執行個體的程式碼  
 在以 .NET Framework 3.5 為目標的文件層級專案中，專案中的產生的類別衍生自 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 的下列類別：  
  
-   `ThisDocument`: <xref:Microsoft.Office.Tools.Word.Document>  
  
-   `ThisWorkbook`: <xref:Microsoft.Office.Tools.Excel.Workbook>  
  
-   `Sheet` *n*: <xref:Microsoft.Office.Tools.Excel.Worksheet>  
  
-   `Chart` *n*: <xref:Microsoft.Office.Tools.Excel.ChartSheet>  
  
 在以 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本為目標的專案中，上文列出的 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 類型是介面，而不是類別。 以 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本為目標的專案中之產生的類別，衍生自 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 的下列新類別：  
  
-   `ThisDocument`: <xref:Microsoft.Office.Tools.Word.DocumentBase>  
  
-   `ThisWorkbook`: <xref:Microsoft.Office.Tools.Excel.WorkbookBase>  
  
-   `Sheet` *n*: <xref:Microsoft.Office.Tools.Excel.WorksheetBase>  
  
-   `Chart` *n*: <xref:Microsoft.Office.Tools.Excel.ChartSheetBase>  
  
 如果專案中的程式碼將參考的其中一個產生的類別執行個體，視為其衍生來源的基底類別，您必須修改程式碼。  
  
 例如，在以 .NET Framework 3.5 為目標的 Excel 活頁簿專案中，您可能有個 helper 方法，會對專案中之產生的 `Sheet`*n* 類別執行個體執行一些工作。  
  
```vb  
Private Sub DoSomethingToSheet(ByVal worksheet As Microsoft.Office.Tools.Excel.Worksheet) ' Do something to the worksheet object. End Sub  
```  
  
```csharp  
private void DoSomethingToSheet(Microsoft.Office.Tools.Excel.Worksheet worksheet) { // Do something to the worksheet object. }  
```  
  
 如果專案重定目標為 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本，您必須對程式碼進行下列一種變更：  
  
-   修改專案中呼叫 `DoSomethingToSheet` 方法以傳遞 <xref:Microsoft.Office.Tools.Excel.WorksheetBase> 物件之 <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Base%2A> 屬性的所有程式碼。 這個屬性會傳回 <xref:Microsoft.Office.Tools.Excel.Worksheet> 物件。  
  
    ```vb  
    DoSomethingToSheet(Globals.Sheet1.Base)  
    ```  
  
    ```csharp  
    DoSomethingToSheet(Globals.Sheet1.Base);  
    ```  
  
-   修改 `DoSomethingToSheet` 方法參數，預期會改為 <xref:Microsoft.Office.Tools.Excel.WorksheetBase> 物件。  
  
    ```vb  
    Private Sub DoSomethingToSheet(ByVal worksheet As Microsoft.Office.Tools.Excel.WorksheetBase) ' Do something to the worksheet object. End Sub  
    ```  
  
    ```csharp  
    private void DoSomethingToSheet (Microsoft.Office.Tools.Excel.WorksheetBase worksheet) { // Do something to the worksheet object. }  
    ```  
  
##  <a name="winforms"></a> 更新在文件上使用 Windows Form 控制項的程式碼  
 您必須將 <xref:Microsoft.Office.Tools.Excel> 或 <xref:Microsoft.Office.Tools.Word> 命名空間的 **using** \(C\#\) 或 **Imports** \(Visual Basic\) 陳述式加入具有後列特性的任何程式碼檔頂端，這種程式碼檔會以程式設計的方式，使用 Controls 屬性將 Windows Form 控制項加入文件或工作表。  
  
 在以 .NET Framework 3.5 為目標的專案中，加入 Windows Form 控制項的方法\(例如 AddButton 方法\)，都是在 <xref:Microsoft.Office.Tools.Excel.ControlCollection> 和 <xref:Microsoft.Office.Tools.Word.ControlCollection> 類別中所定義。  
  
 在以 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本為目標的專案中，這些方法都是 Controls 屬性所提供的擴充方法。 若要使用這些擴充方法，方法使用所在的程式碼檔中必須有 <xref:Microsoft.Office.Tools.Excel> 或 <xref:Microsoft.Office.Tools.Word> 命名空間的 **using** 或 **Imports** 陳述式。 以 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本為目標的新專案中，會自動產生這個陳述式。 不過，以 .NET Framework 3.5 為目標的專案不會自動加入這個陳述式，所以您必須在重定專案目標時將其加入。  
  
 如需詳細資訊，請參閱[在執行階段將控制項加入至 Office 文件](../vsto/adding-controls-to-office-documents-at-run-time.md)。  
  
##  <a name="ccevents"></a> 更新處理 Word 內容控制項事件的程式碼  
 在以 .NET Framework 3.5 為目標的專案中，Word 內容控制項的事件是由泛型 <xref:System.EventHandler%601> 委派所處理。 在以 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本為目標的專案中，這些事件是由其他委派處理。  
  
 下表列出在以 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本為目標的專案中，與它們相關聯的 Word 內容控制項事件和委派。  
  
|事件|在 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 及更新版本的專案中要使用的委派|  
|--------|-------------------------------------------------------------------------------|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Added>|<xref:Microsoft.Office.Tools.Word.ContentControlAddedEventHandler>|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.ContentUpdating>|<xref:Microsoft.Office.Tools.Word.ContentControlContentUpdatingEventHandler>|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Deleting>|<xref:Microsoft.Office.Tools.Word.ContentControlDeletingEventHandler>|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering>|<xref:Microsoft.Office.Tools.Word.ContentControlEnteringEventHandler>|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Exiting>|<xref:Microsoft.Office.Tools.Word.ContentControlExitingEventHandler>|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.StoreUpdating>|<xref:Microsoft.Office.Tools.Word.ContentControlStoreUpdatingEventHandler>|  
  
##  <a name="ole"></a> 更新使用 OLEObject 和 OLEControl 類別的程式碼  
 在以 .NET Framework 3.5 為目標的專案中，您可以使用 Microsoft.Office.Tools.Excel.OLEObject 和 Microsoft.Office.Tools.Word.OLEControl 類別，將自訂控制項 \(例如 Windows Form 使用者控制項\) 加入文件或工作表。  
  
 在以 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本為目標的專案中，<xref:Microsoft.Office.Tools.Excel.ControlSite> 和 <xref:Microsoft.Office.Tools.Word.ControlSite> 介面已取代這些類別。 您必須修改原參考 Microsoft.Office.Tools.Excel.OLEObject 和 Microsoft.Office.Tools.Word.OLEControl 的程式碼，改為參考 <xref:Microsoft.Office.Tools.Excel.ControlSite> 和 <xref:Microsoft.Office.Tools.Word.ControlSite>。 除了新名稱以外，這些控制項的行為方式和它們在以 .NET Framework 3.5 為目標的專案中一樣。  
  
 如需詳細資訊，請參閱[在執行階段將控制項加入至 Office 文件](../vsto/adding-controls-to-office-documents-at-run-time.md)。  
  
##  <a name="itemproperty"></a> 更新使用 Controls.Item\(Object\) 屬性的程式碼  
 在以 .NET Framework 3.5 為目標的專案中，您可以使用 Microsoft.Office.Tools.Word.Document.Controls 或 Microsoft.Office.Tools.Excel.Worksheet.Controls 集合的 Item\(Object\) 屬性，判斷文件或工作表是否有指定的控制項。  
  
 在以 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本為目標的專案中，Item\(Object\) 屬性已經從這些集合中移除。 若要判斷文件或工作表是否包含指定的控制項，請改用 <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> 或 <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> 集合的 Contains\(System.Object\) 方法。  
  
 如需文件和工作表 Controls 集合的詳細資訊，請參閱 [在執行階段將控制項加入至 Office 文件](../vsto/adding-controls-to-office-documents-at-run-time.md)。  
  
##  <a name="collections"></a> 更新使用衍生自 CollectionBase 集合的程式碼  
 在以 .NET Framework 3.5 為目標的專案中，[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 有數個集合類型衍生自 <xref:System.Collections.CollectionBase> 類別，如 Microsoft.Office.Tools.SmartTagCollection、Microsoft.Office.Tools.Excel.ControlCollection 和 Microsoft.Office.Tools.Word.ControlCollection。  
  
 在以 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本為目標的專案中，這些集合類型現在是非衍生自 <xref:System.Collections.CollectionBase> 的介面。 這些集合類型也不再提供某些成員，例如 <xref:System.Collections.CollectionBase.Capacity%2A>、<xref:System.Collections.CollectionBase.List%2A> 和 <xref:System.Collections.CollectionBase.InnerList%2A>。  
  
## 請參閱  
 [將 Office 方案移轉至 .NET Framework 4 或更新版本](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)   
 [內容控制項](../vsto/content-controls.md)   
 [在 VSTO 增益集的執行階段中擴充 Word 文件和 Excel 活頁簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [在執行階段將控制項加入至 Office 文件](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [全域存取 Office 專案中的物件](../vsto/global-access-to-objects-in-office-projects.md)  
  
  