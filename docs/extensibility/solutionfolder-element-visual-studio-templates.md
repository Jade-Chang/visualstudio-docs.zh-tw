---
title: "SolutionFolder 項目 (Visual Studio 範本) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#SolutionFolder"
helpviewer_keywords: 
  - "<SolutionFolder> 項目 [Visual Studio 樣板]"
  - "SolutionFolder 項目 [Visual Studio 樣板]"
ms.assetid: 963f0398-fb50-4d8e-879d-d48f8b7c6d80
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# SolutionFolder 項目 (Visual Studio 範本)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

將多專案範本中的專案分組。  
  
## 語法  
  
```  
<SolutionFolder Name="DirectoryName">  
    ...  
</SolutionFolder>  
```  
  
## 屬性和項目  
 下列章節將說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`Name`|必要屬性。<br /><br /> 方案資料夾的名稱。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[ProjectTemplateLink](../extensibility/projecttemplatelink-element-visual-studio-templates.md)|選擇性項目。<br /><br /> 指定多專案範本中某一個專案的 .vstemplate 檔路徑。|  
|`SolutionFolder`|選擇性項目。<br /><br /> 將多專案範本中的專案分組。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|指定多專案範本的組織和內容。|  
|`SolutionFolder`|將多專案範本中的專案分組。|  
  
## 備註  
 多專案範本是做為兩個以上專案的容器使用。  `SolutionFolder` 項目可將範本中的專案分成群組。  由 `SolutionFolder` 項目所指定的資料夾會建立為 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 之專案中的方案資料夾。  如需有關多專案範本的詳細資訊，請參閱[如何：建立多專案的範本](../ide/how-to-create-multi-project-templates.md)。  
  
## 範例  
 這個範例會使用 `SolutionFolder` 項目將多專案範本分成兩個群組，也就是 `Math Classes` 和 `Graphics Classes`。  範本包含四個專案，每個方案資料夾各包含兩個專案。  
  
```  
<VSTemplate Version="3.0.0" Type="ProjectGroup"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>Multi-Project Template Sample</Name>  
        <Description>An example of a multi-project template</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>VisualBasic</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectCollection>  
            <SolutionFolder Name="Math Classes">  
                <ProjectTemplateLink ProjectName="MathClassLib1">  
                    MathClassLib1\MyTemplate.vstemplate  
                </ProjectTemplateLink>  
                <ProjectTemplateLink ProjectName="MathClassLib2">  
                    MathClassLib2\MyTemplate.vstemplate  
                </ProjectTemplateLink>  
            </SolutionFolder>  
            <SolutionFolder Name="Graphics Classes">  
                <ProjectTemplateLink ProjectName="GraphicsClassLib1">  
                    GraphicsClassLib1\MyTemplate.vstemplate  
                </ProjectTemplateLink>  
                <ProjectTemplateLink ProjectName="GraphicsClassLib2">  
                    GraphicsClassLib2\MyTemplate.vstemplate  
                </ProjectTemplateLink>  
            </SolutionFolder>  
        </ProjectCollection>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## 請參閱  
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)   
 [建立自訂專案與項目範本](../ide/creating-project-and-item-templates.md)   
 [如何：建立多專案的範本](../ide/how-to-create-multi-project-templates.md)