---
title: CA1307： 指定 StringComparison |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1307
- SpecifyStringComparison
helpviewer_keywords:
- CA1307
- SpecifyStringComparison
ms.assetid: 9b0d5e71-1683-4a0d-bc4a-68b2fbd8af71
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b8d51d55c1528af38c142c115165278503bc50fd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="ca1307-specify-stringcomparison"></a>CA1307：指定 StringComparison
|||  
|-|-|  
|TypeName|SpecifyStringComparison|  
|CheckId|CA1307|  
|分類|Microsoft.Globalization|  
|中斷變更|非中斷|  
  
## <a name="cause"></a>原因  
 字串比較作業使用的方法多載不會設定<xref:System.StringComparison>參數。  
  
## <a name="rule-description"></a>規則描述  
 許多字串作業，最重要<xref:System.String.Compare%2A>和<xref:System.String.Equals%2A>方法，提供可接受的多載<xref:System.StringComparison>做為參數的列舉值。  
  
 每當有多載存在該採用<xref:System.StringComparison>參數，它應該用來取代不接受此參數的多載。 藉由明確設定此參數，通常的程式碼就會較清楚、 更容易維護。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，變更的字串比較方法多載，可接受<xref:System.StringComparison>列舉型別做為參數。 例如： 變更`String.Compare(str1, str2)`至`String.Compare(str1, str2, StringComparison.Ordinal)`。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 它可以安全地隱藏此規則的警告，當程式庫或應用程式適用於有限制的本機使用者，並因此不會當地語系化。  
  
## <a name="see-also"></a>另請參閱  
 [全球化警告](../code-quality/globalization-warnings.md)   
 [CA1309：使用循序的 StringComparison](../code-quality/ca1309-use-ordinal-stringcomparison.md)