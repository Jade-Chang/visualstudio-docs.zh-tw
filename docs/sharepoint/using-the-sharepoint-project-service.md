---
title: 使用 SharePoint 專案服務 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project service
- SharePoint development in Visual Studio, extensibility features
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: efe2e2073ead64bfbc697b9d6c824066af947580
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="using-the-sharepoint-project-service"></a>使用 SharePoint 專案服務
  SharePoint 專案系統包含可讓您執行專案系統相關工作的專案服務。 專案服務是 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> 物件。  
  
 您可以在任何 SharePoint 工具擴充功能中存取 SharePoint 專案服務。 您也可以在其他類型的 Visual Studio 擴充功能 (例如增益集和 VSPackages) 中存取 SharePoint 專案服務。 如需詳細資訊，請參閱[How to： 擷取 SharePoint 專案服務](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)。  
  
## <a name="project-service-features"></a>專案服務功能  
 下表列出您可以使用 SharePoint 專案服務執行的工作和可使用的 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> 方法或屬性，以執行每項工作。  
  
|工作|要使用的成員|  
|----------|-------------------|  
|存取任何在 Visual Studio 中開啟的 SharePoint 專案。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Projects%2A> 屬性。|  
|存取所有可用 (包括內建和自訂專案項目類型) 的 SharePoint 專案項目類型。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.ProjectItemTypes%2A> 屬性。|  
|存取所有 SharePoint 專案可用的部署步驟 (包括內建和自訂部署步驟)。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.DeploymentSteps%2A> 屬性。|  
|存取開發人員在 SharePoint 專案中重構程式碼時所引發的事件。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.CodeRefactoringEvents%2A> 屬性。|  
|執行自訂*SharePoint 命令*呼叫 SharePoint 伺服器物件模型。 如需有關 SharePoint 命令的詳細資訊，請參閱[呼叫 SharePoint 物件模型](../sharepoint/calling-into-the-sharepoint-object-models.md)。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A> 屬性。|  
|將 SharePoint 專案系統中的類型轉換成 Visual Studio 自動化物件模型或整合物件模型中的類型，反之亦然。 如需詳細資訊，請參閱[轉換之間 SharePoint 專案系統類型與其他 Visual Studio 專案類型](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> 方法。|  
|寫入訊息至**輸出**視窗或**錯誤清單**Visual Studio 中的視窗。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Logger%2A> 屬性。|  
|存取 Visual Studio 中其他可用的服務。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.ServiceProvider%2A> 屬性。|  
|擷取用來偵錯方案之本機 SharePoint 網站的安裝資料夾路徑。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointInstallPath%2A> 屬性。|  
|判斷電腦上是否安裝 [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] 或 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.IsSharePointInstalled%2A> 屬性。|  
|驗證 SharePoint 方案中的功能或封裝。|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.PackageValidationProvider%2A> 屬性。|  
  
## <a name="see-also"></a>另請參閱  
 [SharePoint 專案系統類型與其他 Visual Studio 專案類型之間轉換](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [如何： 擷取 SharePoint 專案服務](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)   
 [擴充 Visual Studio 中的 SharePoint 工具](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [工具擴充功能的 SharePoint 程式撰寫模型概觀](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)   
 [如何：從 DTE 物件取得服務](http://msdn.microsoft.com/library/bb166401.aspx)  
  
  