---
title: CA2130：安全性關鍵常數應該是透明的
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2130
ms.assetid: 344c7f7b-9130-4675-ae7f-9fa260cc9789
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 999a4a15dd83db66365bc9ee3701fd3130cedeb1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31914350"
---
# <a name="ca2130-security-critical-constants-should-be-transparent"></a>CA2130：安全性關鍵常數應該是透明的
|||
|-|-|
|TypeName|ConstantsShouldBeTransparent|
|CheckId|CA2130|
|分類|Microsoft.Security|
|中斷變更|中斷|

## <a name="cause"></a>原因
 常數欄位或列舉的成員會標示<xref:System.Security.SecurityCriticalAttribute>。

## <a name="rule-description"></a>規則描述
 因為編譯器內嵌常數的值，所以沒有針對常數值強制透明度，因此在執行階段不需要查詢。 常數欄位應該具備安全性透明，程式碼檢閱者才不會假設透明程式碼無法存取常數。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請從欄位或值移除 SecurityCritical 屬性。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 在下列範例中，列舉值`EnumWithCriticalValues.CriticalEnumValue`和常數`CriticalConstant`引發此警告。 若要修正問題，請移除 [`SecurityCritical`]，使其安全性透明的屬性。

 [!code-csharp[FxCop.Security.CA2130.ConstantsShouldBeTransparent#1](../code-quality/codesnippet/CSharp/ca2130-security-critical-constants-should-be-transparent_1.cs)]