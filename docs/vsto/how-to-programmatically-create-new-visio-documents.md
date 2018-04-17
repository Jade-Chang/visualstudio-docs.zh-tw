---
title: 如何： 以程式設計方式建立新的 Visio 文件 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], creating Visio documents
- documents [Office development in Visual Studio], creating Visio documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e2dd64b2996df4ed75cd45cd741619658f9b3654
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-create-new-visio-documents"></a>如何：以程式設計方式建立新的 Visio 文件
  當您建立新的 Microsoft Office Visio 繪圖文件時，您會將它加入 Microsoft.Office.Interop.Visio.Documents 開啟 Visio 文件的集合。 因此，Microsoft.Office.Interop.Visio.Documents.Add 方法會建立新的 Visio 繪圖文件。 如需詳細資訊，請參閱 Microsoft.Office.Interop.Visio.Documents.Add [myTemplate.vst](http://msdn.microsoft.com/library/office/ff766868.aspx) 方法的 VBA 參考文件。  
  
## <a name="creating-new-blank-documents"></a>建立新的空白文件  
  
#### <a name="to-create-a-new-document"></a>建立新文件  
  
-   使用 Microsoft.Office.Interop.Visio.Documents.Add 方法建立新的空白文件不是以範本為基礎。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#1](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#1)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#1](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#1)]  
  
## <a name="creating-documents-copied-from-existing-documents"></a>建立從現有文件複製的文件  
 Microsoft.Office.Interop.Visio.Documents.Add 方法可以建立現有 Visio 文件的複本的新文件。 您必須提供圖表的檔案名稱和完整路徑。  
  
#### <a name="to-create-a-new-document-that-is-copied-from-an-existing-document"></a>建立從現有文件複製的新文件  
  
-   呼叫 Microsoft.Office.Interop.Visio.Documents.Add 方法，並指定 Visio 圖表的路徑。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#2](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#2)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#2](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#2)]  
  
## <a name="creating-stencils-copied-from-existing-stencils"></a>建立從現有樣板複製的樣板  
 Microsoft.Office.Interop.Visio.Documents.Add [myTemplate.vst](http://msdn.microsoft.com/library/office/ff766868.aspx) 方法可建立現有 Visio 樣板複本的新樣板。 您必須提供樣板的檔案名稱和完整路徑。  
  
#### <a name="to-create-a-new-stencil-that-is-copied-from-an-existing-stencil"></a>建立從現有樣板複製的新樣板  
  
-   呼叫 Microsoft.Office.Interop.Visio.Documents.Add 方法，並指定樣板的路徑。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#3](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#3](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#3)]  
  
## <a name="creating-documents-based-on-existing-templates"></a>建立以現有範本為基礎的文件  
 Microsoft.Office.Interop.Visio.Documents.Add 方法可以建立新文件 （.vsd 檔案） 為基礎的現有 Visio 範本 （.vst 檔案）。 這個方法會複製屬於範本工作區一部分的樣板、樣式和設定。 您必須提供範本的檔案名稱和完整路徑。  
  
#### <a name="to-create-a-new-document-that-is-based-on-an-existing-template"></a>建立以現有範本為基礎的新文件  
  
-   呼叫 Microsoft.Office.Interop.Visio.Documents.Add 方法，並指定範本的路徑。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#4](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#4)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#4](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#4)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個程式碼範例需要下列項目：  
  
-   [我的文件] 資料夾 (Windows XP 及更早版本) 或 [文件] 資料夾 (Windows Vista) 中，名為 `myDrawing.vsd` 的目錄中必須有名為 `Test` 的 Visio 文件。  
  
-   [我的文件] 資料夾 (Windows XP 及更早版本) 或 [文件] 資料夾 (Windows Vista) 中，名為 `myStencil.vss` 的目錄中必須有名為 `Test` 的 Visio 文件。  
  
-   [我的文件] 資料夾 (Windows XP 及更早版本) 或 [文件] 資料夾 (Windows Vista) 中，名為 `myTemplate.vst` 的目錄中必須有名為 `Test` 的 Visio 文件。  
  
## <a name="see-also"></a>另請參閱  
 [Visio 方案](../vsto/visio-solutions.md)   
 [Visio 物件模型概觀](../vsto/visio-object-model-overview.md)   
 [如何： 以程式設計方式開啟 Visio 文件](../vsto/how-to-programmatically-open-visio-documents.md)   
 [如何： 以程式設計方式關閉 Visio 文件](../vsto/how-to-programmatically-close-visio-documents.md)   
 [如何： 以程式設計方式儲存 Visio 文件](../vsto/how-to-programmatically-save-visio-documents.md)   
 [如何：以程式設計方式列印 Visio 文件](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  