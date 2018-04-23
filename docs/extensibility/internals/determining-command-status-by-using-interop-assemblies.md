---
title: 使用 Interop 組件判斷命令狀態 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, determining command status
- command handling with interop assemblies, status
ms.assetid: 2f5104d1-7b4c-4ca0-a626-50530a8f7f5c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4989910fdec968a4a05e2459e6625ee2c15fd9a4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="determining-command-status-by-using-interop-assemblies"></a>使用 Interop 組件判斷命令狀態
VSPackage 必須持續追蹤的命令，它可以處理的狀態。 當 VSPackage 內處理的命令會變成啟用或停用，無法判斷環境。 負責 VSPackage 來通知有關命令狀態的環境，例如，狀態的一般命令例如**剪下**，**複製**，和**貼上**。  
  
## <a name="status-notification-sources"></a>狀態通知來源  
 環境接收透過 Vspackage 命令的相關資訊<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>方法的 VSPackage 實作的一部分的<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>介面。 環境呼叫<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>方法的 VSPackage 在兩個情況下：  
  
-   當使用者開啟主功能表或內容功能表 （按一下滑鼠右鍵） 時，環境執行<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>該功能表上的命令，以判斷其狀態的所有方法。  
  
-   當 VSPackage 要求環境更新目前的使用者介面 (UI)。 這是目前顯示給使用者，這類的命令，就會發生**剪下**，**複製**，和**貼上**分組在 [標準] 工具列上，會變成啟用和停用中回應內容和使用者的動作。  
  
 因為 shell 裝載多個的 Vspackage，殼層效能會實在會降低，如果它才能輪詢每個 VSPackage 也可以判斷命令狀態。 相反地，VSPackage 應主動通知環境變更時變更其 UI 時。 如需有關更新通知的詳細資訊，請參閱[更新使用者介面](../../extensibility/updating-the-user-interface.md)。  
  
## <a name="status-notification-failure"></a>狀態通知失敗  
 通知命令狀態變更的環境中失敗 VSPackage 可以將 UI 置於不一致的狀態。 請記住，您的功能表或內容功能表命令的任何可放入工具列上的使用者。 因此，更新 UI，功能表或內容功能表開啟時，只是不夠的。  
  
## <a name="see-also"></a>另請參閱  
 [Vspackage 如何新增使用者介面項目](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [實作](../../extensibility/internals/command-implementation.md)