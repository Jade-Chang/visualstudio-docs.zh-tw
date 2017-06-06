---
title: "Visio 物件模型概觀"
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
  - "Visio [Visual Studio 中的 Office 開發]，物件模型"
  - "物件模型 [Visual Studio 中的 Office 程式開發]，Office"
  - "物件模型 [Visual Studio 中的 Office 程式開發]，Visio"
  - "物件 [Visual Studio 中的 Office 程式開發]，Office 物件模型"
  - "Office 物件模型"
  - "Visio 物件模型"
ms.assetid: 11f0ae0c-feff-46c7-9885-b968391718f7
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Visio 物件模型概觀
  若要開發 Microsoft Office Visio 的 Office 方案，您可以與 Visio 物件模型互動。 組成這個物件模型的類別和介面，是由 Visio 的主要 Interop 組件所提供，並在 Microsoft.Office.Interop.Visio 命名空間中定義。  
  
 本主題提供簡短的 Visio 物件模型概觀。 如需使用 Visio 物件模型在 Office 專案中執行工作的詳細資訊，請參閱下列主題：  
  
-   [使用 Visio 文件](../vsto/working-with-visio-documents.md)  
  
-   [使用 Visio 圖案](../vsto/working-with-visio-shapes.md)  
  
## 了解 Visio 物件模型  
 Visio 會提供許多您可以與之互動的物件。 這些物件是在密切遵循使用者介面的階層內組合管理。 階層的頂端是 [Microsoft.Office.Interop.Visio.Application](HV10077088) 物件。 這個物件代表 Visio 目前的執行個體。Microsoft.Office.Interop.Visio.Application 物件包含 Microsoft.Office.Interop.Visio.Document 和 Microsoft.Office.Interop.Visio.Page  物件以及 Microsoft.Office.Interop.Visio.Documents 和 Microsoft.Office.Interop.Visio.Pages 集合。 這些物件和集合每個都有許多方法和屬性，您可以存取操作並與之互動。  
  
 如需詳細資訊，請參閱 [Microsoft.Office.Interop.Visio.Application](HV10077088)、[Microsoft.Office.Interop.Visio.Document](HV10077095) 和 [Microsoft.Office.Interop.Visio.Page](HV10077063) 物件，以及 [Microsoft.Office.Interop.Visio.Documents](HV10077062) 和 [Microsoft.Office.Interop.Visio.Pages](HV10077074) 集合的 VBA 參考文件。  
  
 下列各節簡述最上層物件，以及它們彼此之間的互動方式。 這些物件包含下列物件：  
  
-   Application 物件  
  
-   Document 物件  
  
-   Page 物件  
  
### Application 物件  
 Microsoft.Office.Interop.Visio.Application 物件代表 Visio 應用程式，而且是所有其他物件的父系。 其成員通常會整體套用至 Visio。 您可以使用 Microsoft.Office.Interop.Visio.Application 和 Microsoft.Office.Interop.Visio.ApplicationSettings 物件的屬性和方法來控制 Visio 環境。  
  
 在 VSTO 增益集專案中，您可以使用 `ThisAddIn` 類別的 `Application` 欄位存取 Microsoft.Office.Interop.Visio.Application 物件。 如需詳細資訊，請參閱[VSTO 增益集程式設計](../vsto/programming-vsto-add-ins.md)。  
  
### Document 物件  
 Microsoft.Office.Interop.Visio.Document 物件是 Visio 程式設計的核心。 它代表繪圖、樣板或範本檔案。 當您開啟 Visio 文件或建立新的文件時，即建立新的 Microsoft.Office.Interop.Visio.Document 物件，它會加入 Microsoft.Office.Interop.Visio.Application 物件的 Microsoft.Office.Interop.Visio.Documents 集合 。  
  
 具有焦點的文件稱為使用中文件。 它是由 Microsoft.Office.Interop.Visio.Application 物件的Microsoft.Office.Interop.Visio.Application.ActiveDocument 屬性所代表。  
  
### Page 物件  
 Microsoft.Office.Interop.Visio.Page 物件代表前景頁面或背景頁面的繪圖區域。 您可以使用 Microsoft.Office.Interop.Visio.Page.Background 屬性判斷頁面為前景或背景頁面。  
  
 若要建立圖形，您可以使用包含 Microsoft.Office.Interop.Visio.Page.DrawSpline 和 Microsoft.Office.Interop.Visio.Page.DrawOval 方法的方法。 此外，您可以使用 Microsoft.Office.Interop.Visio.Page.Drop 或 Microsoft.Office.Interop.Visio.Page.DropMany 方法，從樣板擷取主圖形，並將圖形放在頁面上。  
  
## 使用 Visio 物件模型文件  
 如需 Visio 物件模型的完整資訊，您可以參考 Visio VBA 物件模型參考。 VBA 物件模型參考記載公開給 Visual Basic for Applications \(VBA\) 程式碼時的 Visual 物件模型。 如需詳細資訊，請參閱 [Visio 2010 物件模型參考](http://go.microsoft.com/fwlink/?LinkId=199775)。  
  
 VBA 物件模型參考中的所有物件和成員都會對應至 Visio 主要 Interop 組件 \(PIA\) 中的類型和成員。 例如，VBA 物件模型參考中的 Document 物件會對應至 Visio PIA 中的 Microsoft.Office.Interop.Visio.Document 類型。 雖然 VBA 物件模型參考會提供大部分屬性、方法和事件的程式碼範例，但如果您想要在以 Visual Studio 建立的 Visio VSTO 增益集專案中使用這些程式碼範例，您必須將此參考中的 VBA 程式碼改成 Visual Basic 或 Visual C\# 程式碼。  
  
> [!NOTE]  
>  目前沒有 Visio 主要 Interop 組件的參考文件。  
  
 如需相關程式碼範例及其他建立 Visio 解決方案的工具，請參閱 [Visio 2010 軟體開發套件](http://go.microsoft.com/fwlink/?LinkId=196501)。  
  
### 主要 Interop 組件中的其他類型  
 因為實作差異之故，您可以在主要 Interop 組件中找到對 VBA 不可見的類型。 VBA 提供檢視 Visio 物件模型，內含您可直接使用的物件和成員。 主要 Interop 組件會公開相同的物件模型，但也包含其他介面、類別和成員，可將 COM 物件模型中的物件轉譯成 managed 程式碼。 這些額外的項目不宜直接在程式碼中使用。  
  
 如需詳細資訊，請參閱 [Office 主要 Interop 組件中的類別和介面概觀](http://go.microsoft.com/fwlink/?LinkId=189592)和 [Office 主要 Interop 組件](../vsto/office-primary-interop-assemblies.md)。  
  
## 請參閱  
 [Visio 方案](../vsto/visio-solutions.md)   
 [使用 Visio 文件](../vsto/working-with-visio-documents.md)   
 [使用 Visio 圖案](../vsto/working-with-visio-shapes.md)  
  
  