---
title: 如何：使用逸出序列從範本產生範本
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, generating templates from templates
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 13ca6a9aef2f0944ba1f42c849d9f8079a56a82b
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31947478"
---
# <a name="how-to-generate-templates-from-templates-by-using-escape-sequences"></a>如何：使用逸出序列從範本產生範本
您可以建立可建立另一個文字範本產生的文字輸出的文字範本。 若要這樣做，您必須使用逸出序列來描述文字範本標記。 如果您不使用逸出序列，產生的文字範本必須預先定義的意義。 如需在文字範本中使用逸出序列的詳細資訊，請參閱[文字範本中使用逸出序列](../modeling/using-escape-sequences-in-text-templates.md)。

### <a name="to-generate-a-text-template-from-within-a-text-template"></a>若要產生的文字範本內從文字範本

-   使用反斜線 (\\) 做為逸出字元，以產生必要的標記內的標記文字範本指示詞、 陳述式、 運算式和類別中的個別文字範本檔案的功能。

    ```
    \<#@ directive \#>
    \<# statement \#>
    \<#= expression \#>
    \<#+ classfeature \#>
    ```

## <a name="example"></a>範例
 下列範例會使用逸出字元來產生文字範本，從文字範本。 `output`指示詞設定目的地檔案類型為文字範本的檔案類型 (.tt)。

```csharp
\<#@ output extension=".tt" \#>
\<#@ assembly name="System.Xml.dll" \#>
\<#@ import namespace="System.Xml" \#>
\<#
XmlDocument xDoc = new XmlDocument();
//System.Diagnostics.Debugger.Break();
    xDoc.Load(@"E:\CSharp\Overview.xml");
    XmlAttributeCollection attributes = xDoc.Attributes;
    if (attributes != null)
    {
       foreach (XmlAttribute attr in attributes)
       {\#>
           \<#= attr.Name \#>
       \<#}
     }
\#>
```

 產生的文字輸出是以文字範本。

```
<#@ output extension=".tt" #>
<#@ assembly name="System.Xml.dll" #>
<#@ import namespace="System.Xml" #>
<#
XmlDocument xDoc = new XmlDocument();
//System.Diagnostics.Debugger.Break();
    xDoc.Load(@"E:\CSharp\Overview.xml");
    XmlAttributeCollection attributes = xDoc.Attributes;
    if (attributes != null)
    {
       foreach (XmlAttribute attr in attributes)
       {#>
           <#= attr.Name #>
       <#}
     }
#>
```