---
title: 命令列擷取工具 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: db75b3a7-80b2-4a74-91d2-fd6e0f73b45d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4e083a0db3fbe85b793f9190b35112fd0aeb6a4b
ms.sourcegitcommit: 80f9daba96ff76ad7e228eb8716df3abfd115bc3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2018
ms.locfileid: "37433505"
---
# <a name="command-line-capture-tool"></a>命令列擷取工具
DXCap.exe 是圖形診斷擷取及播放的命令列工具。 它支援 Direct3D 10 到 Direct3D 12 的所有功能層級。  
  
## <a name="syntax"></a>語法  
  
```cmd  
DXCap.exe [-file filename] [-frame frames | -period periods | -manual] -c app [args...]  
DXCap.exe -p [filename] [-debug | -warp | -hw] [-config] [-rawmode]  
DXCap.exe -p [filename] -screenshot [-frame frames]  
DXCap.exe -p [filename] -toXML [xml_filename]  
DXCap.exe -v [-file filename] [-examine events] [-haltonfail | -exitonfail] [-showprogress]  
DXCap.exe -e [search_string]  
DXCap.exe -info  
```  
  
#### <a name="parameters"></a>參數  
 `-file` `filename`  
 在擷取模式下 (`-c`)，`filename`指定圖形資訊記錄到圖形記錄檔的名稱。 如果`filename`未指定，圖形資訊會記錄到名為`<appname>-<date>-<time>.vsglog`預設。  
  
 在驗證 (-v) 模式中，`filename` 指定要驗證的圖形記錄檔名稱。 如果`filename`未指定，會再次使用上次驗證的圖形記錄檔。  
  
 `-frame` `frames`  
 在擷取模式下，`frames` 指定您想要擷取的框架。 第一個框架為 1。 您可以使用逗號和範圍，以指定數個畫面格。 例如，如果`frames`是`2, 5, 7-9, 15`，然後框架`2`， `5`， `7`， `8`， `9`，和`15`所擷取。  

> [!TIP]
> 使用`-frame``manual`指定框架將會以手動方式擷取按 Print Screen 鍵。 應用程式啟動時，就可以擷取框架；若要停止擷取框架，請返回到命令列介面並按下 Enter 鍵。  
  
 `-period` `periods`  
 在擷取模式下，`periods` 指定您要擷取框架的時間範圍，以秒為單位。 您可以使用逗號和範圍，以指定數個週期。 比方說如果`periods`是`2.1-5, 7.0-9.3`，然後之間呈現的畫面格`2.1`並`5`（秒)，之間及`7`和`9.3`擷取秒數。  
  
 `-c` `app` [`args...`]  
 擷取模式。 在擷取模式下，`app` 指定您想要從其中擷取圖形資訊的應用程式名稱；`args...` 指定該應用程式的其他命令列參數。  
  
 `-p` [`filename`]  
 播放模式 (`-p`)。 在播放模式中，`filename` 指定要播放的圖形記錄檔名稱。 如果`filename`未指定，會再次使用前次播放的圖形記錄檔。  
  
 `-debug`  
 在播放模式中，`-debug`指定應該啟用 Direct3D 偵錯層級與播放播放。  
  
 `-warp`  
 在播放模式中，`-warp`指定應該使用 WARP 軟體呈現器播放播放。  
  
 `-hw`  
 在播放模式中，`-hw`指定應該使用 GPU 硬體播放播放。  
  
 `-config`  
 在播放模式中，`-config`顯示用來擷取圖形記錄檔的電腦相關的任何資訊。  
  
 `-rawmode`  
 在播放模式中，`-rawmode`指定播放執行時應該不需要修改記錄的事件。 在正常操作下，播放模式可能會對播放進行次要變更，以簡化偵錯，並加快播放的速度。 例如，它可能會模擬交換鏈結輸出，而不是執行交換鏈結命令。 通常此播放不成問題，但您可能需要讓播放時更忠實呈現記錄的事件的方式發生。 例如，您可以使用此選項還原應用程式在全螢幕模式中執行時所擷取的全螢幕呈現行為。  
  
 `-toXML` [`xml_filename`]  
 在播放模式中，`xml_filename` 指定 XML 代表寫入的播放檔案名稱。 如果 `xml_filename` 未指定，XML 代表將會寫入一個名稱與播放中檔案相同的檔案，但其具有 `.xml` 副檔名。  
  
 `-v`  
 驗證模式。 在驗證模式下，所擷取的框架會在硬體和 WARP 上播放，並會使用影像比較函式來比較它們的結果。 您可以使用這項功能，來快速找出影響您呈現的驅動程式問題。  
  
 `-examine` `events`  
 在驗證模式下，`events` 指定會比較其立即結果的圖形事件集。 比方說，`-examine present,draw,copy,clear`限制只有屬於那些類別的事件比較。  
  
> [!TIP]
>  我們建議您從`-examine present,draw,copy,clear`因為這會顯示大部分的問題，但需要更少的時間比更廣泛的事件集。 如有必要，您可以指定較大或不同的事件集來驗證這些事件，並且顯示其他種類的問題。  
  
 `-haltonfail`  
 在驗證模式下`-haltonfail`硬體和 WARP 轉譯器之間偵測到差異時，中止驗證。 按下按鍵之後，會繼續執行驗證。  
  
 `-exitonfail`  
 在驗證模式下`-exitonfail`當硬體和 WARP 轉譯器之間偵測到差異時，立即結束驗證。 當程式結束，如此一來時，它會傳回`0`給環境; 否則會傳回`1`。  
  
 `-showprogress`  
 在驗證模式下`-showprogress`會顯示驗證工作階段的進度資訊。 WARP 進度顯示在左邊，而硬體進度顯示在右邊。  
  
 `-e` `search_string`  
 列舉已安裝的 UWP 應用程式。 您可以使用這項資訊來執行與 UWP 應用程式的命令列擷取。  
  
 `-info`  
 顯示電腦的相關資訊，並擷取 DLL。  
  
## <a name="remarks"></a>備註  
 DXCap.exe 有三種操作模式：  
  
 擷取模式 (-c)  
 擷取正在執行的應用程式中的圖形資訊，並將它記錄到圖形記錄檔。 擷取功能及檔案格式與 Visual Studio 的完全相同。  
  
 播放模式 (-p)  
 播放先前擷取的圖形事件，從現有的圖形記錄檔。 根據預設會以視窗播放，即使圖形記錄檔是從全螢幕應用程式擷取也一樣。 播放就會發生在全螢幕中，只有當圖形記錄檔從全螢幕應用程式來擷取和`-rawmode`指定。  
  
 驗證模式 (`-v`)  
 藉由在硬體和 WARP 播放擷取的框架，然後使用影像比較功能比較它們的結果，來驗證轉譯行為。 您可以使用這項功能，來快速找出影響您呈現的驅動程式問題。  
  
 除了這些模式，dxcap.exe 還會執行其他兩個不會擷取或播放圖形資訊的功能。  
  
 列舉型別函式 (`-e`)  
 顯示安裝在電腦的 UWP 應用程式的相關詳細資料。 這些詳細資料包含套件名稱和識別在 UWP 應用程式可執行檔的 appid。 若要使用 DXCap.exe 擷取來自 Windows 市集應用程式的圖形資訊，請使用套件名稱和 appid，而不是擷取桌面應用程式時使用的可執行檔名稱。  
  
 資訊函數 (`-info)`  
 顯示電腦的詳細資料，並擷取 DLL。  
  
## <a name="examples"></a>範例  
  
### <a name="capture-graphics-information-from-a-desktop-app"></a>擷取桌面應用程式中的圖形資訊  
 使用`-c`來指定您要從中擷取圖形資訊的應用程式。  
  
```cmd  
DXCap.exe -c BasicHLSL11.exe  
```  
  
 根據預設，圖形資訊記錄到名為`<appname>-<date>-<time>.vsglog`。 使用`-file`來指定記錄到不同的檔案。  
  
```cmd  
DXCap.exe -file regression_test_12.vsglog -c BasicHLSL11.exe  
```  
  
 指定您正在從中擷取的應用程式的其他命令列參數，將它們包括在應用程式的檔名之後。  
  
```cmd  
DXCap.exe -c "C:\Program Files\Internet Explorer\iexplorer.exe" "www.fishgl.com"  
```  
  
 在上述範例中的命令會擷取桌面版本的 Internet Explorer 檢視網頁位於 www.fishgl.com 使用 WebGL API 來呈現 3d 內容時的圖形資訊。  
  
> [!NOTE]
>  因為應用程式之後，會出現的命令列引數會傳遞給它，您必須指定使用之前用於 DXCap.exe 的引數`-c`選項。  
  
### <a name="capture-graphics-information-from-a-uwp-app"></a>擷取圖形資訊從 UWP 應用程式。  
 您可以擷取從 UWP 應用程式的圖形資訊。  
  
```cmd  
DXCap.exe -c Microsof.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe,AppexMaps  
```  
  
 使用 DXCap.exe 來擷取從 UWP 應用程式，類似於使用它來擷取 Windows 桌面應用程式，但改為依檔名識別桌面應用程式，您識別 UWP 應用程式的套件名稱和名稱，或想要的可執行檔封裝您的內部識別碼 從擷取。 若要讓您更輕鬆地了解如何識別您的電腦安裝的 UWP 應用程式，使用`-e`選項搭配 DXCap.exe 來列舉它們：  
  
```cmd  
DXCap.exe -e  
```  
  
 您可以提供選擇性的搜尋字串，以協助找出您要尋找的應用程式。 提供搜尋字串時，DXCap.exe 會列舉其封裝名稱、 應用程式名稱或應用程式識別碼符合搜尋字串的 UWP 應用程式。 搜尋不區分大小寫。  
  
```cmd  
DXCap.exe -e map  
```  
  
 上述命令會列舉符合"map"的 UWP 應用程式輸出如下：  
  
 **封裝"Microsoft.BingMaps 」:**  
 **Installdirectory 出現： C:\Program Files\WindowsApps\Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe**  
 **FullName: Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe**  
 **UserSID: S-1-5-21-2127521184-1604012920-1887927527-5603533**  
 **名稱： Microsoft.BingMaps**  
 **發行者： CN = Microsoft Corporation，O = Microsoft Corporation，L = Redmond，S = Washington，C = US**  
 **版本： 2.1.2914.1734**  
 **可啟動的應用程式：**  
 **識別碼： AppexMaps**  
 **Exe: C:\Program Files\WindowsApps\Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe\Map.exe**  
 **IsWWA： 否**  
 * * AppSpec （以啟動）： **DXCap.exe-c Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe,AppexMaps*** 每個列舉的應用程式的輸出的最後一行會顯示您可用來從其擷取圖形資訊的命令。  
  
### <a name="capture-specific-frames-or-frames-between-specific-times"></a>擷取特定框架或特定時間之間的框架。  
 使用`-frame`來指定您想要使用逗號和範圍擷取的框架：  
  
```cmd  
DXCap.exe -frame 2,5,7-9,15 -c SimpleBezier11.exe  
```  
  
 或者，您也可以使用`-period`來指定一組要擷取的畫面格的時間範圍。 時間範圍以秒為指定單位，且您可以指定多個範圍：  
  
```cmd  
DXCap.exe -period 2.1-5, 7.0-9.3 -c SimpleBezier11.exe  
```  
  
### <a name="capture-frames-interactively"></a>以互動方式擷取框架。  
 使用`-manual`以互動方式擷取框架。 按下 Enter 鍵開始擷取，然後再按一次 Enter 鍵停止。  
  
```cmd  
DXCap.exe -manual -c SimpleBezier11.exe  
```  
  
### <a name="play-back-a-graphic-log-file"></a>播放圖形記錄檔  
 使用`-p`播放先前所擷取的圖形記錄檔。  
  
```cmd  
DXCap.exe -p regression_test_12.vsglog  
```  
  
 排除播放最近擷取的圖形記錄檔檔名。  
  
```cmd  
DXCap.exe -p  
```  
  
### <a name="play-back-in-raw-mode"></a>在原始模式中播放  
 使用`-rawmode`播放擷取的命令，完全依照其發生。 在正常播放下，某些命令是經過模擬的，例如，從全螢幕應用程式擷取的圖形記錄檔將在視窗中播放；啟用原始模式時，相同的檔案將會嘗試以全螢幕播放。  
  
```cmd  
DXCap.exe -p regression_test_12.vsglog -rawmode  
```  
  
### <a name="play-back-using-warp-or-a-hardware-device"></a>使用 WARP 或硬體裝置播放  
 您可能想要在硬體裝置上強制使用 WARP 播放擷取的圖形記錄檔，或是強制使用硬體裝置播放在 WARP 上擷取的記錄檔。 使用`-warp`以 WARP 進行播放。  
  
```cmd  
DXCap.exe -p regression_test_12.vsglog -warp  
```  
  
 使用`-hw`以硬體進行播放。  
  
```cmd  
DXCap.exe -p regression_test_12.vsglog -hw  
```  
  
### <a name="validate-a-graphics-log-file-against-warp"></a>針對 WARP 驗證圖形記錄檔  
 在驗證模式中，圖形記錄檔會在硬體和 WARP 上播放，並比較其結果。 這可以協助您識別驅動程式所造成的轉譯錯誤。 您可以使用 hyper-v 來驗證針對 WARP 的圖形硬體的正確行為。  
  
```cmd  
DXCap.exe -v regression_test_12.vsglog  
```  
  
 若要減少比較次數，您可以指定驗證要比較的命令子集，將會忽略其他命令。 使用-examine 指定您想要比較其結果的命令。  
  
```cmd  
DXCap.exe -v regression_test_12.vsglog -examine present,draw,copy,clear  
```  
  
### <a name="convert-a-graphics-log-file-to-pngs"></a>將圖形記錄檔轉換成 PNG  
 若要檢視或分析圖形記錄檔中的框架，DXCap.exe 可以將擷取的框架儲存為 .png (可攜式網路圖形) 影像檔。 使用`-screenshot`來擷取 在播放模式中輸出的 為.png 檔案的框架。  
  
```cmd  
DXCap.exe -p BasicHLSL11.vsglog -screenshot  
```  
  
 使用`-frame`與`-screenshot`來指定您想要輸出的框架。  
  
```cmd  
DXCap.exe -p BasicHLSL11.vsglog -screenshot -frame 5, 7-9  
```  
  
### <a name="convert-a-graphics-log-file-to-xml"></a>將圖形記錄檔轉換成 XML  
 若要使用熟悉的工具，如 FindStr 或 XSLT 處理及分析圖形記錄檔，DXCap.exe 可以將圖形記錄檔轉換成 XML。 使用`-toXML`在播放模式中將記錄檔轉換成 XML，而非播放它回復。  
  
```cmd  
DXCap.exe -p regression_test_12.vsglog -toXML  
```  
  
 根據預設，XML 輸出會寫入至與圖形記錄檔同名的檔案，但它具有 .xml 副檔名。 在上述範例中，將會命名為 XML 檔案**regression_test_12.xml**。 若要為 XML 檔案指定不同的名稱，指定它之後`-toXML`。  
  
```cmd  
DXCap.exe -p regression_test_12.vsglog -toXML temp.xml  
```  
  
 產生的檔案會包含類似如下的 XML：  
  
```xml  
<Moment value="67"/>  
<Method name="CreateDXGIFactory1" >  
    <Return type="HRESULT" value="S_OK" />  
    <Parameter name="riid" type="IID" value="770AAE78-F26F-4DBA-A829-253C83D1B387" />  
    <Parameter name="ppFactory" type="void" handle="1" isOutput="true" />  
</Method>  
  
<Moment value="167"/>  
<Method name="D3D11CreateDevice" >  
    <Return type="HRESULT" value="S_OK" />  
    <Parameter name="pAdapter" type="IDXGIAdapter" handle="34" />  
    <Parameter name="DriverType" type="D3D_DRIVER_TYPE" value="D3D_DRIVER_TYPE_UNKNOWN" />  
    <Parameter name="Software" type="HMODULE" value="pointer" />  
    <Parameter name="Flags" type="UINT" value="0" />  
    <Parameter name="pFeatureLevels" type="D3D_FEATURE_LEVEL" arrSize="1" >  
        <Element value="D3D_FEATURE_LEVEL_11_0" />  
    </Parameter>  
    <Parameter name="FeatureLevels" type="UINT" value="1" />  
    <Parameter name="SDKVersion" type="UINT" value="7" />  
    <Parameter name="ppDevice" type="ID3D11Device" handle="35" isOutput="true" />  
    <Parameter name="pFeatureLevel" type="D3D_FEATURE_LEVEL" value="D3D_FEATURE_LEVEL_11_0" isOutput="true" />  
    <Parameter name="ppImmediateContext" type="ID3D11DeviceContext" value="nullptr" isOutput="true" />  
</Method>  
```  
  
## <a name="requirements"></a>需求