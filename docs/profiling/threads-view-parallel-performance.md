---
title: "執行緒檢視 (平行處理效能) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.threadblocking"
helpviewer_keywords: 
  - "並行視覺化檢視，執行緒檢視 (平行處理效能)"
ms.assetid: 2e441103-a266-407b-88c3-fb58716257a3
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# <a name="threads-view-parallel-performance"></a>執行緒檢視 (平行處理效能)
執行緒檢視是並行視覺化檢視中最詳細且功能豐富的檢視。 使用此檢視，您可以識別執行緒是否在執行中，或因為同步處理、 I/O 或因其他原因而遭到封鎖。  
  
 在設定檔分析期間，並行視覺化檢視會檢查每個應用程式執行緒的所有作業系統內容切換事件。 發生內容切換的原因有很多，例如：  
  
-   同步處理原始物件封鎖執行緒。  
  
-   執行緒配量期間已過。  
  
-   執行緒產生封鎖 I/O 要求。  
  
 執行緒檢視會在執行緒停止執行時，指派每次內容切換的分類。 分類會以檢視左下方組件中的圖例顯示。 並行視覺化檢視會透過搜尋已知封鎖 API 的執行緒呼叫堆疊，來將內容切換事件分類。 如果沒有呼叫堆疊，會使用由 [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] 提供的等候原因。 不過，[!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] 分類可能依實作詳細資料而定，並不一定能反映使用者意圖。 例如，[!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] 會將原生輕型 Reader-Writer 鎖定的封鎖等候原因報告為 I/O，而不是同步處理。 在大部分情況下，您可以檢查對應到內容切換事件的呼叫堆疊，來識別封鎖事件的根本原因。  
  
 執行緒檢視也會顯示執行緒之間的相依性。 例如，如果您找到同步處理物件上封鎖的執行緒，您可以尋找將其解除封鎖的執行緒，並在該執行緒將另一執行緒解除封鎖時，檢查其呼叫堆疊上的活動。  
  
 當執行緒正在執行時，並行視覺化檢視會收集範例。 在執行緒檢視中，您可以分析在執行區段期間，哪個程式碼是由一或多個執行緒執行。 您也可以檢查封鎖報表，以及剖析呼叫堆疊樹狀結構執行的報表。  
  
## <a name="usage"></a>使用方式  
 以下是一些您可以使用執行緒檢視的方法︰  
  
-   找出應用程式的使用者介面 (UI) 在某些執行階段沒有回應的原因。  
  
-   指出花費在封鎖同步處理、I/O、分頁錯誤和其他事件的時間量。  
  
-   指出受到系統上其他執行中處理序的干擾程度。  
  
-   識別平行執行的負載平衡問題。  
  
-   找出延展性較差或不存在的原因 (例如，為什麼有多個邏輯核心可用時，也無法改善平行應用程式的效能)。  
  
-   了解應用程式中的並行程度以協助平行處理。  
  
-   了解在背景工作執行緒與執行的關鍵路徑之間的相依性。  
  
## <a name="examining-specific-time-intervals-and-threads"></a>檢查特定時間間隔和執行緒  
 執行緒檢視會顯示時間軸。 您可以在時間軸內縮放和移動瀏覽，檢查應用程式的特定間隔與執行緒。 x 軸上是時間，而 y 軸上有幾個通道︰  
  
-   系統上的每個磁碟機各有兩個 I/O 通道，一個通道用來讀取，而另一個用來寫入。  
  
-   處理序中的每個執行緒各有一個通道。  
  
-   標記通道，如果在追蹤中有標記事件。 標記通道一開始會出現在產生這些事件的執行緒通道下。  
  
-   GPU 通道。  
  
 下圖是執行緒檢視：  
  
 ![執行緒檢視](../profiling/media/threadsviewnarrowing.png "ThreadsViewNarrowing")  
執行緒檢視  
  
 一開始會依照執行緒建立的順序排列，因此第一個是主應用程式。 您可以使用檢視左上角的排序選項，根據另一準則來排序執行緒 (例如，依據最常執行的工作)。  
  
 您可以在左邊資料行中選取執行緒的名稱，然後選擇工具列上的 [隱藏選取的執行緒] 按鈕，來隱藏未在執行工作的執行緒。 建議您隱藏完全遭到封鎖的執行緒，因為其統計資料無關緊要，並會塞滿報表。  
  
 若要識別要隱藏的其他執行緒，請在作用中圖例中，選擇 [設定檔報告] 索引標籤上的 [個別執行緒摘要] 報表。 這會顯示執行解析圖形，顯示目前選取的時間間隔內的執行緒狀態。 在一些縮放層級，可能不會顯示某些執行緒。 發生這種情況時，會在右邊顯示省略符號。  
  
 當您選取一段時間間隔和其中的一些執行緒後，就可以開始進行效能分析。  
  
## <a name="analysis-tools"></a>分析工具  
 本章節描述報表和其他分析工具。  
  
### <a name="thread-blocking-details"></a>執行緒封鎖詳細資料  
 若要取得執行緒上特定區域中的封鎖事件相關資訊，重設該區域的指標，即可顯示工具提示。 這類資訊包含分類、區域開始時間、封鎖持續時間以及封鎖 API (若有的話) 等。 如果您選取封鎖的區域，該時間點的堆疊會連同工具提示中顯示相同的資訊，一起顯示在底部窗格中。 檢查呼叫堆疊，可以判斷執行緒封鎖事件的根本原因。 您可以選取區段並檢查 [目前] 索引標籤，來找到額外的處理序和執行緒資訊。  
  
 執行路徑可能會有多個封鎖事件。 您可以根據封鎖分類來檢查這些項目，以便更快速地找到問題所在區域。 只在左邊圖例中，選擇其中一種封鎖分類。  
  
### <a name="dependencies-between-threads"></a>執行緒之間的相依性  
 並行視覺化檢視可以顯示處理序中執行緒之間的相依性，以便您判斷遭封鎖執行緒嘗試執行的作業，並了解將其啟用來執行的其他執行緒。 若要判斷將另一個執行緒解除封鎖的是哪一個執行緒，請選取相關的封鎖區段。 如果並行視覺化檢視可以判斷解除封鎖執行緒，會在解除封鎖執行緒和封鎖區段後面的執行區段之間繪製一條線。 此外，[解除封鎖堆疊] 索引標籤會顯示相關的呼叫堆疊。  
  
### <a name="thread-execution-details"></a>執行緒執行詳細資料  
 在執行緒的時間軸圖形中，當執行緒正在執行程式碼時，會顯示綠色區段。 您可以取得有關執行區段的詳細資訊。  
  
 當您選取執行區段中的某點時，並行視覺化檢視會在相關的呼叫堆疊上尋找該時間點，然後在執行區段中選取的那點上方顯示黑色插入號，並在 [目前的堆疊] 索引標籤上顯示本身的呼叫堆疊。 您可以在執行區段上選取多個點。  
  
> [!NOTE]
>  並行視覺化檢視可能無法解析執行區段上的選取範圍。 通常，當區段的持續時間少於一毫秒時，才會發生這種情況。  
  
 若要取得目前所選取時間範圍內所有已啟用 (未隱藏) 執行緒的執行設定檔，請在作用中圖例中，選取 [執行] 按鈕。  
  
### <a name="timeline-graph"></a>時間軸圖形  
 時間軸圖形顯示處理序中所有執行緒和主機電腦上所有實體磁碟裝置的活動。 其也顯示 GPU 活動和標記事件。  您可以放大以檢視更多詳細資料，或縮小以檢視更長的時間間隔。 您也可以選取圖形上的各點，取得有關分類、開始時間、持續時間及呼叫堆疊狀態的詳細資料。  
  
 在時間軸圖形中，以色彩表示指定時間的執行緒狀態。 例如，綠色區段表示執行中，紅色區段表示遭封鎖進行同步處理、黃色區段表示遭到先佔，而紫色區段表示忙於裝置 I/O。 您可以使用此檢視，檢查平行迴圈或並行工作中相關執行緒之間的平衡。 如果完成某執行緒所花的時間比其他執行緒長，可能會造成工作分攤不均。 您可以使用這項資訊，在執行緒之間更平均分配工作，以改善程式效能。  
  
 如果在某個時間點只有一個執行緒是綠色 (正在執行)，應用程式可能未充分利用系統上的並行處理能力。 您可以使用時間軸圖形，檢查執行緒之間的相依性，以及封鎖中和已封鎖執行緒之間的暫時關聯性。 若要重新排列執行緒，請選取執行緒，然後在工具列上，選擇向上或向下按鈕。 若要隱藏的執行緒，請加以選取，然後選擇 [隱藏執行緒] 按鈕。  
  
### <a name="profile-reports"></a>設定檔報告  
 時間軸圖形下方是時間表分析，以及一個有各種報表索引標籤的窗格。 當您變更執行緒檢視時，會自動更新報表。 進行大規模追蹤時，可能無法在計算更新時使用報表窗格。 每份報表都有兩個篩選調整選項：減少雜訊和 Just My Code。 使用減少雜訊，篩選掉所花時間極短的呼叫樹狀圖項目。 預設的篩選值為 2%，但您可以在 0% 到 99% 之間調整。 若只要檢視您的程式碼呼叫樹狀圖，請選取 [Just My Code] 核取方塊。 若要檢視所有的呼叫樹狀圖，請清除核取方塊。  
  
#### <a name="profile-report"></a>設定檔報告  
 此索引標籤會顯示和作用中圖例中的項目對應的報表。 若要顯示報表，請選擇其中一個項目。  
  
#### <a name="current-stack"></a>目前的堆疊  
 此索引標籤會顯示在時間軸圖形的執行緒區段上所選取時間點的呼叫堆疊。 顯示的呼叫堆疊會經過修剪，只顯示與您的程式相關的活動。  
  
#### <a name="unblocking-stack"></a>解除封鎖堆疊  
 若要查看是哪一個執行緒和在哪一行程式碼，將選取的執行緒解除封鎖，請選擇 [解除鎖定堆疊] 索引標籤。  
  
#### <a name="execution"></a>執行  
 執行報表會顯示應用程式花費的執行時間解析。  
  
 若要找出執行時間花費在哪一行程式碼，請展開呼叫樹狀圖，然後在呼叫樹狀圖項目的捷徑功能表上，選擇 [檢視原始檔] 或 [檢視呼叫位置]。 [檢視原始檔] 會找到執行的那一行程式碼。 [檢視呼叫位置] 會找到呼叫所執行那一行程式碼的程式碼行。 如果只有一個呼叫位置存在，會反白顯示其程式碼行。 如果有多個呼叫位置存在，您可以在出現的對話方塊中選取想的位置，然後選擇 [移至原始檔] 以反白顯示呼叫位置程式碼。 找到有最多執行個體、花費最多時間 (或兩者) 的呼叫位置通常最有用。 如需詳細資訊，請參閱[設定檔報告](../profiling/execution-profile-report.md)。  
  
#### <a name="synchronization"></a>同步處理  
 同步處理報表顯示負責同步處理區塊的呼叫，以及每個呼叫堆疊的彙總封鎖時間。 如需詳細資訊，請參閱[同步處理時間](../profiling/synchronization-time.md)。  
  
#### <a name="io"></a>I/O  
 I/O 報表顯示負責 I/O 區塊的呼叫，以及每個呼叫堆疊的彙總封鎖時間。 如需詳細資訊，請參閱 [I/O 時間 (執行緒檢視)](../profiling/i-o-time-threads-view.md)。  
  
#### <a name="sleep"></a>Sleep  
 睡眠報表顯示負責睡眠區塊的呼叫，以及每個呼叫堆疊的彙總封鎖時間。 如需詳細資訊，請參閱[睡眠時間](../profiling/sleep-time.md)。  
  
#### <a name="memory-management"></a>記憶體管理  
 記憶體管理報表會顯示記憶體管理區塊發生位置的呼叫，以及每個呼叫堆疊的彙總封鎖時間。 您可以使用這項資訊來識別有過多分頁或記憶體回收問題的區域。  如需詳細資訊，請參閱[記憶體管理時間](../profiling/memory-management-time.md)。  
  
#### <a name="preemption"></a>先佔  
 先佔報表會顯示系統上的處理序先佔目前處理序的執行個體，以及取代目前處理序中執行緒的個別執行緒 。 您可以使用這項資訊來識別要對先佔負最大責任的處理序和執行緒。 如需詳細資訊，請參閱[先佔時間](../profiling/preemption-time.md)。  
  
#### <a name="ui-processing"></a>UI 處理  
 UI 處理報表顯示負責 UI 處理區塊的呼叫，以及每個呼叫堆疊的彙總封鎖時間。 如需詳細資訊，請參閱 [UI 處理時間](../profiling/ui-processing-time.md)。  
  
#### <a name="per-thread-summary"></a>個別執行緒摘要  
 此索引標籤以色彩編碼在資料行檢視顯示每個執行緒花費在執行、I/O 及其他狀態的時間總計。 資料行標示在底部。 當您在時間軸圖形中調整縮放層級時，會自動更新此索引標籤。 在一些縮放層級，可能不會顯示某些執行緒。 發生這種情況時，會在右邊顯示省略符號。 如果您想要的執行緒並未出現，您可以隱藏其他執行緒。 如需詳細資訊，請參閱[個別執行緒摘要](../profiling/per-thread-summary-report.md)。  
  
#### <a name="disk-operations"></a>磁碟作業  
 此索引標籤會顯示和代表目前處理序的磁碟 I/O 相關的處理序和執行緒，接觸到哪些檔案 (例如，載入的 DLL)、一共讀取多少個位元組以及其他資訊。 您可以使用此報表來評估執行期間花費在存取檔案的時間，尤其是處理序似乎為 I/O 繫結時。 如需詳細資訊，請參閱[磁碟作業報告](../profiling/disk-operations-report-threads-view.md)。  
  
## <a name="see-also"></a>另請參閱  
 [並行視覺化檢視](../profiling/concurrency-visualizer.md)


<!--HONumber=Feb17_HO4-->

