---
title: 無法刪除選取的類別，因為它一或多個 DataContext 方法的傳回型別當做使用 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 0b5781508083524a5cf7374a12fd962f0fe34aaf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods"></a>無法刪除所選取的類別，因為它是用來當做一或多個 DataContext 方法的傳回型別。
有一個或多個 <xref:System.Data.Linq.DataContext> 方法的傳回型別是選取的實體類別 (Class)。 刪除被 <xref:System.Data.Linq.DataContext> 方法當做傳回型別的實體類別，會使專案編譯作業失敗。 若要刪除選取的實體類別，請識別使用它的 <xref:System.Data.Linq.DataContext> 方法，並將這些方法的傳回型別設定為不同的實體類別。  
  
 若要還原的傳回型別<xref:System.Data.Linq.DataContext>方法，以其原始自動產生的類型，先刪除<xref:System.Data.Linq.DataContext>方法從方法窗格，然後將物件從**伺服器總管**/ **資料庫總管**拖曳至 O/R 設計工具一次。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  識別<xref:System.Data.Linq.DataContext>方法作為傳回型別中的實體類別，藉由選取<xref:System.Data.Linq.DataContext>方法中的方法窗格，並檢查**傳回型別**屬性**屬性**視窗.  
  
2.  設定**傳回型別**給不同的實體類別，或是刪除<xref:System.Data.Linq.DataContext>從方法窗格的方法。  
  
## <a name="see-also"></a>另請參閱
[O/R 設計工具訊息](../data-tools/o-r-designer-messages.md)  
[LINQ to SQL 工具，Visual Studio 中](../data-tools/linq-to-sql-tools-in-visual-studio2.md)