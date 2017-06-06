---
title: "逐步解說：為您的 Outlook 建立第一個 VSTO 增益集"
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
  - "應用程式層級增益集 [Visual Studio 中的 Office 程式開發]，建立第一個專案"
  - "Visual Studio 中的 Office 程式開發，建立第一個專案"
  - "增益集 [Visual Studio 中的 Office 程式開發]，建立第一個專案"
  - "Outlook [Visual Studio 中的 Office 程式開發]，建立第一個專案"
ms.assetid: 2c5c5d75-27ee-471f-9328-58f0cf05b2b7
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# 逐步解說：為您的 Outlook 建立第一個 VSTO 增益集
  本逐步解說將示範如何建立 Microsoft Office Outlook 的 VSTO 增益集。 無論開啟的 Outlook 項目為何，您在這類解決方案中建立的功能都可供應用程式本身使用。 如需詳細資訊，請參閱[Office 方案開發概觀 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 這個逐步解說將說明下列工作：  
  
-   建立 Outlook 的 Outlook VSTO 增益集專案。  
  
-   撰寫使用 Outlook 物件模型的程式碼，將文字加入新郵件訊息的主旨和本文。  
  
-   建置和執行專案來進行測試。  
  
-   清除已完成的專案，使得 VSTO 增益集不再於開發電腦上自動執行。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Outlook  
  
## 建立專案  
  
#### 在 Visual Studio 中建立新的 Outlook 專案  
  
1.  啟動 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
2.  在 \[檔案\] 功能表中，指向 \[新增\]，然後按一下 \[專案\]。  
  
3.  在範本窗格中，展開 \[Visual C\#\] 或 \[Visual Basic\]，然後展開 \[Office\/SharePoint\]。  
  
4.  在展開的 \[Office\/SharePoint\] 節點下，選取 \[Office 增益集\] 節點。  
  
5.  在專案範本清單中，選取 Outlook VSTO 增益集專案。  
  
6.  在 \[名稱\] 方塊中輸入 **FirstOutlookAddIn**。  
  
7.  按一下 \[**確定**\]。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會建立 **FirstExcelAddIn** 專案，並在編輯器中開啟 \[ThisAddIn\] 程式碼檔。  
  
## 撰寫可將文字加入每封新郵件的程式碼  
 接著，將程式碼加入 ThisAddIn 程式碼檔。 新的程式碼會使用 Outlook 的物件模型將文字加入每封新郵件。 根據預設，ThisAddIn 程式碼檔包含下列產生的程式碼：  
  
-   `ThisAddIn` 類別的部分定義。 這個類別提供您撰寫程式碼的進入點，並提供對 Outlook 物件模型的存取。 如需詳細資訊，請參閱[VSTO 增益集程式設計](../vsto/programming-vsto-add-ins.md)。`ThisAddIn` 類別的其餘部分則定義於您不應修改的隱藏程式碼檔中。  
  
-   `ThisAddIn_Startup` 和 `ThisAddIn_Shutdown` 事件處理常式。 當 Outlook 載入和卸載 VSTO 增益集時，會呼叫這些事件處理常式。 請使用這些事件處理常式，在 VSTO 增益集載入時將它初始化，以及在 VSTO 增益集卸載時清除它所用的資源。 如需詳細資訊，請參閱[Office 專案中的事件](../vsto/events-in-office-projects.md)。  
  
#### 將文字加入每封新郵件的主旨和本文  
  
1.  在 ThisAddIn 程式碼檔中，宣告 `ThisAddIn` 類別中名為 `inspectors` 的欄位。`inspectors` 欄位會維護目前 Outlook 執行個體中偵測器視窗的集合參考。 這個參考可以防止記憶體回收行程釋放包含 <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> 事件之事件處理常式的記憶體。  
  
     [!code-csharp[Trin_OutlookAddInTutorial#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OutlookAddInTutorial/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_OutlookAddInTutorial#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OutlookAddInTutorial/VB/ThisAddIn.vb#1)]  
  
2.  以下列程式碼取代 `ThisAddIn_Startup` 方法。 這個程式碼會將事件處理常式附加到 <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> 事件。  
  
     [!code-csharp[Trin_OutlookAddInTutorial#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OutlookAddInTutorial/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_OutlookAddInTutorial#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OutlookAddInTutorial/VB/ThisAddIn.vb#2)]  
  
3.  在 ThisAddIn 程式碼檔中，將下列程式碼加入 `ThisAddIn` 類別。 這個程式碼會定義 <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> 事件的事件處理常式。  
  
     當使用者建立新郵件時，這個事件處理常式會將文字加入郵件的主旨和本文。  
  
     [!code-csharp[Trin_OutlookAddInTutorial#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OutlookAddInTutorial/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_OutlookAddInTutorial#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OutlookAddInTutorial/VB/ThisAddIn.vb#3)]  
  
 若要修改每封新郵件，前面的程式碼範例會使用下列物件：  
  
-   `ThisAddIn` 類別的 `Application` 欄位。`Application` 欄位會傳回 <xref:Microsoft.Office.Interop.Outlook.Application> 物件，此物件代表 Outlook 目前的執行個體。  
  
-   <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> 事件之事件處理常式的 `Inspector` 參數。`Inspector` 參數是 <xref:Microsoft.Office.Interop.Outlook.Inspector> 物件，代表新郵件的偵測器視窗。 如需詳細資訊，請參閱[Outlook 方案](../vsto/outlook-solutions.md)。  
  
## 測試專案  
 當您建置並執行專案時，請確認文字會出現在新郵件的主旨行和本文中。  
  
#### 測試專案  
  
1.  按 **F5** 建置及執行專案。  
  
     當您建置專案時，程式碼會編譯到包含在專案建置輸出資料夾中的組件。 Visual Studio 也會建立一組登錄項目，以便 Outlook 探索和載入 VSTO 增益集，而且會設定開發電腦中的安全性設定，讓 VSTO 增益集可以執行。 如需詳細資訊，請參閱[Office Solution Build Process Overview](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)。  
  
2.  在 Outlook 中建立新郵件。  
  
3.  請確認下列文字加入郵件的主旨行和本文中。  
  
     **This text was added by using code.**  
  
4.  關閉 Outlook。  
  
## 清除 Project  
 當您完成專案開發時，請從開發電腦移除 VSTO 增益集組件、登錄項目和安全性設定。 否則，每次在開發電腦上開啟 Outlook 時，都會執行 VSTO 增益集。  
  
#### 清除專案  
  
1.  在 Visual Studio 中，按一下 \[建置\] 功能表上的 \[清除方案\]。  
  
## 後續步驟  
 現在您已經建立 Outlook 的基本 VSTO 增益集，可以從下列主題進一步了解如何開發 VSTO 增益集：  
  
-   您可以使用 Outlook VSTO 增益集執行的一般程式設計工作。 如需詳細資訊，請參閱[VSTO 增益集程式設計](../vsto/programming-vsto-add-ins.md)。  
  
-   使用 Outlook 的物件模型。 如需詳細資訊，請參閱[Outlook 方案](../vsto/outlook-solutions.md)。  
  
-   自訂 Outlook 的 UI，例如，透過將自訂索引標籤加入功能區，或建立您專屬自訂工作窗格的方式。 如需詳細資訊，請參閱[Office UI 自訂](../vsto/office-ui-customization.md)。  
  
-   建置及偵錯 Outlook VSTO 增益集。 如需詳細資訊，請參閱[建置 Office 方案](../vsto/building-office-solutions.md)。  
  
-   部署 Outlook VSTO 增益集。 如需詳細資訊，請參閱[部署 Office 方案](../vsto/deploying-an-office-solution.md)。  
  
## 請參閱  
 [VSTO 增益集程式設計](../vsto/programming-vsto-add-ins.md)   
 [Outlook 方案](../vsto/outlook-solutions.md)   
 [Office UI 自訂](../vsto/office-ui-customization.md)   
 [建置 Office 方案](../vsto/building-office-solutions.md)   
 [部署 Office 方案](../vsto/deploying-an-office-solution.md)   
 [Office 專案範本概觀](../vsto/office-project-templates-overview.md)  
  
  