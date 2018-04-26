---
title: 計算在 Visual Studio 中的程式碼度量
ms.date: 12/12/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code metrics [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f3d0bf9b0bf689be847e7f16f2ee01db6e3df6d7
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="code-metrics-values"></a>程式碼度量值

增加的複雜性現代的軟體應用程式也會增加可靠且可維護性，讓程式碼的困難度。 程式碼度量資訊是一組軟體測量數據，可以讓開發人員更深入了解他們正在開發的程式碼。 利用程式碼度量，開發人員可以了解哪些類型和/或方法應該修改設計或更徹底的測試。 開發團隊可以識別潛在風險、 了解專案的目前狀態和追蹤軟體開發過程的進度。

開發人員可以使用 Visual Studio 產生的量值的複雜度和維護的 managed 程式碼的程式碼度量資料。 可以產生整個方案或單一專案的程式碼度量資料。

如需如何在 Visual Studio 中產生程式碼度量資料的資訊，請參閱[如何： 產生程式碼度量資料](../code-quality/how-to-generate-code-metrics-data.md)。

## <a name="software-measurements"></a>軟體測量

下列清單顯示的程式碼度量結果，Visual Studio 計算：

- **可維護性指數**-計算表示相對容易維護的程式碼的索引值 0 和 100 之間。 較高的值表示較佳的可維護性。 色彩編碼分級可用來快速找出您的程式碼中的問題點。 綠色的評等是介於 20 到 100 之間，並指出程式碼可維護性良好。 黃色等級介於 10 到 19 之間，並指出程式碼會比較容易維護。 紅色評等是介於 0 到 9 的等級，和表示低可維護性。

- **循環複雜度**-測量結構程式碼的複雜度。 它會建立計算的資料流程中的程式不同的程式碼路徑數目。 複雜控制流程的程式將需要更多測試來達成良好的程式碼涵蓋範圍，而將會比較不容易維護。

- **繼承深度**-表示類別階層的根擴充的類別定義的數目。 階層愈深，就越難了解定義特定的方法和欄位可能會或 / 及重新定義。

- **類別結合**-測量透過參數、 區域變數、 傳回型別、 方法呼叫、 泛型或樣板具現化、 基底類別、 介面實作、 外部型別上定義欄位的唯一類別結合程度和屬性裝飾。 好的軟體設計會要求的型別和方法應該有高的一致性和低耦合。 結合程度高表示很難重複使用，以及許多其他類型上相依性由於維護的設計。

- **程式碼行**-指出程式碼行的近似數目。 計數為基礎的 IL 程式碼，因此不精確的原始程式碼檔案中的行數。 類型或方法嘗試執行太多工作，應該分割，可能表示非常高的計數。 它也可能表示類型或方法可能會難以維護。

## <a name="anonymous-methods"></a>匿名方法

*匿名方法*是只要沒有名稱的方法。 匿名方法最常用來做為委派的參數傳遞的程式碼區塊。 匿名方法中的成員，例如方法或存取子，宣告的度量結果與相關聯的宣告方法的成員。 它們不會在呼叫方法的成員與相關聯。

如需程式碼度量資訊會如何處理匿名方法的詳細資訊，請參閱[匿名方法和程式碼分析](../code-quality/anonymous-methods-and-code-analysis.md)。

## <a name="generated-code"></a>產生的程式碼

某些軟體工具和編譯器會產生程式碼加入至專案和專案的開發人員看不到或不應隨意變更。 大部分程式碼度量資訊會忽略產生的程式碼計算的度量值時。 這可讓度量值，以反映哪些開發人員可以檢視和變更。

產生適用於 Windows Form 程式碼不會進行忽略，因為它是開發人員可查看與變更的程式碼。

## <a name="next-steps"></a>後續步驟

- [如何： 產生程式碼度量資料](../code-quality/how-to-generate-code-metrics-data.md)
- [使用程式碼度量結果視窗](../code-quality/working-with-code-metrics-data.md)