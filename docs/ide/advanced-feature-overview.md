---
title: Visual Studio 2017 的進階功能
ms.date: 06/01/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a60e340639a023adf50b739870035c0b81a82643
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/20/2018
ms.locfileid: "36282521"
---
# <a name="features-of-visual-studio-2017"></a>Visual Studio 2017 的功能

[Visual Studio IDE 概觀](../ide/visual-studio-ide.md)主題提供 Visual Studio 的基本介紹。 本文描述的功能可能更適合資深開發人員或已十分熟悉 Visual Studio 的人員使用。

## <a name="modular-installation"></a>模組安裝

Visual Studio 的模組安裝程式可讓您選擇並安裝「工作負載」，這些是您慣用的程式設計語言或平台所需的幾組功能。 此策略有助於將 Visual Studio 安裝項的資源使用量降到更低，這意謂著它的安裝和更新速度也更快。

如果您尚未安裝 Visual Studio 2017，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)頁面免費進行安裝。

若要深入了解如何在您的系統上設定 Visual Studio，請參閱 [Install Visual Studio 2017](../install/install-visual-studio.md)。

## <a name="create-cloud-enabled-apps-for-azure"></a>建立已啟用雲端的 Azure 應用程式

Visual Studio 提供一套工具，可讓您輕鬆建立由 Microsoft Azure 提供技術之支援雲端的應用程式。 您可以直接從 IDE，在 Microsoft Azure 上設定、建置、偵錯、封裝及部署應用程式和服務。 若要取得 Azure 工具和專案範本，請在安裝 Visual Studio 時，選取 [Azure 開發] 工作負載。

![Azure 開發工作負載](../data-tools/media/azure-development-workload.png)

安裝 **Azure 開發**工作負載之後，即可在 [新增專案] 對話方塊中使用 C# 的下列**雲端**範本：

![Visual Studio 的雲端專案範本](media/cloud-project-templates.png)

Visual Studio 的 [Cloud Explorer](/azure/vs-azure-tools-resources-managing-with-cloud-explorer) 可讓您在 Visual Studio 內檢視和管理 Azure 型雲端資源。 這些資源可能包含虛擬機器、資料表、SQL 資料庫等。 **Cloud Explorer** 會顯示在您所登入 Azure 訂用帳戶下管理之所有帳戶中的 Azure 資源。 此外，如果特定作業需要 Azure 入口網站，**Cloud Explorer** 會提供連結，將您帶到入口網站中您所需前往的位置。

![Visual Studio 中的 Cloud Explorer](media/cloud-explorer.png)

您可以使用**連線服務**，將 Azure 服務運用到您的應用程式，例如：

- [Active Directory 連線服務](/azure/active-directory/develop/vs-active-directory-add-connected-service)，讓使用者可以使用其帳戶從 [Azure Active Directory](/azure/active-directory/active-directory-whatis) 連線至 Web 應用程式
- [Azure 儲存體連線服務](/azure/vs-azure-tools-connected-services-storage)，適用於 Blob 儲存體、佇列和資料表
- [Key Vault 連線服務](/azure/key-vault/vs-key-vault-add-connected-service)，用來管理 Web 應用程式的祕密

可用的**連線服務**取決於您的專案類型。 以滑鼠右鍵按一下 [方案總管] 中的專案，然後選擇 [新增] > [連線服務] 來新增服務。

![Visual Studio 連線服務](media/connected-services.png)

如需詳細資訊，請參閱[使用 Visual Studio 和 Azure 移至雲端](https://visualstudio.microsoft.com/vs/azure-tools/)。

## <a name="create-apps-for-the-web"></a>建立適用於 Web 的應用程式

Web 推動我們的現代化世界，而 Visual Studio 則可協助您撰寫適用於 Web 的應用程式。 您可以使用 ASP.NET、Node.js、Python、JavaScript 及 TypeScript 來建立 Web 應用程式。 Visual Studio 了解 Angular、jQuery、Express 等 Web 架構。 ASP.NET Core 和 .NET Core 可在 Windows、Mac 及 Linux 作業系統上執行。 [ASP.NET Core](http://www.asp.net/core/overview) 是 MVC、WebAPI 及 SignalR 的重大更新，可以在 Windows、Mac 及 Linux 上執行。  ASP.NET Core 是全新的設計，提供您可組合的簡式 .NET 堆疊，讓您建置現代化的雲端架構 Web 應用程式和服務。

如需詳細資訊，請參閱[新式 Web 工具](https://visualstudio.microsoft.com/vs/modern-web-tooling/)。

## <a name="build-cross-platform-apps-and-games"></a>建置跨平台應用程式和遊戲

您可以使用 Visual Studio 建置 macOS、Linux、Windows、Android、iOS 和其他[行動裝置](https://visualstudio.microsoft.com/vs/mobile-app-development/)用的應用程式和遊戲。

- 建置在 Windows、macOS 和 Linux 上執行的 [.NET Core](/dotnet/core/) 應用程式。

- 使用 [Xamarin](https://developer.xamarin.com/guides/cross-platform/windows/visual-studio/) 以 C# 和 F# 建置 iOS、Android 和 Windows 用的行動應用程式。

- 透過 [Apache Cordova](/visualstudio/cross-platform/tools-for-cordova/)，使用標準 Web 技術 &mdash;HTML、CSS 和 JavaScript&mdash; 建置 iOS、Android 和 Windows 用的行動應用程式。

- 使用 [Visual Studio Tools for Unity](../cross-platform/visual-studio-tools-for-unity.md) 以 C# 建置 2D 和 3D 遊戲。

- 以[適用於跨平台開發的 C++](../cross-platform/visual-cpp-for-cross-platform-mobile-development.md) 建置 iOS、Android 和 Windows 裝置用的原生 C++ 應用程式，以及在為 iOS、Android 和 Windows 建置的程式庫中共用通用程式碼。

- 使用 [Android 模擬器](../cross-platform/visual-studio-emulator-for-android.md)部署、測試及偵錯 Android 應用程式。

## <a name="connect-to-databases"></a>連線至資料庫

[伺服器總管] 可協助您在本機、從遠端瀏覽和管理 Azure、Salesforce.com、Office 365 及網站上的 SQL Server 執行個體和資產。 若要開啟 [伺服器總管]，請選擇主功能表上的 [檢視] > [伺服器總管]。 如需有關使用 [伺服器總管] 的詳細資訊，請參閱[新增連線 (英文)](../data-tools/add-new-connections.md)。

[SQL Server Data Tools (SSDT)](/sql/ssdt/download-sql-server-data-tools-ssdt) 是一個適用於 SQL Server、Azure SQL Database 及「Azure SQL 資料倉儲」的強大開發環境。 它可讓您建置、偵錯、維護及重構資料庫。 您可以使用資料庫專案，或直接使用內部或外部所連接的資料庫執行個體。

Visual Studio 中的 [SQL Server 物件總管] 提供與 SQL Server Management Studio 類似的資料庫物件檢視。 [SQL Server 物件總管] 可讓您執行輕型的資料庫管理和設計工作，包括編輯資料表資料、比較結構描述、直接從 [SQL Server 物件總管] 使用內容功能表來執行查詢等。

![SQL Server 物件總管](../ide/media/vs2015_sqlobjectexplorer.png)

## <a name="debug-test-and-improve-your-code"></a>偵錯、測試及改善您的程式碼

當您撰寫程式碼時，必須執行它並測試它，以找出錯誤 (bug) 及改善效能。 Visual Studio 的先進偵錯系統可讓您針對在本機專案、遠端裝置或[裝置模擬器](../cross-platform/visual-studio-emulator-for-android.md)上執行的程式碼進行偵錯。 您可以以一次一個陳述式的方式逐步偵錯程式碼，並一邊檢查變數。 您可以將中斷點設定成只在指定的條件為 true 時才叫用。 這些全部都可以在程式碼編輯器本身中管理，如此您就不需要離開您的程式碼。 如需有關 Visual Studio 中之 偵錯的更多詳細資料，請參閱[偵錯工具功能導覽](../debugger/debugger-feature-tour.md)。

若要深入了解如何改善您應用程式的效能，請查看 Visual Studio 的[分析](../profiling/profiling-feature-tour.md)功能。

在[測試](../test/improve-code-quality.md)方面，Visual Studio 提供單元測試、Live Unit Testing、IntelliTest、負載和效能測試等。 Visual Studio 也具有進階[程式碼分析](../code-quality/code-analysis-for-managed-code-overview.md)功能，可攔截設計、安全性和其他類型的缺陷。

## <a name="deploy-your-finished-application"></a>部署已完成的應用程式

當您的應用程式已準備就緒而可部署到使用者或客戶時，Visual Studio 會提供工具來執行部署，不論您是要部署到 Microsoft Store、SharePoint 網站，還是透過 InstallShield 或 Windows Installer 技術來部署，都可以。 全部都可透過 IDE 來存取。 如需詳細資訊，請參閱[部署應用程式、服務和元件](../deployment/deploying-applications-services-and-components.md)。

## <a name="manage-your-source-code-and-collaborate-with-others"></a>管理您的原始程式碼並與其他人共同作業

您可以在任何提供者所裝載的 Git 儲存機制 (包括 GitHub) 中管理您的原始程式碼。 或是使用 [Visual Studio Team Services (VSTS)](/vsts/index) 來一邊管理整個專案的程式碼，一邊管理錯誤 (bug) 與工作項目。 若要深入了解如何在 Visual Studio 中使用 Team Explorer 來管理 Git 存放庫，請參閱 [Git 與 Team Services (VSTS) 使用者入門](/vsts/git/gitquickstart?tabs=visual-studio)。 Visual Studio 也有其他內建原始檔控制功能。 如需詳細資訊，請參閱 [New Git Features in Visual Studio 2017 (blog)](https://blogs.msdn.microsoft.com/visualstudioalm/2017/03/06/new-git-features-in-visual-studio-2017/) (Visual Studio 2017 的新 Git 功能 (部落格))。

Visual Studio Team Services 是一項雲端式服務，可用來裝載軟體專案及允許以小組進行共同作業。 VSTS 支援 Git 和 Team Foundation 原始檔控制系統，以及 Scrum、CMMI 和 Agile 開發方法。 Team Foundation 版本控制 (TFVC) 使用單一且集中式伺服器儲存機制來追蹤和版本化檔案。 在其他開發人員取得最新變更的地方，一律將本機變更簽入中央伺服器。

Team Foundation Server (TFS) 是 Visual Studio 的應用程式生命週期管理中樞。 其可讓所有人使用單一方案參與開發流程。 TFS 也適合用來管理異質小組和專案

如果您在網路上有 Visual Studio Team Services 帳戶或 Team Foundation Server，便可以透過 Visual Studio 中的 [Team Explorer] 視窗與其連接。 在這個視窗中，您可以在原始檔控制簽入或簽出程式碼、管理工作項目、啟動建置和存取小組聊天室及工作區。 您可以從 [快速啟動] 方塊開啟 [Team Explorer]，也可以從主功能表的 [檢視] > [Team Explorer] 或從 [小組] > [管理連線] 來開啟它。

下圖顯示裝載於 VSTS 中之方案的 [Team Explorer] 視窗。

![Visual Studio Team Explorer](../ide/media/vs2017_teamexplorer.png)

您也可以自動化建置流程，來建置您小組開發人員已簽入版本控制的程式碼。 例如，您可以每晚或在每次簽入程式碼時建置一或多個專案。 如需詳細資訊，請參閱[建置及發行 (VSTS 和 TFS)](/vsts/build-release/index)。

## <a name="extend-visual-studio"></a>擴充 Visual Studio

如果 Visual Studio 沒有您所需的確切功能，您可以新增功能！ 您可以根據您的工作負載和風格將 IDE 個人化、針對尚未與 Visual Studio 整合的外部工具新增支援，以及修改現有的功能以提升您的生產力。 若要尋找最新版本的 Visual Studio 擴充性工具 (VS SDK)，請參閱 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)。

您可以使用 .NET 編譯器平台 ("Roslyn") 來撰寫自己的程式碼分析器和程式碼產生器。 前往 [Roslyn](https://github.com/dotnet/Roslyn)尋找您所需要的各項資源。

尋找由 Microsoft 開發人員和開發社群所建立的 Visual Studio [現有延伸模組](https://marketplace.visualstudio.com/vs)。

若要深入了解如何擴充 Visual Studio，請參閱[擴充 Visual Studio IDE](https://visualstudio.microsoft.com/vs/extend/)。

## <a name="see-also"></a>另請參閱

- [Visual Studio IDE 概觀](../ide/visual-studio-ide.md)
- [Visual Studio 2017 的新功能](../ide/whats-new-in-visual-studio.md)