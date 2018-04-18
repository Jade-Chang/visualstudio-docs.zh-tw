---
title: CA1719： 參數名稱不應符合成員名稱 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- ParameterNamesShouldNotMatchMemberNames
- CA1719
helpviewer_keywords:
- CA1719
- ParameterNamesShouldNotMatchMemberNames
ms.assetid: c6fea690-1659-4ee7-a1c5-125ad6754525
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 402744debf3ad94ff303a5d27a39b67d41faa341
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="ca1719-parameter-names-should-not-match-member-names"></a>CA1719：參數名稱不應符合成員名稱
|||  
|-|-|  
|TypeName|ParameterNamesShouldNotMatchMemberNames|  
|CheckId|CA1719|  
|分類|Microsoft.Naming|  
|中斷變更|中斷|  
  
## <a name="cause"></a>原因  
 外部可見成員的名稱比對，在不區分大小寫比較，其中一個參數的名稱。  
  
## <a name="rule-description"></a>規則描述  
 參數名稱應該要能傳達參數的意義，而成員名稱應該要能傳達成員的意義。 兩者相同屬罕見的設計。 如果將參數命名為與成員名稱相同的名稱，則不僅會不容易了解，也會讓程式庫難以使用。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 選取 不符合成員名稱的參數名稱。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 進行新開發，已知情況下會發生您必須在此隱藏此規則的警告。 傳送文件庫，您可能要隱藏此規則的警告。  
  
## <a name="related-rules"></a>相關的規則  
 [CA1709：識別項名稱應該使用正確的大小寫](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708：識別項名稱不應該只靠大小寫區別](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
 [CA1707：識別項名稱不應該包含底線](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)