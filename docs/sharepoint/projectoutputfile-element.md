---
title: ProjectOutputFile 項目 |Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectOutputFile element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 99f8173da22f631a1be74c18d4312f74958259e9
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/29/2018
ms.locfileid: "37118615"
---
# <a name="projectoutputfile-element"></a>ProjectOutputFile 項目
  表示要部署到 SharePoint 時，與專案項目包含的個別專案的輸出。  
  
## <a name="syntax"></a>語法  
  
```xml  
<ProjectOutputFile ProjectId = "GUID of the project"  
    ProjectPath = "Relative path of the project"  
    Target = "Deployment path of the project output"  
    Type = "Type of deployment for the project output" />  
```  
  
## <a name="type"></a>類型  
 **ProjectOutputFileType**  
  
## <a name="attributes-and-elements"></a>屬性和元素
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|**專案識別碼**|所需**xs: string**屬性。<br /><br /> 您想要包含輸出相依專案的 GUID。 這會對應至**ProjectGuid**相依的專案檔中的項目。|  
|**ProjectPath**|所需**xs: string**屬性。<br /><br /> 相對路徑，包括專案檔案名稱的相依專案具有您想要包含的輸出。 這個路徑是相對於包含 SharePoint 專案項目之 SharePoint 專案的根資料夾。|  
|**Target**|選擇性**xs: string**屬性。<br /><br /> 相依專案輸出到部署在 SharePoint 伺服器上，相對於部署根資料夾的所在路徑。 部署根資料夾由所指定之部署類型**型別**屬性。<br /><br /> 如需詳細資訊，請參閱描述**部署路徑**並**Deployment Root**屬性的 SharePoint 專案中的項目[開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)。|  
|**Type**|所需**xs: string**屬性。<br /><br /> 若要使用的相依專案輸出的部署類型。 如需可能值的詳細資訊，請參閱的描述**部署類型**屬性中的 SharePoint 專案項目的[開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)。|  
  
### <a name="child-elements"></a>子元素
 無。  
  
### <a name="parent-elements"></a>父元素
  
|元素|描述|  
|-------------|-----------------|  
|[檔案](../sharepoint/files-element.md)|指定要部署到 SharePoint 時，與 SharePoint 專案項目包含的檔案。|  
  
## <a name="remarks"></a>備註  
 使用**ProjectOutputFile**項目來部署的 SharePoint 專案項目中包含專案的輸出。 您可以指定不同的專案或相同的專案，其中包含的專案項目。 如需詳細資訊，請參閱 <<c0> [ 提供專案項目中的封裝和部署資訊](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)。  
  
## <a name="element-information"></a>項目資訊
  
|||  
|-|-|  
|**命名空間**|http<nolink>: //schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|  
|**結構描述名稱**|SharePoint 專案項目結構描述|  
|**驗證檔案**|ProjectItemModelSchema.xsd|  
|**可以是空的**|否|  
  
## <a name="see-also"></a>另請參閱
 [SharePoint 專案項目結構描述參考](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [提供專案項目中的封裝和部署資訊](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)   
 [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)  
  
