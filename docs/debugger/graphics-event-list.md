---
title: "圖形事件清單 | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.graphics.eventlist"
ms.assetid: a1252e19-b27d-4dc7-a16b-fdac894c1f0e
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 圖形事件清單
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

使用 Visual Studio 圖形分析器中的 [圖形事件清單]，來探索在轉譯遊戲或應用程式的畫面格時所記錄的 Direct3D 事件。  
  
 這是 [事件清單]：  
  
 ![名稱包含 "Index" 的事件清單。](../debugger/media/gfx_diag_demo_event_list_orientation.png "gfx_diag_demo_event_list_orientation")  
  
## <a name="using-the-event-list"></a>使用事件清單  
 當您選取事件清單中的事件時，該事件會反映在其他圖形分析工具所顯示的資訊中；透過搭配這些其他工具使用事件清單，您可以更詳細地檢查呈現問題以判斷原因。 若要深入了解如何搭配其他圖形分析工具使用事件清單以解決轉譯問題，請參閱[範例](../debugger/graphics-diagnostics-examples.md)。  
  
 有效率地使用事件清單的功能，對於避開可能包含數千個事件的複雜畫面格十分重要。 若要有效率地使用事件清單，請選擇最適合您的檢視，並使用搜尋來篩選事件清單、進入連結以深入了解與事件相關聯的 Direct3D 物件，以及使用方向按鈕快速在繪製呼叫之間移動。  
  
### <a name="color-coded-events-in-direct3d-12"></a>Direct3D 12 中的色彩編碼事件  
 Direct3D 12 公開對應至不同硬體功能的多個佇列。 為了協助識別與 Direct3D 12 中特定圖形事件相關聯的佇列，在處理 Direct3D 12 應用程式的擷取時，會根據其佇列將事件清單中的事件加上色彩。  
  
|Direct3D 12 佇列|色彩|  
|-----------------------|-----------|  
|轉譯佇列|綠色|  
|計算佇列|黃色|  
|複製佇列|橙色|  
  
 Direct3D 11 不公開多個佇列，因此，在處理 Direct3D 11 應用程式的擷取時，不會將事件清單中的事件加上色彩。  
  
### <a name="event-list-views"></a>事件清單檢視  
 事件清單支援兩個不同的檢視，而這兩個檢視透過不同的方式來組織圖形事件，以支援您的工作流程和喜好設定。 第一個檢視是 *「繪製呼叫檢視」* (draw calls view)，其透過階層方式組織事件以及與事件相關聯的狀態。 第二個檢視是 *「時間軸檢視」* (timeline view)，其依時間順序組織事件，且格式為一般清單。  
  
 **繪製呼叫** 檢視  
 以階層形式顯示所擷取的事件和其狀態。 階層最上層是由事件 (例如繪製呼叫、清除、存在以及處理檢視的繪製呼叫、清除、存在) 所構成。 在事件清單中，您可以展開繪製呼叫，以顯示繪製呼叫時的目前裝置狀態，而且可以進一步展開每種狀態類型，以顯示設定其值的事件。 您也可以在此層級中，查看先前的畫面格中是否有設定特定狀態，或是否在最後一次繪製呼叫之後多次設定特定狀態。  
  
 **時間軸** 檢視  
 依時間順序顯示每個擷取的事件。 這種組織事件清單的方式與舊版 Visual Studio 相同。  
  
##### <a name="to-change-the-event-list-view-mode"></a>變更事件清單檢視模式  
  
-   在 [圖形事件清單]  視窗的事件清單上方，找到 [檢視]  下拉式清單，並選擇 [時間軸]  檢視或 [繪製呼叫]  檢視。  
  
### <a name="filtering-events"></a>篩選事件  
 您可以使用 [搜尋] 方塊 (位在 [圖形事件清單]  視窗右上角) 篩選事件清單，使清單只包括名稱包含特定關鍵字的事件。 如上圖所示，您可以指定單一關鍵字 (如 `Vertex`)，或使用以分號分隔清單指定多個關鍵字，例如 `Draw;Primitive`，其符合名稱中有 `Draw` 或 `Primitive` 的事件。 搜尋會受到空格影響；例如， `VSSet` 和 `VS Set` 是不同的搜尋，因此，請務必小心地建立搜尋。  
  
### <a name="moving-between-draw-calls"></a>在繪製呼叫之間移動  
 因為檢查 `Draw` 呼叫相當重要，所以您可以使用 [移至下一個繪製呼叫]  和 [移至上一個繪製呼叫]  按鈕 (位在 [圖形事件清單]  視窗左上角)，尋找繪製呼叫並快速在其間移動。  
  
### <a name="links-to-graphics-objects"></a>圖形物件連結  
 若要了解特定圖形事件，您可能需要目前 Direct3D 狀態或事件所參考 Direct3D 物件的其他資訊。 許多事件都提供您可進入以取得其他詳細資料的資訊連結。  
  
## <a name="kinds-of-events-and-event-markers"></a>事件類型和事件標記  
 事件清單中所顯示的事件會組織成四種分類：一般事件、繪製事件、使用者定義事件群組，以及使用者定義事件標記。 除了一般事件之外，每個事件都會與指出事件所屬分類的圖示一起顯示。  
  
|圖示|事件描述|  
|----------|-----------------------|  
|(無圖示)|一般事件<br /> 使用者定義事件、使用者定義事件群組或繪製事件以外的事件。|  
|![繪製事件圖示](../debugger/media/vsg_eventlist_icon_draw.png "vsg_eventlist_icon_draw")|繪製事件<br /> 標記在所擷取之畫面格期間發生的繪製事件。|  
|![使用者定義的事件標記圖示](../debugger/media/vsg_eventlist_icon_user.png "vsg_eventlist_icon_user")|使用者定義事件群組<br /> 群組應用程式所定義的相關事件。|  
|![使用者定義的事件標記圖示](../debugger/media/vsg_eventlist_icon_user.png "vsg_eventlist_icon_user")|使用者定義事件標記<br /> 標記應用程式所定義的特定位置。|  
  
## <a name="marking-user-defined-events-in-your-app"></a>標記應用程式中的使用者定義事件  
 使用者定義事件是您應用程式特有的。 您可以使用它們，將應用程式中發生的重大事件與 [圖形事件清單] 中的事件相互關聯。 例如，您可以建立使用者定義事件群組，以將相關事件 (如呈現使用者介面的事件) 組織成群組或階層，讓您可以更輕鬆地瀏覽事件清單，也可以在繪製特定類型的物件時建立標記，讓您可以更輕鬆地在事件清單中找到其圖形事件。  
  
 若要在應用程式中建立群組和標記，請使用 Direct3D 所提供，以供其他 Direct3D 偵錯工具使用的相同 API。 這些 API 在 Direct3D 版本之間有時會變更，但是基本功能相同。  
  
### <a name="user-defined-events-in-direct3d-12"></a>Direct3D 12 中的使用者定義事件  
 若要在 Direct3D 12 中建立群組和標記，請使用本節所述的 API。 下表總結根據您要標記命令佇列還是命令清單中的事件而可以使用的 API。  
  
|API 描述|[ID3D12CommandQueue](https://msdn.microsoft.com/library/dn788627.aspx)|[ID3D12GraphicsCommandList](https://msdn.microsoft.com/library/dn903537.aspx)|  
|---------------------|----------------------------------------------------------------------------|-----------------------------------------------------------------------------------|  
|檢查使用者定義事件可用性|[PIXGetStatus](http://msdn.microsoft.com/zh-tw/f7ebd985-fb5d-46d7-abec-099df4b9be0e)|[PIXGetStatus](http://msdn.microsoft.com/zh-tw/1046ac43-a0a3-42bf-bae8-14aa72fa7567)|  
|開始事件群組|[PIXBeginEvent](http://msdn.microsoft.com/zh-tw/5f51fff7-f313-4558-965b-2a443653cd7b)|[PIXBeginEvent](http://msdn.microsoft.com/zh-tw/4ddb3311-b9b5-449a-bbfb-7634e0d56e87)|  
|結束事件群組|[PIXEndEvent](http://msdn.microsoft.com/zh-tw/fb526bf2-c17d-4a2a-8665-3b577a0f7fba)|[PIXEndEvent](http://msdn.microsoft.com/zh-tw/a3cd34a9-9dd9-40e1-ae86-0214b25ff185)|  
|建立事件標記|[PIXSetMarker](http://msdn.microsoft.com/zh-tw/0caf49ed-c99d-405e-89f4-0c887b8474ad)|[PIXSetMarker](http://msdn.microsoft.com/zh-tw/6610e5b9-a0c5-4236-b551-b6eb9fac64c1)|  
  
### <a name="user-defined-events-in-direct3d-11-and-earlier"></a>Direct3D 11 和更早版本中的使用者定義事件  
 若要在 Direct3D 11 或更早版本中建立群組和標記，請使用本節所述的 API。 下表總結您可用於不同 Direct3D 11 版本和舊版 Direct3D 的 API。  
  
|API 描述|[ID3D11DeviceContext2](http://msdn.microsoft.com/library/windows/desktop/dn280498.aspx) (Direct3D 11.2)|[ID3DUserDefinedAnnotation](http://go.microsoft.com/fwlink/p/?LinkID=250967) (Direct3D 11.1)|D3DPerf_ API 系列 (Direct3D 11.0 和更早版本)|  
|---------------------|---------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------|--------------------------------------------------------|  
|開始事件群組|`BeginEventInt`|`BeginEvent`|`D3DPerf_BeginEvent`|  
|結束事件群組|`EndEventInt`|`EndEvent`|`D3DPerf_EndEvent`|  
|建立事件標記|`SetMarkerInt`|`SetMarker`|`D3DPerf_SetMarker`|  
  
 您可以使用 Direct3D 版本所支援的這些 API 之一 (例如，如果您的目標設為 Direct3D 11.1 API，則可以使用 `SetMarker` 或 `D3DPerf_SetMarker` 建立事件標記，而非 `SetMarkerInt` ，因為它只適用於 Direct3D 11.2)，還可以在相同的應用程式中，混合使用支援不同版本的 Direct3D 的 API。  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說：因裝置狀態而遺漏的物件](../debugger/walkthrough-missing-objects-due-to-device-state.md)