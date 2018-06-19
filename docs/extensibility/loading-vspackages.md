---
title: 載入 Vspackage |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, loading
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 008cd31bc3d9f909477089e608393f596bfb0682
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31140010"
---
# <a name="loading-vspackages"></a>載入 Vspackage
只有需要其功能時，只有 Vspackage 會載入 Visual Studio。 例如，VSPackage 會在 Visual Studio 會使用專案工廠或 VSPackage 實作的服務時載入。 這項功能稱為延遲的載入，會盡可能使用來改善效能。  
  
> [!NOTE]
>  Visual Studio 可以判斷特定的 VSPackage 資訊，例如 VSPackage 提供的服務，而不必載入 VSPackage 的命令。  
  
 Vspackage 可以例如設定要自動載入在特定的使用者介面 (UI) 內容中，開啟方案時。 <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>屬性會設定此內容。  
  
### <a name="autoloading-a-vspackage-in-a-specific-context"></a>自動載入特定的內容中 VSPackage  
  
-   新增`ProvideAutoLoad`屬性加入 VSPackage 屬性：  
  
    ```csharp  
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID  
    public class MyAutoloadedPackage : Package  
    {. . .}  
    ```  
  
     請參閱列舉的欄位<xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>UI 內容，以及其 GUID 值的清單。  
  
-   在設定的中斷點<xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>方法。  
  
-   建置 VSPackage 並開始偵錯。  
  
-   載入方案，或建立一個。  
  
     載入 VSPackage，並在中斷點停止。  
  
## <a name="forcing-a-vspackage-to-load"></a>強制載入 VSPackage  
 在某些情況下 VSPackage 可能要強制另一個要載入的 VSPackage。 例如，輕量型 VSPackage 可能會載入較大的 VSPackage 不是 CMDUIContext 可用的內容中。  
  
 您可以使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A>方法，以強制載入 VSPackage。  
  
-   插入到這個程式碼<xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>可強制另一個 VSPackage，載入 VSPackage 的方法：  
  
    ```csharp  
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;  
    if (shell == null) return;  
  
    IVsPackage package = null;  
    Guid PackageToBeLoadedGuid =   
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);  
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);  
  
    ```  
  
     當初始化 VSPackage 時，它會強制`PackageToBeLoaded`載入。  
  
     強制載入不應該用於 VSPackage 通訊。 使用[使用並提供服務](../extensibility/using-and-providing-services.md)改為。
  
## <a name="see-also"></a>另請參閱  
 [VSPackage](../extensibility/internals/vspackages.md)
