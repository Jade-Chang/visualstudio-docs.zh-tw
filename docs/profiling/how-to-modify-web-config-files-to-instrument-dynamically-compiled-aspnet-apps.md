---
title: 如何：修改 Web.Config 檔案以檢測並分析動態編譯的 ASP.NET Web 應用程式 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: a92e5692-2183-4ae3-9431-b067c6a7aab4
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: ceee8ee3781a367f351f20ca92b83f4db000b42b
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/07/2018
ms.locfileid: "34844761"
---
# <a name="how-to-modify-webconfig-files-to-instrument-and-profile-dynamically-compiled-aspnet-web-applications"></a>如何：修改 Web.Config 檔案以檢測並分析動態編譯的 ASP.NET Web 應用程式
您可以使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 程式碼剖析工具檢測方法從動態編譯的 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 應用程式收集詳細執行時間資料、.NET 記憶體配置資料，以及 .NET 物件存留期資料。  
  
 本主題描述如何修改 *web.config* 組態檔，以啟用 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 應用程式的檢測和分析。  
  
> [!NOTE]
>  當您使用取樣分析方法，或是想要檢測先行編譯的 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 模組時，不需要修改 *web.config* 檔案。  
  
 *web.config* 檔案的根是 **configuration** 項目。 若要檢測動態編譯的 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 應用程式並對其進行分析，您必須新增或修改下列項目：  
  
-   **configuration/runtime/assemblyBinding/dependentAssembly** 項目，識別控制程式碼剖析的 Microsoft.VisualStudio.Enterprise.ASPNetHelper 組件。 **dependentAssembly** 項目包含兩個子項目：**assemblyIdentity** 和 **codeBase**。  
  
-   **configuration/system.web/compilation** 項目，識別目標組件的分析工具後續處理編譯步驟。  
  
-   兩個 **add** 項目，識別加入至 **configuration/appSettings** 區段之程式碼剖析工具的位置。  
  
 建議您建立原始的 *web.config* 檔案複本，以便用來還原應用程式的組態。  
  
### <a name="to-add-the-aspnethelper-assembly-as-a-configurationruntimeassemblybindingdependentassembly-element"></a>加入 ASPNetHelper 組件做為 configuration/runtime/assemblyBinding/dependentAssembly 項目  
  
1.  如有需要，加入 **runtime** 項目做為 **configuration** 項目的子項目，否則移至下一個步驟。  
  
     **runtime** 項目沒有任何屬性。 **configuration** 項目只能有一個 **runtime** 子項目。  
  
2.  如有需要，加入 **assemblyBinding** 項目做為 **runtime** 項目的子項目，否則移至下一個步驟。  
  
     **runtime** 項目只能有一個 **assemblyBinding** 項目。  
  
3.  將下列屬性名稱和值加入至 **assemblyBinding** 項目：  
  
    |屬性名稱|屬性值|  
    |--------------------|---------------------|  
    |**Xmlns**|**urn:schemas-microsoft-com:asm.v1**|  
  
4.  加入 **dependentAssembly** 項目做為 **assemblyBinding** 項目的子項目。  
  
     **dependentAssembly** 項目沒有任何屬性。  
  
5.  加入 **assemblyIdentity** 項目做為 **dependentAssembly** 項目的子系。  
  
6.  將下列屬性名稱和值加入至 **assemblyIdentity** 項目：  
  
    |屬性名稱|屬性值|  
    |--------------------|---------------------|  
    |**name**|**Microsoft.VisualStudio.Enterprise.ASPNetHelper**|  
    |**PublicKeyToken**|**b03f5f7f11d50a3a**|  
    |**culture**|**Neutral**|  
  
7.  加入 **codeBase** 項目做為 **dependentAssembly** 項目的子系。  
  
8.  將下列屬性名稱和值加入至 **codeBase** 項目：  
  
    |屬性名稱|屬性值|  
    |--------------------|---------------------|  
    |**version**|**10.0.0.0**|  
    |**href**|`PathToASPNetHelperDll`|  
  
     `PathToASPNetHelperDll` 是 Microsoft.VisualStudio.Enterprise.ASPNetHelper.dll 的檔案 URL。 如果 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 安裝在預設位置中，**href** 值應該是 `C:/Program%20Files/Microsoft%20Visual%20Studio%202010.0/Common7/IDE/PrivateAssemblies/Microsoft.VisualStudio.Enterprise.ASPNetHelper.DLL`  
  
```xml  
    <configuration>  
        <runtime>  
            <assemblyBinding   
                xmlns="urn:schemas-microsoft-com:asm.v1"  
            >  
                <dependentAssembly>  
                    <assemblyIdentity name="Microsoft.VisualStudio.Enterprise.ASPNetHelper"   
                        publicKeyToken="b03f5f7f11d50a3a"
                        culture="neutral"   
                    />  
                    <codeBase   
                        version="10.0.0.0"  
                        href="file:///C:/Program%20Files/Microsoft%20Visual%20Studio%2010.0/Common7/IDE/PrivateAssemblies/Microsoft.VisualStudio.Enterprise.ASPNetHelper.DLL"   
                    />  
                </dependentAssembly>  
            </assemblyBinding>  
        </runtime>  
```  
  
### <a name="to-add-the-profiler-post-process-step-to-the-configurationsystemwebcompilation-element"></a>將分析工具的後續處理步驟加入至 configuration/system.web/compilation 元素  
  
1.  如有需要，加入 **system.web** 項目做為 **configuration** 項目的子項目，否則移至下一個步驟。  
  
     **system.web** 項目沒有任何屬性。 **configuration** 項目只能有一個 **system.web** 子項目。  
  
2.  如有需要，加入 **compilation** 項目做為 **system.web** 項目的子項目，否則移至下一個步驟。  
  
     **system.web** 項目只能有一個 **compilation** 子項目。  
  
3.  從 **compilation** 項目移除任何現有的屬性，並且加入下列屬性名稱和值：  
  
    |屬性名稱|屬性值|  
    |--------------------|---------------------|  
    |**assemblyPostProcessorType**|**Microsoft.VisualStudio.Enterprise.Common.AspPerformanceInstrumenter, Microsoft.VisualStudio.Enterprise.ASPNetHelper, Version=10.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a**|  
  
```xml  
    <configuration>  
        <runtime>  
        . . .  
        </runtime>  
        <system.web>  
            <compilation  
                assemblyPostProcessorType="Microsoft.VisualStudio.Enterprise.Common.AspPerformanceInstrumenter,  
                    Microsoft.VisualStudio.Enterprise.ASPNetHelper,  
                    Version=10.0.0.0,  
                    Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"   
            />  
        </system.web>  
    <configuration>  
```  
  
### <a name="to-add-profiler-location-settings-to-the-configurationappsettings-element"></a>將分析工具位置設定加入至 configuration/appSettings 元素  
  
1.  如有需要，加入 **appSettings** 項目做為 **configuration** 項目的子項目，否則移至下一個步驟。  
  
     **appSettings** 項目沒有任何屬性。 **configuration** 項目只能有一個 **appSettings** 子項目。  
  
2.  加入 **add** 項目做為 **appSettings** 項目的子系。  
  
3.  將下列屬性名稱和值加入至 **add** 項目：  
  
    |屬性名稱|屬性值|  
    |--------------------|---------------------|  
    |**key**|**Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrLocation**|  
    |**value**|`PerformanceToolsFolder` **\VSInstr.Exe**|  
  
4.  加入另一個 **add** 項目做為 **appSettings** 項目的子系。  
  
5.  將下列屬性名稱和值加入此 **add** 項目：  
  
    |屬性名稱|屬性值|  
    |--------------------|---------------------|  
    |**key**|**Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrTools**|  
    |**value**|`PerformanceToolsFolder`|  
  
     `PerformanceToolsFolder` 是程式碼剖析工具可執行檔的路徑。 如果 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 是安裝到預設位置，則此值將是 **C:\Program Files\Microsoft Visual Studio 10.0\Team Tools\Performance Tools**  
  
```xml  
    <configuration>  
        <runtime>  
        . . .  
        </runtime>  
        . . .  
        <system.web>  
        </system.web>  
        <appSettings>  
            <add  
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrLocation"  
                value="C:\Program Files\Microsoft Visual Studio 10.0\Team Tools\Performance Tools\vsinstr.exe"  
        />  
            <add  
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrTools"  
                value="C:\Program Files\Microsoft Visual Studio 10.0\Team Tools\Performance Tools\"  
            />  
        </appSettings>  
    </configuration>  
```  
  
## <a name="example"></a>範例  
 以下為完整的 *web.config* 檔案，會啟用動態編譯之 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 應用程式的檢測和分析。 本範例假設修改前檔案中沒有其他設定。  
  
```xml  
<?xml version="1.0"?>  
    <configuration>  
        <runtime>  
            <assemblyBinding   
                xmlns="urn:schemas-microsoft-com:asm.v1"  
            >  
                <dependentAssembly>  
                    <assemblyIdentity   
                        name="Microsoft.VisualStudio.Enterprise.ASPNetHelper"   
                        publicKeyToken="b03f5f7f11d50a3a"  
                        culture="neutral"   
                    />  
                    <codeBase   
                        version="10.0.0.0"  
                        href="file:///C:/Program%20Files/Microsoft%20Visual%20Studio%2010.0/Common7/IDE/PrivateAssemblies/Microsoft.VisualStudio.Enterprise.ASPNetHelper.DLL"   
                    />  
                </dependentAssembly>  
            </assemblyBinding>  
        </runtime>  
        <system.web>  
            <compilation  
                assemblyPostProcessorType="Microsoft.VisualStudio.Enterprise.Common.AspPerformanceInstrumenter,  
                    Microsoft.VisualStudio.Enterprise.ASPNetHelper,  
                    Version=10.0.0.0,  
                    Culture=neutral,  
                    PublicKeyToken=b03f5f7f11d50a3a"   
            />  
        </system.web>  
        <appSettings>  
            <add  
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrLocation"  
                value="C:\Program Files\Microsoft Visual Studio 10.0\Team Tools\Performance Tools\vsinstr.exe"  
            />  
            <add  
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrTools"  
                value="C:\Program Files\Microsoft Visual Studio 10.0\Team Tools\Performance Tools\"  
            />  
        </appSettings>  
    </configuration>  
  
```  
  
## <a name="see-also"></a>另請參閱  
 [如何：檢測動態編譯的 ASP.NET 應用程式並收集詳細計時資料](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-app-and-collect-timing-data.md)   
 [如何：檢測動態編譯的 ASP.NET 應用程式並收集記憶體資料](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data.md)