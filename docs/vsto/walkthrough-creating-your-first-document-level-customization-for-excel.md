---
title: 逐步解說： 建立您第一個適用於 Excel 的文件層級自訂
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, creating your first project
- Excel [Office development in Visual Studio], creating your first project
- document-level customizations [Office development in Visual Studio], creating your first project
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2a63dd4eae31b99646af04ceabe76e4edb946027
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38800928"
---
# <a name="walkthrough-create-your-first-document-level-customization-for-excel"></a>逐步解說： 建立您第一個適用於 Excel 的文件層級自訂
  本入門逐步解說將示範如何建立 Microsoft Office Excel 的文件層級自訂。 只有在特定的活頁簿開啟時，才能使用您在這種方案中建立的功能。 您不能使用文件層級自訂來進行應用程式層級的變更，例如在任何活頁簿開啟時顯示新功能區索引標籤。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 這個逐步解說將說明下列工作：  
  
-   建立 Excel 活頁簿專案。  
  
-   將文字加入 [Visual Studio 設計工具] 中裝載的工作表。  
  
-   撰寫可使用 Excel 物件模型的程式碼，該程式碼會在自訂工作表開啟時將文字加入此工作表。  
  
-   建置和執行專案來進行測試。  
  
-   清除完成的專案，將不需要的組建檔案和安全性設定從開發電腦上移除。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] 或 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)]。  
  
## <a name="create-the-project"></a>建立專案  
  
### <a name="to-create-a-new-excel-workbook-project-in-visual-studio"></a>在 Visual Studio 中建立新的 Excel 活頁簿專案  
  
1.  啟動 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
2.  在 [檔案] **Deploying Office Solutions** 功能表中，指向 [新增] ，然後按一下 [專案] 。  
  
3.  在範本窗格中，展開 [Visual C#] **Deploying Office Solutions** 或 [Visual Basic] ，然後展開 [Office/SharePoint] 。  
  
4.  在展開的 [Office/SharePoint] **Deploying Office Solutions** 節點下，選取 [Office 增益集]  節點。  
  
5.  在專案範本清單中，選擇 Excel VSTO 增益集專案。  
  
6.  在 **名稱**方塊中，輸入**FirstWorkbookCustomization**。  
  
7.  按一下 [確定 **Deploying Office Solutions**]。  
  
     隨即開啟 [Visual Studio Tools for Office 專案精靈]  。  
  
8.  選取 **建立新的文件**，然後按一下**確定**。  
  
    -   [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會建立**FirstWorkbookCustomization**專案，然後將下列檔案加入專案。  
  
    -   *FirstWorkbookCustomization*.xlsx： 代表專案中的 Excel 活頁簿。 包含所有工作表和圖表。  
  
    -   Sheet1 (*.vb* Visual basic 中的檔案或 *.cs* Visual C# 的檔案)-所提供的活頁簿中第一個工作表的設計介面和程式碼的工作表。 如需詳細資訊，請參閱 <<c0> [ 工作表主項目](../vsto/worksheet-host-item.md)。  
  
    -   Sheet2 (*.vb* Visual basic 中的檔案或 *.cs* Visual C# 的檔案)-提供活頁簿中的第二個工作表的設計介面和程式碼的工作表。  
  
    -   Sheet3 (*.vb* Visual basic 中的檔案或 *.cs* Visual C# 的檔案)-所提供的活頁簿中的第三個工作表的設計介面和程式碼的工作表。  
  
    -   ThisWorkbook (*.vb* Visual basic 中的檔案或 *.cs* Visual C# 的檔案)-包含的設計介面和活頁簿層級自訂的程式碼。 如需詳細資訊，請參閱 < [Workbook 主項目](../vsto/workbook-host-item.md)。  
  
     Sheet1 程式碼檔案會在此設計工具中自動開啟。  
  
## <a name="close-and-reopen-worksheets-in-the-designer"></a>關閉並重新開啟設計工具中的工作表  
 如果您在開發專案時有意或無意地關閉設計工具中的活頁簿或工作表，您都可以將它重新開啟。  
  
### <a name="to-close-and-reopen-a-worksheet-in-the-designer"></a>使用設計工具關閉並重新開啟工作表  
  
1.  按一下 [關閉活頁簿**關閉**設計工具視窗] 按鈕 (X)。  
  
2.  在 **方案總管**，以滑鼠右鍵按一下**Sheet1**程式碼檔案，然後按一下**檢視表設計工具**。  
  
     \-或-  
  
     在 **方案總管**，按兩下**Sheet1**程式碼檔案。  
  
## <a name="add-text-to-a-worksheet-in-the-designer"></a>將文字加入至設計工具中的工作表  
 您可以修改設計工具中開啟的工作表，藉此設計自訂的使用者介面 (UI)。 例如，您可以將文字加入儲存格、套用公式，或加入 Excel 控制項。 如需如何使用設計工具的詳細資訊，請參閱[Visual Studio 環境中的 Office 專案](../vsto/office-projects-in-the-visual-studio-environment.md)。  
  
### <a name="to-add-text-to-a-worksheet-by-using-the-designer"></a>使用設計工具將文字加入工作表  
  
1.  在設計工具中開啟工作表中，選取儲存格**A1**，然後輸入下列文字。  
  
     **這段文字已加入使用設計工具。**  
  
> [!WARNING]  
>  如果您將這行文字加入儲存格中**A2**，它將會覆寫在這個範例中的其他程式碼。  
  
## <a name="add-text-to-a-worksheet-programmatically"></a>以程式設計方式將文字加入工作表  
 接著，將程式碼加入 Sheet1 程式碼檔案。 新程式碼會使用 Excel 物件模型，將第二行文字加入活頁簿。 根據預設，Sheet1 程式碼檔案包含下列產生的程式碼：  
  
-   `Sheet1` 類別的部分定義，此定義代表該工作表的程式設計模型，而且會提供 Excel 物件模型的存取。 如需詳細資訊，[工作表主項目](../vsto/worksheet-host-item.md)並[Word 物件模型概觀](../vsto/word-object-model-overview.md)。 `Sheet1` 類別的其餘部分則定義於您不應修改的隱藏程式碼檔中。  
  
-   `Sheet1_Startup` 和 `Sheet1_Shutdown` 事件處理常式。 當 Excel 載入和卸載您的自訂時，會呼叫這些事件處理常式。 請使用這些事件處理常式，在自訂載入時將它初始化，以及在自訂卸載時清除它所用的資源。 如需詳細資訊，請參閱 < [Office 專案中的事件](../vsto/events-in-office-projects.md)。  
  
### <a name="to-add-a-second-line-of-text-to-the-worksheet-by-using-code"></a>使用程式碼將第二行文字加入工作表  
  
1.  在 [**方案總管] 中**，以滑鼠右鍵按一下**Sheet1**，然後按一下**檢視程式碼**。  
  
     程式碼檔案隨即在 Visual Studio 中開啟。  
  
2.  以下列程式碼取代 `Sheet1_Startup` 事件處理常式。 當 Sheet1 開啟時，此程式碼會將第二行文字加入工作表。  
  
     [!code-csharp[Trin_ExcelWorkbookTutorial#1](../vsto/codesnippet/CSharp/Trin_ExcelWorkbookTutorial/Sheet1.cs#1)]
     [!code-vb[Trin_ExcelWorkbookTutorial#1](../vsto/codesnippet/VisualBasic/Trin_ExcelWorkbookTutorial/Sheet1.vb#1)]  
  
## <a name="test-the-project"></a>測試專案  
  
### <a name="to-test-your-workbook"></a>測試您的活頁簿  
  
1.  按 F5 **Deploying Office Solutions** 建置及執行專案。  
  
     當您建置專案時，程式碼會編譯為與活頁簿相關聯的組件。 Visual Studio 會將活頁簿複本和組件置於專案的建置輸出資料夾中，而且會設定開發電腦中的安全性設定以執行自訂。 如需詳細資訊，請參閱 <<c0> [ 建置 Office 方案](../vsto/building-office-solutions.md)。  
  
2.  確認活頁簿中出現下列文字：  
  
     **這段文字已加入使用設計工具。**  
  
     **This text was added by using code.**  
  
3.  關閉活頁簿。  
  
## <a name="clean-up-the-project"></a>清除專案  
 當您完成專案開發時，必須移除建置輸出資料夾中的檔案和建置程序建立的安全性設定。  
  
### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>清除開發電腦上已完成的專案  
  
1.  在 Visual Studio 中，按一下 [建置] **Deploying Office Solutions** 功能表上的 [清除方案] 。  
  
## <a name="next-steps"></a>後續步驟  
 現在您已經建立 Excel 的基本文件層級自訂，可以從下列主題進一步了解如何開發自訂：  
  
-   您可以在文件層級自訂中執行的一般程式設計工作：[程式的文件層級自訂](../vsto/programming-document-level-customizations.md)。  
  
-   適用於 Excel 的文件層級自訂專屬的程式設計工作： [Excel 方案](../vsto/excel-solutions.md)。  
  
-   使用 Excel 物件模型： [Excel 物件模型概觀](../vsto/excel-object-model-overview.md)。  
  
-   自訂 Excel 的 UI，比方說，藉由在功能區中加入自訂索引標籤或建立您自己的執行窗格： [Office UI 自訂](../vsto/office-ui-customization.md)。  
  
-   使用 Visual Studio 中的 Office 開發工具所提供的擴充的 Excel 物件來執行，不能使用 Excel 物件模型 （例如，裝載 managed 的控制項上的文件和資料的 Excel 控制項繫結使用 Windows Form 的工作資料繫結模型）：[使用擴充的物件自動化 Excel](../vsto/automating-excel-by-using-extended-objects.md)。  
  
-   建置和偵錯適用於 Excel 的文件層級自訂：[建置 Office 方案](../vsto/building-office-solutions.md)。  
  
-   部署適用於 Excel 的文件層級自訂：[部署 Office 方案](../vsto/deploying-an-office-solution.md)。  
  
## <a name="see-also"></a>另請參閱  
 [Office 方案開發概觀&#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Excel 方案](../vsto/excel-solutions.md)   
 [程式文件層級自訂](../vsto/programming-document-level-customizations.md)   
 [Excel 物件模型概觀](../vsto/excel-object-model-overview.md)   
 [使用擴充的物件自動化 Excel](../vsto/automating-excel-by-using-extended-objects.md)   
 [Office UI 自訂](../vsto/office-ui-customization.md)   
 [建置 Office 方案](../vsto/building-office-solutions.md)   
 [部署 Office 方案](../vsto/deploying-an-office-solution.md)   
 [Office 專案範本概觀](../vsto/office-project-templates-overview.md)  
  
  