---
title: "管理編輯器 中的擴充性架構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - using MEF for extensions
ms.assetid: 3f59a285-6c33-4ae3-a4fb-ec1f5aa21bd1
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 6a5cb0ae0f8da6af939588ad358e6b5b1b3b108e
ms.lasthandoff: 02/22/2017

---
# <a name="managed-extensibility-framework-in-the-editor"></a>在編輯器中的受管理的擴充性架構
使用 Managed Extensibility Framework (MEF) 元件建置編輯器。 您可以建立 MEF 元件，以便擴充編輯器，，而且您的程式碼可以使用編輯器元件。  
  
## <a name="overview-of-the-managed-extensibility-framework"></a>受管理的擴充性架構的概觀  
 MEF 是.NET 程式庫，可讓您加入和修改功能的應用程式或遵循 MEF 程式設計模型的元件。 在 Visual Studio 編輯器可提供和取用 MEF 元件組件。  
  
 MEF 被包含在.NET Framework 第 4 版 System.ComponentModel.Composition.dll 組件。  
  
 如需 MEF 的詳細資訊，請參閱[Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/Library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)。  
  
### <a name="component-parts-and-composition-containers"></a>組件的元件和組合容器  
 元件組件是類別或類別的其中一個 （或兩者） 的下列成員︰  
  
-   使用另一個元件  
  
-   可供另一個元件  
  
 例如，請考慮具有取決於產品可用性資料倉儲的清查元件所提供的訂單項目元件的購物應用程式。 MEF 而言，可以清查一部分*匯出*產品可用性資料和訂單項目組件可以*匯入*資料。 訂單項目和清查部分不需要知道彼此。*組合容器*（由主應用程式提供） 會負責維護組匯出，以及解決匯出和匯入。  
  
 組合容器， <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>，通常由主機所擁有。</xref:System.ComponentModel.Composition.Hosting.CompositionContainer> 組合容器會維護*目錄*匯出的元件組件。  
  
### <a name="exporting-and-importing-component-parts"></a>匯出和匯入組件的元件  
 您可以匯出任何功能，只要它以公用類別或類別 （屬性或方法） 的公用成員實作。 您沒有從<xref:System.ComponentModel.Composition.Primitives.ComposablePart>.</xref:System.ComponentModel.Composition.Primitives.ComposablePart>衍生您的元件組件 相反地，您必須新增<xref:System.ComponentModel.Composition.ExportAttribute>屬性至類別或您想要匯出的類別成員。</xref:System.ComponentModel.Composition.ExportAttribute> 這個屬性會指定*合約*的另一個元件組件可以匯入您的功能。  
  
### <a name="the-export-contract"></a>匯出合約  
 <xref:System.ComponentModel.Composition.ExportAttribute>定義正在匯出的實體 （類別、 介面或結構）。</xref:System.ComponentModel.Composition.ExportAttribute> 一般而言，匯出屬性採用參數，指定匯出的類型。  
  
```  
[Export(typeof(ContentTypeDefinition))]  
class TestContentTypeDefinition : ContentTypeDefinition {   }  
```  
  
 根據預設，<xref:System.ComponentModel.Composition.ExportAttribute>屬性會定義的合約，這種匯出的類別。</xref:System.ComponentModel.Composition.ExportAttribute>  
  
```  
[Export]  
[Name("Structure")]  
[Order(After = "Selection", Before = "Text")]  
class TestAdornmentLayerDefinition : AdornmentLayerDefinition {   }  
```  
  
 在範例中，預設`[Export]`屬性就相當於`[Export(typeof(TestAdornmentLayerDefinition))]`。  
  
 您也可以匯出屬性或方法，如下列範例所示。  
  
```  
[Export]  
[Name("Scarlet")]  
[Order(After = "Selection", Before = "Text")]  
public AdornmentLayerDefinition scarletLayerDefinition;  
```  
  
### <a name="importing-a-mef-export"></a>匯入 MEF 匯出  
 當您想要使用 MEF 匯出時，您必須知道的合約 （通常是型別），它已匯出，以及加入<xref:System.ComponentModel.Composition.ImportAttribute>該值的屬性。</xref:System.ComponentModel.Composition.ImportAttribute> 根據預設，匯入屬性會接受一個參數，也就是它會修改類別的型別。 下列幾行程式碼匯入的<xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>型別。</xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>  
  
```  
[Import]  
internal IClassificationTypeRegistryService ClassificationRegistry;  
```  
  
## <a name="getting-editor-functionality-from-a-mef-component-part"></a>取得從 MEF 元件組件的編輯器功能  
 如果現有的程式碼是 MEF 元件組件，您可以使用組件的元件編輯器使用 MEF 中繼資料。  
  
#### <a name="to-consume-editor-functionality-from-a-mef-component-part"></a>若要使用的 MEF 元件組件的編輯器功能  
  
1.  將參考加入 System.Composition.ComponentModel.dll，也就是在全域組件快取 (GAC)，以及編輯器組件。  
  
2.  新增相關 using 陳述式。  
  
    ```  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text;  
    ```  
  
3.  新增`[Import]`屬性至您的服務介面，如下所示。  
  
    ```  
    [Import]  
    ITextBufferFactoryService textBufferService;  
    ```  
  
4.  當您取得的服務時，您可以使用其中一個元件。  
  
5.  當您編譯組件，將它放入...您的 Visual Studio 安裝 \Common7\IDE\Components\ 資料夾。  
  
## <a name="see-also"></a>另請參閱  
 [語言服務及編輯器擴充點](../extensibility/language-service-and-editor-extension-points.md)