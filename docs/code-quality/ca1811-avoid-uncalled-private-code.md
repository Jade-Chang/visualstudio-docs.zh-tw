---
title: CA1811：避免使用未呼叫的私用程式碼
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidUncalledPrivateCode
- CA1811
helpviewer_keywords:
- CA1811
- AvoidUncalledPrivateCode
ms.assetid: aadbba74-7821-475f-8980-34d17c0a0a8b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d7f31b27740b286065221838e733d99e94b3307d
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="ca1811-avoid-uncalled-private-code"></a>CA1811：避免使用未呼叫的私用程式碼
|||
|-|-|
|TypeName|AvoidUncalledPrivateCode|
|CheckId|CA1811|
|分類|Microsoft.Performance|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 私用或內部 （組件層級） 成員並沒有呼叫端組件中，common language runtime 不會叫用而不會透過委派叫用。 此規則不會檢查下列成員：

-   明確介面成員。

-   靜態建構函式。

-   序列化建構函式。

-   標記為<xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName>或<xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>。

-   會覆寫的成員。

## <a name="rule-description"></a>規則描述
 此規則可報告的進入點會在發生的誤判不會目前識別規則邏輯。 此外，編譯器可能會發出 noncallable 的程式碼的組件。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，移除 noncallable 或程式碼加入程式碼呼叫它。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 它可以安全地隱藏此規則的警告。

## <a name="related-rules"></a>相關的規則
 [CA1812：避免使用未執行個體化的內部類別](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801：必須檢閱未使用的參數](../code-quality/ca1801-review-unused-parameters.md)

 [CA1804：必須移除未使用的區域變數](../code-quality/ca1804-remove-unused-locals.md)