---
title: ClickOnce 執行應用程式更新的方式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- updates, ClickOnce
- ClickOnce deployment, updates
- deploying applications [ClickOnce], application updates
ms.assetid: d54313c2-cf0c-420d-b151-99953a95f0bb
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a1f5d9b67633ffa2b14f780b9588f526372a4f5d
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/19/2018
ms.locfileid: "39152509"
---
# <a name="how-clickonce-performs-application-updates"></a>ClickOnce 執行應用程式更新的方式
ClickOnce 會使用應用程式的部署資訊清單中指定的檔案版本資訊，決定是否要更新應用程式的檔案。 更新開始之後，ClickOnce 使用一種叫做*修補檔案*以避免重複下載應用程式檔案。  
  
## <a name="file-patching"></a>修補檔案  
 在更新應用程式時，ClickOnce 不會下載所有應用程式的新版本的檔案除非檔案已變更。 相反地，它會比較目前的應用程式針對新版本的資訊清單中的簽章的應用程式資訊清單中指定的檔案雜湊簽章。 如果檔案的簽章不同，ClickOnce 會下載新版本。 如果簽章相符，該檔案已不從某個版本變更為下一步。 在此情況下，ClickOnce 會將現有的檔案複製，並使用它在應用程式的新的版本。 這種方法避免 ClickOnce 下載整個應用程式一次，即使只有一個或兩個檔案已變更。  
  
 修補檔案也適用於下載的組件的視需要使用<xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A>和<xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroupAsync%2A>方法。  
  
 如果您使用 Visual Studio 編譯您的應用程式時，它就會產生新的雜湊簽章的所有檔案，每當您重建整個專案。 在此情況下，所有組件將會下載到用戶端，但只有少數的組件可能已變更。  
  
 修補檔案不適用於標示為 資料和資料目錄中儲存的檔案。 這些一律都會下載不論檔案的雜湊簽章。 如需有關資料目錄的詳細資訊，請參閱[存取 ClickOnce 應用程式中的本機和遠端資料](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)。  
  
## <a name="see-also"></a>另請參閱  
 [選擇 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)   
 [選擇 ClickOnce 部署策略](../deployment/choosing-a-clickonce-deployment-strategy.md)