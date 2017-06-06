---
title: "C++ 偵錯組態的專案設定 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCDebugSettings.WebBrowser.DebuggerType"
  - "VC.Project.IVCGPUDebugPageObject.EnvironmentMerge"
  - "VC.Project.VCDebugSettings.SymbolPath"
  - "VC.Project.IVCClusterDebugPageObject.ApplicationCommand"
  - "VC.Project.IVCRemoteDebugPageObject.WorkingDirectory"
  - "VC.Project.VCDebugSettings.DebuggerType"
  - "VC.Project.IVCLocalDebugPageObject.GPUDebuggerTargetType"
  - "VC.Project.IVCRemoteDebugPageObject.SQLDebugging"
  - "VC.Project.IVCRemoteDebugPageObject.Remote"
  - "VC.Project.IVCGPUDebugPageObject.CommandArguments"
  - "VC.Project.VCDebugSettings.CommandArguments"
  - "VC.Project.IVCClusterDebugPageObject.MPIRunWorkingDirectory"
  - "VC.Project.IVCLocalDebugPageObject.SQLDebugging"
  - "VC.Project.IVCWebSvcDebugPageObject.HttpUrl"
  - "VC.Project.IVCLocalDebugPageObject.WorkingDirectory"
  - "VC.Project.IVCLocalDebugPageObject.CommandArguments"
  - "VC.Project.IVCClusterDebugPageObject.MPIRunCommand"
  - "VC.Project.IVCGPUDebugPageObject.WorkingDirectory"
  - "VC.Project.IVCWebSvcDebugPageObject.DebuggerType"
  - "VC.Project.IVCRemoteDebugPageObject.CommandArguments"
  - "VC.Project.IVCRemoteDebugPageObject.DebuggerType"
  - "VC.Project.IVCLocalDebugPageObject.GPUBreakOnAllThreads"
  - "VC.Project.IVCRemoteDebugPageObject.RemoteMachine"
  - "VC.Project.IVCClusterDebugPageObject.MPIRunArguments"
  - "VC.Project.IVCClusterDebugPageObject.MPIAcceptFilter"
  - "VC.Project.IVCGPUDebugPageObject.RemoteConnection"
  - "VC.Project.VCDebugSettings.PDBPath"
  - "VC.Project.IVCRemoteDebugPageObject.DeploymentDirectory"
  - "VC.Project.VCDebugSettings.SQLDebugging"
  - "VC.Project.VCDebugSettings.RemoteCommand"
  - "VC.Project.IVCClusterDebugPageObject.ShimCommand"
  - "VC.Project.IVCLocalDebugPageObject.Command"
  - "VC.Project.IVCRemoteDebugPageObject.GPUBreakOnAllThreads"
  - "VC.Project.IVCLocalDebugPageObject.Attach"
  - "VC.Project.VCDebugSettings.Command"
  - "VC.Project.IVCRemoteDebugPageObject.GPUDebuggerTargetType"
  - "VC.Project.IVCRemoteDebugPageObject.RemoteCommand"
  - "VC.Project.IVCClusterDebugPageObject.ApplicationArguments"
  - "VC.Project.IVCLocalDebugPageObject.Environment"
  - "VC.Project.IVCGPUDebugPageObject.DeploymentDirectory"
  - "VC.Project.IVCLocalDebugPageObject.EnvironmentMerge"
  - "VC.Project.VCDebugSettings.Environment"
  - "VC.Project.IVCGPUDebugPageObject.BreakpointBehavior"
  - "VC.Project.IVCLocalDebugPageObject.DebuggerType"
  - "VC.Project.VCDebugSettings.WebBrowser.WebBrowserDebuggerHttpUrl"
  - "VC.Project.IVCWebSvcDebugPageObject.SQLDebugging"
  - "VC.Project.IVCGPUDebugPageObject.AcceleratorType"
  - "VC.Project.IVCGPUDebugPageObject.Environment"
  - "VC.Project.VCDebugSettings.RemoteMachine"
  - "VC.Project.IVCGPUDebugPageObject.AdditionalFilesToDeploy"
  - "VC.Project.VCDebugSettings.WorkingDirectory"
  - "vs.debug.builds"
  - "VC.Project.VCDebugSettings.Attach"
  - "VC.Project.VCDebugSettings.HttpUrl"
  - "VC.Project.IVCClusterDebugPageObject.MPIAcceptMode"
  - "VC.Project.IVCGPUDebugPageObject.Attach"
  - "VC.Project.IVCRemoteDebugPageObject.AdditionalFiles"
  - "VC.Project.IVCGPUDebugPageObject.Command"
  - "VC.Project.VCDebugSettings.Remote"
  - "VC.Project.IVCRemoteDebugPageObject.Attach"
  - "VC.Project.VCDebugSettings.EnvironmentMerge"
  - "VC.Project.IVCGPUDebugPageObject.MachineName"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - ".pdb 檔案, 偵錯建置專案設定"
  - "/DEBUG 連結器選項"
  - "/MAP 連結器選項"
  - "/MAPINFO 連結器選項"
  - "/PDB 連結器選項"
  - "/PDBSTRIPPED 連結器選項"
  - "/Z7 編譯器選項 [C++]"
  - "/Zd 編譯器選項 [C++]"
  - "/ZI 編譯器選項 [C++]"
  - "偵錯組建, 專案設定"
  - "偵錯組態, C++"
  - "DEBUG 連結器選項"
  - "-DEBUG 連結器選項"
  - "偵錯 [C++], 偵錯工具設定"
  - "MAP 連結器選項"
  - "-MAP 連結器選項"
  - "對應檔, 專案設定"
  - "MAPINFO 連結器選項"
  - "-MAPINFO 連結器選項"
  - "pdb 檔案, 偵錯建置專案設定"
  - "PDB 連結器選項"
  - "-PDB 連結器選項"
  - "PDBSTRIPPED 連結器選項"
  - "-PDBSTRIPPED 連結器選項"
  - "專案組態, 偵錯"
  - "專案設定 [Visual Studio]"
  - "專案設定 [Visual Studio], 偵錯組態"
  - "專案 [Visual Studio], 偵錯組態"
  - "Z7 編譯器選項 [C++]"
  - "-Z7 編譯器選項 [C++]"
  - "Zd 編譯器選項 [C++]"
  - "-Zd 編譯器選項 [C++]"
  - "ZI 編譯器選項 [C++]"
  - "-Zl 編譯器選項 [C++]"
ms.assetid: 860c7f13-a108-4fe5-8fca-d235cd3ca1cb
caps.latest.revision: 49
caps.handback.revision: 49
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# C++ 偵錯組態的專案設定
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以在 \[**屬性頁**\] 對話方塊中變更 C 或 Visual C\+\+ 偵錯組態的專案設定，如 [如何：設定偵錯和發行組態](../debugger/how-to-set-debug-and-release-configurations.md)中所討論。  下表顯示 \[**屬性頁**\] 對話方塊中，與偵錯工具相關的設定位置。  
  
> [!WARNING]
>  **組態屬性\/偵錯**分類中針對以 C\+\+ 撰寫之 Windows 市集應用程式和元件的偵錯專案設定並不相同。  請參閱 Windows 開發人員中心的[啟動偵錯工作階段 \(VB、C\#、C\+\+ 和 XAML\)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)。  
  
 在 \[**要啟動的偵錯工具**\] 清單方塊中，指定要使用的偵錯工具。  您的選擇將影響屬性的可見性。  
  
 當您儲存方案時，每一項偵錯屬性設定都會針對您的方案自動寫入並儲存至「個別使用者」檔案 \(.vcxproj.user\) 中。  
  
### 組態屬性資料夾 \(偵錯分類\)  
  
|**設定**|**說明**|  
|------------|------------|  
|**要啟動的偵錯工具**|指定要執行的偵錯工具，並提供下列選項：<br /><br /> -   **本機 Windows 偵錯工具**<br />-   **遠端 Windows 偵錯工具**<br />-   **Web 瀏覽器偵錯工具**<br />-   **Web 服務偵錯工具**|  
|**命令** \(本機 Windows 偵錯工具\)|指定用來啟動將於本機電腦上進行偵錯之程式的命令。|  
|**遠端命令** \(遠端 Windows 偵錯工具\)|遠端電腦上 .exe 的路徑。  依照在遠端電腦上輸入路徑的方式輸入路徑。|  
|**命令引數** \(本機 Windows 偵錯工具和遠端 Windows 偵錯工具\)|-   指定先前指定之命令的引數。<br /><br /> 您可以在這個方塊中使用下列重新導向運算子：<br /><br /> \< `file`<br /> 從檔案讀取 stdin。<br /><br /> \> `file`<br /> 將 stdout 寫入檔案。<br /><br /> \>\> `file`<br /> 將 stdout 附加至檔案。<br /><br /> 2\> `file`<br /> 將 stderr 寫入檔案。<br /><br /> 2\>\> `file`<br /> 將 stderr 附加至檔案。<br /><br /> 2\> &1<br /> 將 stderr \(2\) 輸出傳送到與 stdout \(1\) 相同的位置。<br /><br /> 1\> &2<br /> 將 stdout \(1\) 輸出傳送到與 stderr \(2\) 相同的位置。<br /><br /> 在大多數情況下，這些運算子只適用於主控台應用程式。|  
|**工作目錄**|指定要進行偵錯之程式的工作目錄 \(相對於您的 EXE 所在的專案目錄\)。  如果您將這個項目保持空白，工作目錄就會是專案目錄。  若為遠端偵錯，專案目錄將會在遠端伺服器上。|  
|**附加** \(本機 Windows 偵錯工具和遠端 Windows 偵錯工具\)|指定是否要啟動或附加至應用程式。  預設設定為 \[否\]。|  
|**遠端伺服器名稱** \(遠端 Windows 偵錯工具\)|指定要用於應用程式偵錯的電腦名稱 \(並非您的電腦\)。<br /><br /> RemoteMachine 建置巨集會設定為這個屬性的值。如需詳細資訊，請參閱[建置命令和屬性的巨集](/visual-cpp/ide/common-macros-for-build-commands-and-properties)。|  
|**連接** \(遠端 Windows 偵錯工具\)|可讓您在標準和無驗證連線類型之間切換，以進行遠端偵錯。  在 \[**遠端伺服器名稱**\] 方塊中指定遠端電腦名稱。  連線類型如下：<br /><br /> -   **遠端使用 Windows 驗證**<br />-   **遠端未使用驗證 \(僅限原生\)**<br /><br /> **注意**：\[遠端未使用驗證\] 可能容易使遠端電腦因為安全性違規而受到損害。  Windows 驗證模式較為安全。<br /><br /> 如需詳細資訊，請參閱[遠端偵錯設定](../debugger/remote-debugging.md)。|  
|**HTTP URL** \(Web 服務偵錯工具和 Web 瀏覽器偵錯工具\)|指定要偵錯之專案所在的 URL。|  
|**偵錯工具類型**|指定要使用的偵錯工具類型：\[**僅限原生**\]、\[**僅限 Managed**\]、\[**僅限 GPU**\]、\[**混合**\]、\[**自動**\] \(預設值\) 或 \[**指令碼**\]。<br /><br /> -   \[**僅限原生**\] 適用於 Unmanaged C\+\+ 程式碼。<br />-   \[**僅限 Managed**\] 適用於 Common Language Runtime \(Managed 程式碼\) 下執行的程式碼。<br />-   \[**混合**\] 會針對 Managed 和 Unmanaged 程式碼叫用偵錯工具。<br />-   \[**自動**\] 會根據編譯器和 EXE 資訊判斷偵錯工具類型。<br />-   \[**指令碼**\] 會針對指令碼叫用偵錯工具。<br />-   \[**僅限 GPU**\] 適用於 GPU 裝置或 DirectX 參考轉譯器上執行的 C\+\+ AMP 程式碼。  請參閱 [偵錯 GPU 程式碼](../debugger/debugging-gpu-code.md)。|  
|**環境** \(本機 Windows 偵錯工具\)|為您要進行偵錯的程式指定環境變數。  使用標準環境變數語法 \(例如，`PATH="%SystemRoot%\..."`\)。  依據 \[**合併環境**\] 設定而定，這些變數會覆寫系統環境或與系統環境合併。  在 \[設定\] 資料行中按一下，就會出現 \[編輯…\]。  按一下該連結，即可編輯環境變數。|  
|**合併環境** \(本機 Windows 偵錯工具\)|判斷 \[**環境**\] 方塊中指定的變數是否要與作業系統所定義的環境合併。  預設設定為 \[是\]。|  
|**SQL 偵錯** \(適用所有偵錯工具，但 MPI 叢集偵錯工具除外\)|從您的 [!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)] 應用程式啟用 SQL 程序的偵錯功能。  預設設定為 \[否\]。|  
|**偵錯加速器類型** \(僅適用於 GPU 偵錯\)|指定要用來進行偵錯的 GPU 裝置。  安裝相容 GPU 裝置的裝置驅動程式將會加入額外的選項。  預設設定為 \[GPU \- 軟體模擬器\]。|  
|**GPU 預設中斷點行為** \(僅適用於 GPU 偵錯\)|指定是否應針對 SIMD 變形的每個執行緒引發中斷點事件。  預設設定為僅針對每次變形引發中斷點事件一次。|  
|**AMP 的預設加速器** \(僅適用於 GPU 偵錯\)|指定對 GPU 程式碼進行偵錯時的預設 AMP 加速器。  如果問題是由硬體或驅動程式所造成，而不是您的程式碼所造成，請選擇 \[**WARP 軟體加速器**\] 進行調查。|  
|**部署目錄** \(遠端 Windows 偵錯工具\)|指定遠端電腦上的路徑，在啟動之前專案輸出會複製到這個路徑中。  路徑可以是遠端電腦上的網路共用，或是遠端電腦上資料夾的路徑。  預設設定為空白，表示專案輸出不會複製到網路共用。  若要啟用檔案部署，您還必須選取 \[組態管理員\] 對話方塊中的 \[**部署**\] 核取方塊。  如需詳細資訊，請參閱 [如何：建立和編輯組態](../ide/how-to-create-and-edit-configurations.md)。|  
|**其他要部署的檔案** \(遠端 Windows 偵錯工具\)|如果 \[部署目錄\] 屬性已設定，這會是要複製到部署目錄的其他檔案清單 \(以分號分隔\)。  預設設定為空白，表示不會將其他檔案複製到部署目錄。  若要啟用檔案部署，您還必須選取 \[組態管理員\] 對話方塊中的 \[**部署**\] 核取方塊。  如需詳細資訊，請參閱 [如何：建立和編輯組態](../ide/how-to-create-and-edit-configurations.md)。|  
|**部署 Visual C\+\+ 偵錯執行階段程式庫** \(遠端 Windows 偵錯工具\)|如果 \[部署目錄\] 屬性已設定，這會指定是否應將目前平台的 Visual C\+\+ 偵錯執行階段程式庫複製到網路共用。  預設設定為 \[是\]。|  
  
### C\/C\+\+ 資料夾 \(一般分類\)  
  
|設定|說明|  
|--------|--------|  
|**偵錯資訊格式** \([\/Z7、\/Zd、Zi、\/ZI](/visual-cpp/build/reference/z7-zi-zi-debug-information-format)\)|指定要為專案建立的偵錯資訊類型。<br /><br /> 預設選項 \(\/ZI\) 會以 \[編輯後繼續\] 相容格式建立程式資料庫 \(PDB\)。  如需詳細資訊，請參閱 [\/Z7、\/Zd、\/Zi、\/ZI \(偵錯資訊格式\)](/visual-cpp/build/reference/z7-zi-zi-debug-information-format)。|  
  
### C\/C\+\+ 資料夾 \(最佳化分類\)  
  
|設定|說明|  
|--------|--------|  
|**最佳化**|指定編譯器是否應該將它所產生的程式碼最佳化。  最佳化會變更執行的程式碼。  最佳化的程式碼將不再符合原始程式碼，  因此不容易進行偵錯。<br /><br /> 預設選項 \(\[**停用 \(\/0d**\]\) 會隱藏最佳化。  您可以在隱藏最佳化的情況下進行開發，然後在建立程式碼的生產環境版本時再將此功能開啟。|  
  
### 連結器資料夾 \(偵錯分類\)  
  
|設定|說明|  
|--------|--------|  
|**產生偵錯資訊** \([\/DEBUG](/visual-cpp/build/reference/debug-generate-debug-info)\)|通知連結器要包含偵錯資訊，資訊的格式是由 \/Z7、\/Zd、Zi 或 \/ZI 所指定。|  
|**產生程式資料庫檔** \([\/PDB:name](/visual-cpp/build/reference/pdb-use-program-database)\)|在這個方塊中指定 PDB 檔的名稱。  您必須選取 ZI 或 \/Zi 以指定 \[偵錯資訊格式\]。|  
|**移除專用符號** \([\/PDBSTRIPPED:filename](/visual-cpp/build/reference/pdbstripped-strip-private-symbols)\)|如果您不想要在 PDB 檔中包含專用符號，請在這個方塊中指定 PDB 檔的名稱。  當您以任何會產生 PDB 檔的編譯器或連結器選項建置程式映像時，這個選項就會建立第二個程式資料庫 \(PDB\) 檔 \(這些選項包括 \/DEBUG、\/Z7、\/Zd   或 \/Zi\)。  第二個 PDB 檔會省略您不想要出貨給客戶的符號。  如需詳細資訊，請參閱 [\/PDBSTRIPPED \(移除專用符號\)](/visual-cpp/build/reference/pdbstripped-strip-private-symbols)。|  
|**產生對應檔** \([\/MAP](/visual-cpp/build/reference/map-generate-mapfile)\)|通知連結器在連結期間產生對應檔。  預設設定為 \[否\]。  如需詳細資訊，請參閱 [\/MAP \(產生對應檔\)](/visual-cpp/build/reference/map-generate-mapfile)。|  
|**對應檔名稱** \([\/MAP:](/visual-cpp/build/reference/map-generate-mapfile)*name*\)|如果您選擇 \[產生對應檔\]，就可以在這個方塊中指定對應檔。  如需詳細資訊，請參閱 [\/MAP \(產生對應檔\)](/visual-cpp/build/reference/map-generate-mapfile)。|  
|**對應匯出** \([\/MAPINFO:EXPORTS](/visual-cpp/build/reference/mapinfo-include-information-in-mapfile)\)|在對應檔中包含匯出函式。  預設設定為 \[否\]。  如需詳細資訊，請參閱 [\/MAPINFO \(將資訊包括在對應檔中\)](/visual-cpp/build/reference/mapinfo-include-information-in-mapfile)。|  
|**可偵錯組件** \([\/ASSEMBLYDEBUG](/visual-cpp/build/reference/mapinfo-include-information-in-mapfile)\)|指定連結器 \/ASSEMBLYDEBUG 選項的設定。  可能的值如下：<br /><br /> -   **沒有發出可偵錯屬性**。<br />-   **正在進行執行階段追蹤並停用最佳化 \(\/ASSEMBLYDEBUG\)**。  這是預設設定。<br />-   **沒有執行階段追蹤並啟用最佳化 \(\/ASSEMBLYDEBUG:DISABLE\)**。<br />-   **\<從父代或專案預設值繼承\>**。<br />-   如需詳細資訊，請參閱 [\/ASSEMBLYDEBUG \(加入 DebuggableAttribute\)](/visual-cpp/build/reference/assemblydebug-add-debuggableattribute)。|  
  
 您可以使用 Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings 介面，以程式設計的方式在 \[組態屬性\] 資料夾 \(\[偵錯\] 分類\) 中變更這些設定。  如需詳細資訊，請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCDebugSettings>。  
  
## 請參閱  
 [偵錯機器碼](../debugger/debugging-native-code.md)   
 [偵錯設定和準備](../debugger/debugger-settings-and-preparation.md)   
 [建立和管理 Visual C\+\+ 專案](/visual-cpp/ide/creating-and-managing-visual-cpp-projects)   
 [\/ASSEMBLYDEBUG \(加入 DebuggableAttribute\)](/visual-cpp/build/reference/assemblydebug-add-debuggableattribute)   
 [建置命令和屬性的巨集](/visual-cpp/ide/common-macros-for-build-commands-and-properties)