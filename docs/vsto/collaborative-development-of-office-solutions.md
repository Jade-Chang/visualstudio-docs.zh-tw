---
title: Office 方案的共同開發
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], collaborative development
- Office development in Visual Studio, collaboration
- source control [Office development in Visual Studio]
- collaborative development [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9bf85dd1ba39df35e337f1b6b80099e3d5bcd774
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
---
# <a name="collaborative-development-of-office-solutions"></a>Office 方案的共同開發
  多位開發人員可以在 Office 專案工作，如同它們在其他 Visual Studio 專案上共同作業。 Visual Studio 正確地找出每一部做為 Microsoft Office 安裝，即使將 Office 安裝在不同的位置。 不過，有一些要注意的重要的考量。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="debug-properties-are-not-shared"></a>偵錯內容不會共用  
 偵錯屬性不是在原始檔控制中由多位使用者共用。 Visual Basic 和 Visual C# 專案的偵錯屬性儲存使用者專屬檔案中 (*ProjectName*.vbproj.user 或*ProjectName*。 副檔名為.csproj.user)，而此檔案不在原始檔控制。 如果有多人同時進行偵錯，每個人都必須手動輸入偵錯屬性。  
  
 如果專案存放在網路共用而不是原始檔控制中，某些額外的步驟必須前往啟用共同作業以開啟方案，並測試組件的開發。  
  
## <a name="source-control-requires-checking-out-all-files"></a>原始檔控制需要簽出的所有檔案  
 如果您使用原始檔控制專案時，您應該檢查所有下的檔案中的程式碼檔案**方案總管 中**(例如*ThisDocument*， *ThisWorkbook*，或*ThisAddIn*程式碼檔案) 每次您變更程式碼檔案，即使是預設為隱藏的檔案。 如果您簽出最上層的程式碼檔案，您的變更可能會遺失。  
  
 您進行變更之後，所有檔案重新都簽入。 如需專案中的隱藏程式碼檔案的詳細資訊，請參閱[Visual Studio 環境中的 Office 專案](../vsto/office-projects-in-the-visual-studio-environment.md)。  
  
## <a name="security-for-informal-collaboration-on-a-network"></a>在網路上的非正式地共同作業的安全性  
 網路位置中的所有文件層級解決方案 (例如\\ \\ *Servername*\\*Sharename*)，完整的位置必須加入至您正在使用的 Microsoft Office 應用程式中受信任的資料夾清單。 選取的選項時請包含子目錄的主要資料夾下方，或特別加入偵錯及建置資料夾加入受信任的資料夾清單。 如需如何執行這項操作的詳細資訊，請參閱[授與信任給文件](../vsto/granting-trust-to-documents.md)。  
  
 在建置期間自動產生的暫存憑證未受到密碼。 憑證中包含開發人員的登入名稱和其他個人資訊。 如果您部署自訂的暫時憑證所簽署，其他人可以存取這項資訊。  
  
## <a name="see-also"></a>另請參閱  
 [保護 Office 方案](../vsto/securing-office-solutions.md)   
 [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)   
 [建置 Office 方案](../vsto/building-office-solutions.md)  
  
  