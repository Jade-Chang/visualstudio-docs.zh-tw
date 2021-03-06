---
title: 建立 Visual Studio 的離線安裝
description: 了解如何離線安裝 Visual Studio。
ms.custom: ''
ms.date: 01/17/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
- layout [Visual Studio]
ms.assetid: f8625d5e-f6ea-4db0-83c0-619b77fab3cf
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1ef917b4e8aa5cde8d95c036523bb525799cc19e
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/20/2018
ms.locfileid: "36279959"
---
# <a name="create-an-offline-installation-of-visual-studio-2017"></a>建立 Visual Studio 2017 的離線安裝

我們設計了 Visual Studio 2017 安裝程式，以適用於各種不同的網路和電腦情況。

- 新的工作負載型模型表示您需要下載的內容將會遠小於舊版的 Visual Studio (針對最小的安裝僅需下載 300 MB 的內容)。
- 相較於一般 "ISO" 或 ZIP 檔案，我們只會下載電腦所需的套件。 例如，如果您不需要 64 位元檔案，我們不會進行下載。
- 在安裝程序期間，我們會嘗試三種不同的下載技術 (WebClient、BITS 和 WinInet) 以將防毒和 Proxy 軟體的干擾降到最低；
- 安裝 Visual Studio 所需的檔案分佈在全球傳遞網路，因此我們可從當地伺服器提供檔案給您。

建議您嘗試使用 [Visual Studio Web 安裝程式](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)&mdash;相信您會發現這是很好的體驗。

 > [!div class="button"]
 > [下載 Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)

如果您由於網際網路連線無法使用或不可靠而想要離線安裝，請參閱[在低頻寬或不可靠的網路環境安裝 Visual Studio 2017](../install/install-vs-inconsistent-quality-network.md)。 您可以使用命令列來建立完成離線安裝所需之檔案的本機快取。 此程序會取代適用於舊版的 ISO 檔案。

> [!NOTE]
> 如果您是企業系統管理員，而且想要將Visual Studio 2017 部署至已啟用網際網路防火牆的用戶端工作站網路，請參閱[建立 Visual Studio 2017 的網路安裝](../install/create-a-network-installation-of-visual-studio.md)和[安裝 Visual Studio 離線安裝所需的憑證](../install/install-certificates-for-visual-studio-offline.md)頁面。

## <a name="get-support"></a>取得支援

有時可能會發生一些問題。 如果您的 Visual Studio 安裝失敗，請參閱[針對 Visual Studio 2017 安裝和升級問題進行疑難排解](troubleshooting-installation-issues.md)頁面。 如果所有疑難排解步驟都沒有幫助，您可以透過即時聊天與我們連絡，以取得安裝協助 (僅限英文)。 如需詳細資訊，請參閱 [Visual Studio 支援頁面](https://visualstudio.microsoft.com/vs/support/#talktous) \(英文\)。

以下是一些支援選項：

* 您可以透過 Visual Studio 安裝程式和 Visual Studio IDE 中的[回報問題](../ide/how-to-report-a-problem-with-visual-studio-2017.md)工具來向我們報告產品問題。
* 您可以在 [UserVoice](https://visualstudio.uservoice.com/forums/121579) 上與我們分享產品建議。
* 您可以追蹤產品問題並在 [Visual Studio 開發人員社群](https://developercommunity.visualstudio.com/) \(英文\) 中尋找解答。
* 您也可以透過[在 Gitter 社群中的 Visual Studio 交談](https://gitter.im/Microsoft/VisualStudio)，與我們以及其他 Visual Studio 開發人員進行互動。 (這個選項需要 [GitHub](https://github.com/) 帳戶)。
