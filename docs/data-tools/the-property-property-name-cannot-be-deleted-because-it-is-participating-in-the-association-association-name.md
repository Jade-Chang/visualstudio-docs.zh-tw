---
title: 屬性&lt;屬性名稱&gt;無法刪除，因為它正參與關聯&lt;關聯名稱&gt;|Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 5121d79e6db6bdef1deb0ee04540295b2a109f72
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>屬性&lt;屬性名稱&gt;無法刪除，因為它正參與關聯&lt;關聯名稱&gt;
選取的屬性設定為**關聯屬性**錯誤訊息中所指出的類別之間的關聯。 如果屬性已參與資料類別之間的關聯，就無法刪除屬性。  
  
 設定**關聯屬性**不同的屬性，為資料類別，以啟用成功刪除的所需的屬性。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  在 O/R Designer 上，選取在錯誤訊息指出的資料類別之間連接的關聯線。  
  
2.  若要開啟的該行上按兩下**關聯編輯器** 對話方塊。  
  
3.  移除從屬性**關聯屬性**。  
  
4.  試著再次刪除屬性。  
  
## <a name="see-also"></a>另請參閱
[O/R 設計工具訊息](../data-tools/o-r-designer-messages.md)  
[LINQ to SQL 工具，Visual Studio 中](../data-tools/linq-to-sql-tools-in-visual-studio2.md)