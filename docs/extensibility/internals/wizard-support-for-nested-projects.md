---
title: 巢狀專案的精靈支援 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 14e8a32db2542ae1729a7fdc87cc2ab32845f8ca
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="wizard-support-for-nested-projects"></a>巢狀專案的精靈支援
IDE 執行兩個精靈，可實作用於巢狀專案父專案：**新專案**精靈和**加入項目**精靈。  
  
 如果使用者啟動**新專案**精靈選取**加入專案**按一下**新專案**檔案 功能表上，或選取**新增**並以滑鼠右鍵按一下**新專案**在方案總管 中，IDE 會執行**AddProject**命令與父專案實作**AddProject**命令可能會傳回範本專案檔中或具有一組內容參數的精靈 (.vsz) 檔案。  
  
 同樣地，父專案的實作**AddItem**精靈傳回.vsz 檔案具有一組不同的內容參數。  
  
 如需有關精靈的詳細資訊，請參閱[精靈 (。Vsz) 檔案](../../extensibility/internals/wizard-dot-vsz-file.md)，[內容參數](../../extensibility/internals/context-parameters.md)和[註冊專案和項目範本](../../extensibility/internals/registering-project-and-item-templates.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>   
 [巢狀專案](../../extensibility/internals/nesting-projects.md)