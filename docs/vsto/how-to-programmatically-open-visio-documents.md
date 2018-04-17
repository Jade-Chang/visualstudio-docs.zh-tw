---
title: 如何： 以程式設計方式開啟 Visio 文件 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], opening Visio documents
- Visio [Office development in Visual Studio], opening Visio documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b5a837b4b12420c65817b6dfb156e0fe47fcdba6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-open-visio-documents"></a>如何：以程式設計方式開啟 Visio 文件
  有兩種方法來開啟現有的 Microsoft Office Visio 文件： 開啟和 OpenEx。 OpenEx 方法等於開啟方法，不同之處在於它會提供引數中的呼叫端指定文件開啟的方式。  
  
 如需此物件模型的詳細資訊，請參閱 [Microsoft.Office.Interop.Visio.Documents.Open](https://msdn.microsoft.com/library/office/ff765240.aspx) 方法和 [Microsoft.Office.Interop.Visio.Documents.OpenEx](https://msdn.microsoft.com/library/office/ff767229.aspx) 方法的 VBA 參考文件。  
  
## <a name="opening-a-visio-document"></a>開啟 Visio 文件  
  
#### <a name="to-open-a-visio-document"></a>開啟 Visio 文件  
  
-   呼叫 Microsoft.Office.Interop.Visio.Documents.Open 方法，並提供 Visio 文件的完整的路徑。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#5)]  
  
## <a name="opening-a-visio-document-with-specified-arguments"></a>以指定的引數開啟 Visio 文件  
  
#### <a name="to-open-a-visio-document-as-read-only-and-docked"></a>開啟 Visio 文件為唯讀並停駐  
  
-   呼叫 Microsoft.Office.Interop.Visio.Documents.OpenEx 方法，提供 Visio 文件的完整的路徑，並包含您想要使用的引數，在本例中，停駐 」 和 「 唯讀狀態。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#6)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個程式碼範例需要下列項目：  
  
-   [我的文件] 資料夾 (Windows XP 及更早版本) 或 [文件] 資料夾 (Windows Vista) 中，名為 `myDrawing.vsd` 的目錄中必須有名為 `Test` 的 Visio 文件。  
  
## <a name="see-also"></a>另請參閱  
 [Visio 方案](../vsto/visio-solutions.md)   
 [Visio 物件模型概觀](../vsto/visio-object-model-overview.md)   
 [如何： 以程式設計方式建立新的 Visio 文件](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [如何： 以程式設計方式關閉 Visio 文件](../vsto/how-to-programmatically-close-visio-documents.md)   
 [如何： 以程式設計方式儲存 Visio 文件](../vsto/how-to-programmatically-save-visio-documents.md)   
 [如何：以程式設計方式列印 Visio 文件](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  