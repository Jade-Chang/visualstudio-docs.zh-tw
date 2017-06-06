---
title: "逐步解說：建立 Project 的第一個 VSTO 增益集"
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
  - "Project [Visual Studio 中的 Office 程式開發]，建立第一個專案"
  - "增益集 [Visual Studio 中的 Office 程式開發]，建立第一個專案"
ms.assetid: da2b727e-6db8-4853-bf00-7afe0ef13213
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# 逐步解說：建立 Project 的第一個 VSTO 增益集
  本逐步解說示範如何建立 Microsoft Office Project 的 VSTO 增益集。 不論開啟哪一個專案，您在這類方案中建立的功能都可供應用程式本身使用。 如需詳細資訊，請參閱[Office 方案開發概觀 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)。  
  
 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]  
  
 這個逐步解說將說明下列工作：  
  
-   建立 Project VSTO 增益集專案。  
  
-   撰寫使用 Project 物件模型將工作加入新專案的程式碼。  
  
-   建置和執行專案來進行測試。  
  
-   清除已完成的專案，使得 VSTO 增益集不再於開發電腦上自動執行。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Project_15_short](../vsto/includes/project-15-short-md.md)] 或 [!INCLUDE[Project_14_short](../vsto/includes/project-14-short-md.md)]。  
  
## 建立專案  
  
#### 在 Visual Studio 中建立新專案  
  
1.  啟動 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
2.  在 \[檔案\] 功能表中，指向 \[新增\]，然後按一下 \[專案\]。  
  
3.  在範本窗格中，展開 \[Visual C\#\] 或 \[Visual Basic\]，然後展開 \[Office\/SharePoint\]。  
  
4.  在展開的 \[Office\/SharePoint\] 節點下，選取 \[Office 增益集\] 節點。  
  
5.  在專案範本清單中，選取 \[Project 2010 增益集\] 或 \[Project 2013 增益集\]。  
  
6.  在 \[名稱\] 方塊中，輸入 **FirstProjectAddIn**。  
  
7.  按一下 \[**確定**\]。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會建立 **FirstProjectAddIn** 專案，並在編輯器中開啟 **ThisAddIn** 程式碼檔。  
  
## 撰寫將新工作加入專案的程式碼  
 接著，將程式碼加入 ThisAddIn 程式碼檔。 新的程式碼會使用 Project 的物件模型將新工作加入專案。 根據預設，ThisAddIn 程式碼檔包含下列產生的程式碼：  
  
-   `ThisAddIn` 類別的部分定義。 這個類別提供您撰寫程式碼的進入點，並提供對 Project 物件模型的存取。 如需詳細資訊，請參閱[VSTO 增益集程式設計](../vsto/programming-vsto-add-ins.md)。`ThisAddIn` 類別的其餘部分則定義於您不應修改的隱藏程式碼檔中。  
  
-   `ThisAddIn_Startup` 和 `ThisAddIn_Shutdown` 事件處理常式。 當 Project 載入和卸載 VSTO 增益集時，會呼叫這些事件處理常式。 請使用這些事件處理常式，在 VSTO 增益集載入時將它初始化，以及在 VSTO 增益集卸載時清除它所用的資源。 如需詳細資訊，請參閱[Office 專案中的事件](../vsto/events-in-office-projects.md)。  
  
#### 將工作加入新專案  
  
1.  在 ThisAddIn 程式碼檔中，將下列程式碼加入 `ThisAddIn` 類別。 這段程式碼會定義 Microsoft.Office.Interop.MSProject.Application 類別之 NewProject 事件的事件處理常式。  
  
     當使用者建立新專案時，這個事件處理常式會將工作加入專案。  
  
     [!code-csharp[Trin_ProjectAddInTutorial#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ProjectAddInTutorial/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_ProjectAddInTutorial#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ProjectAddInTutorial/VB/ThisAddIn.vb#1)]  
  
 為了修改專案，這個程式碼範例使用了下列物件：  
  
-   `ThisAddIn` 類別的 `Application` 欄位。`Application` 欄位會傳回 Microsoft.Office.Interop.MSProject.Application 物件，此物件代表 Project 目前的執行個體。  
  
-   NewProject 事件的事件處理常式的 `pj` 參數。`pj` 參數是 Microsoft.Office.Interop.MSProject.Project 物件，此物件代表專案。 如需詳細資訊，請參閱[專案方案](../vsto/project-solutions.md)。  
  
1.  如果使用的是 C\#，請將下列程式碼加入 `ThisAddIn_Startup` 事件處理常式中。 這段程式碼會連接 `Application_Newproject` 事件處理常式和 NewProject 事件。  
  
     [!code-csharp[Trin_ProjectAddInTutorial#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ProjectAddInTutorial/CS/ThisAddIn.cs#2)]  
  
-  
  
## 測試專案  
 當您建置並執行專案時，請確認新工作會出現在產生的新專案中。  
  
#### 測試專案  
  
1.  按 **F5** 建置及執行專案。 Microsoft Project 會啟動並自動開啟新的空白專案。  
  
     當您建置專案時，程式碼會編譯到包含在專案建置輸出資料夾中的組件。 Visual Studio 也會建立一組登錄項目，以便 Project 探索和載入 VSTO 增益集，而且會設定開發電腦中的安全性設定，讓 VSTO 增益集可以執行。 如需詳細資訊，請參閱 [Office 解決方案建置流程概觀](http://msdn.microsoft.com/zh-tw/a9d12e4f-c9ea-4a62-a841-c42b91f831ee)。  
  
2.  確認新工作已加入空白專案。  
  
3.  確認下列文字出現在工作的 \[工作名稱\] 欄位中。  
  
     **This text was added by using code.**  
  
4.  關閉 Microsoft Project。  
  
## 清除 Project  
 當您完成專案開發時，請從開發電腦移除 VSTO 增益集組件、登錄項目和安全性設定。 否則，每次在開發電腦上開啟 Microsoft Project 時，就會執行 VSTO 增益集。  
  
#### 清除專案  
  
1.  在 Visual Studio 中，按一下 \[建置\] 功能表上的 \[清除方案\]。  
  
## 後續步驟  
 現在您已經建立 Project 的基本 VSTO 增益集，可以從下列主題進一步了解如何開發 VSTO 增益集：  
  
-   您可以在 Project VSTO 增益集中執行的一般程式設計工作：[VSTO 增益集程式設計](../vsto/programming-vsto-add-ins.md)。  
  
-   使用 Project 的物件模型：[專案方案](../vsto/project-solutions.md)。  
  
-   建置及偵錯 Project VSTO 增益集：[建置 Office 方案](../vsto/building-office-solutions.md)。  
  
-   部署 Project VSTO 增益集：[部署 Office 方案](../vsto/deploying-an-office-solution.md)。  
  
## 請參閱  
 [VSTO 增益集程式設計](../vsto/programming-vsto-add-ins.md)   
 [專案方案](../vsto/project-solutions.md)   
 [建置 Office 方案](../vsto/building-office-solutions.md)   
 [部署 Office 方案](../vsto/deploying-an-office-solution.md)   
 [Office 專案範本概觀](../vsto/office-project-templates-overview.md)  
  
  