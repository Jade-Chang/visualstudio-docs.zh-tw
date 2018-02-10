---
title: "程式碼分析，Managed 程式碼的概觀 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.projectpropertypages.codeanalysis
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 5d30f84194ef7a48de106698c9ad4569e947923c
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="code-analysis-for-managed-code-overview"></a>程式碼分析 managed 程式碼的概觀

Managed 程式碼的程式碼分析可以分析 Managed 組件並回報有關組件的資訊，例如是否違反 Microsoft .NET Framework 設計方針所制定的程式設計和設計規則。

分析工具會將分析期間所做的檢查顯示為警告訊息。 警告訊息會識別任何相關的程式設計和設計問題，並且在可能的時候，提供如何修正問題的資訊。

## <a name="ide-integrated-development-environment-integration"></a>IDE （整合式的開發環境） 整合

您可以手動或自動執行您的專案程式碼分析。

若要建立專案時，您每次執行程式碼分析，選取**建置時啟用程式碼分析**專案屬性頁上。 如需詳細資訊，請參閱[How to： 啟用和停用自動程式碼分析](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)。

若要手動執行程式碼分析的專案上，從功能表列選擇**分析** > **執行程式碼分析** > **上執行程式碼分析<project>** . 如需詳細資訊，請參閱[How to： 啟用和停用自動程式碼分析](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)。

## <a name="rule-sets"></a>規則集

Managed 程式碼的程式碼分析規則分組為*規則集*。 您可以使用其中一個 Microsoft 標準規則集，或建立自訂規則集來滿足特定需求。 如需詳細資訊，請參閱[使用規則集分組程式碼分析規則](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)。

## <a name="suppress-warnings"></a>隱藏警告

最大的用途是指出某個警告不適用。 這會通知程式開發人員和其他稍後可能會檢閱程式碼的人員，指出您已經調查此警告並且隱藏或忽略它。

在原始程式檔的警告的隱藏項目是透過自訂屬性來實作。 若要隱藏警告，請將 `SuppressMessage` 屬性加入至原始程式碼，如下列範例所示：

```csharp
[System.Diagnosis.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]
Public class MyClass
{
   // code
}
```

如需詳細資訊，請參閱[隱藏的警告，](../code-quality/in-source-suppression-overview.md)。

> [!NOTE]
> 如果您將專案移轉至 Visual Studio 2017 時，可能會突然面臨著產生大量的程式碼分析警告。 如果您不可以修正警告，並想要暫時關閉程式碼分析，請開啟專案屬性頁 (**專案** > ***專案*屬性...**)，並移至**程式碼分析** 索引標籤。取消選取**建置時啟用程式碼分析**，然後重建您的專案。 或者，您可以選取不同的小型規則集執行程式碼。 請記得在當您準備好修正警告的程式碼分析。

## <a name="run-code-analysis-as-part-of-check-in-policy"></a>執行程式碼分析做為簽入原則的一部分

從組織的角度來看，您可能想指定所有的簽入都要滿足特定的原則， 尤其您會想要確認您已經確實遵循這些原則：

- 正在簽入程式碼中有任何建置錯誤。

- 執行程式碼分析做為最新組建的一部分。

您可以指定簽入原則，達成上述要求。 如需詳細資訊，請參閱[使用 Team 專案簽入原則強化程式碼品質](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)。

## <a name="team-build-integration"></a>Team build 整合

您可以使用建置系統的整合式功能，執行分析工具做為建置流程的一部分。 如需詳細資訊，請參閱[組建與版本 (VSTS)](/vsts/build-release/index)。

## <a name="see-also"></a>另請參閱

[使用規則集分組程式碼分析規則](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)   
[如何： 啟用和停用自動程式碼分析](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
