---
title: 在 Visual Studio 中分析記憶體使用量 | Microsoft Docs
ms.custom: ''
ms.date: 01/02/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 20c483b40cf1cc45b730ea67bf01ea452c42af1e
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
---
# <a name="analyze-memory-usage"></a>分析記憶體使用量
使用與偵錯工具整合的 [記憶體使用量] 診斷工具，來找出記憶體遺漏和記憶體使用沒有效率等問題。 記憶體使用量工具可讓您擷取 Managed 和原生記憶體堆積的一個或多個 *「快照」* (Snapshot)。 您可以收集 .NET、原生或混合模式 (.NET 和原生) 應用程式的快照。  
  
-   您可以分析一份快照，了解物件類型對於記憶體使用的相對影響，並找出應用程式中無效率使用記憶體的程式碼。  
  
-   您也可以比較 (差異比對) 應用程式的兩個快照，找出造成記憶體使用量隨著時間逐漸增加的程式碼部分。  

如需詳細指示，請參閱[分析記憶體使用量](../profiling/memory-usage.md)教學課程。 若要分析記憶體使用量但不附加偵錯工具，請參閱[記憶體使用量 (不使用偵錯工具)](memory-usage-without-debugging2.md)。
  
## <a name="blogs-and-videos"></a>部落格和影片  

|         |         |
|---------|---------|
|  ![影片的電影攝影機圖示](../install/media/video-icon.png "觀看影片")  |    [觀看使用診斷工具的影片](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Profiling-with-Diagnostics-Tools-in-Visual-Studio-2017-daHnzMD6D_9211787171)，了解如何在 Visual Studio 2017 中分析記憶體使用量和 CPU 使用量。 |

 [偵錯時分析 CPU 與記憶體](https://blogs.msdn.microsoft.com/visualstudio/2016/02/15/analyze-cpu-memory-while-debugging/)  
  
 [Visual C++ 部落格：Visual C++ 2015 中的記憶體分析](https://blogs.msdn.microsoft.com/vcblog/2015/10/21/memory-profiling-in-visual-c-2015/)  

## <a name="see-also"></a>另請參閱
 [Visual Studio 中的分析](../profiling/index.md)  
 [分析功能導覽](../profiling/profiling-feature-tour.md)