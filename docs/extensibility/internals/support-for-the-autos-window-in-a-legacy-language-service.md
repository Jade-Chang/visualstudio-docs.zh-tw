---
title: 支援舊版語言服務中的 [自動變數] 視窗 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], Autos window
- Autos window, supporting in language services [managed package framework]
ms.assetid: 47d40aae-7a3c-41e1-a949-34989924aefb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a1a2627bd36e6047db00afaada231dc49cde2cc3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="support-for-the-autos-window-in-a-legacy-language-service"></a>支援舊版語言服務中的 [自動變數] 視窗
**自動變數**視窗會顯示運算式，例如變數和參數的範圍內時進行偵錯的程式已暫停 （可能是因為中斷點或例外狀況）。 運算式可以包含變數，本機或全域和區域範圍中已變更的參數。 **自動變數**視窗也可以包含的類別、 結構或其他類型具現化。 任何可以評估的運算式評估工具的項目可能會顯示在**自動變數**視窗。  
  
 Managed 的 package framework (MPF) 不提供直接支援**自動變數**視窗。 不過，如果您覆寫<xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A>方法，您可以傳回的運算式，以顯示在清單**自動變數**視窗。  
  
## <a name="implementing-support-for-the-autos-window"></a>實作支援 [自動變數] 視窗  
 您需要支援**自動變數**視窗是實作<xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A>方法中的<xref:Microsoft.VisualStudio.Package.LanguageService>類別。 您的實作必須決定指定的位置，以在來源檔案中，運算式應該會出現在**自動變數**視窗。 方法會傳回的字串，其中每個字串代表單一運算式清單。 傳回值為<xref:Microsoft.VisualStudio.VSConstants.S_OK>指出清單是否包含運算式，而<xref:Microsoft.VisualStudio.VSConstants.S_FALSE>表示沒有要顯示運算式。  
  
 傳回實際的運算式是變數或參數，都會出現在程式碼中的該位置的名稱。 這些名稱會傳遞給運算式評估工具，若要取得的值和類型，然後顯示在**自動變數**視窗。  
  
### <a name="example"></a>範例  
 下列範例示範實作<xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A>方法，以取得運算式從一份<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>方法使用剖析原因<xref:Microsoft.VisualStudio.Package.ParseReason>。 每個運算式做為包裝`TestVsEnumBSTR`實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsEnumBSTR>介面。  
  
 請注意，`GetAutoExpressionsCount`和`GetAutoExpression`方法都是自訂的方法上`TestAuthoringSink`物件，並已加入以支援這個範例。 它們代表新增至哪一個運算式中的一種方式`TestAuthoringSink`剖析器的物件 (藉由呼叫<xref:Microsoft.VisualStudio.Package.AuthoringSink.AutoExpression%2A>方法) 剖析器外部存取。  
  
```csharp  
using Microsoft.VisualStudio;  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        public override int GetProximityExpressions(IVsTextBuffer buffer,  
                                                    int line,  
                                                    int col,  
                                                    int cLines,  
                                                    out IVsEnumBSTR ppEnum)  
        {  
            int retval = VSConstants.E_NOTIMPL;  
            ppEnum = null;  
            if (buffer != null)  
            {  
                IVsTextLines textLines = buffer as IVsTextLines;  
                if (textLines != null)  
                {  
                    Source src = this.GetSource(textLines);  
                    if (src != null)  
                    {  
                        TokenInfo tokenInfo = new TokenInfo();  
                        string text = src.GetText();  
                        ParseRequest req = CreateParseRequest(src,  
                                                              line,  
                                                              col,  
                                                              tokenInfo,  
                                                              text,  
                                                              src.GetFilePath(),  
                                                              ParseReason.Autos,  
                                                              null);  
                        req.Scope = this.ParseSource(req);  
                        TestAuthoringSink sink = req.Sink as TestAuthoringSink;  
  
                        retval = VSConstants.S_FALSE;  
                        int spanCount = sink.GetAutoExpressionsCount();  
                        if (spanCount > 0) {  
                            TestVsEnumBSTR bstrList = new TestVsEnumBSTR();  
                            for (int i = 0; i < spanCount; i++)  
                            {  
                                TextSpan span;  
                                sink.GetAutoExpression(i, out span);  
                                string expression = src.GetText(span.iStartLine,  
                                                                span.iStartIndex,  
                                                                span.iEndLine,  
                                                                span.iEndIndex);  
                                bstrList.AddString(expression);  
                            }  
                            ppEnum = bstrList;  
                            retval = VSConstants.S_OK;  
                        }  
                    }  
                }  
            }  
            return retval;  
        }  
    }  
}  
```