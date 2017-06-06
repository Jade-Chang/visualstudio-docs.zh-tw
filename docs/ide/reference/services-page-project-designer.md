---
title: "專案設計工具、服務頁面 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vb.ProjectPropertiesServices
helpviewer_keywords:
- Services page in Project Designer
- Project Designer, Services page
ms.assetid: 6dd9e0fa-acba-4d7d-b081-705b0fc86ff5
caps.latest.revision: 26
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
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
translationtype: Human Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 2ad2f42f28e58def5ba721a061fc0f271dba5fe6
ms.lasthandoff: 02/22/2017

---
# <a name="services-page-project-designer"></a>專案設計工具、服務頁
用戶端應用程式服務簡化了對 [!INCLUDE[ajax_current_short](../../ide/reference/includes/ajax_current_short_md.md)] 登入、角色以及 Windows Forms 和 Windows Presentation Foundation (WPF) 應用程式的設定檔服務的存取。 您可以使用 [專案設計工具] 的 [服務] 頁面來啟用和設定專案的用戶端應用程式服務。  
  
 使用用戶端應用程式服務，您可以使用集中式伺服器來驗證使用者、判斷每位使用者已獲指派的角色，以及儲存您可透過網路共用的個別使用者應用程式設定。 如需詳細資訊，請參閱[用戶端應用程式服務](http://msdn.microsoft.com/Library/1487d8df-089e-4f21-abfb-a791a652b58e)。  
  
 若要存取 [服務] 頁面，請選取方案總管中的專案節點，然後按一下 [專案] 功能表上的 [屬性]。 [專案設計工具] 出現時，請按一下 [服務] 索引標籤。  
  
> [!NOTE]
>  用戶端應用程式服務需要完整版的 .NET Framework，且 .NET Framework 用戶端設定檔中不支援這些服務。 如果停用 [啟用用戶端應用程式服務] 核取方塊，請確認 [目標 Framework] 已設定為 .NET Framework 3.5 (含) 以後版本。 若要檢視 C# 中的 [目標 Framework]，請開啟 [專案設計工具]，然後按一下 [應用程式] 頁面。 若要檢視 Visual Basic 中的 [目標 Framework] 設定，請開啟 [專案設計工具]，並按一下 [編譯] 頁面，然後按一下 [進階編譯選項]。  
  
## <a name="task-list"></a>工作清單  
 [如何：設定用戶端應用程式服務](http://msdn.microsoft.com/Library/34a8688a-a32c-40d3-94be-c8e610c6a4e8)  
  
## <a name="uielement-list"></a>UIElement 清單  
 **組態**  
 在這個頁面上無法編輯此控制項。 如需此控制項的描述，請參閱[專案設計工具、編譯頁面 (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) 或[專案設計工具、建置頁面 (C#)](../../ide/reference/build-page-project-designer-csharp.md)。  
  
 **平台**  
 在這個頁面上無法編輯此控制項。 如需此控制項的描述，請參閱[專案設計工具、編譯頁面 (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) 或[專案設計工具、建置頁面 (C#)](../../ide/reference/build-page-project-designer-csharp.md)。  
  
 **啟用用戶端應用程式服務**  
 選取以啟用用戶端應用程式服務。 您必須在 [服務] 頁面上指定服務位置，以使用用戶端應用程式服務。  
  
 **使用 Windows 驗證**  
 指出驗證提供者將使用 Windows 驗證，也就是 Windows 作業系統所提供的身分識別。  
  
 **使用表單驗證**  
 指出驗證提供者將使用表單驗證。 這表示您的應用程式必須提供進行登入的使用者介面。 如需詳細資訊，請參閱[如何：使用用戶端應用程式服務實作使用者登入](http://msdn.microsoft.com/Library/5431a671-eb02-4e18-a651-24764fccec9a)。  
  
 **驗證服務位置**  
 只能與表單驗證搭配使用。 指定驗證服務的位置。  
  
 **選擇性︰認證提供者**  
 只能與表單驗證搭配使用。 指出當您的應用程式呼叫 `static`<xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName> 方法並且針對參數傳遞空字串或 `null` 時，驗證服務將用來顯示登入對話方塊的 <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> 實作。 如果您將此方塊空白，則必須將有效的使用者名稱和密碼傳遞給 <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName> 方法。 您必須將認證提供者指定為組件限定類型名稱。 如需詳細資訊，請參閱 <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=fullName> 和[組件名稱](http://msdn.microsoft.com/Library/8f8c2c90-f15d-400e-87e7-a757e4f04d0e)。 最簡單的組件限定類型名稱格式看起來類似下列範例：`MyNamespace.MyLoginClass, MyAssembly`  
  
 **角色服務位置**  
 指定角色服務的位置。  
  
 **Web 設定服務位置**  
 指定設定檔 (Web 設定) 服務的位置。  
  
 **進階**  
 開啟可用來覆寫預設行為的[服務對話方塊的進階設定](../../ide/reference/advanced-settings-for-services-dialog-box.md)。 例如，您可以使用此對話方塊指定資料庫來進行離線儲存，而不是使用本機檔案系統。 如需詳細資訊，請參閱[服務對話方塊的進階設定](../../ide/reference/advanced-settings-for-services-dialog-box.md)。  
  
## <a name="see-also"></a>另請參閱  
 [用戶端應用程式服務](http://msdn.microsoft.com/Library/1487d8df-089e-4f21-abfb-a791a652b58e)   
 [服務對話方塊的進階設定](../../ide/reference/advanced-settings-for-services-dialog-box.md)   
 [如何：設定用戶端應用程式服務](http://msdn.microsoft.com/Library/34a8688a-a32c-40d3-94be-c8e610c6a4e8)   
 [專案設計工具、編譯頁面 (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)   
 [專案設計工具、建置頁面 (C#)](../../ide/reference/build-page-project-designer-csharp.md)   
 [專案設計工具簡介](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)