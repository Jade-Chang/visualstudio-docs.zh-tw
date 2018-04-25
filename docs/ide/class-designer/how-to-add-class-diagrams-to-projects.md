---
title: 如何：將類別圖表新增至專案 (類別設計工具) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- class diagrams, creating
- Class Designer [Visual Studio], opening
ms.assetid: 0eac1b54-2711-4e4b-9654-a0c429c08c8f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e1e67d5a1ca899605d3456d8d68f4b3c04fc8bd2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-class-diagrams-to-projects-class-designer"></a>如何：將類別圖表加入至專案 (類別設計工具)
若要設計、編輯和重構類別及其他類型，請將類別圖加入至 C#、Visual Basic 或 C++ 專案。 若要在專案中視覺化程式碼的不同部分，請將多個類別圖加入至專案。  
  
您不能從跨多個應用程式共用程式碼的專案建立類別圖。 若要建立 UML 類別圖表，請參閱[建立 UML 模組化專案和圖表](../../modeling/create-uml-modeling-projects-and-diagrams.md)。  
  
### <a name="to-add-a-blank-class-diagram-to-a-project"></a>若要將空白類別圖加入至專案  
  
1.  在 [方案總管] 中，以滑鼠右鍵按一下專案名稱。 接著請選擇 [加入新項目] 或 [新增]、[新增項目]。  
  
2.  從範本清單中，選擇 [類別圖表]。 若是 Visual C++ 專案，請查看 [範本] 下方和 [公用程式] 下方以尋找這個範本。  
  
     類別圖便會在 [類別設計工具] 中開啟，並會在 [方案總管] 的專案階層架構內，顯示為具有 .cd 副檔名的檔案。 使用 [類別設計工具] 工具箱將圖案和線條拖曳至圖表。  
  
3.  若要加入多個類別圖，請重複本程序的步驟。  
  
### <a name="to-add-a-class-diagram-based-on-existing-types"></a>根據現有類別加入類別圖  
  
1.  在方案總管中，開啟類別檔案操作功能表，然後選擇 [檢視類別圖表]。  
  
     -或-  
  
     在 [類別檢視] 中，開啟命名空間或類型操作功能表，然後選擇 [檢視類別圖表]。  
  
### <a name="to-display-the-contents-of-a-complete-project-in-a-class-diagram"></a>在類別圖表中顯示完整專案的內容  
  
1.  在方案總管或 [類別檢視] 中，在專案上按一下滑鼠右鍵並選擇 [檢視]，然後選擇 [類別圖表檢視]。

     就會建立會自動填入內容的類別圖。  
  
## <a name="see-also"></a>另請參閱
[如何：使用類別設計工具建立類型](how-to-create-types.md)   
[如何：檢視現有類型](how-to-view-existing-types.md)   
[設計類別和類型](designing-classes-and-types.md)   
[檢視類型與關聯性](viewing-types-and-relationships.md)   
[使用類別圖表](working-with-class-diagrams.md)