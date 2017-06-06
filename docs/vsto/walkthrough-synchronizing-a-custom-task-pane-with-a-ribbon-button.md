---
title: "逐步解說：使用功能區按鈕同步處理自訂工作窗格"
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
  - "自訂工作窗格 [Visual Studio 中的 Office 程式開發]，顯示和隱藏"
  - "顯示自訂工作窗格"
  - "功能區 [Visual Studio 中的 Office 程式開發]，自訂工作窗格"
  - "切換按鈕 [Visual Studio 中的 Office 程式開發]"
  - "自訂工作窗格 [Visual Studio 中的 Office 程式開發]，與功能區按鈕同步處理"
  - "使用者介面 [Visual Studio 中的 Office 程式開發]，自訂工作窗格"
  - "同步處理 [Visual Studio 中的 Office 程式開發]，自訂工作窗格"
  - "工作窗格 [Visual Studio 中的 Office 程式開發]，顯示和隱藏"
  - "自訂工作窗格 [Visual Studio 中的 Office 程式開發]，建立"
  - "隱藏自訂工作窗格"
  - "工作窗格 [Visual Studio 中的 Office 程式開發]，建立"
  - "工作窗格 [Visual Studio 中的 Office 程式開發]，與功能區按鈕同步處理"
ms.assetid: 00ce8b1e-1370-42f2-9dc9-609cada392f1
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# 逐步解說：使用功能區按鈕同步處理自訂工作窗格
  這項逐步解說示範如何建立使用者按一下功能區上的切換按鈕以隱藏或顯示的自訂工作窗格。 您應該一律建立使用者介面 \(UI\) 元素，例如按鈕，讓使用者按一下即可顯示或隱藏自訂工作窗格；因為 Microsoft Office 應用程式不提供使用者顯示或隱藏自訂工作窗格的預設方式。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 雖然這個逐步解說特地使用 Excel，但所示範的概念同樣適用以上所列的任何應用程式。  
  
 這個逐步解說將說明下列工作：  
  
-   設計自訂工作窗格的 UI。  
  
-   在功能區加入切換按鈕。  
  
-   同步處理切換按鈕和自訂工作窗格。  
  
> [!NOTE]  
>  在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置： 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱[在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Excel 或 Microsoft [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)]。  
  
## 建立增益集專案  
 在這個步驟中，您會建立 Excel VSTO 增益集專案。  
  
#### 若要建立新的專案  
  
1.  使用 Excel 增益集專案範本建立名為 **SynchronizeTaskPaneAndRibbon** 的 Excel 增益集專案。 如需詳細資訊，請參閱[如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會開啟 **ThisAddIn.cs** 或 **ThisAddIn.vb** 程式碼檔案，並將 **SynchronizeTaskPaneAndRibbon** 專案加入 \[方案總管\]。  
  
## 在功能區加入切換按鈕  
 其中一個 Office 應用程式設計方針是使用者應一律具有 Office 應用程式 UI 的控制項。 為讓使用者能夠控制自訂工作窗格，您可以加入會顯示和隱藏工作窗格的功能區切換按鈕。 若要建立切換按鈕，請將 \[功能區 \(視覺化設計工具\)\] 項目加入專案。 設計工具可協助您加入及定位控制項、設定控制項屬性及處理控制項事件。 如需詳細資訊，請參閱[功能區設計工具](../vsto/ribbon-designer.md)。  
  
#### 在功能區加入切換按鈕  
  
1.  在 \[專案\] 功能表中，按一下 \[加入新項目\]。  
  
2.  選取 \[**加入新項目**\] 對話方塊中的 \[**功能區 \(視覺化設計工具\)**\]。  
  
3.  將新功能區的名稱變更為 **ManageTaskPaneRibbon**，然後按一下 \[加入\]。  
  
     **ManageTaskPaneRibbon.cs** 或 **ManageTaskPaneRibbon.vb** 檔案會在功能區設計工具中開啟，並顯示預設的索引標籤和群組。  
  
4.  在功能區設計工具中，按一下 \[group1\]。  
  
5.  在 \[屬性\] 視窗中，將 \[標籤\] 屬性設定為「工作窗格管理員」。  
  
6.  從 \[工具箱\] 的 \[Office 功能區控制項\] 索引標籤，將 **ToggleButton** 拖曳至 \[工作窗格管理員\] 群組。  
  
7.  按一下 \[toggleButton1\]。  
  
8.  在 \[屬性\] 視窗中，將 \[標籤\] 屬性設定為「顯示工作窗格」。  
  
## 設計自訂工作窗格的使用者介面  
 自訂工作窗格沒有視覺化的設計工具，但是您可以根據需要設計使用者控制項的版面配置。 稍後在本逐步解說中，您會在自訂工作窗格中加入使用者控制項。  
  
#### 設計自訂工作窗格的使用者介面  
  
1.  在 \[專案\] 功能表上，按一下 \[加入使用者控制項\]。  
  
2.  在 \[加入新項目\] 對話方塊中，將使用者控制項的名稱變更為 **TaskPaneControl**，然後按一下 \[加入\]。  
  
     使用者控制項隨即在設計工具中開啟。  
  
3.  從 \[工具箱\] 的 \[通用控制項\] 索引標籤，將 **TextBox** 控制項拖曳至使用者控制項。  
  
## 建立自訂工作窗格  
 若要在 VSTO 增益集啟動時建立自訂工作窗格，請在 VSTO 增益集的 <xref:Microsoft.Office.Tools.AddIn.Startup> 事件處理常式中，將使用者控制項加入工作窗格。 自訂工作窗格預設不顯示。 稍後在本逐步解說中，您將加入在使用者按一下您在功能區加入的切換按鈕時，會顯示或隱藏工作窗格的程式碼。  
  
#### 建立自訂工作窗格  
  
1.  展開 \[方案總管\] 中的 \[Excel\]。  
  
2.  以滑鼠右鍵按一下 **ThisAddIn.cs** 或 **ThisAddIn.vb**，然後按一下 \[檢視程式碼\]。  
  
3.  將下列程式碼加入 `ThisAddIn` 類別。 這段程式碼會宣告 `TaskPaneControl` 執行個體為 `ThisAddIn` 成員。  
  
     [!code-csharp[Trin_TaskPaneRibbonSynchronize#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_TaskPaneRibbonSynchronize/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_TaskPaneRibbonSynchronize/VB/ThisAddIn.vb#1)]  
  
4.  以下列程式碼取代 `ThisAddIn_Startup` 事件處理常式。 這段程式碼將 `TaskPaneControl` 物件加入 `CustomTaskPanes` 欄位，但它不顯示自訂工作窗格 \(<xref:Microsoft.Office.Tools.CustomTaskPane> 類別的 <xref:Microsoft.Office.Tools.CustomTaskPane.Visible%2A> 屬性預設是 **false**\)。 Visual C\# 程式碼也會將事件處理常式連結到 <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> 事件。  
  
     [!code-csharp[Trin_TaskPaneRibbonSynchronize#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_TaskPaneRibbonSynchronize/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_TaskPaneRibbonSynchronize/VB/ThisAddIn.vb#2)]  
  
5.  將下列方法加入 `ThisAddIn` 類別中。 這個方法會處理 <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> 事件。 當使用者按一下 \[關閉\] 按鈕 \(X\) 關閉工作窗格時，這個方法會更新功能區的切換按鈕狀態。  
  
     [!code-csharp[Trin_TaskPaneRibbonSynchronize#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_TaskPaneRibbonSynchronize/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_TaskPaneRibbonSynchronize/VB/ThisAddIn.vb#3)]  
  
6.  將下列屬性加入 `ThisAddIn` 類別。 這個屬性會向其他類別公開私用的 `myCustomTaskPane1` 物件。 稍後在本逐步解說中，您會將程式碼加入使用這個屬性的 `MyRibbon` 類別。  
  
     [!code-csharp[Trin_TaskPaneRibbonSynchronize#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_TaskPaneRibbonSynchronize/CS/ThisAddIn.cs#4)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_TaskPaneRibbonSynchronize/VB/ThisAddIn.vb#4)]  
  
## 使用切換按鈕隱藏和顯示自訂工作窗格  
 最後一個步驟是加入在使用者按一下功能區的切換按鈕時，顯示或隱藏自訂工作窗格的程式碼。  
  
#### 使用切換按鈕顯示和隱藏自訂工作窗格  
  
1.  在功能區設計工具中，按兩下 \[顯示工作窗格\] 切換按鈕。  
  
     Visual Studio 會自動產生名為 `toggleButton1_Click` 的事件處理常式，以處理切換按鈕的 <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> 事件。 Visual Studio 也會在程式碼編輯器中開啟 **MyRibbon.cs** 或 **MyRibbon.vb** 檔案。  
  
2.  以下列程式碼取代 `toggleButton1_Click` 事件處理常式。 當使用者按一下切換按鈕時，這段程式碼會顯示或隱藏自訂工作窗格，取決於按下或不按切換按鈕。  
  
     [!code-csharp[Trin_TaskPaneRibbonSynchronize#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_TaskPaneRibbonSynchronize/CS/ManageTaskPaneRibbon.cs#5)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_TaskPaneRibbonSynchronize/VB/ManageTaskPaneRibbon.vb#5)]  
  
## 測試增益集  
 當您執行專案時，Excel 會開啟但不顯示自訂工作窗格。 按一下功能區的切換按鈕以測試程式碼。  
  
#### 測試 VSTO 增益集  
  
1.  請按 F5 執行您的專案。  
  
     確認 Excel 開啟，而且 \[增益集\] 索引標籤出現在功能區上。  
  
2.  按一下功能區的 \[增益集\] 索引標籤。  
  
3.  在 \[工作窗格管理員\] 群組中，按一下 \[顯示工作窗格\] 切換按鈕。  
  
     請確認當您按一下切換按鈕時，工作窗格會切換顯示和隱藏。  
  
4.  當工作窗格出現時，請按一下工作窗格角落的 \[關閉\] 按鈕 \(X\)。  
  
     確認切換按鈕出現時未被按下。  
  
## 後續步驟  
 您可以透過下列主題，進一步了解如何建立自訂工作窗格：  
  
-   在 VSTO 增益集中為不同應用程式建立自訂工作窗格。 如需支援自訂工作窗格之應用程式的詳細資訊，請參閱 [自訂工作窗格](../vsto/custom-task-panes.md)。  
  
-   運用自訂工作窗格自動化應用程式。 如需詳細資訊，請參閱[逐步解說：運用自訂工作窗格自動化應用程式](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)。  
  
-   針對在 Outlook 中開啟的每一封電子郵件建立自訂工作窗格。 如需詳細資訊，請參閱[逐步解說：在 Outlook 中的電子郵件訊息顯示自訂工作窗格](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)。  
  
## 請參閱  
 [自訂工作窗格](../vsto/custom-task-panes.md)   
 [如何：在應用程式中加入自訂工作窗格](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)   
 [逐步解說：運用自訂工作窗格自動化應用程式](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)   
 [逐步解說：在 Outlook 中的電子郵件訊息顯示自訂工作窗格](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)   
 [功能區概觀](../vsto/ribbon-overview.md)  
  
  