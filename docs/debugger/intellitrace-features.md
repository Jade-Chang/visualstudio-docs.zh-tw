---
title: "IntelliTrace 功能 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "偵錯 [Visual Studio ALM], IntelliTrace"
  - "偵錯 [Visual Studio ALM], 錄製執行記錄"
  - "IntelliTrace, 使用事件偵錯"
  - "IntelliTrace, 使用事件和呼叫資訊偵錯"
  - "IntelliTrace, 停用"
  - "IntelliTrace, 啟用"
  - "IntelliTrace, 巡覽事件和呼叫記錄"
  - "IntelliTrace, 錄製執行記錄"
  - "IntelliTrace, 儲存工作階段"
  - "IntelliTrace, 開始偵錯"
  - "IntelliTrace, 關閉"
  - "IntelliTrace, 開啟"
ms.assetid: 5ccc059c-6097-46b4-9d4b-34236c02d549
caps.latest.revision: 67
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 67
---
# IntelliTrace 功能
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以使用 IntelliTrace 記錄您應用程式的事件和方法呼叫，以讓您檢查它在執行之不同時間點的狀態 \(呼叫堆疊和區域變數值\)。  只要如常開始偵錯 \- 預設會開啟 IntelliTrace，而您可以在新 \[診斷工具\] 視窗的 \[事件\] 索引標籤中查看 IntelliTrace 所記錄的資訊。  選取事件，然後按一下 \[啟用歷程偵錯\] 以查看針對此事件記錄的呼叫堆疊和區域變數。  
  
 如需逐步說明，請參閱[逐步解說：使用 IntelliTrace](../debugger/walkthrough-using-intellitrace.md)。  
  
 Visual Studio Enterprise 版本 \(而非 Visual Studio Professional 或 Community 版本\) 中提供 IntelliTrace。  
  
 若要確認已開啟 IntelliTrace，請開啟 \[工具\] \/ \[選項\] \/ \[IntelliTrace\] 選項頁面。  預設應該會核取 \[啟用 IntelliTrace\]。  
  
> [!NOTE]
>  \[IntelliTrace\] 選項頁面上所有設定的範圍是整個 Visual Studio，而不是個別專案或方案。  這些設定的變更會套用至所有 Visual Studio 執行個體、所有偵錯工作階段，以及所有專案或方案。  
  
##  <a name="ChooseEvents"></a> 選擇 IntelliTrace 所記錄的事件  
 您可以開啟或關閉特定 IntelliTrace 事件的記錄。  
  
 如果您正在偵錯，請停止偵錯。  移至 \[工具\] \/ \[選項\] \/ \[IntelliTrace\] \/ \[IntelliTrace 事件\]。  選擇您要 IntelliTrace 記錄的事件。  
  
##  <a name="GoingFurther"></a> 收集 IntelliTrace 事件和呼叫資訊  
 這預設不會予以啟用，但 IntelliTrace 可以記錄方法呼叫和事件。  若要啟用方法呼叫的收集，請移至 \[工具\] \/ \[選項\] \/ \[IntelliTrace\] \/ \[一般\]，然後選取 \[IntelliTrace 事件和呼叫資訊\]。  
  
 這可讓您查看呼叫堆疊記錄，並在程式碼中逐步返回及逐步前進。  IntelliTrace 會記錄資料 \(例如方法名稱、方法進入點與結束點，以及特定參數值與傳回值\)。  
  
> [!TIP]
>  預設不會啟用此選項，因為這樣會增加可觀的額外負荷。  IntelliTrace 不只需要攔截您應用程式所進行的每個方法呼叫，還需要在將它顯示在螢幕上或將它保存到磁碟時處理更大的資料集。  
>   
>  限制 IntelliTrace 所記錄的事件清單，以及將所收集的模組數目保持為最小值，即可減少效能額外負荷。  如需詳細資訊，請參閱[控制 IntelliTrace 記錄多少呼叫資訊](../debugger/intellitrace-features.md#ControlCallData)。  
  
### 使用巡覽邊  
 您可以使用出現在程式碼視窗左邊的巡覽邊。  如果您看不到巡覽邊，請移至 \[工具\] \/ \[選項\] \/ \[IntelliTrace\] \/ \[進階\]，然後選取 \[在偵錯模式中顯示巡覽邊\]。  
  
 巡覽邊可讓您以歷程偵錯模式向前及向後移動方法呼叫和事件。  如需歷程偵錯的詳細資訊，請參閱[歷程偵錯](../debugger/historical-debugging.md)。  它有一些命令：  
  
|||  
|-|-|  
|**在此設定偵錯工具內容**|將偵錯內容設定為它所在的呼叫時間範圍。<br /><br /> 這個圖示只會出現在目前呼叫堆疊上。|  
|**返回呼叫位置**|將游標和偵錯內容向後移至呼叫目前函式的位置。<br /><br /> 如果您使用 \[即時偵錯\] 模式，此命令會開啟 \[歷程偵錯\]。  如果您導覽回到原始執行中斷，則會關閉 \[歷程偵錯\] 並開啟 \[即時偵錯\]。|  
|**移至上一個呼叫或 IntelliTrace 事件**|將游標和偵錯內容向後移至上一個呼叫或事件。<br /><br /> 如果您使用 \[即時偵錯\] 模式，此命令會開啟 \[歷程偵錯\]。|  
|**逐步執行**|逐步執行目前選取的函式。<br /><br /> 只有在您使用 \[歷程偵錯\] 模式時，才能使用這個命令。|  
|**移至下一個呼叫或 IntelliTrace 事件**|將指標和偵錯內容向前移至存在 IntelliTrace 資料的下一個呼叫或事件。<br /><br /> 只有在您使用 \[歷程偵錯\] 模式時，才能使用這個命令。|  
|**移至即時模式**|返回 \[即時偵錯\] 模式。|  
  
### 在 IntelliTrace 中搜尋某行或方法  
 只有在已啟用方法呼叫資訊時，才能搜尋方法。  您可以搜尋特定行或方法的 IntelliTrace 歷程。  偵錯工具執行停止時，以滑鼠右鍵按一下函式主體來查看內容功能表，然後按一下 \[在 IntelliTrace 中搜尋這一行\] 或 \[在 IntelliTrace 中搜尋這個方法\]。  
  
###  <a name="ControlCallData"></a> 控制 IntelliTrace 記錄多少呼叫資訊  
 IntelliTrace 預設會記錄您方案所使用之所有模組的資訊。  您可以設定 IntelliTrace 只記錄您感興趣之模組的呼叫資訊。  在 \[工具\] \/ \[選項\] \/ \[IntelliTrace\] \/ \[模組\] 中，您可以指定要包括的模組或要從 IntelliTrace 排除的模組。  IntelliTrace 只會收集源自所指定模組的事件，以及在您感興趣的模組內發生的方法呼叫。  
  
 若要加入多個模組，請在字串開頭或結尾使用萬用字元 \*。  模組名稱必須使用檔案名稱，而非組件名稱。  不接受檔案路徑。  
  
 嘗試將模組數目保持為最小值。  因為要收集的資料比較少，所以效能會更好。  因為通過的資料較少，所以 UI 中的雜訊也會較少。  
  
##  <a name="SaveSession"></a> 將 IntelliTrace 資料儲存至檔案  
 如果您正在進行偵錯，而且應用程式處於中斷狀態，則可以移至 \[偵錯\] \/ \[IntelliTrace\] \/ \[儲存 IntelliTrace 工作階段\] 來儲存 IntelliTrace 已收集的資料。  已停用此功能表項目，因此，如果應用程式仍在執行，或您已停止偵錯，則無法儲存 IntelliTrace 已收集的資料。  
  
 移至 \[工具\] \/ \[選項\] \/ \[IntelliTrace\] \/ \[進階\]，然後選取 \[將 IntelliTrace 記錄儲存在這個目錄\]，即可設定 IntelliTrace 自動儲存至檔案。  您也可以設定為產生的檔案所設定的大小，而這樣會讓 IntelliTrace 在空間不足時覆寫較舊的資料。  自動儲存 IntelliTrace 工作階段時，以及 Visual Studio 裝載處理序 \(vshost.exe\) 開啟時，Visual Studio 會針對每個工作階段建立兩個檔案。  
  
> [!TIP]
>  為了節省磁碟空間，當您不再需要它們時，請關閉自動儲存檔案。  系統不會刪除所有現有檔案。  您一律可以從內容功能表依需要儲存至檔案。  
  
 將 IntelliTrace 資料儲存至檔案時，IntelliTrace 從中收集的每個處理序都會有一個 .itrace 檔案。  之後，移至 \[檔案\] \/ \[開啟\] \/ \[檔案\]，然後從 \[開啟檔案\] 對話方塊中選取 .itrace 檔案，即可在 Visual Studio 中開啟 .itrace 檔案。  如需詳細資訊，請參閱[使用儲存的 IntelliTrace 資料偵錯應用程式](../debugger/using-saved-intellitrace-data.md)。  
  
## 網誌  
 [Visual Studio Enterprise 2015 中的 IntelliTrace](http://blogs.msdn.com/b/visualstudioalm/archive/2015/01/16/intellitrace-in-visual-studio-ultimate-2015.aspx)  
  
 [在 Visual Studio 2015 \(文字編輯器\) 中使用 IntelliTrace 即時偵錯的逐步解說](http://blogs.msdn.com/b/visualstudioalm/archive/2015/01/16/walkthrough-of-live-debugging-using-intellitrace-in-visual-studio-2015-text-editor.aspx)  
  
 [在 Visual Studio 2015 \(社團\) 中使用 IntelliTrace 即時偵錯的逐步解說](http://blogs.msdn.com/b/visualstudioalm/archive/2000/1/1/walkthrough-of-live-debugging-using-intellitrace-in-visual-studio-2015-social-club.aspx)  
  
 [Visual Studio Enterprise 2015 中的 IntelliTrace 現在支援附加！](http://blogs.msdn.com/b/visualstudioalm/archive/2015/05/14/intellitrace-in-visual-studio-enterprise-2015-now-supports-attach.aspx)。  
  
 [使用 IntelliTrace 獨立收集器收集來自 Windows 服務的資料](http://blogs.msdn.com/b/visualstudioalm/archive/2015/05/14/collect-data-from-a-windows-service-using-the-intellitrace-standalone-collector.aspx)  
  
 [編輯 IntelliTrace 收集計畫](http://blogs.msdn.com/b/visualstudioalm/archive/2015/03/09/editing-the-intellitrace-collection-plan.aspx)  
  
 [使用 IntelliTrace 的自訂 TraceSource 和偵錯](http://blogs.msdn.com/b/visualstudioalm/archive/2014/12/17/custom-tracesource-and-debugging-using-intellitrace.aspx)  
  
 [在 Active Directory 帳戶下執行的 IntelliTrace 獨立收集器和應用程式集區](http://blogs.msdn.com/b/visualstudioalm/archive/2014/12/22/intellitrace-standalone-collector-and-application-pools-running-under-active-directory-accounts.aspx)  
  
## 論壇  
 [Visual Studio Debugger](http://go.microsoft.com/fwlink/?LinkId=262263)  
  
## 視訊  
 [IntelliTrace 經驗](https://channel9.msdn.com/Series/Visual-Studio-2015-Enterprise-Videos/IntelliTrace-Experience)  
  
 [Microsoft Visual Studio Ultimate 2015 中的 IntelliTrace 歷程偵錯](https://channel9.msdn.com/events/Ignite/2015/BRK3716)