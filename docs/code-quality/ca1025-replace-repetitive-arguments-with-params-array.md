---
title: Ca1025： 必須以參數陣列取代重複的引數 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1025
- ReplaceRepetitiveArgumentsWithParamsArray
helpviewer_keywords:
- ReplaceRepetitiveArgumentsWithParamsArray
- CA1025
ms.assetid: f009b340-dea3-4459-8fe1-2143aa8b5d0b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a9d42e7109d75f14d51e0e7834bc996f6f8864dc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="ca1025-replace-repetitive-arguments-with-params-array"></a>CA1025：必須以參數陣列取代重複的引數
|||  
|-|-|  
|TypeName|ReplaceRepetitiveArgumentsWithParamsArray|  
|CheckId|CA1025|  
|分類|Microsoft.Design|  
|中斷變更|非中斷|  
  
## <a name="cause"></a>原因  
 公用或受保護的方法中的公用型別有三個以上的參數，且其最後三個參數都是相同的型別。  
  
## <a name="rule-description"></a>規則描述  
 當引數的正確數目未知，且變數引數都是相同的型別，或可以傳遞相同的類型，請使用參數陣列而不是重複的引數。 例如，<xref:System.Console.WriteLine%2A>方法提供一般用途的多載用於接受任意數目的參數陣列<xref:System.Object>引數。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，請以參數陣列取代重複的引數。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 可永遠放心隱藏的警告，這項規則。不過，這項設計可能會導致可用性的問題。  
  
## <a name="example"></a>範例  
 下列範例顯示違反此規則的類型。  
  
 [!code-csharp[FxCop.Design.RepeatArgs#1](../code-quality/codesnippet/CSharp/ca1025-replace-repetitive-arguments-with-params-array_1.cs)]