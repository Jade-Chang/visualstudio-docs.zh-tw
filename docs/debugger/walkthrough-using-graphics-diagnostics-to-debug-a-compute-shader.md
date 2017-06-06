---
title: "逐步解說：使用圖形診斷來偵錯計算著色器 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 69287456-644b-4aff-bd03-b1bbb2abb82a
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 逐步解說：使用圖形診斷來偵錯計算著色器
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本逐步解說示範如何使用 Visual Studio 圖形診斷工具來調查產生不正確結果的計算著色器。  
  
 本逐步解說將說明下列工作：  
  
-   使用 \[圖形事件清單\] 找出潛在的問題來源。  
  
-   使用 \[圖形事件呼叫堆疊\]，判斷 DirectCompute `Dispatch` 事件執行哪個計算著色器。  
  
-   使用 \[圖形管線階段\] 視窗和 HLSL 偵錯工具，檢查為問題來源的計算著色器。  
  
## 情節  
 在此情況下，您已撰寫流暢動態模擬來使用 DirectCompute 執行模擬更新最需要大量計算的部分。  執行應用程式時，資料集和 UI 的轉譯正確，但模擬未如預期運作。  使用圖形診斷，即可擷取圖形記錄問題，以偵錯應用程式。  在應用程式中，問題看起來如下：  
  
 ![模擬流體的行為不正確。](../debugger/media/gfx_diag_demo_compute_shader_fluid_problem.png "gfx\_diag\_demo\_compute\_shader\_fluid\_problem")  
  
 如需如何擷取圖形記錄中圖形問題的相關資訊，請參閱[擷取圖形資訊](../debugger/capturing-graphics-information.md)。  
  
## 調查  
 若要載入圖形記錄檔，以檢查所擷取的畫面格，您可以使用圖形診斷工具。  
  
#### 檢查圖形記錄中的畫面格  
  
1.  在 Visual Studio 中，載入圖形記錄，內含展示不正確模擬結果的畫面格。  在 Visual Studio 中，即會出現新的 \[圖形診斷\] 索引標籤。  此索引標籤的上半部是所選取畫面格的轉譯目標輸出。  下半部是 \[畫面格清單\]，其中顯示每個所擷取畫面格的縮圖。  
  
2.  在 \[畫面格清單\] 中，選取示範不正確模擬行為的畫面格。  即使錯誤似乎出現在模擬程式碼中，而不是轉譯程式碼，您仍然必須選擇畫面格，因為是根據畫面格擷取 DirectCompute 事件，以及 Direct3D 事件。  在此情況下，圖形記錄索引標籤與下列類似：  
  
     ![Visual Studio 中的圖形記錄文件。](../debugger/media/gfx_diag_demo_compute_shader_fluid_step_1.png "gfx\_diag\_demo\_compute\_shader\_fluid\_step\_1")  
  
 選取示範問題的畫面格之後，即可使用 \[圖形事件清單\] 進行診斷。  \[圖形事件清單\] 包含下列呼叫的事件：在使用中畫面格期間進行的每個 DirectCompute 呼叫和 Direct3D API 呼叫 \(例如，API 呼叫以在 GPU 上執行計算，或轉譯資料集或 UI\)。  在此情況下，我們對 `Dispatch` 事件感興趣，而事件代表 GPU 上執行之模擬的各個部分。  
  
#### 尋找模擬更新的 Dispatch 事件  
  
1.  在 \[圖形診斷\] 工具列上，選擇 \[事件清單\] 開啟 \[圖形事件清單\] 視窗。  
  
2.  檢查會轉譯資料集之繪製事件的 \[圖形事件清單\]。  若要進行簡化，請在 \[圖形事件清單\] 視窗右上角的 \[搜尋\] 方塊中輸入 `Draw`。  這樣會篩選清單，使其只包含標題中具有 "Draw" 的事件。  在此情況下，您會發現發生這些 Draw 事件：  
  
     ![&#91;事件清單&#93; &#40;EL&#41; 顯示繪製事件。](../debugger/media/gfx_diag_demo_compute_shader_fluid_step_2.png "gfx\_diag\_demo\_compute\_shader\_fluid\_step\_2")  
  
3.  在圖形記錄文件索引標籤中監看轉譯目標時，在每個 Draw 事件之間移動。  
  
4.  在轉譯目標第一次顯示轉譯的資料集時停止。  在此情況下，資料集會轉譯在第一個 Draw 事件中。  會顯示模擬中的錯誤：  
  
     ![這個繪製事件會呈現模擬資料集。](../debugger/media/gfx_diag_demo_compute_shader_fluid_step_3.png "gfx\_diag\_demo\_compute\_shader\_fluid\_step\_3")  
  
5.  現在，請檢查可更新模擬之 `Dispatch` 事件的 \[圖形事件清單\]。  因為模擬可能在轉譯之前更新，所以您可以先專心在可轉譯結果的 Draw 事件之前發生的 `Dispatch` 事件。  若要進行簡化，請修改 \[搜尋\] 方塊讀取 `Draw;Dispatch;CSSetShader(`。  這樣會篩選清單，使其除了 Draw 事件之外也會包含 `Dispatch` 和 `CSSetShader` 事件。  在此情況下，您會發現在 Draw 事件之前發生數個 `Dispatch` 事件：  
  
     ![EL 會顯示繪製、Dispatch 和 CSSetShader 事件](../debugger/media/gfx_diag_demo_compute_shader_fluid_step_4.png "gfx\_diag\_demo\_compute\_shader\_fluid\_step\_4")  
  
 現在，您知道許多 `Dispatch` 事件中有一些可能會對應至這個問題，則可以更詳細地檢查它們。  
  
#### 判斷 Dispatch 呼叫執行哪個計算著色器  
  
1.  在 \[圖形診斷\] 工具列上，選擇 \[事件呼叫堆疊\] 開啟 \[圖形事件呼叫堆疊\] 視窗。  
  
2.  從轉譯模擬結果的 Draw 事件開始，會從每個先前的 `CSSetShader` 事件往前移動。  然後，在 \[圖形事件呼叫堆疊\] 視窗中，選擇要瀏覽至呼叫位置的最上層函式。  在呼叫位置，您可以使用 [CSSetShader](http://msdn.microsoft.com/library/ff476402.aspx) 函式呼叫的第一個參數來判斷下一個 `Dispatch` 事件執行哪個計算著色器。  
  
 在此情況下，每個畫面格中都會有三組 `CSSetShader` 和 `Dispatch` 事件。  進行倒推，第三組代表整合步驟 \(其中實際移動流暢物件\)、第二組代表強制計算步驟 \(其中計算會影響每個物件的強制\)，以及第一組代表密度計算步驟。  
  
#### 偵錯計算著色器  
  
1.  在 \[圖形診斷\] 工具列上，選擇 \[管線階段\] 開啟 \[圖形管線階段\] 視窗。  
  
2.  選取第三個 `Dispatch` 事件 \(緊接在 Draw 事件前面的事件\)，然後在 \[圖形管線階段\] 視窗的 \[計算著色器\] 階段下，選擇 \[開始偵錯\]。  
  
     ![在 EL 中選取第三個 Dispatch 事件。](../debugger/media/gfx_diag_demo_compute_shader_fluid_step_6.png "gfx\_diag\_demo\_compute\_shader\_fluid\_step\_6")  
  
     HLSL 偵錯工具是在執行整合步驟的著色器上啟動。  
  
3.  檢查整合步驟的計算著色器原始程式碼來搜尋錯誤來源。  使用圖形診斷偵錯 HLSL 計算著色器程式碼時，即可逐步執行程式碼，並使用其他熟悉的偵錯工具 \(例如監看式視窗\)。  在此情況下，您將判斷在執行整合步驟的計算著色器中似乎未發生錯誤。  
  
     ![偵錯 IntegrateCS 計算著色器。](../debugger/media/gfx_diag_demo_compute_shader_fluid_step_7.png "gfx\_diag\_demo\_compute\_shader\_fluid\_step\_7")  
  
4.  若要停止偵錯計算著色器，請選擇 \[偵錯\] 工具列上的 \[停止偵錯\] \(鍵盤：Shift\+F5\)。  
  
5.  接下來，選取第二個 `Dispatch` 事件，並開始偵錯計算著色器，就像先前的步驟一樣。  
  
     ![在 EL 中選取第二個 Dispatch 事件。](../debugger/media/gfx_diag_demo_compute_shader_fluid_step_8.png "gfx\_diag\_demo\_compute\_shader\_fluid\_step\_8")  
  
     HLSL 偵錯工具會在計算處理每個流暢物件之強制的著色器啟動。  
  
6.  檢查強制計算步驟的計算著色器原始程式碼。  在此情況下，您將判斷這裡是錯誤來源。  
  
     ![偵錯 ForceCS&#95;Simple 計算著色器。](../debugger/media/gfx_diag_demo_compute_shader_fluid_step_9.png "gfx\_diag\_demo\_compute\_shader\_fluid\_step\_9")  
  
 判斷錯誤的位置之後，即可停止偵錯並修改計算著色器原始程式碼，以正確計算互動中物件之間的距離。  在此情況下，您只要將 `float2 diff = N_position + P_position;` 行變更為 `float2 diff = N_position - P_position;`：  
  
 ![修正過的計算著色器程式碼。](../debugger/media/gfx_diag_demo_compute_shader_fluid_step_10.png "gfx\_diag\_demo\_compute\_shader\_fluid\_step\_10")  
  
 在此情況下，因為計算著色器是在執行階段進行編譯，所以只要在變更之後重新啟動應用程式，即可觀察它們如何影響模擬。  您不需要重建應用程式。  執行應用程式時，會發現模擬現在正確運作。  
  
 ![模擬流體的行為正確。](../debugger/media/gfx_diag_demo_compute_shader_fluid_resolution.png "gfx\_diag\_demo\_compute\_shader\_fluid\_resolution")