---
title: 如何： 檢查 IIS 屬性設定 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- IIS, property settings
- debugging Web applications, troubleshooting
- IIS administration tool
- Web applications, setting properties
- properties [debugger], setting with IIS administration tool
ms.assetid: 9efc50bf-02fb-4750-9b3e-f03c38f10d8b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: acd232b76ece37737833d071c8551d1319d4f151
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
ms.locfileid: "31477975"
---
# <a name="how-to-verify-iis-property-settings"></a>如何：檢查 IIS 屬性設定
您可以使用 IIS 系統管理工具設定 Web 應用程式的屬性。 必須正確設定這些屬性才能順利執行應用程式，因此驗證這些設定通常都是疑難排解的必要步驟。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。  
  
### <a name="to-check-iis-settings-for-the-web-application"></a>若要檢查 Web 應用程式的 IIS 設定  
  
1.  開啟**系統管理工具**視窗： 上**啟動**功能表上，指向**程式**，然後按一下 **系統管理工具**。 如果**系統管理工具**不會顯示在**程式**功能表，然後中的尋找**控制台**。  
  
    -   在 Windows 2000 中，選取**網際網路服務管理員**。  
  
    -   在 Windows XP 中，選取**Internet Information Services**。  
  
    -   在 Windows Server 2003 上按兩下**管理您的伺服器**。  
  
         **管理您的伺服器**視窗隨即開啟。 在下**應用程式伺服器**，按一下 **管理此應用程式伺服器**。  
  
         **應用程式伺服器**視窗隨即開啟。 開啟**網際網路資訊服務 (IIS) 管理員**的左窗格中的節點。  
  
2.  在對話方塊中，按一下電腦的樹狀目錄控制項節點。 按一下**網站**] 節點，然後選取 [Web 應用程式的節點。 它將會是 網站 節點中，因此的同層級**Default Web Site**節點或現有的網站 節點底下的虛擬目錄節點。  
  
3.  以滑鼠右鍵按一下 Web 應用程式和捷徑功能表上，按一下 **屬性**。  
  
4.  驗證 Web 應用程式的安全性設定：  
  
    1.  Web 應用程式中**屬性**視窗中，按一下 **目錄安全性**索引標籤，然後按一下**編輯**。  
  
    2.  在**驗證方法**對話方塊中，選取**啟用匿名存取**和**整合式 Windows 驗證**如果尚未選取。  
  
    3.  按一下**確定**關閉**驗證方法** 對話方塊。  
  
5.  對於 ATL Server 應用程式，請驗證偵錯動詞命令 (DEBUG Verb) 是否與您的 ISAPI 副檔名有關聯。 如需詳細資訊，請參閱[How to： 將偵錯動詞命令擴充功能與](http://msdn.microsoft.com/en-us/50d261d3-4bd4-41c0-b44e-3591086f121e)。  
  
6.  如[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]應用程式中，確定應用程式的應用程式名稱中設定的虛擬資料夾**網際網路資訊服務 (IIS) 管理員**，**網際網路服務管理員**或**Internet Information Services**。  
  
    1.  Web 應用程式中**屬性**視窗中，選取**目錄**索引標籤上，如果應用程式的虛擬目錄，或**主目錄**索引標籤上，如果應用程式網站。  
  
    2.  確認中的名稱**本機路徑**符合實際部署應用程式的目錄名稱。  
  
    3.  在下**應用程式設定**，輸入包含應用程式之根目錄名稱。  
  
    4.  按一下**確定**關閉**屬性** 對話方塊。  
  
7.  如[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]應用程式中，按一下  **ASP.NET**索引標籤上，確認正確的版本[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]指定。  
  
8.  按一下**確定**關閉**屬性** 對話方塊。  
  
9. 按一下**確定**關閉**網際網路資訊服務 (IIS) 管理員**，**網際網路服務管理員**，或**Internet Information Services** 對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [疑難排解](../debugger/debugging-web-applications-troubleshooting.md)