---
title: "什麼 &#39; Visual Studio 中設計的新 s |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-modeling
ms.topic: article
helpviewer_keywords:
- what's new [VIsual Studio ALM], architecture and modeling
- architecture [Visual Studio Ultimate], modeling
- modeling software [Visual Studio ALM], What's New
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: c3fe70c36daf9d137e77acf75b9bd712ecf556c7
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="what39s-new-for-design-in-visual-studio"></a>什麼 &#39; s Visual Studio 中設計的新功能

## <a name="live-dependency-validation"></a>即時的相依性驗證

移除不必要的相依性是管理您的技術負債很重要的一部分。
相依性的即時驗證現在包含，提供相關的問題，精確資訊，且完全獲益的錯誤清單，並在編輯器中的新功能。

![在動作中的即時的相依性驗證](media/dep-validation-whatsnew-01.png)

撰寫經驗已進行相依性驗證更容易找到並更容易存取，變更從 「 圖層圖表 」 的術語 「 相依性圖 」 來變更。

**架構**功能表現在包含要直接建立相依性圖表的命令：

![在 [架構] 功能表上的即時的相依性項目](media/dep-validation-whatsnew-02.png)

...且已變更的屬性名稱的相依性圖表中，與它們的描述，在圖層，使其更有意義：

![即時更新的相依性屬性的名稱](media/dep-validation-whatsnew-03.png)

您現在會看到目前方案中的程式碼的分析結果中，立即變更的影響每次您儲存圖表。 您不必再等候完成 「 驗證相依性 」 命令。

如需詳細資訊，請參閱[此部落格文章](https://blogs.msdn.microsoft.com/visualstudioalm/2016/10/07/live-architecture-dependency-validation-in-visual-studio-15-preview-5/)。 
 
## <a name="uml-designers-have-been-removed"></a>已移除 UML 設計工具

UML 設計工具已移除了此版本的 Visual Studio Enterprise。

* UML 圖表現在會顯示為 XML 檔案
* UML 模型總管 不存在
* 模型的專案的參考不會再用於相依性驗證
* 在 [方案總管] 的 「 圖層參考 」 節點不會再顯示
* 不再使用相依性 （圖層） 圖表上的 「 驗證 」 建置動作-已移除建置工作 
* 版本之間的往返，被為了專案結構
* 您可以仍然開啟、 建立、 編輯和儲存為 XML 的相依性 （圖層） 圖表
* TFS 工作項目連結至相依性 （圖層） 圖表不是在設計介面上，您可以存取
* 不再支援 DSL 或圖層從上一頁連結 
* 不再支援 Modeling SDK 中的 UML 擴充性

不過，支援視覺化.NET 和 c + + 程式碼的架構是可透過[code map](map-dependencies-across-your-solutions.md)，和相依性驗證上面所述的重大改良。

如果您是 UML 設計工具的大量使用者時，您可以繼續使用 Visual Studio 2015 或更早版本，而當您決定針對 UML 需求的替代工具。

如需詳細資訊，請參閱[此部落格文章](https://blogs.msdn.microsoft.com/visualstudioalm/2016/10/14/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/)。 

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

<a name="VersionSupport"></a>
##  <a name="version-support-for-architecture-and-modeling-tools"></a>Architecture and Modeling Tools 的版本支援  

Visual Studio 有數個版本。 並非所有版本都提供 Architecture and Modeling Tools 的支援。 下表顯示每個工具的可用性。  
  
|**功能**|**Enterprise**|**Professional**|**Community**|**Express**|  
|-----------------|--------------------|----------------------|-------------------|-----------------|  
|**Code Map**|[是]|請參閱附註 (1)|-|-|  
|**相依性圖表**|[是]|請參閱附註 (2)|請參閱附註 (2)|-|  
|**導向圖形**（DGML 圖表）|[是]|是|[是]|-|  
|**程式碼複製品**|[是]|-|-|-|  
  
注意 (1)：僅支援讀取程式碼對應、篩選程式碼對應、加入新的泛型節點，及從選取範圍建立新的導向圖形。

附註 (2): 僅支援讀取相依性圖表。
