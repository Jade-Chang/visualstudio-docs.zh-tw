---
title: Sdk 元素 (MSBuild) | Microsoft Docs
ms.custom: ''
ms.date: 01/25/2018
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Project
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Sdk element [MSBuild]
- <Sdk> element [MSBuild]
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6e22233d58cdb02194b5d5efe21bc397e9ae3a9c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="sdk-element-msbuild"></a>Sdk 元素 (MSBuild)
參考 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 專案 SDK。  

 \<Project>  
 \<Sdk>  


## <a name="syntax"></a>語法  

```  
<Sdk Name="My.Custom.Sdk"
     Version="1.0.0" />  
```  

## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  

### <a name="attributes"></a>屬性  

|屬性|描述|  
|---------------|-----------------|  
|`Name`|必要屬性。<br /><br /> 專案 SDK 的名稱。|  
|`Version`|選擇性屬性。<br /><br /> 專案 SDK 的版本|  

### <a name="child-elements"></a>子元素  
 無。

### <a name="parent-elements"></a>父項目  
 |元素|描述|  
|-------------|-----------------|  
|[專案](../msbuild/project-element-msbuild.md)|[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 專案檔案的必要根項目。|  

## <a name="see-also"></a>請參閱  
 [如何：參考 MSBuild 專案 SDK](../msbuild/how-to-use-project-sdk.md)   
 [專案檔案結構描述參考](../msbuild/msbuild-project-file-schema-reference.md)   
 [ MSBuild](../msbuild/msbuild.md)
