---
title: CustomParameter 項目 （Visual Studio 範本） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameter
helpviewer_keywords:
- CustomParameters element [Visual Studio project templates]
ms.assetid: 743c4489-74ac-403a-bbaa-eed7d785a3ac
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 154586701386f5f8f56c128920e12ca3147deb6b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31100565"
---
# <a name="customparameter-element-visual-studio-templates"></a>CustomParameter 項目 (Visual Studio 範本)
包含自訂的參數名稱和值，以從範本建立專案或項目時使用。  
  
## <a name="syntax"></a>語法  
  
```  
<CustomParameter Name="name" Value="value">  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`Name`|必要。 參數名稱。 參數的格式為 $*名稱*$。|  
|`Value`|必要。 替代參數值。|  
  
### <a name="child-elements"></a>子項目  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|群組精靈進行參數取代時，應該傳遞至範本精靈的自訂參數。|  
  
## <a name="remarks"></a>備註  
 當範本包含`CustomParameter`項目，每個執行個體`Name`屬性取代`Value`中建立的專案或項目檔案的屬性。  
  
## <a name="example"></a>範例  
 下列範例會示範如何在範本中使用數個自訂參數。 當從使用下列自訂參數的所有執行個體範本建立專案或項目`$color1$`和`$color2$`範本中的檔案將會取代`Red`和`Blue`分別。  
  
```  
<CustomParameters>  
    <CustomParameter Name="$color1$" Value="Red"/>  
    <CustomParameter Name="$color2$" Value="Blue "/>  
</CustomParameters>  
```  
  
## <a name="see-also"></a>另請參閱  
 [CustomParameters 項目 （Visual Studio 範本）](../extensibility/customparameters-element-visual-studio-templates.md)   
 [範本參數](../ide/template-parameters.md)   
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)