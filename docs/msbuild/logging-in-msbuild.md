---
title: "MSBuild 中的記錄 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- msbuild, logging
ms.assetid: 9aea2e76-8f60-4234-913d-598e7bbad808
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: c1c6392dcf887074ec36fb9c6434d2e9437da3f2
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="logging-in-msbuild"></a>MSBuild 中的記錄
記錄功能提供一種方式讓您能夠監視組建的進度。 記錄功能會擷取記錄檔中建置事件、訊息、警告和錯誤。  
  
## <a name="in-this-section"></a>本節內容  
 [取得組建記錄檔](../msbuild/obtaining-build-logs-with-msbuild.md)  
 說明 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 中各個層面的記錄。  
  
 [組建記錄器](../msbuild/build-loggers.md)  
 概述建立單一處理器的記錄器時所需的步驟。  
  
 [在多處理器環境中記錄](../msbuild/logging-in-a-multi-processor-environment.md)  
 說明記錄功能在多處理器環境中的運作方式，以及兩個多處理器記錄模型。  
  
 [撰寫能夠辨識多處理器的記錄器](../msbuild/writing-multi-processor-aware-loggers.md)  
 概述如何建立能夠辨識多處理器的記錄器以及如何使用 ConfigurableForwardingLogger。  
  
 [建立轉送記錄器](../msbuild/creating-forwarding-loggers.md)  
 概述如何建立自訂的轉送記錄器。  
  
## <a name="related-sections"></a>相關章節  
 [同時建置多個專案](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)  
 說明如何透過讓專案平行執行的方式，加快建置多個專案的速度。