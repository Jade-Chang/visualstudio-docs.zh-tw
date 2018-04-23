---
title: 如何： 使用登錄設定來管理私人組件庫 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSIX private galleries, managing
- managing VSIX private galleries
ms.assetid: 86b86442-4293-4cad-9fe2-876eef65f426
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c9631ffa4bce25752b838a78f306ddd3c2313a20
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-manage-a-private-gallery-by-using-registry-settings"></a>如何： 使用登錄設定來管理私人組件庫
如果您是系統管理員或開發人員的 Isolated Shell 擴充功能，您可以控制存取控制項、 範本和 Visual Studio 組件庫、 範例庫或私用組件庫中的工具。 若要讓組件庫可用或無法使用，建立描述的已修改的登錄機碼和其值的.pkgdef 檔。  
  
## <a name="managing-private-galleries"></a>管理私用組件庫  
 您可以建立.pkgdef 檔來控制多部電腦上的組件庫的存取。 這個檔案必須具有下列格式。  
  
```  
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)  
Protocol=Atom Feed|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 `Repositories`索引鍵參考到資源庫來啟用或停用。 Visual Studio 組件庫和範例庫使用下列的儲存機制的 Guid:  
  
-   Visual Studio 組件庫： 0F45E408-7995-4375-9485-86B8DB553DC9  
  
-   範例庫： AEB9CB40-D8E6-4615-B52C-27E307F8506C  
  
 `Disabled`是選擇性的值。 根據預設，會啟用組件庫。  
  
 `Priority`值決定組件庫列於 [選項] 對話方塊中的順序。 在 visual Studio Gallery 優先順序 10 和範例庫優先順序 20。 私用組件庫啟動 100 的優先權。 如果數個組件庫中有相同的優先順序值，以它們出現的順序由其當地語系化值`DisplayName`屬性。  
  
 `Protocol`是 Atom 或 SharePoint 架構的組件庫必要的值。  
  
 可能是`DisplayName`，或兩者都`DisplayNameResourceID`和`DisplayNamePackageGuid`，必須指定。 如果指定 all，則`DisplayNameResourceID`和`DisplayNamePackageGuid`組用。  
  
## <a name="disabling-the-visual-studio-gallery-using-a-pkgdef-file"></a>停用 Visual Studio Gallery 使用.pkgdef 檔  
 您可以停用.pkgdef 檔中的組件庫。 下列項目會停用 Visual Studio 組件庫：  
  
```  
[$RootKey$\ExtensionManager\Repositories\{0F45E408-7995-4375-9485-86B8DB553DC9}]  
"Disabled"=dword:00000001  
  
```  
  
 下列項目會停用範例庫：  
  
```  
[$RootKey$\ExtensionManager\Repositories\{AEB9CB40-D8E6-4615-B52C-27E307F8506C}]  
"Disabled"=dword:00000001  
  
```  
  
## <a name="see-also"></a>另請參閱  
 [私用組件庫](../extensibility/private-galleries.md)