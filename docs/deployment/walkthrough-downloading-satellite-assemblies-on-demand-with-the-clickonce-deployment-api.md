---
title: 逐步解說： 下載需求以 ClickOnce 部署 API 的附屬組件 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, globalization
- localization, Windows Forms
- Windows Forms, localization
- globalization, ClickOnce
- satellite assemblies, ClickOnce
- ClickOnce deployment, on-demand download
- localization, ClickOnce deployment
- ClickOnce deployment, localization
ms.assetid: fdaa553f-a27e-44eb-a4e2-08c122105a87
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b558ca0d5b8080e581dcddd07e2f89511d062cc4
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/19/2018
ms.locfileid: "39154407"
---
# <a name="walkthrough-download-satellite-assemblies-on-demand-with-the-clickonce-deployment-api"></a>逐步解說： 下載附屬組件，依需求以 ClickOnce 部署 API
透過使用附屬組件，Windows Forms 應用程式可以設定為適用多個文化特性。 *「附屬組件」* (Satellite Assembly) 為包含文化特性 (除了應用程式的預設文化特性以外) 之應用程式資源的組件。  
  
 中所述[當地語系化 ClickOnce 應用程式](../deployment/localizing-clickonce-applications.md)，您可以包含在相同的多個文化特性的多個附屬組件[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 預設會下載您部署中所有的附屬組件到用戶端電腦，儘管單一用戶可能只需要一個附屬組件。  
  
 本逐步解說示範如何標示您的附屬組件為選擇性，並僅下載用戶端電腦目前文化特性所需要的附屬組件。 下列程序使用的工具可在 [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]取得。 您也可以在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]執行這個工作。  另請參閱[逐步解說： 下載附屬組件，依需求使用設計工具以 ClickOnce 部署 API](http://msdn.microsoft.com/library/ms366788\(v=vs.110\))或[逐步解說： 下載附屬組件，依需求以 ClickOnce 部署 API 使用設計工具](http://msdn.microsoft.com/library/ms366788\(v=vs.120\))。  
  
> [!NOTE]
>  為了測試用途，下列程式碼範例以程式設計的方式設定文化特性為 `ja-JP`。 如需為生產環境調整程式碼的相關資訊，請參閱本主題＜後續步驟＞一節。  
  
## <a name="prerequisites"></a>必要條件  
 本主題假設您知道如何使用 Visual Studio 將當地語系化的資源新增至您的應用程式。 如需詳細指示，請參閱 <<c0> [ 逐步解說： 當地語系化 Windows forms](https://msdn.microsoft.com/library/vstudio/y99d1cd3\(v=vs.100\).aspx)。  
  
### <a name="to-download-satellite-assemblies-on-demand"></a>隨需下載附屬組件  
  
1.  將下列程式碼加入您的應用程式，以便能夠隨需下載附屬組件。  
  
     [!code-csharp[ClickOnce.SatelliteAssembliesSDK#1](../deployment/codesnippet/CSharp/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api_1.cs)]
     [!code-vb[ClickOnce.SatelliteAssembliesSDK#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api_1.vb)]  
  
2.  使用來產生您的應用程式的附屬組件[Resgen.exe （資源檔產生器）](/dotnet/framework/tools/resgen-exe-resource-file-generator)或[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
3.  產生應用程式資訊清單，或藉由開啟現有的應用程式資訊清單*MageUI.exe*。 如需有關這項工具的詳細資訊，請參閱 < [MageUI.exe (Manifest Generation and Editing Tool，Graphical Client)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)。  
  
4.  按一下 [檔案]  索引標籤。  
  
5.  按一下 **省略符號** 按鈕 (**...**)，然後選取 包含的所有應用程式的組件和檔案，包括使用產生的附屬組件的目錄*Resgen.exe*。 (附屬組件都會有名稱形式 *\<isoCode > \ApplicationName.resources.dll*，其中\<isoCode > 是 RFC 1766 格式的語言識別項。)  
  
6.  按一下 [填入]  將檔案加入您的部署。  
  
7.  選取每個附屬組件的 [選擇性]  核取方塊。  
  
8.  設定群組欄位到每個附屬組件的 ISO 語言識別項。 以日文的附屬組件為例，您會將下載群組名稱指定為 `ja-JP`取得。 這可讓您在步驟 1 加入的程式碼，根據使用者之 <xref:System.Threading.Thread.CurrentUICulture%2A> 屬性設定，下載適合的附屬組件。  
  
## <a name="next-steps"></a>後續步驟  
 在生產環境中，因為用戶端電腦上會有正確的預設值，所以您可能需要移除行程式碼範例中，將 <xref:System.Threading.Thread.CurrentUICulture%2A> 設定為特定值的行。 當您的應用程式在日文的用戶端電腦上執行時， <xref:System.Threading.Thread.CurrentUICulture%2A> 預設會是 `ja-JP` 。 在部署您的應用程式之前，以程式設計方式設定這個值以測試附屬組件，是個好方法。  
  
## <a name="see-also"></a>另請參閱  
 [當地語系化 ClickOnce 應用程式](../deployment/localizing-clickonce-applications.md)