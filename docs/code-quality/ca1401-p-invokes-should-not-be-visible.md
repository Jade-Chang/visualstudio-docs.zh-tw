---
title: 'CA1401: P 叫用不應該為可見'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PInvokesShouldNotBeVisible
- CA1401
helpviewer_keywords:
- CA1401
- PInvokesShouldNotBeVisible
ms.assetid: 0f4d96c1-f9de-414e-b223-4dc7f691bee3
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c2aaadb0570e47e5ef41614925c20f8dc30f1620
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="ca1401-pinvokes-should-not-be-visible"></a>CA1401：P/Invokes 不應該為可見的
|||
|-|-|
|TypeName|PInvokesShouldNotBeVisible|
|CheckId|CA1401|
|分類|Microsoft.Interoperability|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用或受保護的方法中的公用型別具有<xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>屬性 (也是由實作`Declare`關鍵字[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)])。

## <a name="rule-description"></a>規則描述
 方法是，標示<xref:System.Runtime.InteropServices.DllImportAttribute>屬性 (或您可以使用定義的方法`Declare`關鍵字[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) 用於存取 unmanaged 程式碼的平台叫用服務。 但不得公開 (Expose) 此類方法。 私用或內部，請保留這些方法，您確定您的程式庫無法用於安全性破壞所允許的存取權，他們無法呼叫 unmanaged Api 的呼叫端。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，變更方法的存取層級。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例會宣告方法違反此規則。

 [!code-vb[FxCop.Interoperability.DllImports#1](../code-quality/codesnippet/VisualBasic/ca1401-p-invokes-should-not-be-visible_1.vb)]
 [!code-csharp[FxCop.Interoperability.DllImports#1](../code-quality/codesnippet/CSharp/ca1401-p-invokes-should-not-be-visible_1.cs)]