---
title: "管理方案中的專案載入 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- solutions, managing project loading
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 2dbbb8ddcf574f2e3db81ce63db257e21ff88839
ms.sourcegitcommit: a80e7ef2f0a0f6d906a44f4d696aeb208bc1ad70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2018
---
# <a name="managing-project-loading-in-a-solution"></a>管理專案載入方案中
Visual Studio 方案可以包含大量的專案。 預設的 Visual Studio 行為是開啟方案時，在載入方案中的所有專案，而且不允許使用者存取的任何專案，直到全部都已完成載入。 當專案載入的程序將 last 兩分鐘以上時，進度列會顯示顯示載入的專案數目和專案的總數。 使用者可以在方案中使用多個專案中工作時卸載專案，但此程序也有一些缺點： 卸載的專案不會建立為重建方案 命令的一部分，並關閉 IntelliSense 描述的型別和成員專案不會顯示。  
  
 開發人員可以減少方案載入時間，並管理專案載入行為，藉由建立方案負載管理員。 方案載入管理員可以確定專案會載入前啟動背景組建、 背景載入其他背景工作完成之前, 的延遲時間和執行其他專案負載的管理工作。  
  
## <a name="creating-a-solution-load-manager"></a>建立方案負載管理員  
 開發人員可以建立方案載入管理員藉由實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager>，並建議 Visual Studio 方案負載管理員使用中。  
  
#### <a name="activating-a-solution-load-manager"></a>啟用方案負載管理員  
 Visual Studio 允許只有一個方案負載管理員在指定的時間，因此當您要啟動方案載入時，您必須告知可用 Visual Studio 管理員。 如果已在稍後啟動的第二個方案負載管理員，將會中斷您的方案負載管理員。  
  
 您必須取得<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>服務和設定<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>屬性：  
  
```csharp  
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;  
object objLoadMgr = this;   //the class that implements IVsSolutionManager  
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);  
```  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A>關閉 Visual Studio 或不同的封裝已經為作用中的方案負載管理員藉由呼叫時，呼叫方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A>與<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>屬性。  
  
#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>針對不同種類的解決方案負載管理員策略  
 您可以實作方案負載管理員不同的方式，根據它們為了管理的方案的類型。  
  
 如果方案負載管理員就是要管理解決方案載入一般情況下，它可以實作 VSPackage 的一部分。 封裝應該設定為自動載入，藉由新增<xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>值為 vspackage <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid>。 然後可以在中啟動方案負載管理員<xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>方法。  
  
> [!NOTE]
>  如需自動載入封裝的詳細資訊，請參閱[載入 Vspackage](../extensibility/loading-vspackages.md)。  
  
 Visual Studio 可以辨識只有最後一個方案負載管理員啟動，因為一般方案負載管理員一律會偵測是否有現有的負載管理員之後再啟動本身。 如果方案服務上呼叫 GetProperty()<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>傳回`null`，沒有使用中方案負載管理員。 如果它不會傳回 null，請檢查物件是否與您的方案負載管理員相同。  
  
 如果方案負載管理員就是要管理只有幾種類型的方案中，VSPackage 可以訂閱方案載入事件 (藉由呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>)，並使用的事件處理常式<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>啟動方案負載管理員。  
  
 如果方案負載管理員就是要管理特定的解決方案，啟動資訊可以保存方案檔的一部分呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A>方案前一節。  
  
 特定解決方案負載管理員應該停用本身中<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A>事件處理常式，以避免與其他方案負載管理員相衝突。  
  
 如果您需要方案負載管理員，只保存通用專案載入屬性 （例如，屬性選項 頁面上設定），您可以啟動中的方案載入管理員<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>事件處理常式，保存在方案內容中，設定然後停用方案負載管理員。  
  
## <a name="handling-solution-load-events"></a>處理方案載入事件  
 若要訂閱方案載入事件，請呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>當您啟用您的方案負載管理員。 如果您實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents>，您可以回應不同的專案載入屬性與相關的事件。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>： 這個事件一經引發之前開啟方案。
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>： 方案已完全載入，但是背景之前載入的專案重新開始之後，就會引發此事件。
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>： 這個事件一經引發後一開始會完全載入方案時，有解決方案負載管理員。 它也會引發背景載入或視需要載入時，方案會成為完全載入之後。 同時，<xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid>就會重新啟動。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>： 這個事件一經引發之前載入的專案 （或專案）。 若要確保在載入專案之前，會完成其他背景處理序，將`pfShouldDelayLoadToNextIdle`至**true**。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>： 此事件是在專案的批次載入時引發。 如果`fIsBackgroundIdleBatch`為 true，如果專案，則在背景中; 載入`fIsBackgroundIdleBatch`為 false 時，所要載入以同步方式要求的結果使用者，例如使用者如果展開在 [方案總管] 中的暫止專案的專案。 您可以處理這個事件來執行耗費資源的工作，否則需要進行<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>： 已載入專案的批次之後，就會引發此事件。  
  
## <a name="detecting-and-managing-solution-and-project-loading"></a>偵測及管理方案和專案載入  
 若要偵測專案和方案的載入狀態，請呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A>具有下列值：  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>:`var`傳回`true`方案和其所有的專案已載入，否則如果`false`。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>:`var`傳回`true`如果批次的專案目前正在載入的是在背景中，否則`false`。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>:`var`傳回`true`如果批次的專案目前正在載入的是以同步方式因使用者命令或其他明確載入，否則`false`。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>:`var`傳回`true`目前正在關閉方案，否則如果`false`。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>:`var`傳回`true`目前正在開啟方案，否則如果`false`。  
  
 您也可以確保載入專案和方案，藉由呼叫下列方法之一：  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>： 呼叫這個方法會強制方法會傳回之前載入的方案中的專案。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>： 呼叫這個方法會強制中的專案`guidProject`方法會傳回之前載入。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>： 呼叫這個方法會強制在專案`guidProjectID`方法會傳回之前載入。  
