---
title: 測量 Python 程式碼的效能
description: 如何在使用 CPython 型解譯器時，以 Visual Studio 分析工具來檢查 Python 程式碼的效能。
ms.date: 06/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 971eb7ce863fc4281d73e2d4d363805de22810f4
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37058626"
---
# <a name="profiling-python-code"></a>分析 Python 程式碼

您可在使用 CPython 型解譯器時分析 Python 應用程式。 (請參閱[功能矩陣：分析](overview-of-python-tools-for-visual-studio.md#matrix-profiling)以了解這項功能在不同版本 Visual Studio 中的可用性。)

若要進行分析，請執行 [分析] > [啟動 Python 分析] 功能表命令，這將會開啟設定對話方塊：

![分析設定對話方塊](media/profiling-start.png)

當您選取 [確定] 時，分析工具會執行並開啟效能報告，您可以透過該報告探索應用程式中的執行時間：

![分析效能報告](media/profiling-results.png)

|   |   |
|---|---|
| ![影片的電影攝影機圖示](../install/media/video-icon.png "觀看影片") | [觀看示範 Python 分析的影片 (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Profiling-Python-s6FoC6LWE_1005918567) (3 分 00 秒)。|

> [!Note]
> Visual Studio 目前只支援此層級的完整應用程式剖析，我們非常願意聆聽您對未來功能的意見反應。 請使用此頁面底部的 [\[提供產品意見反應\] 按鈕](#feedback)。

## <a name="profiling-for-ironpython"></a>針對 IronPython 的分析

因為 IronPython 不是 CPython 型解譯器，所以上述分析功能無法運作。

請改為直接將 `ipy.exe` 作為目標應用程式啟動來使用 Visual Studio .NET 分析工具，並使用適當的引數來啟動您的啟動指令碼。 將 `-X:Debug` 包含在命令列中，以確保可偵錯與分析您的所有 Python 程式碼。 此引數會產生包含在 IronPython 執行階段及您程式碼上所花費時間的效能報告。 您的程式碼是以損害名稱來識別。

此外，IronPython 本身也有一些內建的分析功能，但它目前並沒有良好的視覺化檢視。 請參閱 [IronPython 分析工具 (英文)](http://blogs.msdn.com/b/curth/archive/2009/03/29/an-ironpython-profiler.aspx) (MSDN 部落格) 來查看可用內容。