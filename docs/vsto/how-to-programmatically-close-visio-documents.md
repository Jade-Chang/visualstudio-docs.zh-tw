---
title: 如何： 以程式設計方式關閉 Visio 文件 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], closing Visio documents
- Visio [Office development in Visual Studio], closing Visio documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 314d8e5bfd40e1e45d4795a6e4523db19124741a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-close-visio-documents"></a>如何：以程式設計方式關閉 Visio 文件
  您可以使用 Microsoft.Office.Interop.Visio.Document.Close 方法來關閉使用中的 Microsoft Office Visio 文件。  
  
 如需這個方法的詳細資訊，請參閱 [Microsoft.Office.Interop.Visio.Document.Close](http://msdn.microsoft.com/library/office/ff767415.aspx) 方法的 VBA 參考文件。  
  
## <a name="closing-the-active-document"></a>關閉使用中的文件  
  
#### <a name="to-close-the-active-document"></a>關閉使用中的文件  
  
-   呼叫 Microsoft.Office.Interop.Visio.Document.Close 方法來關閉使用中文件。  
  
     若要使用下列程式碼範例，請在 Visio VSTO 增益集專案的 `ThisAddIn` 類別中執行程式碼。  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#7)]  
  
## <a name="see-also"></a>另請參閱  
 [Visio 方案](../vsto/visio-solutions.md)   
 [Visio 物件模型概觀](../vsto/visio-object-model-overview.md)   
 [如何： 以程式設計方式建立新的 Visio 文件](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [如何： 以程式設計方式開啟 Visio 文件](../vsto/how-to-programmatically-open-visio-documents.md)   
 [如何： 以程式設計方式儲存 Visio 文件](../vsto/how-to-programmatically-save-visio-documents.md)   
 [如何：以程式設計方式列印 Visio 文件](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  