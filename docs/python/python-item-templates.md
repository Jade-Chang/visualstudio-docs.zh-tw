---
title: Python 專案的項目範本
description: Python 專案項目範本的參考清單可在 Visual Studio 中透過 [加入] > [新項目] 對話方塊取得。
ms.date: 04/25/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 9811905e842eeb62399ef3b88558ee0286b05c84
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
ms.locfileid: "32032674"
---
# <a name="python-item-templates"></a>Python 項目範本

Python 專案中的項目範本可透過 [專案] > [加入新項目] 功能表命令取得，或透過 [方案總管] 中操作功能表上的 [加入] > [新項目] 命令取得。

![加入新項目對話方塊](media/project-item-templates.png)

使用您為項目提供的名稱時，範本通常會在專案中目前所選的資料夾內建立一或多個檔案和資料夾 (以滑鼠右鍵按一下資料夾可自動選取該資料夾的操作功能表)。 新增項目時，會將該項目包含在 Visual Studio 專案中，而且會出現的 [方案總管] 中。

下表簡短說明 Python 專案內每個項目範本的效果：

| 範本 | 範本建立的內容 |
| --- | --- |
| 空白 Python 檔案 | 副檔名為 `.py` 的空白檔案。 |
| Python 類別 | 一個 `.py` 檔案包含一個空白 Python 類別定義。 |
| Python 套件 | 包含 `__init.py__` 檔案的資料夾。 |
| Python 單元測試 | 根據 `unittest`架構進行一個單元測試的 `.py` 檔案，還有呼叫 `unittest.main()` 以便執行檔案中的測試。 |
| HTML 頁面 | `.html` 檔案具有單一頁面結構，其中包含 `<head>` 和 `<body>` 元素。 |
| JavaScript | 空白的 `.js` 檔案。 |
| 樣式表 | `.css` 檔案包含 `body` 的空白樣式 |
| 文字檔 | 空白的 `.txt` 檔案。 |
| Django 1.9 應用程式<br/>Django 1.4 應用程式 | 具有應用程式名稱的資料夾，其中包含如 Django 1.9 的[在 Visual Studio 中學習 Django，步驟 2-2](learn-django-in-visual-studio-step-02-create-an-app.md#step-2-1-create-an-app-with-a-default-structure) 中所說明的 Django 應用程式核心檔案。 針對 Django 1.4，則不包含 `migrations` 資料夾、`admin.py` 檔案和 `apps.py` 檔案。 |
| IronPython WPF 視窗 | WPF 視窗包含兩個並存的檔案：`.xaml` 檔案會使用空白的 `<Grid>` 元素定義 `<Window>`而相關聯的 `.py` 則使用 `wpf` 程式庫來載入 XAML 檔案。 通常是在使用其中一個 IronPython 專案範本所建立的專案中使用。 請參閱[管理 Python 專案 - 專案範本](managing-python-projects-in-visual-studio.md#project-templates)。 |
| Web 角色支援檔案 | 專案根目錄中的 `bin` 資料夾 (不論專案中所選的資料夾為何)。 該資料夾包含預設的部署指令碼和 Azure 雲端服務 Web 角色的 `web.config`檔案。 該範本也包含說明詳細資料的 `readme.html` 檔案。 |
| 背景工作角色支援檔案 | 專案根目錄中的 `bin` 資料夾 (不論專案中所選的資料夾為何)。 該資料夾包含預設部署和啟動指令碼，還有 Azure 雲端服務背景工作角色的 `web.config` 檔案。 該範本也包含說明詳細資料的 `readme.html` 檔案。 |
| Azure web.config (FastCGI) | `web.config` 檔案，其中包含使用 [WSGI](https://wsgi.readthedocs.io/en/latest/) 物件處理傳入連線的應用程式的項目。 此檔案通常部署在執行 IIS (例如 Azure App Service) 的 Web 伺服器根目錄。 如需詳細資訊，請參閱[發行至 Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)。 |
| Azure web.config (HttpPlatformHandler) | `web.config` 檔案，其中包含接聽傳入連線通訊端應用程式的項目。 此檔案通常部署在執行 IIS (例如 Azure App Service) 的 Web 伺服器根目錄。 如需詳細資訊，請參閱[發行至 Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)。 |
| Azure 靜態檔案 web.config | `web.config` 檔案通常會新增到 `static` 資料夾 (或含有靜態項目的其他資料夾) 中，以停用處理該資料夾的 Python。 此組態檔會與上述 FastCGI 或 HttpPlatformHandler 組態檔其中之一搭配運作。 如需詳細資訊，請參閱[發行至 Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)。 |
| Azure 遠端偵錯 web.config | `web.config.debug` 檔案，可透過 WebSockets 啟用遠端偵錯，連同 `Microsoft.PythonTools.WebRole.dll` 和 `ptvsd` 資料夾，其中包含要部署到伺服器以啟用遠端偵測的模組。 您通常會在與 `web.config` 檔案相同的位置建立此項目。 如需詳細資訊，請參閱[對 Azure 上的 Python 程式碼進行遠端偵錯](debugging-remote-python-code-on-azure.md)。 另請參閱下列附註。 |

> [!Note]
> 如果您將偵錯 `web.config` 範本新增到專案，並計劃使用 Python 遠端偵錯，則必須使用 [偵錯] 設定來發行網站。 此設定不同於目前使用中的方案組態，且一律預設為 [發行]。 若要加以變更，請開啟 [設定] 索引標籤，然後使用 [發行精靈] 中的 [組態]下拉式方塊。 (如需有關建立及部署至 Azure Web 應用程式的詳細資訊，請參閱[Azure 文件](https://azure.microsoft.com/develop/python/)。)
>
> ![正在變更發佈設定](media/template-web-publish-config.png)

## <a name="see-also"></a>另請參閱

- [管理 Python 專案 - 專案範本](managing-python-projects-in-visual-studio.md#project-templates)
- [Python Web 專案範本](python-web-application-project-templates.md)
- [發行至 Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)