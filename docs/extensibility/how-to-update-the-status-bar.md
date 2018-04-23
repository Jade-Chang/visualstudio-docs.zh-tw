---
title: 如何： 更新狀態列 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - update status bar
ms.assetid: 7500c8a7-4913-4818-a88b-bfd1b9887cb6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1b5f7e6849736f0fc226c51f69a1526aca8e971a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-update-the-status-bar"></a>如何： 更新狀態列
**狀態列**一種控制列位於包含一或多個狀態的文字行或指標許多應用程式視窗的下方。  
  
### <a name="to-update-the-status-bar"></a>若要更新 [狀態] 列  
  
1.  實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>提供您的編輯器，例如表單檢視和程式碼檢視每個個別的檢視物件 (DocView)。  
  
2.  當 IDE 呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>，更新中的資訊**狀態列**藉由呼叫的方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>。  
  
    > [!NOTE]
    >  IDE 呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>只有當文件視窗一開始啟動。 文件視窗是作用中的時間的其餘部分，您必須更新**狀態列**編輯器變更的狀態資訊。  
  
## <a name="robust-programming"></a>穩固程式設計  
 A**狀態列**包含四個個別欄位：  
  
-   狀態文字  
  
-   進度列  
  
-   動畫的圖示  
  
-   編輯器資訊  
  
 如需詳細資訊，請參閱[狀態列](/cpp/mfc/status-bars)。  
  
 IDE 會自動呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>方法您<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>當啟動文件視窗的實作。  
  
 VSPackage 實作器會負責更新狀態列中的狀態文字。 IDE 在 [狀態] 文字欄位設定為空的文字時，會重設 「 就緒 」 這個字串 ("") 在閒置的時間。  
  
## <a name="see-also"></a>另請參閱  
 [狀態列](/cpp/mfc/status-bars)