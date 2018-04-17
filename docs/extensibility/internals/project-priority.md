---
title: 專案優先順序 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: 9f707592-2fb6-4f75-9269-f6d4700a998e
caps.latest.revision: 11
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: ae692249ea952970b096825c8f6968158eb2f17f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="project-priority"></a>專案優先順序
專案項目通常是在方案中只能有一個專案的成員。 因此，在 IDE 可以輕易地判斷哪一個專案用來開啟項目中。 不過，如果項目是多個專案的成員，IDE 會使用優先順序配置來判斷最佳的專案開啟的項目。  
  
 下列清單會顯示專案優先順序的架構：  
  
-   IDE 呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A>方法來判斷文件是否為成員，該專案的方案中每個專案。  
  
-   如果文件是專案的成員，專案會回應優先順序的專案會指派它的處理該文件的根據。 比方說，語言專案會有高的優先權，其語言原始程式檔以回應，但無法識別的檔案類型不是做為其建置流程的一部分，較低優先順序的回應。  
  
-   提供自訂的專案特定的編輯器或設計工具的文件的專案也會收到有高的優先權。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>列舉型別提供文件的優先權值。  
  
-   指定的最高優先順序的專案會指定要開啟的文件的內容。 如果兩個專案會傳回相同的優先順序值，請在作用中專案是慣用。 如果方案中沒有專案回應，它可以開啟文件，IDE 會將文件放在其他檔案專案中。 如需詳細資訊，請參閱[其他檔案專案](../../extensibility/internals/miscellaneous-files-project.md)。  
  
## <a name="see-also"></a>請參閱  
 [其他檔案專案](../../extensibility/internals/miscellaneous-files-project.md)   
 [如何： 開啟編輯器開啟的文件](../../extensibility/how-to-open-editors-for-open-documents.md)   
 [新增專案與專案項目範本](../../extensibility/internals/adding-project-and-project-item-templates.md)