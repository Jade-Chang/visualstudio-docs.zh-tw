---
title: 如何： 使用設計工具停用 ClickOnce 應用程式的 URL 啟動 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- disallowURLActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: a337a582-e67c-409a-b52e-607cd1a8fc57
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 97357dd92525be2d36b552c5f3df49080f46d29b
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/19/2018
ms.locfileid: "39152030"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer"></a>如何： 使用設計工具停用 ClickOnce 應用程式的 URL 啟動
一般而言，[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]緊接著安裝從 Web 伺服器之後，將會自動啟動 「 應用程式。 基於安全性理由，您可能決定要停用此行為，並告知使用者啟動應用程式**啟動**功能表改。 下列程序描述如何停用 URL 啟用。  
  
 這項技術僅適用於安裝在使用者電腦上的 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式，其來自 Web 伺服器。 它不能用於線上專用的應用程式，可以開始只能透過其 URL。 如需有關線上專用和已安裝的應用程式之間的差異的詳細資訊，請參閱[選擇 ClickOnce 部署策略](../deployment/choosing-a-clickonce-deployment-strategy.md)。  
  
 此程序使用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 您也可以完成這項工作使用[!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]。 如需詳細資訊，請參閱 <<c0> [ 如何： 停用 URL 啟用的 ClickOnce 應用程式](../deployment/how-to-disable-url-activation-of-clickonce-applications.md)。  
  
## <a name="procedure"></a>程序  
  
#### <a name="to-disable-url-activation-for-your-application"></a>若要停用應用程式的 URL 啟用  
  
1.  以滑鼠右鍵按一下您的專案名稱，在**方案總管**，然後按一下**屬性**。  
  
2.  在 [**屬性**頁面上，按一下**發佈**] 索引標籤。  
  
3.  按一下 [選項] 。  
  
4.  按一下 **資訊清單**。  
  
5.  選取核取方塊**封鎖應用程式，使其無法透過 URL 啟動**。  
  
6.  部署您的應用程式。  
  
## <a name="see-also"></a>另請參閱  
 [發行 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)