---
title: 按鈕項目 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Buttons element (VSCT XML schema)
- VSCT XML schema elements, Buttons
ms.assetid: 96dccf51-2b00-4700-9d28-924b34c21ecd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 128016b892206db64a5295c8c15b26b87637b530
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/19/2018
ms.locfileid: "39154267"
---
# <a name="button-element"></a>按鈕項目
定義使用者可以互動的項目。 按鈕可以屬於不同類型： 按鈕、 MenuButton 和 SplitDropDown。  
  
## <a name="syntax"></a>語法  
  
```  
<Button guid="guidMyCommandSet" id="MyCommand" priority="0x102" type="button">  
  <Parent>... </Parent>  
  <Icon>... </Icon>  
  <CommandFlag>... </CommandFlag>  
  <Strings>... </Strings>  
</Button>  
```  
  
## <a name="attributes-and-elements"></a>屬性和元素  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|guid|必要。 GUID/識別碼命令識別碼的 GUID。|  
|id|必要。 GUID/識別碼的命令識別項的識別碼。|  
|priority|選擇性。 數值，指定的優先權。|  
|類型|選擇性。 列舉的值，指定的按鈕類型。<br /><br /> 如果未指定，會使用按鈕。<br /><br /> 按鈕<br /> 會出現在工具列 （通常為圖示的按鈕），功能表和快顯功能表標準命令。<br /><br /> MenuButton<br /> 功能表項目不會執行命令，但會產生另一個功能表。<br /><br /> SplitDropDown<br /> 控制項，例如 Microsoft Word 中的 [標準] 工具列上的 [復原與取消復原] 按鈕。|  
|條件|選擇性。 請參閱[條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[父項目](../extensibility/parent-element.md)|選擇性。 按鈕的父項目。|  
|[Icon 元素](../extensibility/icon-element.md)|選擇性。 與按鈕關聯的圖示。|  
|[Command flag 元素](../extensibility/command-flag-element.md)|必要。 CommandFlag 按鈕有效值，如下所示。<br /><br /> -AllowParams<br /><br /> -CommandWellOnly<br /><br /> -DefaultDisabled<br /><br /> -DefaultInvisible<br /><br /> -DontCache<br /><br /> -DynamicItemStart<br /><br /> -DynamicVisibility<br /><br /> -FixMenuController<br /><br /> -IconAndText<br /><br /> -NoButtonCustomize<br /><br /> -NoCustomize<br /><br /> -NoKeyCustomize<br /><br /> -NoShowOnMenuController<br /><br /> -Pict<br /><br /> -PostExec<br /><br /> -ProfferedCmd<br /><br /> -RouteToDocs<br /><br /> -TextCascadeUseBtn<br /><br /> -TextMenuUseButton<br /><br /> -文字變更<br /><br /> -TextChangesButton<br /><br /> -TextContextUseButton<br /><br /> -TextMenuCtrlUseMenu<br /><br /> -TextMenuUseButton<br /><br /> -TextOnly|  
|[Strings 元素](../extensibility/strings-element.md)|必要。 子系[ButtonText 元素](../extensibility/buttontext-element.md)必須定義。|  
|註釋|選擇性註解。|  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[Buttons 元素](../extensibility/buttons-element.md)|分組按鈕項目。|  
  
## <a name="example"></a>範例  
 下列範例會定義中的按鈕 *.vsct*檔案。  

 ```xml
<Button guid="guidMenuTextCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
    <Parent guid="guidMenuTextCmdSet" id="MyMenuGroup" />
    <Icon guid="guidImages" id="bmpPic1" />
    <CommandFlag>TextChanges</CommandFlag>
    <Strings>
          <CommandName>cmdidMyCommand</CommandName>
          <ButtonText>My Command name</ButtonText>
    </Strings>
</Button>
 ```
 
## <a name="see-also"></a>另請參閱  
 [Visual Studio 命令表檔案 (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)