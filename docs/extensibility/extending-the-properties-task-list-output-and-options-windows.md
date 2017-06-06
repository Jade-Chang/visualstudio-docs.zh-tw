---
title: "擴充屬性、 工作清單、 輸出和選項 視窗 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- properties pane
- task list
- output window
- properties window
- tutorials
- tool windows
ms.assetid: 06990510-5424-44b8-9fd9-6481acec5c76
caps.latest.revision: 37
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 75937e3f2cf1d3fa9c5c78de8b7df5f8869ef49e
ms.lasthandoff: 02/22/2017

---
# <a name="extending-the-properties-task-list-output-and-options-windows"></a>擴充屬性、 工作清單、 輸出和選項 視窗
您可以存取 Visual Studio 中的任何工具視窗。 本逐步解說示範如何整合到新的工具視窗的相關資訊**選項**頁面和新的設定上**屬性** 頁面上，以及如何將寫入**工作清單**和**輸出**windows。  
  
## <a name="prerequisites"></a>必要條件  
 啟動 Visual Studio 2015 中，您未安裝 Visual Studio SDK 從 「 下載中心 」。 它是 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="create-an-extension-with-a-tool-window"></a>建立擴充功能與工具視窗  
  
1.  建立專案，名為**TodoList**使用 VSIX 的範本，並新增名為的自訂工具視窗項目範本**TodoWindow**。  
  
    > [!NOTE]
    >  如需使用工具視窗建立擴充功能的詳細資訊，請參閱[建立擴充功能與工具視窗](../extensibility/creating-an-extension-with-a-tool-window.md)。  
  
## <a name="set-up-the-tool-window"></a>設定工具視窗  
 新增的文字方塊中輸入新的 ToDo 項目，若要加入至清單中，新的項目按鈕和清單方塊中的項目顯示在清單上。  
  
1.  在 TodoWindow.xaml，刪除按鈕、 文字方塊和 StackPanel 控制項從 使用者控制項。  
  
    > [!NOTE]
    >  這並不會刪除**button1_Click**事件處理常式，您將會重複使用在稍後的步驟。  
  
2.  從**所有 WPF 控制項**區段**工具箱**，拖曳**畫布**方格控制項。  
  
3.  拖放到**文字方塊**、**按鈕**，和**ListBox**在畫布上。 排列項目，讓文字方塊和按鈕位於相同層級和清單方塊會填入下方，如下列圖片所示的視窗的其餘部分。  
  
     ![完成工具視窗](../extensibility/media/t5-toolwindow.png "T5 工具視窗")  
  
4.  在 [XAML] 窗格中，尋找按鈕並將其內容的屬性設定為**新增**。 重新連接 按鈕控制項的按鈕事件處理常式加入`Click="button1_Click"`屬性。 畫布區塊看起來應該像這樣︰  
  
    ```xml  
    <Canvas HorizontalAlignment="Left" Width="306">  
        <TextBox x:Name="textBox" HorizontalAlignment="Left" Height="23" Margin="10,10,0,0" TextWrapping="Wrap" Text="TextBox" VerticalAlignment="Top" Width="208"/>  
            <Button x:Name="button" Content="Add" HorizontalAlignment="Left" Margin="236,13,0,0" VerticalAlignment="Top" Width="48" Click="button1_Click"/>  
            <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="222" Margin="10,56,0,0" VerticalAlignment="Top" Width="274"/>  
    </Canvas>  
    ```  
  
#### <a name="customize-the-constructor"></a>自訂建構函式  
  
1.  在 TodoWindowControl.xaml.cs 檔案中，新增下列 using 陳述式︰  
  
    ```c#  
    using System;  
    ```  
  
2.  新增公用 TodoWindow 參考，並有 TodoWindowControl 建構函式會採用 TodoWindow 參數。 程式碼看起來應該像這樣︰  
  
    ```c#  
    public TodoWindow parent;  
  
    public TodoWindowControl(TodoWindow window)  
    {  
        InitializeComponent();  
        parent = window;  
    }  
    ```  
  
3.  在 TodoWindow.cs，變更為包含 TodoWindow 參數 TodoWindowControl 建構函式。 程式碼看起來應該像這樣︰  
  
    ```c#  
    public TodoWindow() : base(null)  
    {  
        this.Caption = "TodoWindow";  
        this.BitmapResourceID = 301;  
        this.BitmapIndex = 1;  
  
         this.Content = new TodoWindowControl(this);  
    }  
    ```  
  
## <a name="create-an-options-page"></a>建立選項 頁面  
 您可以提供分頁**選項**對話方塊，讓使用者可以變更工具視窗的設定。 建立選項 頁面上，需要兩個類別，描述的選項和 TodoListPackage.cs 或 TodoListPackage.vb 檔案中的項目。  
  
1.  新增名為`ToolsOptions.cs`。 使 ToolsOptions 類別繼承自<xref:Microsoft.VisualStudio.Shell.DialogPage>。</xref:Microsoft.VisualStudio.Shell.DialogPage>  
  
    ```c#  
    class ToolsOptions : DialogPage  
    {  
    }  
    ```  
  
2.  新增下列 using 陳述式︰  
  
    ```c#  
    using Microsoft.VisualStudio.Shell;  
    ```  
  
3.  本逐步解說中的 [選項] 頁面會提供名為 DaysAhead 只有一個選項。 新增名為私用欄位**daysAhead**和屬性，名為**DaysAhead** ToolsOptions 類別︰  
  
    ```c#  
    private double daysAhead;  
  
    public double DaysAhead  
    {  
        get { return daysAhead; }  
        set { daysAhead = value; }  
    }  
    ```  
  
 現在您必須先知道這個選項頁面專案。  
  
#### <a name="make-the-options-page-available-to-users"></a>讓使用者使用 [選項] 頁面  
  
1.  在 TodoWindowPackage.cs，加入<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>TodoWindowPackage 類別︰</xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>  
  
    ```c#  
    [ProvideOptionPage(typeof(ToolsOptions), "ToDo", "General", 101, 106, true)]  
    ```  
  
2.  ProvideOptionPage 建構函式的第一個參數是類別 ToolsOptions，您稍早建立的型別。 第二個參數，也就是"ToDo"，是在類別目錄名稱**選項**對話方塊。 第三個參數，[一般]，為的子類別名稱**選項**會使用 [選項] 頁面的對話方塊。 下面兩個參數是資源識別碼字串。第一個是類別目錄的名稱，而第二個是子類別目錄的名稱。 最後一個參數會決定是否可以使用自動化來存取此頁面。  
  
     當使用者開啟選項頁面時，它應該類似下列圖片。  
  
     ![選項頁面](../extensibility/media/t5optionspage.gif "T5OptionsPage")  
  
     請注意分類**ToDo**和子類別目錄**一般**。  
  
## <a name="make-data-available-to-the-properties-window"></a>讓資料可供 [屬性] 視窗  
 您可以提供待辦清單資訊建立名為個別項目的相關資訊儲存在待辦事項 清單中的 TodoItem 類別。  
  
1.  新增名為`TodoItem.cs`。  
  
     使用者可以使用 [工具] 視窗時，都會由 TodoItems 表示清單方塊中的項目。 當使用者選取其中一個項目在清單方塊中，**屬性**視窗將顯示項目的相關資訊。  
  
     若要啟用資料在**屬性** 視窗中，您將資料轉換有兩個的特殊屬性的公用屬性`Description`和`Category`。 `Description`會顯示在底部的文字**屬性**視窗。 `Category`決定屬性應該會出現時**屬性**視窗會顯示在**分類**檢視。 在下列圖片中，**屬性**視窗處於**分類** 檢視中，**名稱**屬性**ToDo 欄位**所選取的類別，和描述**名稱**屬性會顯示在視窗底部。  
  
     ![[屬性] 視窗](../extensibility/media/t5properties.png "T5Properties")  
  
2.  新增下列 using 陳述式 TodoItem.cs 檔案。  
  
    ```c#  
    using System.ComponentModel;  
    using System.Windows.Forms;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
3.  新增`public`在類別宣告的存取修飾詞。  
  
    ```c#  
    public class TodoItem  
    {  
    }  
    ```  
  
     加入兩個屬性名稱和 DueDate。 UpdateList() 和 CheckForErrors() 再處理。  
  
    ```c#  
    public class TodoItem  
    {  
        private TodoWindowControl parent;  
        private string name;  
        [Description("Name of the ToDo item")]  
        [Category("ToDo Fields")]  
        public string Name  
        {  
            get { return name; }  
            set  
            {  
                name = value;  
                parent.UpdateList(this);  
            }  
        }  
  
        private DateTime dueDate;  
        [Description("Due date of the ToDo item")]  
        [Category("ToDo Fields")]  
        public DateTime DueDate  
        {  
            get { return dueDate; }  
            set  
            {  
                dueDate = value;  
                parent.UpdateList(this);  
                parent.CheckForErrors();  
            }  
        }  
    }  
    ```  
  
4.  加入至使用者控制項的私用參考。 新增的建構函式會採用使用者控制項和此 ToDo 項目的名稱。 若要尋找 daysAhead 值，它會取得選項頁面屬性。  
  
    ```c#  
    private TodoWindowControl parent;  
  
    public TodoItem(TodoWindowControl control, string itemName)  
    {  
        parent = control;  
        name = itemName;  
        dueDate = DateTime.Now;  
  
        double daysAhead = 0;  
        IVsPackage package = parent.parent.Package as IVsPackage;  
        if (package != null)  
        {  
            object obj;  
            package.GetAutomationObject("ToDo.General", out obj);  
  
            ToolsOptions options = obj as ToolsOptions;  
            if (options != null)  
            {  
                daysAhead = options.DaysAhead;  
            }  
        }  
  
        dueDate = dueDate.AddDays(daysAhead);  
    }  
    ```  
  
5.  因為執行個體的`TodoItem`類別會儲存在清單方塊和清單方塊會呼叫`ToString`函式，您必須同時多載`ToString`函式。 建構函式之後，以及類別的結尾之前 TodoItem.cs，加入下列程式碼。  
  
    ```c#  
    public override string ToString()  
    {  
        return name + " Due: " + dueDate.ToShortDateString();  
    }  
    ```  
  
6.  TodoWindowControl.xaml.cs，在類別中新增虛設常式方法 TodoWindowControl 的`CheckForError`和`UpdateList`方法。 ProcessDialogChar 之後，以及檔案的結尾之前，請將他們。  
  
    ```c#  
    public void CheckForErrors()  
    {  
    }  
    public void UpdateList(TodoItem item)  
    {  
    }  
    ```  
  
     `CheckForError`方法會呼叫在父物件，具有相同名稱的方法，該方法會檢查是否發生任何錯誤，而正確地處理它們。 `UpdateList`方法會更新的清單方塊中的父控制項; 此方法時，會呼叫`Name`和`DueDate`類別改變的屬性。 它們會稍後實作。  
  
## <a name="integrate-into-the-properties-window"></a>整合到 [屬性] 視窗  
 現在撰寫程式碼，可管理將繫結至 ListBox**屬性**視窗。  
  
 您必須變更按鈕 click 處理常式來讀取文字方塊中，建立 TodoItem，並將它加入至清單方塊。  
  
1.  取代現有`button1_Click`函式的程式碼會建立新的 TodoItem，並將它加入至清單方塊。 它會呼叫 TrackSelection()，稍後定義。  
  
    ```c#  
    private void button1_Click(object sender, RoutedEventArgs e)  
    {  
        if (textBox.Text.Length > 0)  
        {  
            var item = new TodoItem(this, textBox.Text);  
            listBox.Items.Add(item);  
            TrackSelection();  
            CheckForErrors();  
        }  
    }  
    ```  
  
2.  在 [設計] 檢視中選取的清單方塊控制項。 在**屬性**視窗中，按一下**事件處理常式**按鈕，然後找出 SelectionChanged 事件。 在文字方塊中，以填滿**listBox_SelectionChanged**。 如此一來新增虛設常式 SelectionChanged 處理常式，並將它指派給事件。  
  
3.  實作 TrackSelection() 方法。 由於您需要取得<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell><xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>服務，您需要設定<xref:Microsoft.VisualStudio.Shell.WindowPane.GetService%2A>供 TodoWindowControl。</xref:Microsoft.VisualStudio.Shell.WindowPane.GetService%2A> </xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection></xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> 將下列方法加入至 TodoWindow 類別︰  
  
    ```  
    internal object GetVsService(Type service)  
    {  
        return GetService(service);  
    }  
    ```  
  
4.  新增下列 using 陳述式 TodoWindowControl.xaml.cs:  
  
    ```c#  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.Shell.Interop;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Shell;  
    ```  
  
5.  填入 SelectionChanged 處理常式，如下所示︰  
  
    ```  
    private void listBox_SelectionChanged(object sender, SelectionChangedEventArgs e)  
    {  
        TrackSelection();  
    }  
    ```  
  
6.  現在，在 TrackSelection 函數中，將會提供整合的填滿**屬性**視窗。 當使用者將項目加入至清單方塊，或按一下清單方塊中的項目時，會呼叫此函數。 它將清單方塊的內容加入 SelectionContainer 並傳遞至 SelectionContainer**屬性**視窗的<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A>事件處理常式。</xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> TrackSelection 服務會追蹤使用者介面 (UI) 中選取的物件，並顯示其屬性  
  
    ```c#  
    private SelectionContainer mySelContainer;  
    private System.Collections.ArrayList mySelItems;  
    private IVsWindowFrame frame = null;  
  
    private void TrackSelection()  
    {  
        if (frame == null)  
        {  
            var shell = parent.GetVsService(typeof(SVsUIShell)) as IVsUIShell;  
            if (shell != null)  
            {  
                var guidPropertyBrowser = new  
                Guid(ToolWindowGuids.PropertyBrowser);  
                shell.FindToolWindow((uint)__VSFINDTOOLWIN.FTW_fForceCreate,  
                ref guidPropertyBrowser, out frame);  
            }  
        }  
        if (frame != null)  
            {  
                frame.Show();  
            }  
        if (mySelContainer == null)  
        {  
            mySelContainer = new SelectionContainer();  
        }  
  
        mySelItems = new System.Collections.ArrayList();  
  
        var selected = listBox.SelectedItem as TodoItem;  
        if (selected != null)  
        {  
            mySelItems.Add(selected);  
        }  
  
        mySelContainer.SelectedObjects = mySelItems;  
  
        ITrackSelection track = parent.GetVsService(typeof(STrackSelection))  
                                as ITrackSelection;  
        if (track != null)  
        {  
            track.OnSelectChange(mySelContainer);  
        }  
    }  
    ```  
  
     現在，您有一個類別，**屬性** 視窗中可以使用，您可以整合**屬性**視窗在工具視窗。 當使用者按一下 [工具] 視窗中，在清單方塊中的項目**屬性**視窗應該隨之更新。 同樣地，當使用者變更中的 ToDo 項目**屬性** 視窗中，應該更新相關的項目。  
  
7.  現在，在 TodoWindowControl.xaml.cs 加入 UpdateList 函式程式碼的其餘部分。 它應該卸除並重新加入修改過的 TodoItem 從清單方塊。  
  
    ```c#  
    public void UpdateList(TodoItem item)  
    {  
        var index = listBox.SelectedIndex;  
        listBox.Items.RemoveAt(index);  
        listBox.Items.Insert(index, item);  
        listBox.SelectedItem = index;  
    }  
    ```  
  
8.  測試您的程式碼。 建置此專案並開始偵錯。 實驗執行個體應該會出現。  
  
9. 開啟**工具 / 選項**頁面。 您應該會看到 ToDo 類別，在左窗格中。 分類會列在依字母順序排列，所以請查看 Ts。  
  
10. 在 [待辦事項選項] 頁面中，您應該會看到 DaysAhead 屬性設定為**0**。 將它變更為**2**。  
  
11. 在 [檢視 / 其他視窗] 功能表上，開啟**TodoWindow**。 型別**EndDate**文字方塊中按一下**新增**。  
  
12. 清單方塊中您應該會看到兩個日期晚於今天的日期。  
  
## <a name="add-text-to-the-output-window-and-items-to-the-task-list"></a>將文字加入至輸出視窗] 和 [工作清單項目  
 如**工作清單**，您建立新物件的型別 Task，，然後再新增至該工作物件**工作清單**藉由呼叫其 Add 方法。 要寫入**輸出** 視窗中，您呼叫 GetPane 方法來取得窗格物件，然後再呼叫 OutputString 物件的方法窗格。  
  
1.  中 TodoWindowControl.xaml.cs，在`button1_Click`方法，加入程式碼以取得**一般**窗格**輸出** 視窗中 （這是預設值），並將它寫入。 此方法應該看起來像這樣︰  
  
    ```c#  
    private void button1_Click(object sender, EventArgs e)  
    {  
        if (textBox.Text.Length > 0)  
        {  
            var item = new TodoItem(this, textBox.Text);  
            listBox.Items.Add(item);  
  
            var outputWindow = parent.GetVsService(  
                typeof(SVsOutputWindow)) as IVsOutputWindow;  
            IVsOutputWindowPane pane;  
            Guid guidGeneralPane = VSConstants.GUID_OutWindowGeneralPane;  
            outputWindow.GetPane(ref guidGeneralPane, out pane);  
            if (pane != null)  
            {  
                 pane.OutputString(string.Format(  
                    "To Do item created: {0}\r\n",  
                 item.ToString()));  
        }  
            TrackSelection();  
            CheckForErrors();  
        }  
    }  
    ```  
  
2.  若要將項目加入至工作清單，您必須將巢狀的類別新增至 TodoWindowControl 類別。 巢狀的類別必須衍生自<xref:Microsoft.VisualStudio.Shell.TaskProvider>。</xref:Microsoft.VisualStudio.Shell.TaskProvider> 將下列程式碼加入至 TodoWindowControl 類別的結尾。  
  
    ```c#  
    [Guid("72de1eAD-a00c-4f57-bff7-57edb162d0be")]  
    public class TodoWindowTaskProvider : TaskProvider  
    {  
        public TodoWindowTaskProvider(IServiceProvider sp)  
            : base(sp)  
        {  
        }  
    }  
    ```  
  
3.  接下來將私用參考 TodoTaskProvider 和 CreateProvider() 方法加入至 TodoWindowControl 類別。 程式碼看起來應該像這樣︰  
  
    ```c#  
    private TodoWindowTaskProvider taskProvider;  
    private void CreateProvider()  
    {  
        if (taskProvider == null)  
        {  
            taskProvider = new TodoWindowTaskProvider(parent);  
            taskProvider.ProviderName = "To Do";  
        }  
    }  
    ```  
  
4.  ClearError()，清除 工作清單和 ReportError()，將項目加入至工作清單，加入 TodoWindowControl 類別。  
  
    ```c#  
    private void ClearError()  
    {  
        CreateProvider();  
        taskProvider.Tasks.Clear();  
    }  
    private void ReportError(string p)  
    {  
        CreateProvider();  
        var errorTask = new Task();  
        errorTask.CanDelete = false;  
        errorTask.Category = TaskCategory.Comments;  
        errorTask.Text = p;  
  
        taskProvider.Tasks.Add(errorTask);  
  
        taskProvider.Show();  
  
        var taskList = parent.GetVsService(typeof(SVsTaskList))  
            as IVsTaskList2;  
        if (taskList == null)  
        {  
            return;  
        }  
  
        var guidProvider = typeof(TodoWindowTaskProvider).GUID;  
         taskList.SetActiveProvider(ref guidProvider);  
    }  
    ```  
  
5.  實作了 CheckForErrors 方法，如下所示。  
  
    ```c#  
    public void CheckForErrors()  
    {  
        foreach (TodoItem item in listBox.Items)  
        {  
            if (item.DueDate < DateTime.Now)  
            {  
                ReportError("To Do Item is out of date: "  
                    + item.ToString());  
            }  
        }  
    }  
    ```  
  
## <a name="trying-it-out"></a>嘗試進行  
  
1.  建置此專案並開始偵錯。 實驗執行個體隨即出現。  
  
2.  開啟 TodoWindow (**檢視 / 其他視窗 / TodoWindow**)。  
  
3.  在文字方塊中輸入項目，然後按一下**新增**。  
  
     到期日之後今天新增到清單中的 2 天。 沒有產生任何錯誤，而**工作清單**(**檢視 / 工作清單**) 應該包含任何項目。  
  
4.  現在上變更設定**工具 / 選項 / ToDo**頁面**2**回到**0**。  
  
5.  輸入一些文字中的其他**TodoWindow**然後按一下 **新增**一次。 這樣會觸發錯誤，而在項目**工作清單**。  
  
     當您新增的項目時，初始的日期會設定現在再加上 2 天。  
  
6.  在**檢視**] 功能表上，按一下 [**輸出**開啟**輸出**視窗。  
  
     請注意，每次，將項目中顯示一則訊息**工作清單**窗格。  
  
7.  按一下其中一個清單方塊中的項目。  
  
     **屬性** 視窗會顯示兩個項目的屬性。  
  
8.  變更其中一個屬性，然後按 ENTER 鍵。  
  
     清單方塊中更新項目。