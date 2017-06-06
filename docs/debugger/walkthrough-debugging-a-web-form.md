---
title: "逐步解說：偵錯 Web Form | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ASP.NET Web 網頁, 偵錯"
  - "ASP.NET 網站, 偵錯"
  - "ASP.NET, 偵錯 Web 應用程式"
  - "偵錯 [Visual Studio], Web Form"
  - "偵錯 ASP.NET Web 應用程式, Web Form"
  - "Web 應用程式 [.NET Framework], 偵錯"
  - "Web 網頁 [.NET Framework], 偵錯"
  - "網站 [.NET Framework], 偵錯"
ms.assetid: e2b4fa14-8f5b-444d-a903-54070b784bd4
caps.latest.revision: 31
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 31
---
# 逐步解說：偵錯 Web Form
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

這個逐步解說中的步驟將示範如何偵錯 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 應用程式 \(也稱為 Web Form\)。  它會向您示範如何啟動及停止執行、設定中斷點，以及在 \[**監看式**\] 視窗中檢查變數。  
  
> [!NOTE]
>  若要完成本逐步解說，您在伺服器電腦中必須具有系統管理員權限。  根據預設，[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 處理序 aspnet\_wp.exe 或 w3wp.exe 會做為 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 處理序執行。  若要對 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 進行偵錯，您必須在 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 執行的電腦上具有系統管理員權限。  如需詳細資訊，請參閱 [系統需求](../debugger/aspnet-debugging-system-requirements.md)。  
  
 根據目前使用的設定與版本，您所看到的對話方塊與功能表命令可能會與 \[說明\] 中所描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要建立 Web Form  
  
1.  如果您已經開啟方案，請將其關閉。  
  
2.  在 \[**檔案**\] 功能表上按一下 \[**新增**\]，然後按一下 \[**網站**\]。  
  
     \[**新網站**\] 對話方塊隨即出現。  
  
3.  在 \[**範本**\] 窗格中按一下 \[**ASP.NET 網站**\]。  
  
4.  在 \[**位置**\] 行中從清單按一下 \[**HTTP**\]，然後在文字方塊中輸入 http:\/\/localhost\/WebSite。  
  
5.  在 \[**語言**\] 清單中，按一下 \[**Visual C\#**\] 或 \[**Visual Basic**\]。  
  
6.  按一下 \[**確定**\]。  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 會建立新的專案，並且顯示預設的 HTML 原始程式碼。  它也會在 IIS 內的 \[**預設的網站**\] 底下建立名為 \[**網站**\] 的新虛擬目錄。  
  
7.  按一下下方邊界上的 \[**設計**\] 索引標籤。  
  
8.  按一下左邊界的 \[**工具箱**\] 索引標籤，或是在 \[**檢視**\] 功能表上選取它。  
  
     \[**工具箱**\] 會開啟。  
  
9. 按一下 \[**工具箱**\] 中的 \[**Button**\] 控制項，然後將該控制項加入至主要設計介面 Default.aspx。  
  
10. 在 \[**工具箱**\] 中按一下 \[**Textbox**\] 控制項，然後將該控制項拖曳到主要設計介面 Default.aspx。  
  
11. 在您所放置的 Button 控制項上按兩下。  
  
     這會帶您前往字碼頁：Default.aspx.cs \(C\#\) 或 Default.aspx.vb \([!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\)。  資料指標 \(Cursor\) 應該在 `Button1_Click` 函式中。  
  
12. 在 `Button1_Click` 函式中，加入下列程式碼：  
  
    ```  
    ' Visual Basic  
    TextBox1.Text = "Button was clicked!"  
  
    // C#  
    TextBox1.Text = "Button was clicked!";  
    ```  
  
13. 在 \[**建置**\] 功能表上，按一下 \[**建置方案**\]。  
  
     專案應該會建置而無錯誤。  
  
     現在，您可以開始偵錯。  
  
### 若要偵錯 Web Form  
  
1.  在 Default.aspx.cs 或 Default.aspx.vb 視窗中，在與您所加入之文字同一行的左邊界按一下：  
  
    ```  
    ' Visual Basic  
    TextBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!";  
    ```  
  
     會出現一個紅點，並且該行上的文字會以紅色反白顯示。  紅點表示中斷點。  當您在偵錯工具下執行應用程式時，偵錯工具會在遇到程式碼的位置中斷執行。  接著您就可以檢視應用程式的狀態並對它進行偵錯。  如需詳細資訊，請參閱[中斷點](http://msdn.microsoft.com/zh-tw/fe4eedc1-71aa-4928-962f-0912c334d583)。  
  
2.  按一下 \[**偵錯**\] 功能表上的 \[**開始偵錯**\]。  
  
3.  \[**未啟用偵錯**\] 對話方塊會出現。  選取 \[**修改 Web.config 檔以啟用偵錯**\] 選項，然後按一下 \[**確定**\]。  
  
     Internet Explorer 就會啟動並顯示您剛才設計的網頁。  
  
4.  在 Internet Explorer 中按一下按鈕。  
  
     在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中，這會帶您前往在 Default.aspx.cs 或 Default.aspx.vb 字碼頁上設定中斷點的程式行位置。  這行程式碼應該會以黃色反白顯示。  您現在可以檢視應用程式中的變數並控制其執行。  您的應用程式會停止執行並等候您的命令。  
  
5.  在 \[**偵錯**\] 功能表中按一下 \[**視窗**\]，然後按一下 \[**監看式**\]，再按一下 \[**Watch1**\]。  
  
6.  在 \[**監看式**\] 視窗中輸入 TextBox1.Text。  
  
     \[**監看式**\] 視窗會顯示 `TextBox1.Text` 變數的值：  
  
    ```  
    ""  
    ```  
  
7.  按一下 \[**偵錯**\] 功能表上的 \[**不進入函式**\]。  
  
     `TextBox1.Text` 的值會在 \[**監看式**\] 視窗中變更，讀取如下：  
  
    ```  
    "Button was clicked!"  
    ```  
  
8.  在 \[**偵錯**\] 功能表上按一下 \[**繼續**\]。  
  
9. 在 Internet Explorer 中的該按鈕上再按一下。  
  
     執行會在中斷點再次停止。  
  
10. 在 Default.aspx.cs 或 Default.aspx.vb 視窗中按一下左邊界上的紅點。  
  
     這會移除中斷點。  
  
11. 在 \[**偵錯**\] 功能表上，按一下 \[**停止偵錯**\]。  
  
### 若要附加至 Web Form 來進行偵錯  
  
1.  在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中，您可以將偵錯工具附加至執行中的處理序。  若要以最有效的方式來偵錯，請將可執行檔編譯為具有符號 \(PDB\) 檔案的偵錯版本。  
  
2.  在 Default.aspx.cs 或 Default.aspx.vb 視窗中按一下左邊界，以再次於您加入的程式行設定中斷點：  
  
    ```  
    ' Visual Basic  
    TextBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!";  
    ```  
  
3.  在 \[**偵錯**\] 功能表上，請按 \[**啟動但不偵錯**\]。  
  
     Web Form 會開始在 Internet Explorer 下執行，但不會附加偵錯工具。  
  
4.  附加至 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 處理序。  如需詳細資訊，請參閱[偵錯已部署的 Web 應用程式](../debugger/debugging-deployed-web-applications.md)。  
  
5.  在 Internet Explorer 中按一下您表單上的按鈕。  
  
     在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中，您應該在 Default.aspx.cs、Default.aspx.vb 或 Default.aspx 叫用中斷點。  
  
6.  完成偵錯後，請按一下 \[**偵錯**\] 功能表上的 \[**停止偵錯**\]。  
  
## 請參閱  
 [偵錯 ASP.NET 和 AJAX 應用程式](../debugger/debugging-aspnet-and-ajax-applications.md)