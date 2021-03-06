---
title: 元件管理 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], components
- installation [Visual Studio SDK], file management
ms.assetid: 029bffa2-6841-4caa-a41a-442467e1aedc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 00a6ea41d631c171700db75361b7aa0beed81cc2
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2018
ms.locfileid: "39510864"
---
# <a name="component-management"></a>元件管理
Windows 安裝程式中的工作單位被指 Windows 安裝程式元件 （有時稱為 WICs 或只是元件）。 GUID 會識別每個 WIC，也就是安裝和參考計數來使用 Windows 安裝程式的安裝程式的基本單位。  
  
 雖然您可以使用數個產品建立 VSPackage 的安裝程式，在本文中會假設為使用 Windows 安裝程式 (*.msi*) 檔案。 在建立您的安裝程式時，您必須在這樣隨時都正確的參考計數才會正確地管理檔案部署。 因此，不同版本的產品不會干擾或彼此無法在混合的安裝和解除安裝案例。  
  
 在 Windows 安裝程式中，參考計數，就會發生在元件層級。 您必須仔細組織您的資源 — 檔案、 登錄項目，等等 — 元件。 有組織的其他層級 — 例如模組、 功能和產品，可協助在不同案例中。 如需詳細資訊，請參閱 < [Windows Installer 基本概念](../../extensibility/internals/windows-installer-basics.md)。  
  
## <a name="guidelines-of-authoring-setup-for-side-by-side-installation"></a>撰寫並排顯示安裝的安裝程式的指導方針  
  
-   作者的檔案及登錄機碼在版本間共用到他們自己的元件。  
  
     如此一來，可讓您輕鬆使用它們的未來版本。 比方說，已全域註冊的型別程式庫的副檔名，其他項目中註冊**HKEY_CLASSES_ROOT**，依此類推。  
  
-   共用的元件群組成個別的合併模組。  
  
     這項策略可協助您撰寫向前移動的並排顯示安裝正確的。  
  
-   跨版本使用相同的 Windows Installer 元件安裝共用的檔案和登錄機碼。  
  
     如果您使用不同的元件時，檔案和登錄項目會解除安裝時解除安裝一個版本的 VSPackage，但仍然安裝另一個 VSPackage。  
  
-   請勿混用相同的元件版本設定和共用項目。  
  
     如此一來，因此無法安裝共用的項目全域位置和建立版本的項目，以隔離的位置。  
  
-   不需要指向已建立版本的檔案共用的登錄機碼。  
  
     如果您這樣做，共用的金鑰覆寫已安裝另一個版本的 VSPackage。 移除第二個版本之後，索引鍵指向檔案變不見了。  
  
## <a name="see-also"></a>另請參閱  
 [共用和建立版本的 Vspackage 之間進行選擇](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [VSPackage 安裝案例](../../extensibility/internals/vspackage-setup-scenarios.md)