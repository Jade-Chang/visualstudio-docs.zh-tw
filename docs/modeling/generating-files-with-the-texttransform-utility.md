---
title: 使用 TextTransform 公用程式，Visual Studio 中產生檔案
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- text templates, TextTransform utility
- TextTransform.exe
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 065d9e23a8ae8b5e328786bb195d191df1388abb
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="generate-files-with-the-texttransform-utility"></a>產生使用 TextTransform 公用程式的檔案

TextTransform.exe 是命令列工具可讓您轉換文字範本。 當您呼叫 TextTransform.exe 時，您可以指定文字範本檔的名稱做為引數。 TextTransform.exe 呼叫文字轉換引擎，並處理文字範本。 TextTransform.exe 通常會從指令碼呼叫。 不過，它不是通常是必要的因為您可以在 Visual Studio 中或在建置流程中執行文字轉換。

> [!NOTE]
> 如果您想要執行文字轉換做為建置流程的一部分，請考慮使用 MSBuild 文字轉換工作。 如需詳細資訊，請參閱[建置流程中的程式碼產生](../modeling/code-generation-in-a-build-process.md)。 所在的電腦中[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]已安裝，您也可以撰寫應用程式或[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]可以轉換文字範本的副檔名。 如需詳細資訊，請參閱[使用自訂主機處理文字範本](../modeling/processing-text-templates-by-using-a-custom-host.md)。

 TextTransform.exe 位於下列目錄：

 **\Program Files (x86)\Microsoft Visual Studio\2017\Professional\Common7\IDE**

Professional edition 中，或

 **\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE**

 針對 Enterprise edition。

在舊版的 Visual Studio 中，檔案位於下列位置：

**\Program Files (x86)\Common Files\Microsoft Shared\TextTemplating\{version}**

其中，{版本} 取決於所安裝的先前版本。

## <a name="syntax"></a>語法

```
TextTransform [<options>] <templateName>
```

### <a name="parameters"></a>參數

|**引數**|**描述**|
|------------------|---------------------|
|`templateName`|識別您想要轉換的範本檔案的名稱。|

|**選項**|**描述**|
|----------------|---------------------|
|**-out** \<filename>|要轉換的輸出寫入檔案。|
|**-r** \<assembly>|用於編譯和執行文字範本的組件。|
|**-u** \<namespace>|用來編譯範本命名空間。|
|**-I** \<includedirectory>|包含指定的文字範本中所包含的文字範本的目錄。|
|**-P** \<重新整理路徑 >|若要搜尋的文字範本中指定的組件，或是使用目錄 **-r**選項。<br /><br /> 例如，若要包含使用 Visual Studio API 的組件，使用<br /><br /> `-P "%VSSHELLFOLDER%\Common7\IDE\PublicAssemblies"`|
|**-dp** \<processorName>!\<className>!\<assemblyName&#124;codeBase>|名稱、 完整型別名稱和組件可以用來處理自訂指示詞的文字範本中的指示詞處理器。|
|**-a** [processorName]![directiveName]!\<parameterName>!\<parameterValue>|指定指示詞處理器的參數值。 如果您指定參數名稱和值，此參數可指示詞的所有處理器。 如果您指定指示詞處理器，參數是僅適用於指定的處理器。 如果您指定指示詞的名稱，參數才可使用正在處理指定的指示詞。<br /><br /> 若要存取的參數值，指示詞處理器或文字範本中，使用[ITextTemplatingEngineHost.ResolveParameterValue](https://msdn.microsoft.com/library/microsoft.visualstudio.texttemplating.itexttemplatingenginehost.resolveparametervalue.aspx)。 在文字範本中，包括`hostspecific`範本指示詞中，並在叫用訊息`this.Host`。 例如: <br /><br /> `<#@template language="c#" hostspecific="true"#> [<#= this.Host.ResolveParameterValue("", "", "parameterName") #>]`.<br /><br /> 一律使用類型 '！' 標記，即使您省略選擇性的處理器和指示詞名稱。 例如: <br /><br /> `-a !!param!value`|
|**-h**|提供說明。|

## <a name="related-topics"></a>相關主題

|工作|主題|
|----------|-----------|
|在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 方案中產生檔案。|[使用 T4 文字範本在設計階段產生程式碼](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|
|撰寫指示詞處理器，以轉換您專屬的資料來源。|[自訂 T4 文字轉換](../modeling/customizing-t4-text-transformation.md)|
|撰寫文字範本化主應用程式，可讓您叫用您自己的應用程式從文字範本。|[使用自訂主機處理文字範本](../modeling/processing-text-templates-by-using-a-custom-host.md)|