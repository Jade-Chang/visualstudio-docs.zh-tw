---
title: 附加至執行程序中使用 Visual Studio 中偵錯工具 |Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 06/20/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.processes.attach
- vs.debug.process
- vs.debug.programs
- vs.debug.detaching
- vs.debug.processes
- vs.debug.error.attach
- vs.debug.remotemachine
dev_langs:
- CSharp
- FSharp
- C++
- VB
helpviewer_keywords:
- remote debugging, attaching to programs
- processes, attaching to running processes
- Attach to Process dialog box
- debugging [Visual Studio], attaching to processes
- debugger, processes
ms.assetid: 27900e58-090c-4211-a309-b3e1496d5824
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 260047497ddb9515505c13f0b861c8eee05d71b0
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/22/2018
ms.locfileid: "36327329"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>使用 Visual Studio Debugger 附加至執行中處理序
您可以將 Visual Studio 偵錯工具附加至本機或遠端電腦上執行的處理序。 此程序執行之後，請按一下**偵錯 > 附加至處理序**(或按**CTRL + ALT + P**) 以開啟**附加至處理序**對話方塊。

您可以使用這項功能來偵錯在本機或遠端電腦執行的應用程式，同時，偵錯多個處理序或不是在 Visual Studio 中建立應用程式進行偵錯。 通常會很有用時您想要偵錯應用程式，但 （基於任何原因） 未啟動應用程式從 Visual Studio 附加偵錯工具。 例如，如果您正在執行的應用程式，而不偵錯工具，並叫用例外狀況，您可能會再附加至執行的應用程式，以開始偵錯的處理序。

> [!TIP]
> 不確定是否要使用**附加至處理序**偵錯案例嗎？ 請參閱[常見偵錯案例](#BKMK_Scenarios)。 如果您想要偵錯 ASP.NET 應用程式已部署至 IIS，請參閱[在執行 IIS 的遠端電腦上的遠端偵錯 ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)。

##  <a name="BKMK_Attach_to_a_running_process"></a> 附加至本機電腦上執行的處理序  
 若要附加至處理序，您必須知道處理序名稱 (請參閱[常見偵錯案例](#BKMK_Scenarios)的幾個常見的程序名稱)。
  
1.  在 Visual Studio 中，選取**偵錯 > připojit k procesu** (或按**CTRL + ALT + P**)。

    如果您想要快速重新附加至處理程序相反地，請參閱[重新附加至處理序](#BKMK_reattach)。
  
2.  請在 [附加至處理序]  對話方塊的 [可使用的處理序]  清單中，尋找您要附加的程式。  

     若要快速地選取您想要的程序，輸入處理序名稱的第一個字母，或您可以搜尋處理序名稱的 [篩選] 方塊中輸入的值。 如果您不知道處理程序名稱，請參閱[常見偵錯案例](#BKMK_Scenarios)。
     
     ![DBG_Basics_Attach_To_Process](../debugger/media/DBG_Basics_Attach_To_Process.png "DBG_Basics_Attach_To_Process") 
  
     如果該處理序正在不同的使用者帳戶下執行，請選取 [顯示所有使用者的處理序]  核取方塊。
  
3.  在 [附加至]  方塊中，確定其中已列出您要偵錯的程式碼類型。 預設的 [自動]  設定會自動判斷您要偵錯的程式碼類型。 若要手動設定程式碼類型，請執行下列程序  
  
    1.  按一下 [附加至]  方塊中的 [選取] 。  
  
    2.  在 [選取程式碼類型]  對話方塊中，按一下 [偵錯這些程式碼類型]  ，然後選取要偵錯的類型。

        預設值**自動**設定適用於大部分的應用程式類型。 偵錯在 Chrome 上的用戶端指令碼中，選擇**Webkit**做為程式碼類型。 針對 Chrome，您可能需要啟動瀏覽器中偵錯模式，根據您的應用程式類型 (類型`chrome.exe --remote-debugging-port=9222`從命令列)。

        > [!NOTE]
        > 針對用戶端指令碼偵錯，必須在瀏覽器中啟用指令碼偵錯。 
  
    3.  按一下 [確定 **Deploying Office Solutions**]。  
  
4.  按一下 [附加] 。

##  <a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a> 附加至遠端電腦上的處理序  
若要附加至處理序，您必須知道處理序名稱 (請參閱[常見偵錯案例](#BKMK_Scenarios)的幾個常見的程序名稱)。 如需更完整的已部署至 IIS 的 ASP.NET 應用程式的詳細指引，請參閱[在執行 IIS 的遠端電腦上的遠端偵錯 ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)。 如果您不知道處理序的名稱，您的案例，請參閱[常見偵錯案例](#BKMK_Scenarios)
  
當您使用**附加至處理序** 對話方塊中，您可以選取已針對遠端偵錯設定的另一部電腦 （也就遠端偵錯工具必須執行遠端電腦上）。 如需詳細資訊，請參閱 <<c0> [ 遠端偵錯](../debugger/remote-debugging.md)。 當您選取了遠端電腦時，您可以檢視該電腦上正在執行的可使用處理序清單，並附加至其中一個或多個處理序進行偵錯。
  
**若要選取遠端電腦：**  

1. 在 Visual Studio 中，選取**偵錯 > připojit k procesu** (或按**CTRL + ALT + P**)。

    如果您想要快速重新附加至處理程序相反地，請參閱[重新附加至處理序](#BKMK_reattach)。

2.  在 [附加至處理序]  對話方塊中，從 [傳輸]  清單選取適當的連接類型。 [預設值] 是適合大部分情況的正確設定

    [傳輸]  設定在偵錯工作階段之間持續維持。 
  
3.  利用下列其中一種方法，使用 [限定詞]  清單方塊選擇遠端電腦名稱：  
  
    1.  在 [限定詞]  清單方塊中輸入名稱。
    
        > [!Note]
        > 如果您在稍後步驟中，您無法使用連接遠端電腦名稱，使用的 IP 位址。 （連接埠號碼可能會出現自動選取處理程序之後。 您也可以輸入它以手動方式。 在下圖 4020 是遠端偵錯工具的預設連接埠）。  

        如果您想要使用**尋找** 按鈕，您可能需要[開啟 UDP 連接埠 3702](../debugger/remote-debugger-port-assignments.md)伺服器上。
  
    2.  按一下附加至 [限定詞]  清單方塊的下拉箭號，然後從下拉式清單中選取電腦名稱。  
  
    3.  按一下 [限定詞]  清單旁的 [尋找] 按鈕，開啟 [遠端偵錯工具連接]  對話方塊。 [選取遠端偵錯工具連接]  對話方塊會列出位於您本機子網路上的所有裝置，以及透過乙太網路纜線直接附加至電腦的裝置。 按一下您想要的電腦或裝置，然後按一下 [選取] 。 
  
     [限定詞]  設定只有在使用該限定詞成功產生偵錯連接時，才會在偵錯工作階段之間持續維持。
     
4.  按一下 **重新整理**。

      [可使用的處理序]  清單會在您開啟 [處理序]  對話方塊時自動顯示。 當對話方塊開啟時，處理序可以在背景中啟動和停止。 但內容不一定是最新的。 您可以隨時按一下 [重新整理] 以重新整理該清單，查看目前的處理序清單。 
     
4.  請在 [附加至處理序]  對話方塊的 [可使用的處理序]  清單中，尋找您要附加的程式。

     若要快速地選取您想要的程序，輸入處理序名稱的第一個字母，或您可以搜尋處理序名稱的 [篩選] 方塊中輸入的值。 如果您不知道處理程序名稱，請參閱[常見偵錯案例](#BKMK_Scenarios)。
  
     如果該處理序正在不同的使用者帳戶下執行，請選取 [顯示所有使用者的處理序]  核取方塊。
     
5.  按一下 [附加] 。

## <a name="BKMK_reattach"></a> 重新附加至處理程序

您可以快速重新附加至您先前選擇附加至的處理序**偵錯 > 重新附加至處理序...**(**Shift + Alt + P**)。 當您選擇此命令時，偵錯工具會立即嘗試將附加到最後一個處理序您附加至使用**附加至處理序** 對話方塊。

偵錯工具會重新附加藉由先嘗試比對上一個處理序識別碼，然後，如果失敗，藉由比對先前的程序名稱。 如果找不到任何相符項目，或多個處理序有相同的名稱，則**附加至處理序**對話方塊隨即出現，讓您可以選取正確的處理序。

> [!NOTE]
> **重新附加至處理序**命令是 Visual Studio 2017 的新功能。

## <a name="additional-info"></a>其他資訊

偵錯時，您可以附加至多個程式，但是無論在任何時間，偵錯工具一次只能有一個使用中程式。 您可以在 [偵錯位置]  工具列或 [處理序]  視窗中設定使用中的程式。  
  
如果您嘗試附加至未受信任的使用者帳戶所擁有的處理序，會出現安全性警告對話方塊確認訊息。 如需詳細資訊，請參閱[安全性警告： 附加至不受信任的使用者所擁有的處理序可能會造成危險。如果下列資訊看起來有問題，或您不確定，不會附加至這個處理序](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)。  
  
在某些情況下，在遠端桌面 (終端機服務) 工作階段中進行偵錯時，[可使用的處理序]  清單並不會顯示所有可使用的處理序。 如果您是以受限制的使用者身分執行 Visual Studio，則 [可使用的處理序]  清單不會顯示在工作階段 0 中執行的處理序，因為工作階段 0 是用於服務以及其他包括 w3wp.exe 的伺服器處理序。 您可藉由使用系統管理員帳戶來執行 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，或是從伺服器主控台 (而非終端機服務工作階段) 執行 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，來解決這個問題。 如果這些解決方法都沒有效，第三個方法就是從 Windows 命令列執行 `vsjitdebugger.exe -p` *ProcessId* 以連結至流程。 您可以使用 tlist.exe 來判斷處理序 ID。 若要取得 tlist.exe，下載並安裝偵錯工具針對 Windows，網址[WDK 和 WinDbg 下載](/windows-hardware/drivers/download-the-wdk)。

## <a name="BKMK_Scenarios"></a> 常見的偵錯案例

若要可協助您識別您需要使用是否**附加至處理序**和要附加至哪個處理程序如下所示的一些常見的偵錯案例 （清單未全部列出）。 其中有提供詳細的指示，我們會提供連結。 若要快速存取 對話方塊中，請使用**CTRL + ALT + P** ，然後輸入 處理序名稱的第一個字母。

對於某些應用程式類型 （例如 UWP app) 中，您不直接附加到處理序名稱，但使用**偵錯 Installed App Package**功能表選項 （請參閱資料表）。

> [!NOTE]
> 如需在 Visual Studio 中的基本偵錯資訊，請參閱[開始使用偵錯工具](../debugger/getting-started-with-the-debugger.md)。

|情節|偵錯方法|處理序名稱|附註和連結|
|-|-|-|-|
|遠端偵錯 ASP.NET 4 或 4.5 上 IIS 伺服器|使用遠端工具，並附加至處理序|w3wp.exe|請參閱[IIS 的遠端電腦上的遠端偵錯 ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|在 IIS 伺服器上遠端偵錯 ASP.NET Core|使用遠端工具，並附加至處理序|dotnet.exe|應用程式部署，請參閱[發行至 IIS](https://docs.asp.net/en/latest/publishing/iis.html)。 進行偵錯，請參閱[遠端偵錯 ASP.NET Core 上執行 IIS 的遠端電腦](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)|
|本機 IIS 伺服器 （支援的應用程式類型） 上的用戶端指令碼偵錯|使用附加至處理序|chrome.exe、 MicrosoftEdgeCP.exe 或 iexplore.exe|必須啟用指令碼偵錯。 Chrome 中，您也必須針對執行 Chrome 偵錯模式，然後選取**Webkit 程式碼**中**附加至**欄位。|
|偵錯在本機電腦上的 C#、 Visual Basic 或 c + + 應用程式|使用任何一種[標準偵錯](../debugger/getting-started-with-the-debugger.md)或附加至處理序|*appname*.exe|在大部分情況下，使用標準偵錯並不會附加至處理序。|
|遠端偵錯 Windows 傳統型應用程式|遠端工具|N/A| 請參閱[遠端偵錯的 C# 或 Visual Basic 應用程式](../debugger/remote-debugging-csharp.md)或[遠端偵錯 c + + 應用程式](../debugger/remote-debugging-cpp.md)|
|之後啟動的應用程式，而不偵錯工具偵錯在本機電腦上的 ASP.NET 應用程式|使用附加至處理序|iiexpress.exe|這可能是很有幫助您載入的應用程式更快，這類 （例如） 程式碼剖析時。 |
|在 伺服器處理序上其他支援的應用程式類型進行偵錯|使用遠端工具 （如果伺服器位於遠端），並附加至處理序|chrome.exe、 iexplore.exe 或其他處理序|如有必要，使用資源監視器來識別處理程序。 請參閱[遠端偵錯](../debugger/remote-debugging.md)和本主題稍後的章節|
|遠端偵錯的通用 (UWP)、 OneCore、 HoloLens、 或 IoT 應用程式|偵錯已安裝的應用程式套件|N/A|請參閱[偵錯 Installed App Package](debug-installed-app-package.md)而不是使用**附加至處理序**|
|您未從 Visual Studio 啟動的通用 Windows App (UWP)、 OneCore、 HoloLens、 或 IoT 應用程式進行偵錯|偵錯已安裝的應用程式套件|N/A|請參閱[偵錯 Installed App Package](debug-installed-app-package.md)而不是使用**附加至處理序**|  
  
> [!NOTE]
>  偵錯工具若要附加至以 C++ 撰寫的程式碼，該程式碼必須發出 `DebuggableAttribute`。 您可以使用 [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) 連結器選項連結，將其自動加入程式碼。

## <a name="what-debugger-features-can-i-use"></a>可以使用哪些偵錯工具功能？

若要使用完整的功能，Visual Studio 偵錯工具 （例如叫用中斷點） 時附加至處理序，可執行檔必須完全符合您的本機來源和符號 (也就是偵錯工具必須能夠載入正確[符號 (.pbd) 檔](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)). 根據預設，這需要偵錯組建。

遠端偵錯的情況下，您必須擁有原始碼 （或一份原始碼） 已在 Visual Studio 中開啟。 在本機電腦上，在遠端電腦上的已編譯的應用程式二進位碼檔案必須來自同一個組建。

在本機偵錯案例，您可以偵錯在 Visual Studio 中而無法存取來源如果應用程式有正確的符號檔 （根據預設，這需要偵錯組建）。 如需詳細資訊，請參閱 <<c0> [ 指定的符號和原始程式檔](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)。
  
##  <a name="BKMK_Troubleshoot_attach_errors"></a> 疑難排解附加錯誤  
 當偵錯工具附加至執行中的處理序時，該處理序可以包含一種或多種程式碼類型。 偵錯工具可附加的程式碼類型會在 [選取程式碼類型]  對話方塊中顯示並供您選取。  
  
 有時候，偵錯工具可以成功附加至一種程式碼類型，而無法附加至另一種程式碼類型。 如果您嘗試附加至遠端電腦上正在執行的處理序，可能會發生這種狀況。 遠端電腦可能為某些程式碼類型安裝了遠端偵錯元件，但沒有安裝其他程式碼類型的遠端偵錯元件。 如果您嘗試附加至兩個或多個處理序以進行直接的資料庫偵錯，也可能會發生這種狀況。 (SQL 偵錯僅支援附加至單一處理序)。  
  
 如果偵錯工具能附加至某些程式碼類型 (而非所有程式碼類型)，您可能會看到識別無法附加之類型的訊息。  
  
 如果偵錯工具成功附加到至少一種程式碼類型，您可以繼續偵錯該處理序。 您只能偵錯已附加成功的程式碼類型。 上述範例訊息顯示該指令碼類型附加失敗。 因此，您無法在處理序內偵錯指令碼。 處理序中的指令碼仍可執行，但是您將無法在指令碼內設定中斷點、檢視資料，或執行其他的偵錯作業。  
  
 如果您需要更多相關資訊以了解偵錯工具無法附加至程式碼類型的原因，可以嘗試重新附加至該程式碼。  
  
 **若要取得特定資訊的程式碼類型附加失敗的原因**  
  
1.  與處理序中斷連結。 在 [偵錯]  功能表上按一下 [中斷所有連結] 。  
  
2.  重新附加至處理序，並只選取單一程式碼類型。  
  
    1.  在 [附加至處理序]  對話方塊的 [可使用的處理序]  清單中，選取該處理序。  
  
    2.  按一下 [選取] 。  
  
    3.  在 [選取程式碼類型]  對話方塊中，選取 [偵錯這些程式碼類型]  以及之前附加失敗的程式碼類型。 清除任何其他程式碼。  
  
    4.  按一下 [確定] 。 [選取程式碼類型]  對話框會關閉。  
  
    5.  在 [附加至處理序]  對話方塊中按一下 [附加] 。  
  
     這時，該附加將完全失敗，您將取得特定的錯誤訊息。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯多個處理序](../debugger/debug-multiple-processes.md)   
 [在 Just-in-time 偵錯](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [遠端偵錯](../debugger/remote-debugging.md)