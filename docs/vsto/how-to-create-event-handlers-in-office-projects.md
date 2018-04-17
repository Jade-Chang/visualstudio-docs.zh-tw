---
title: 如何： 在 Office 專案中建立事件處理常式 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Basic [Office development in Visual Studio], event handlers
- event handlers [Office development in Visual Studio]
- Visual C# [Office development in Visual Studio], event handlers
- events [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 833e41979d1dac9def7e647b396161d0ac5e2b67
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-event-handlers-in-office-projects"></a>如何：在 Office 專案中建立事件處理常式
  有幾種方式在 Visual Basic 和 C# 中建立事件處理常式。 在 [設計] 檢視中，您可以建立預設值為控制項的事件處理常式，方法是按兩下控制項，或使用 [事件] 窗格的**屬性**視窗控制項上建立的任何事件處理常式。 不過，如果您是在程式碼 檢視中，您可能不想要切換至 設計 檢視中建立事件處理常式。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-create-an-event-handler-in-visual-basic"></a>若要在 Visual Basic 中建立事件處理常式  
  
1.  從**類別名稱**的程式碼編輯器頂端的下拉式清單，選取您想要的物件建立的事件處理常式。  
  
    > [!NOTE]  
    >  如果您想要建立事件處理常式`ThisDocument`或`ThisWorkbook`，您必須選取**（ThisDocument 事件）**或**（ThisWorkbook 事件）**中**類別名稱**下拉式清單  
  
2.  從**方法名稱**下拉式清單上方的程式碼編輯器中，選取的事件。  
  
     Visual Studio 會建立事件處理常式，並將插入點移至新建立的事件處理常式。 如果事件處理常式已經存在，將插入點移到現有的事件處理常式。  
  
### <a name="to-create-an-event-handler-in-c"></a>在 C# 中建立事件處理常式  
  
1.  建立中的事件委派**啟動**輸入完整的事件名稱後接空格，然後再輸入類別的事件**+=**之後沒有空格。 例如:   
  
     `this.<object name>.<event name> +=`  
  
2.  在下一行程式碼結束時，按兩次 TAB 鍵。  
  
     Visual Studio 自動完成的一行程式碼、 建立事件處理常式，並將插入點移至新建立的事件處理常式。  
  
## <a name="see-also"></a>另請參閱  
 [撰寫 Office 方案中的程式碼](../vsto/writing-code-in-office-solutions.md)   
 [逐步解說： 針對 NamedRange 控制項的事件進行程式設計](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)   
 [建置 Office 方案](../vsto/building-office-solutions.md)  
  
  