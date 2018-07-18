---
title: 資料夾項目 （Visual Studio 專案範本） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Folder
helpviewer_keywords:
- Folder element [Visual Studio project templates]
ms.assetid: 558e3d41-0db5-4c44-82bb-6bb87892b093
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c2ecf9c2973a5fb09cf1a217bd700882dce41626
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132811"
---
# <a name="folder-element-visual-studio-project-templates"></a>資料夾項目 (Visual Studio 專案範本)
指定將會加入至專案的資料夾。  
  
 \<VSTemplate >  
 \<TemplateContent >  
 \<Project>  
 \<資料夾 >  
  
## <a name="syntax"></a>語法  
  
```  
<Folder Name="Project Folder">  
    <Folder> ... </Folder>  
    <ProjectItem> ... </ProjectItem>  
</Folder>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節將說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`Name`|必要屬性。<br /><br /> 專案資料夾的名稱。|  
|`TargetFolderName`|選擇性屬性。<br /><br /> 指定要從範本建立專案時，提供給資料夾的名稱。 這個屬性可用於使用取代參數建立的資料夾名稱或命名的資料夾有國際字串不能直接在.zip 檔案。|  
  
### <a name="child-elements"></a>子項目  
  
|項目|描述|  
|-------------|-----------------|  
|`Folder`|指定要加入至專案的資料夾。 `Folder` 項目可以包含子`Folder`項目。|  
|[專案項目](../extensibility/projectitem-element-visual-studio-item-templates.md)|指定要加入至專案的檔案。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[Project](../extensibility/project-element-visual-studio-templates.md)|選擇性子項目[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)。|  
  
## <a name="remarks"></a>備註  
 `Folder` 是選擇性的子系的`Project`。  
  
 您可以使用任何下列方法，以將專案項目組織成範本中的資料夾：  
  
-   在範本的.zip 檔案，包括資料夾並將它們加入至專案的.vstemplate 檔案中指定的路徑中的檔案`ProjectItem`項目，不含`Folder`項目。 這是建議的方法。 例如:   
  
     `...`  
  
     `<ProjectItem>\Folder\item.cs</ProjectItem>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
-   將資料夾加入範本的.zip 檔案，並將它們加入使用.vstemplate 檔案中的專案`Folder`項目。 例如:   
  
     `...`  
  
     `<Folder name="Folder">`  
  
     `<ProjectItem>item.cs</ProjectItem>`  
  
     `</Folder>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
-   在範本的.zip 檔案中，不包含資料夾，但將使用的資料夾新增`TargetFileName`屬性`ProjectItem`項目。 例如:   
  
     `...`  
  
     `<ProjectItem TargetFileName="\Folder\item.cs">item.cs</ProjectItem>`  
  
     `<ProjectItem>Form1.cs</ProjectItem>`  
  
     `...`  
  
## <a name="example"></a>範例  
 下列範例說明的專案範本的中繼資料[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]Windows 應用程式。  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyTemplate.csproj">  
            <ProjectItem>Form1.cs<ProjectItem>  
            <ProjectItem>Form1.Designer.cs</ProjectItem>  
            <ProjectItem>Program.cs</ProjectItem>  
            <Folder Name="Properties">  
                <ProjectItem>AssemblyInfo.cs</ProjectItem>  
                <ProjectItem>Resources.resx</ProjectItem>  
                <ProjectItem>Resources.Designer.cs</ProjectItem>  
                <ProjectItem>Settings.settings</ProjectItem>  
                <ProjectItem>Settings.Designer.cs</ProjectItem>  
            </Folder>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)   
 [建立專案和項目範本](../ide/creating-project-and-item-templates.md)   
 [ProjectItem 元素 (Visual Studio 項目範本)](../extensibility/projectitem-element-visual-studio-item-templates.md)