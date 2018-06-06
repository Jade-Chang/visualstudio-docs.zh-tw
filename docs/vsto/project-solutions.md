---
title: 專案的方案
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [Office development in Visual Studio], Project
- Office solutions [Office development in Visual Studio], Project
- Project [Office development in Visual Studio]
- templates [Office development in Visual Studio], Project
- Office projects [Office development in Visual Studio], Project
- solutions [Office development in Visual Studio], Project
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c3364c778b8dfc290ef06b7daa5ba063ac31f3db
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34692596"
---
# <a name="project-solutions"></a>專案的方案
  [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] 提供的專案範本可用來建立 Microsoft Office Project 的 VSTO 增益集。 您可以使用 VSTO 增益集來自動化 Project、擴充 Project 功能，或自訂 Project 的使用者介面 (UI)。  
  
 如需 VSTO 增益集的詳細資訊，請參閱[VSTO 增益集進行程式設計快速入門](../vsto/getting-started-programming-vsto-add-ins.md)和[架構的 VSTO 增益集](../vsto/architecture-of-vsto-add-ins.md)。如果您不熟悉使用 Microsoft Office 進行程式設計，請參閱[開始&#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/getting-started-office-development-in-visual-studio.md)。  
  
 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]  
  
> [!NOTE]  
>  感興趣開發方案，擴充的 Office 體驗，跨[多個平台](https://dev.office.com/add-in-availability)嗎？ 查看新[Office 增益集模型](https://dev.office.com/docs/add-ins/overview/office-add-ins)。 Office 增益集有相較於 VSTO 增益集和方案、 較小的耗用量，您可以使用幾乎任何 web 程式設計技術，例如 HTML5、 JavaScript、 CSS3 和 XML 來建置。  
  
## <a name="automate-project-by-using-the-project-object-model"></a>使用 project 物件模型自動化 project  
 Project 物件模型公開許多可用於自動化 Project 的類別。 這些類別可讓您撰寫程式碼以完成一般工作，例如以程式設計方式建立和修改專案中的工作。  
  
 若要存取 VSTO 增益集中的 Project 物件模型，請使用專案中 `Application` 類別的 `ThisAddIn` 欄位。 `Application`欄位會傳回`Microsoft.Office.Interop.MsProject.Application`物件，代表目前的執行個體的專案。 如需詳細資訊，請參閱[程式 VSTO 增益集](../vsto/programming-vsto-add-ins.md)。  
  
 呼叫 Project 物件模型時，您使用的類型是由 Project 的主要 Interop 組件所提供。 主要 Interop 組件的作用，如同 VSTO 增益集中 Managed 程式碼與專案中 COM 物件模型之間的橋樑。 Project 主要 interop 組件中的所有類型都定義在`Microsoft.Office.Interop.MSProject`命名空間。 如需主要 interop 組件的詳細資訊，請參閱[Office 方案開發概觀&#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md)和[Office 主要 interop 組件](../vsto/office-primary-interop-assemblies.md)。  
  
## <a name="use-the-project-object-model-documentation"></a>使用 project 物件模型文件  
 如需 Project 物件模型的完整資訊，您可以參考 Project VBA 物件模型參考。 VBA 物件模型參考記載公開給 Visual Basic for Applications (VBA) 程式碼時的專案物件模型。 如需詳細資訊，請參閱[Project 2010 物件模型參考](http://go.microsoft.com/fwlink/?LinkId=199771)。  
  
 VBA 物件模型參考中的所有物件和成員都會對應至 Project 主要 Interop 組件 (PIA) 中的類型和成員。 例如，VBA 物件模型參考中的行事曆物件會對應至`Microsoft.Office.Interop.MSProject.Calendar`Project PIA 中的型別。 雖然 VBA 物件模型參考會提供大部分屬性、方法和事件的程式碼範例，但如果您想要在以 Visual Studio 建立的 Project VSTO 增益集專案中使用這些程式碼範例，您必須將此參考中的 VBA 程式碼改成 Visual Basic 或 Visual C# 程式碼。  
  
> [!NOTE]  
>  目前沒有 Project 主要 Interop 組件的參考文件。  
  
### <a name="infrastructure-types-in-the-project-primary-interop-assembly"></a>Project 主要 interop 組件中的基礎結構類型  
 在您撰寫使用 Project PIA 的程式碼時，可能會注意到未在 VBA 參考中描述的許多類型。 這些額外類型會協助將 Project 的 COM 架構物件模型轉譯成 Managed 程式碼，不適合直接在程式碼中使用。  
  
 如需詳細資訊，請參閱[Office 主要 interop 組件中類別和介面概觀](http://go.microsoft.com/fwlink/?LinkId=189592)。  
  
## <a name="customize-the-user-interface-of-project"></a>自訂使用者介面的專案  
 您可以使用下列方式自訂 Project UI。  
  
|工作|如需詳細資訊|  
|----------|--------------------------|  
|在 Project 的功能區中加入自訂索引標籤。|[功能區概觀](../vsto/ribbon-overview.md)|  
  
 如需有關自訂 UI 的專案範本和其他 Microsoft Office 應用程式的詳細資訊，請參閱[Office UI 自訂](../vsto/office-ui-customization.md)。  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說： 建立第一個 VSTO 增益集專案](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)   
 [VSTO 增益集進行程式設計快速入門](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Office 方案開發概觀&#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [VSTO 增益集的架構](../vsto/architecture-of-vsto-add-ins.md)   
 [如何： 在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [撰寫 VSTO 增益集](../vsto/programming-vsto-add-ins.md)   
 [在 Office 方案中撰寫程式碼](../vsto/writing-code-in-office-solutions.md)   
 [Office 主要 interop 組件](../vsto/office-primary-interop-assemblies.md)   
 [Office UI 自訂](../vsto/office-ui-customization.md)   
 [Project 2010 和 Project Server 2010 中的 Office 程式開發](http://go.microsoft.com/fwlink/?LinkId=199016)  
  
  