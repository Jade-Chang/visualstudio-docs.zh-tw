---
title: "逐步解說： 從編輯器延伸模組存取 DTE 物件 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: af14fa5f9a76e08a1fba3355e9391ce8229bd652
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-accessing-the-dte-object-from-an-editor-extension"></a>逐步解說： 從編輯器延伸模組存取 DTE 物件
在 Vspackage 中，您可以藉由呼叫取得 DTE 物件<xref:Microsoft.VisualStudio.Shell.Package.GetService%2A>DTE 物件的型別方法。 在 Managed Extensibility Framework (MEF) 擴充功能，您可以匯入<xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>，然後呼叫<xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A>具有一種方法<xref:EnvDTE.DTE>。  
  
## <a name="prerequisites"></a>必要條件  
 若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 如需詳細資訊，請參閱[Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  
  
## <a name="getting-the-dte-object"></a>取得 DTE 物件  
  
#### <a name="to-get-the-dte-object-from-the-serviceprovider"></a>若要從 ServiceProvider 取得 DTE 物件  
  
1.  C# VSIX 專案建立一個名為`DTETest`。 加入編輯器分類器項目範本並將其命名`DTETest`。 如需詳細資訊，請參閱[編輯器項目範本以建立擴充](../extensibility/creating-an-extension-with-an-editor-item-template.md)。  
  
2.  加入下列組件參考加入專案：  
  
    -   EnvDTE  
  
    -   EnvDTE80  
  
    -   Microsoft.VisualStudio.Shell.Immutable.10.0  
  
3.  請移至 DTETest.cs 檔案，並加入下列`using`指示詞：  
  
    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    using Microsoft.VisualStudio.Shell;  
  
    ```  
  
4.  在`GetDTEProvider`類別中，匯入<xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>。  
  
    ```csharp  
    [Import]  
    internal SVsServiceProvider ServiceProvider = null;  
  
    ```  
  
5.  在 `GetClassifier()` 方法中，加入下列程式碼。  
  
    ```csharp  
    DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));  
  
    ```  
  
6.  如果您必須使用<xref:EnvDTE80.DTE2>介面，您可以將 DTE 物件轉換成它。  
  
## <a name="see-also"></a>請參閱  
 [語言服務及編輯器擴充點](../extensibility/language-service-and-editor-extension-points.md)