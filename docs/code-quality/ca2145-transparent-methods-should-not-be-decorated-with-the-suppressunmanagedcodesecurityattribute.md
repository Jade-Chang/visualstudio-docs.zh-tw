---
title: CA2145： 透明方法不應該使用 SuppressUnmanagedCodeSecurityAttribute 裝飾 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2145
ms.assetid: 81970700-b438-4b3b-9239-16887e16f7b7
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2c6fcfc32dc8ab8a90ea555f43c253a5d93e72a3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute"></a>CA2145：透明方法不可以使用 SuppressUnmanagedCodeSecurityAttribute 來裝飾
|||  
|-|-|  
|TypeName|TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity|  
|CheckId|CA2145|  
|分類|Microsoft.Security|  
|中斷變更|中斷|  
  
## <a name="cause"></a>原因  
 透明方法，以標記的方法<xref:System.Security.SecuritySafeCriticalAttribute>方法或包含一種方法的類型會標示<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>屬性。  
  
## <a name="rule-description"></a>規則描述  
 方法使用裝飾<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>屬性有任何方法呼叫它時放置隱含的 LinkDemand。 這個 LinkDemand 會要求呼叫程式碼具備安全性關鍵。 標記使用 SuppressUnmanagedCodeSecurity 的方法<xref:System.Security.SecurityCriticalAttribute>屬性使這個需求更為明顯呼叫端的方法。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，將方法標示，或輸入與<xref:System.Security.SecurityCriticalAttribute>屬性。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
### <a name="code"></a>程式碼  
 [!code-csharp[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../code-quality/codesnippet/CSharp/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute_1.cs)]  
  
### <a name="comments"></a>註解