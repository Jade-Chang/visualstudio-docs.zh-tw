---
title: CommandTable 項目 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- CommandTable
helpviewer_keywords:
- CommandTable element (VSCT XML schema)
- VSCT XML schema elements, CommandTable
ms.assetid: 15c38159-660a-4ef4-9643-aa6fcfca82a9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5f2dd2ebd076d4225adc86e5ba0cdc9af6ca40df
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="commandtable-element"></a>CommandTable 項目
CommandTable 是.vsct 檔的根項目。 這是定義的實際配置和 ide 提供 VSPackage 的命令類型的檔案。 命令可能會包含功能表項目、 功能表、 工具列和下拉式方塊。 如需詳細資訊，請參閱 [Visual Studio Command Table (.Vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)。  
  
## <a name="syntax"></a>語法  
  
```  
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema" >  
  <Extern>... </Extern>  
  <Include>... </Include>  
  <Define>... </Define>  
  <Commands>... </Commands>  
  <CommandPlacements>... </CommandPlacements>  
  <VisibilityConstraints>... </VisibilityConstraints>  
  <KeyBindings>... </KeyBindings>  
  <UsedCommands... </UsedCommands>  
  <Symbols>... </Symbols>  
</CommandTable>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|xmlns|必要。 XML 命名空間：<br /><br /> xmlns ="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"<br /><br /> xmlns:xs ="http://www.w3.org/2001/XMLSchema"|  
|語言|選擇性。 Language 屬性可能用來指定所有的預設語言\<字串 > 命令表中的項目。  如果未指定的語言，將使用目前的處理序的語言：<br /><br /> 語言 ="en-我們"|  
  
### <a name="child-elements"></a>子項目  
  
|項目|描述|  
|-------------|-----------------|  
|[Extern 元素](../extensibility/extern-element.md)|選擇性。 包含編譯器前置處理器指示詞。|  
|[Include 元素](../extensibility/include-element.md)|選擇性。 包含要包含在編譯中的任何檔案的路徑。|  
|[Define 元素](../extensibility/define-element.md)|選擇性。 定義指定的名稱和值的符號。|  
|[Commands 元素](../extensibility/commands-element.md)|選擇性。 Vspackage，其中包含所有其他項目定義的所有命令的父項目。|  
|[CommandPlacements 元素](../extensibility/commandplacements-element.md)|選擇性。 定義命令列上的命令的位置放置。|  
|[VisibilityConstraints 元素](../extensibility/visibilityconstraints-element.md)|選擇性。 決定命令和工具列的靜態可見性。|  
|[KeyBindings 元素](../extensibility/keybindings-element.md)|選擇性。 快速鍵組合，如果指定任何命令。|  
|[UsedCommands 元素](../extensibility/usedcommands-element.md)|選擇性。 可讓 VSPackage 也可以選擇性地實作自己的版本原本支援其他 Vspackage 的功能。|  
|[Symbols 元素](http://msdn.microsoft.com/en-us/f2ddd0aa-c3dd-439e-834d-28f136a27ffa)|選擇性。 包含的所有符號資料-Guid、 識別碼和其他等等-編譯器。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|無||  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 命令表檔案 (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)