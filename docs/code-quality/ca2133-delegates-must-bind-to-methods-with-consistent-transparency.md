---
title: CA2133：委派必須繫結至透明度一致的方法
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2133
ms.assetid: a09672e2-63cb-4abd-9e8f-dff515e101ce
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 389de424c3d9e2cd0e12431e857983b267213f9c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31920915"
---
# <a name="ca2133-delegates-must-bind-to-methods-with-consistent-transparency"></a>CA2133：委派必須繫結至透明度一致的方法
|||
|-|-|
|TypeName|DelegatesMustBindWithConsistentTransparency|
|CheckId|CA2133|
|分類|Microsoft.Security|
|中斷變更|中斷|

> [!NOTE]
>  這個警告只會套用至執行 CoreCLR （Silverlight Web 應用程式特有的 clr 版本） 的程式碼中。

## <a name="cause"></a>原因
 標記與委派繫結的方法會引發此警告<xref:System.Security.SecurityCriticalAttribute>透明或標記的方法<xref:System.Security.SecuritySafeCriticalAttribute>。 此警告也會引發將透明或安全關鍵性的委派繫結至關鍵方法的方法。

## <a name="rule-description"></a>規則描述
 委派型別和它們繫結至的方法必須一致的透明度。 透明和安全關鍵委派可能只能繫結至其他透明或安全關鍵方法。 同樣地，關鍵委派可能只能繫結至關鍵方法。 這些繫結規則可確保只可以叫用方法，以透過委派的程式碼可能有也叫用的相同方法直接。 例如，繫結規則防止透明的程式碼呼叫關鍵程式碼直接透過透明的委派。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正這個警告的違規情形，變更其繫結，讓兩個透明度是相等的方法或委派的透明度。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Security.CA2133.DelegatesMustBindWithConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2133-delegates-must-bind-to-methods-with-consistent-transparency_1.cs)]