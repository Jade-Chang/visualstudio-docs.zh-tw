---
title: "MSBuild 已知的項目中繼資料 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, item metadata
- MSBuild, well-known item metadata
ms.assetid: b5e791b5-c68f-4978-ad8a-9247d03bb6c0
caps.latest.revision: 12
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 79460291e91f0659df0a4241e17616e55187a0e2
ms.openlocfilehash: 89e1497061d0720590d8abd6e35fbb3422ba51ef
ms.lasthandoff: 02/22/2017

---
# <a name="msbuild-well-known-item-metadata"></a>MSBuild 已知的項目中繼資料
下表說明在建立期間指派給每個項目的中繼資料。 每個範例都使用了下列項目宣告，以在專案中包含 `C:\MyProject\Source\Program.cs` 檔案。  
  
```xml  
<ItemGroup>  
    <MyItem Include="Source\Program.cs" />  
</ItemGroup>  
```  
  
|項目中繼資料|描述|  
|-------------------|-----------------|  
|%(FullPath)|包含項目的完整路徑。 例如: <br /><br /> `C:\MyProject\Source\Program.cs`|  
|%(RootDir)|包含項目的根目錄。 例如: <br /><br /> `C:\`|  
|%(Filename)|包含項目的檔案名稱 (不含副檔名)。 例如: <br /><br /> `Program`|  
|%(Extension)|包含項目的副檔名。 例如: <br /><br /> `.cs`|  
|%(RelativeDir)|包含 `Include` 屬性中指定的路徑，直到最後一個反斜線 (\\) 為止。 例如: <br /><br /> `Source\`|  
|%(Directory)|包含項目的目錄 (不含根目錄)。 例如: <br /><br /> `MyProject\Source\`|  
|%(RecursiveDir)|如果 `Include` 屬性包含萬用字元 \*\*，此中繼資料會指定取代萬用字元的部分路徑。 如需萬用字元的詳細資訊，請參閱[如何：選取要建置的檔案](../msbuild/how-to-select-the-files-to-build.md)。<br /><br /> 如果資料夾 *C:\MySolution\MyProject\Source\\* 包含 Program.cs 檔案，而且專案檔包含此項目：<br /><br /> `<ItemGroup>`<br /><br /> `<MyItem Include="C:\**\Program.cs" />`<br /><br /> `</ItemGroup>`<br /><br /> 則 `%(MyItem.RecursiveDir)` 的值會是 *MySolution\MyProject\Source\\*。|  
|%(Identity)|`Include` 屬性中指定的項目。 例如: <br /><br /> `Source\Program.cs`|  
|%(ModifiedTime)|包含上次修改項目時間的時間戳記。 例如: <br /><br /> `2004-07-01 00:21:31.5073316`|  
|%(CreatedTime)|包含項目建立時間的時間戳記。 例如: <br /><br /> `2004-06-25 09:26:45.8237425`|  
|%(AccessedTime)|包含上次存取項目時間的時間戳記。<br /><br /> `2004-08-14 16:52:36.3168743`|  
  
## <a name="see-also"></a>另請參閱  
 [項目](../msbuild/msbuild-items.md)   
 [批次處理](../msbuild/msbuild-batching.md)   
 [MSBuild 參考](../msbuild/msbuild-reference.md)