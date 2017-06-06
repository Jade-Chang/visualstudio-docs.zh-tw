---
title: "MSBuild 轉換 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, 轉換"
  - "轉換 [MSBuild]"
ms.assetid: d0bcfc3c-14fa-455e-805c-63ccffa4a3bf
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# MSBuild 轉換
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

轉換是以一對一的方式將某個項目清單轉換成另一個。  轉換除了可以讓專案轉換項目清單以外，也可以讓目標識別出其輸入和輸出之間的直接對應。  本主題解釋轉換，以及 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 如何使用轉換更有效率地建置專案。  
  
## 轉換修飾詞  
 轉換並非任意執行，而是受限於特定語法，其中所有轉換修飾詞 \(Modifier\) 的格式須為 %\(*ItemMetaDataName*\)。  任何項目中繼資料都可用來做為轉換修飾詞。  這包括建立每個項目時，指派給項目的已知項目中繼資料。  如需已知項目中繼資料的清單，請參閱 [Well\-known Item Metadata](../msbuild/msbuild-well-known-item-metadata.md)。  
  
 在下列範例中，會將 .resx 檔的清單轉換成 .resources 檔的清單。  轉換修飾詞 %\(檔名\) 會指定每個 .resources 檔的檔名與對應的 .resx 檔相同。  
  
```  
@(RESXFile->'%(filename).resources')  
```  
  
> [!NOTE]
>  您可以使用為標準項目清單指定分隔符號的方式，為已轉換的項目清單指定自訂分隔符號。  例如，若要使用逗號 \(,\) 而非預設的分號 \(;\) 分隔已轉換的項目清單，請使用下列 XML。  
  
```  
@(RESXFile->'Toolset\%(filename)%(extension)', ',')  
```  
  
 例如，如果 @\(RESXFile\) 項目清單中的項目為 `Form1.resx`、`Form2.resx` 與 `Form3.resx`，則已轉換清單中的輸出將會是 `Form1.resources`、`Form2.resources` 與 `Form3.resources`。  
  
## 使用多個修飾詞  
 轉換運算式可包含多個能夠依據任意順序結合而且可以重複的修飾詞。  在下列範例中，包含檔案的目錄名稱已變更，但檔案仍維持原始名稱與副檔名。  
  
```  
@(RESXFile->'Toolset\%(filename)%(extension)')  
```  
  
 例如，如果 `RESXFile` 項目清單中的項目為 `Project1\Form1.resx`、`Project1\Form2.resx` 與 `Project1\Form3.text`，則已轉換清單中的輸出將會是 `Toolset\Form1.resx`、`Toolset\Form2.resx` 與 `Toolset\Form3.text`。  
  
## 相依性分析  
 轉換能保證已轉換項目清單與原始項目清單之間的一對一對應。  因此，當目標建立的輸出為輸入的轉換時，[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 即可分析輸入和輸出的時間戳記，並決定要略過、建置或部分重建目標。  
  
 在下列範例的[Copy Task](../msbuild/copy-task.md)中，`BuiltAssemblies` 項目清單中的每個檔案都會對應至該工作目的資料夾中的某個檔案，此檔案是使用轉換，在 `Outputs` 屬性中指定。  如果 `BuiltAssemblies` 項目清單中的檔案發生變更，則只會針對已變更的檔案執行 `Copy` 工作，並且略過其他所有檔案。  如需相依性分析及如何使用轉換的詳細資訊，請參閱 [如何：累加建置](../msbuild/how-to-build-incrementally.md)。  
  
```  
<Target Name="CopyOutputs"  
    Inputs="@(BuiltAssemblies)"  
    Outputs="@(BuiltAssemblies -> '$(OutputPath)%(Filename)%(Extension)')">  
  
    <Copy  
        SourceFiles="@(BuiltAssemblies)"  
        DestinationFolder="$(OutputPath)"/>  
  
</Target>  
```  
  
## 範例  
  
### 描述  
 下列範例說明使用轉換的 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 專案檔。  這個範例假設 c:\\sub0\\sub1\\sub2\\sub3 目錄中只有一個 .xsd 檔，而且工作目錄是 c:\\sub0。  
  
### 程式碼  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <Schema Include="sub1\**\*.xsd"/>  
    </ItemGroup>  
  
    <Target Name="Messages">  
        <Message Text="rootdir: @(Schema->'%(rootdir)')"/>  
        <Message Text="fullpath: @(Schema->'%(fullpath)')"/>  
        <Message Text="rootdir + directory + filename + extension: @(Schema->'%(rootdir)%(directory)%(filename)%(extension)')"/>  
        <Message Text="identity: @(Schema->'%(identity)')"/>  
        <Message Text="filename: @(Schema->'%(filename)')"/>  
        <Message Text="directory: @(Schema->'%(directory)')"/>  
        <Message Text="relativedir: @(Schema->'%(relativedir)')"/>  
        <Message Text="extension: @(Schema->'%(extension)')"/>  
    </Target>  
</Project>  
```  
  
### 註解  
 這個範例產生下列輸出。  
  
```  
rootdir: C:\  
fullpath: C:\xmake\sub1\sub2\sub3\myfile.xsd  
rootdir + directory + filename + extension: C:\xmake\sub1\sub2\sub3\myfile.xsd  
identity: sub1\sub2\sub3\myfile.xsd  
filename: myfile  
directory: xmake\sub1\sub2\sub3\  
relativedir: sub1\sub2\sub3\  
extension: .xsd  
```  
  
## 請參閱  
 [MSBuild 概念](../msbuild/msbuild-concepts.md)   
 [MSBuild Reference](../msbuild/msbuild-reference.md)   
 [如何：累加建置](../msbuild/how-to-build-incrementally.md)