---
title: '&lt;自訂&gt;元素 （在 Visual Studio 中的 Office 程式開發）'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- <customizations> element
- customizations element
- application manifests [Office development in Visual Studio], <customizations> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ef7aa93494ef2b2a33ab4533e217bd37ccd07420
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
---
# <a name="ltcustomizationsgt-element-office-development-in-visual-studio"></a>&lt;自訂&gt;元素 （在 Visual Studio 中的 Office 程式開發）
  `customizations` 命名空間的 `vstov4` 項目包含安裝及載入每個 Office 方案的所有資訊。  
  
## <a name="syntax-for-document-level-customizations"></a>文件層級自訂的語法  
  
```xml
<customizations>  
  <customization  
    id  
    <document  
      solutionId  
    />  
  </customization>  
</customizations>  
```  
  
## <a name="syntax-for-vsto-add-ins"></a>VSTO 增益集的語法  
  
```xml
<customizations>  
  <customization  
    id  
    <appAddin  
      application  
      loadBehavior  
      keyName>  
    <friendlyName></friendlyName>  
    <description></description>  
    <formRegions></formRegions>  
  </customization>  
</customizations>  
```  
  
## <a name="elements-and-attributes"></a>項目和屬性  
 `customizations` 項目包含每個 Office 方案的特定資訊。 這個項目必須位於下列命名空間： `vstov4=urn:schemas-microsoft-com:vsto.v4`。 組件的子項目也必須在這個命名空間中。  
  
 `customizations` 項目沒有任何屬性。  
  
 `customizations` 項目具有下列子項目。  
  
### <a name="customization"></a>自訂  
 必要。 `customization`中的項目`vstov4`命名空間中定義[&#60;自訂&#62;元素&#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/customization-element-office-development-in-visual-studio.md)。  
  
## <a name="example-of-a-document-level-customization"></a>文件層級自訂範例  
  
### <a name="description"></a>描述  
 下列程式碼範例說明文件層級自訂的 `customizations` 項目。  
  
> [!NOTE]  
>  這個程式碼範例是中提供之較大範例的一部分[Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)。  
  
### <a name="code"></a>程式碼  
  
```xml
<vstov4:customizations   
  xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4">  
  <vstov4:customization>  
    <vstov4:document   
      solutionId="73e" />  
  </vstov4:customization>  
</vstov4:customizations>  
```  
  
## <a name="example-of-an-vsto-add-in"></a>VSTO 增益集的範例  
  
### <a name="description"></a>描述  
 下列程式碼範例說明 VSTO 增益集的 `customizations` 項目。 這是包含表單區域的 Outlook VSTO 增益集。 這個程式碼範例是中提供之較大範例的一部分[Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)。  
  
### <a name="code"></a>程式碼  
  
```xml
<vstov4:customizations   
  xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4">  
  <vstov4:customization>  
    <vstov4:appAddIn   
      application="Outlook"   
      loadBehavior="3"   
      keyName="ContosoOutlookAddIn">  
      <vstov4:friendlyName>  
        ContosoOutlookAddIn  
      </vstov4:friendlyName>  
      <vstov4:description>  
        ContosoOutlookAddIn - Outlook VSTO Add-in   
        created with Visual Studio Tools for Office  
      </vstov4:description>  
      <vstov4:formRegions>  
        <vstov4:formRegion  
            name="OutlookAddIn1.FormRegion1">  
          <vstov4:messageClass name="IPM.Note" />  
          <vstov4:messageClass name="IPM.Contact" />  
          <vstov4:messageClass name="IPM.Appointment" />  
        </vstov4:formRegion>  
      </vstov4:formRegions>  
    </vstov4:appAddIn>  
  </vstov4:customization>  
</vstov4:customizations>  
```  
  
## <a name="see-also"></a>另請參閱  
 [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)   
 [Office 方案的部署資訊清單](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce 應用程式資訊清單](/visualstudio/deployment/clickonce-application-manifest)  
  
  