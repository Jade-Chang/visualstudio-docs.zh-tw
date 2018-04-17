---
title: 資訊版權管理和 Managed 程式碼擴充概觀 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Information Rights Management [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- IRM [Office development in Visual Studio]
- documents [Office development in Visual Studio], restricted permissions
- rights management [Office development in Visual Studio]
- Office documents [Office development in Visual Studio, restricted permissions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c70f5667cf7b2d795083589db9d9e4d5ca92193d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="information-rights-management-and-managed-code-extensions-overview"></a>資訊版權管理和 Managed 程式碼擴充概觀
  Microsoft Office Word 和 Microsoft Office Excel 提供的資訊版權管理 (IRM)，可協助防止未經授權的人員檢視或變更敏感資訊的功能。 如需資訊版權管理的運作方式的詳細資訊，請參閱特定 Office 應用程式中的說明。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="running-code-behind-documents-with-restricted-permissions"></a>限制的使用權限以執行文件背後的程式碼  
 如果解決方案包含文件或活頁簿使用 IRM，根據預設，Word 和 Excel 都不允許執行的任何程式碼。 如果您是撰寫的文件，或具有完整控制存取，您可以變更預設值，使您的方案運作方式。 如需詳細資訊，請參閱[如何： 允許程式碼，以執行文件背後以限制使用權限](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)。  
  
 IRM 會防止使用<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ServerDocument>擷取或操作文件中快取的資料。  
  
## <a name="end-users-restricting-permissions-to-documents-that-use-managed-code-extensions"></a>限制使用 Managed 程式碼擴充的文件的權限的使用者  
 能夠完全控制存取文件或活頁簿方案中的任何人都可以使用 IRM 限制權限。 例如，如果終端使用者將會計部門中使用一種解決方案，會自動填入工作表的資料庫中的資料，該使用者可能要允許變更只能存取其部門的人 」 和 「 讀取權限給其他人。 當使用者將限制的使用權限時，根據預設，工作表背後的程式碼無法執行，而且工作表不會填入資料。  
  
 若要修正此問題，具有完整控制存取文件或活頁簿的人員必須變更為允許以程式設計方式存取物件模型的預設權限設定。 如需詳細資訊，請參閱[如何： 允許程式碼，以執行文件背後以限制使用權限](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)。  
  
## <a name="see-also"></a>另請參閱  
 [在文件層級方案中的文件保護](../vsto/document-protection-in-document-level-solutions.md)   
 [Office 文件上的密碼保護](../vsto/password-protection-on-office-documents.md)   
 [保護 Office 方案](../vsto/securing-office-solutions.md)   
 [部署 Office 方案](../vsto/deploying-an-office-solution.md)   
 [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)  
  
  