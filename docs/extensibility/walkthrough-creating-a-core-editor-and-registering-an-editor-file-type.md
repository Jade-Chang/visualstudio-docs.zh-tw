---
title: "建立核心編輯器和註冊編輯器檔案類型 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - walkthrough
ms.assetid: 24d2bffd-a35c-46db-8515-fd60b884b7fb
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: ace475cb94920a5c0470c1d16265349edfa441f4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-a-core-editor-and-registering-an-editor-file-type"></a>逐步解說： 建立核心編輯器和登錄編輯程式檔案類型
本逐步解說示範如何建立啟動的 VSPackage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .myext 副檔名的檔案時，核心編輯器會載入。  
  
## <a name="prerequisites"></a>必要條件  
 若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 如需詳細資訊，請參閱[Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Visual Studio 封裝專案範本位置  
 Visual Studio Package 專案範本位在 [新增專案]  對話方塊的三個不同位置：  
  
1.  位在 Visual Basic 擴充性下。 專案的預設語言為 Visual Basic。  
  
2.  位在 C# 擴充性下。 專案的預設語言為 C#。  
  
3.  位在其他專案類型擴充性下。 專案的預設語言為 C++。  
  
### <a name="to-create-the-vspackage"></a>若要建立 VSPackage  
  
-   啟動[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]並建立[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]名為 VSPackage `MyPackage`，如下所述[逐步解說： 建立功能表命令 VSPackage](http://msdn.microsoft.com/en-us/d699c149-5d1e-47ff-94c7-e1222af02c32)。  
  
### <a name="to-add-the-editor-factory"></a>若要加入編輯器 factory  
  
1.  以滑鼠右鍵按一下**MyPackage**專案，指向**新增**，然後按一下 **類別**。  
  
2.  在**加入新項目**對話方塊方塊中，請確定**類別**選取範本時，型別`EditorFactory.cs`為名稱，然後按一下**新增**將類別加入您的專案。  
  
     應該會自動開啟 EditorFactory.cs 檔案。  
  
3.  請參考下列組件從您的程式碼。  
  
    ```vb  
    Imports System.Runtime.InteropServices  
    Imports Microsoft.VisualStudio  
    Imports Microsoft.VisualStudio.Shell  
    Imports Microsoft.VisualStudio.Shell.Interop  
    Imports Microsoft.VisualStudio.OLE.Interop  
    Imports Microsoft.VisualStudio.TextManager.Interop  
    Imports IOleServiceProvider = Microsoft.VisualStudio.OLE.Interop.IServiceProvider  
    ```  
  
    ```csharp  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio.TextManager.Interop;  
    using IOleServiceProvider = Microsoft.VisualStudio.OLE.Interop.IServiceProvider;  
  
    ```  
  
4.  新增的 GUID`EditorFactory`類別藉由新增`Guid`屬性立即在類別宣告之前。  
  
     您可以使用 guidgen.exe 程式在產生新的 GUID[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]命令提示字元，或按一下**建立 GUID**上**工具**功能表。 這裡使用的 GUID 只是舉例;請勿使用您的專案中。  
  
    ```vb  
    <Guid("0eea3187-c5fa-48d4-aa72-b5eecd3b17b1")> _  
    ```  
  
    ```csharp  
    [Guid("0eea3187-c5fa-48d4-aa72-b5eecd3b17b1")]   
    ```  
  
5.  在類別定義中，加入包含父封裝和服務提供者的兩個私用變數。  
  
    ```vb  
    Class EditorFactory  
        Private parentPackage As Package  
        Private serviceProvider As IOleServiceProvider  
    ```  
  
    ```csharp  
    class EditorFactory  
    {  
        private Package parentPackage;  
        private IOleServiceProvider serviceProvider;  
    }  
  
    ```  
  
6.  新增公用類別建構函式接受一個參數的型別<xref:Microsoft.VisualStudio.Shell.Package>:  
  
    ```vb  
    Public Sub New(ByVal parentPackage As Package)  
        Me.parentPackage = parentPackage  
    End Sub  
    ```  
  
    ```csharp  
    public EditorFactory(Package parentPackage)  
    {  
        this.parentPackage = parentPackage;  
    }  
    ```  
  
7.  修改`EditorFactory`類別衍生自宣告<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>介面。  
  
    ```vb  
    Class EditorFactory Implements IVsEditorFacto  
    ```  
  
    ```csharp  
    class EditorFactory : IVsEditorFactory  
  
    ```  
  
8.  以滑鼠右鍵按一下<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>，按一下 **實作介面**，然後按一下 **明確實作介面**。  
  
     這會將必須在中實作的四個方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>介面。  
  
9. 以下列程式碼取代 `IVsEditorFactory.Close` 方法的內容。  
  
    ```vb  
    Return VSConstants.S_OK  
    ```  
  
    ```csharp  
    return VSConstants.S_OK;  
    ```  
  
10. 取代內容`IVsEditorFactory.SetSite`為下列程式碼。  
  
    ```vb  
    Me.serviceProvider = psp  
    Return VSConstants.S_OK  
    ```  
  
    ```csharp  
    this.serviceProvider = psp;  
    return VSConstants.S_OK;  
    ```  
  
11. 以下列程式碼取代 `IVsEditorFactory.MapLogicalView` 方法的內容。  
  
    ```vb  
    Dim retval As Integer = VSConstants.E_NOTIMPL  
    pbstrPhysicalView = Nothing ' We support only one view.  
    If rguidLogicalView.Equals(VSConstants.LOGVIEWID_Designer)OrElse _  
    rguidLogicalView.Equals(VSConstants.LOGVIEWID_Primary) Then  
        retval = VSConstants.S_OK  
    End If  
    Return retval  
    ```  
  
    ```csharp  
    int retval = VSConstants.E_NOTIMPL;  
    pbstrPhysicalView = null;   // We support only one view.  
    if (rguidLogicalView.Equals(VSConstants.LOGVIEWID_Designer) ||  
    rguidLogicalView.Equals(VSConstants.LOGVIEWID_Primary))  
    {  
        retval = VSConstants.S_OK;  
    }  
    return retval;  
    ```  
  
12. 以下列程式碼取代 `IVsEditorFactory.CreateEditorInstance` 方法的內容。  
  
    ```vb  
    Dim retval As Integer = VSConstants.E_FAIL          
  
    ' Initialize these to empty to start with   
    ppunkDocView = IntPtr.Zero  
    ppunkDocData = IntPtr.Zero  
    pbstrEditorCaption = ""  
    pguidCmdUI = Guid.Empty  
    pgrfCDW = 0  
  
    If (grfCreateDoc And (VSConstants.CEF_OPENFILE Or _  
    VSConstants.CEF_SILENT)) = 0 Then  
        Throw New ArgumentException("Only Open or Silent is valid")  
    End If  
    If punkDocDataExisting <> IntPtr.Zero Then  
        Return VSConstants.VS_E_INCOMPATIBLEDOCDATA  
    End If  
  
    ' Instantiate a text buffer of type VsTextBuffer.   
    ' Note: we only need an IUnknown (object) interface for   
    ' this invocation.   
    Dim clsidTextBuffer As Guid = GetType(VsTextBufferClass).GUID  
    Dim iidTextBuffer As Guid = VSConstants.IID_IUnknown  
    Dim pTextBuffer As Object = pTextBuffer = _  
    parentPackage.CreateInstance(clsidTextBuffer, iidTextBuffer, _  
    GetType(Object))  
  
    If Not pTextBuffer Is Nothing Then  
        ' "Site" the text buffer with the service provider we were   
        ' provided.   
        Dim textBufferSite As IObjectWithSite = TryCast(pTextBuffer, _  
        IObjectWithSite)  
        If Not textBufferSite Is Nothing Then  
            textBufferSite.SetSite(Me.serviceProvider)  
        End If  
  
        ' Instantiate a code window of type IVsCodeWindow.   
        Dim clsidCodeWindow As Guid = GetType(VsCodeWindowClass).GUID  
        Dim iidCodeWindow As Guid = GetType(IVsCodeWindow).GUID  
        Dim pCodeWindow As IVsCodeWindow = _  
        CType(Me.parentPackage.CreateInstance(clsidCodeWindow, _  
        iidCodeWindow, GetType(IVsCodeWindow)), IVsCodeWindow)  
        If Not pCodeWindow Is Nothing Then  
            ' Give the text buffer to the code window.   
            ' We are giving up ownership of the text buffer!   
            pCodeWindow.SetBuffer(CType(pTextBuffer, IVsTextLines))  
  
            ' Now tell the caller about all this new stuff   
            ' that has been created.   
            ppunkDocView = Marshal.GetIUnknownForObject(pCodeWindow)  
            ppunkDocData = Marshal.GetIUnknownForObject(pTextBuffer)  
  
            ' Specify the command UI to use so keypresses are   
            ' automatically dealt with.   
            pguidCmdUI = VSConstants.GUID_TextEditorFactory  
  
            ' This caption is appended to the filename and   
            ' lets us know our invocation of the core editor   
            ' is up and running.   
            pbstrEditorCaption = " [MyPackage]"  
  
            retval = VSConstants.S_OK  
        End If  
    End If  
    Return retval  
    ```  
  
    ```csharp  
    int retval = VSConstants.E_FAIL;  
  
    // Initialize these to empty to start with  
    ppunkDocView       = IntPtr.Zero;  
    ppunkDocData       = IntPtr.Zero;  
    pbstrEditorCaption = "";  
    pguidCmdUI         = Guid.Empty;   
    pgrfCDW            = 0;  
  
    if ((grfCreateDoc & (VSConstants.CEF_OPENFILE |   
          VSConstants.CEF_SILENT)) == 0)  
    {   
        throw new ArgumentException("Only Open or Silent is valid");  
    }  
    if (punkDocDataExisting != IntPtr.Zero)  
    {  
        return VSConstants.VS_E_INCOMPATIBLEDOCDATA;  
    }  
  
    // Instantiate a text buffer of type VsTextBuffer.  
    // Note: we only need an IUnknown (object) interface for   
    // this invocation.  
    Guid clsidTextBuffer = typeof(VsTextBufferClass).GUID;  
    Guid iidTextBuffer   = VSConstants.IID_IUnknown;  
    object pTextBuffer   = pTextBuffer = parentPackage.CreateInstance(  
          ref clsidTextBuffer,  
          ref iidTextBuffer,  
          typeof(object));  
  
    if (pTextBuffer != null)  
    {  
        // "Site" the text buffer with the service provider we were  
        // provided.  
        IObjectWithSite textBufferSite = pTextBuffer as IObjectWithSite;  
        if (textBufferSite != null)  
        {  
            textBufferSite.SetSite(this.serviceProvider);  
        }  
  
        // Instantiate a code window of type IVsCodeWindow.  
        Guid clsidCodeWindow = typeof(VsCodeWindowClass).GUID;  
        Guid iidCodeWindow   = typeof(IVsCodeWindow).GUID;  
        IVsCodeWindow pCodeWindow =  
        (IVsCodeWindow)this.parentPackage.CreateInstance(   
              ref clsidCodeWindow,  
              ref iidCodeWindow,  
              typeof(IVsCodeWindow));  
        if (pCodeWindow != null)  
        {  
            // Give the text buffer to the code window.  
            // We are giving up ownership of the text buffer!  
            pCodeWindow.SetBuffer((IVsTextLines)pTextBuffer);  
  
            // Now tell the caller about all this new stuff   
            // that has been created.  
            ppunkDocView = Marshal.GetIUnknownForObject(pCodeWindow);  
            ppunkDocData = Marshal.GetIUnknownForObject(pTextBuffer);  
  
            // Specify the command UI to use so keypresses are   
            // automatically dealt with.  
            pguidCmdUI = VSConstants.GUID_TextEditorFactory;  
  
            // This caption is appended to the filename and  
            // lets us know our invocation of the core editor   
            // is up and running.  
            pbstrEditorCaption = " [MyPackage]";  
  
            retval = VSConstants.S_OK;  
        }   
    }   
    return retval;   
    ```  
  
13. 編譯專案，並確定沒有任何錯誤。  
  
### <a name="to-register-the-editor-factory"></a>若要登錄 editor factory  
  
1.  在**方案總管 中**，按兩下 Resources.resx 檔案開啟至字串資料表，在其中的項目**String1 為**選取。  
  
2.  變更的識別項名稱`IDS_EDITORNAME`和以文字**MyPackage 編輯器。** 這個字串會顯示為您的編輯器的名稱。  
  
3.  開啟 VSPackage.resx 檔案並加入新的字串，將名稱設定為**101**和要值`IDS_EDITORNAME`。 這會將封裝提供的資源 ID，才能存取您剛才建立的字串。  
  
    > [!NOTE]
    >  如果 VSPackage.resx 檔案包含另一個字串`name`屬性設為**101**，以另一個唯一的、 數字的值，取代及的下列步驟。  
  
4.  在**方案總管 中**，開啟 MyPackagePackage.cs 檔案。  
  
     這是主套件檔案。  
  
5.  之前加入下列使用者屬性`Guid`屬性。  
  
    ```vb  
    <ProvideEditorFactoryAttribute(GetType(EditorFactory), 101)> _  
    <ProvideEditorExtensionAttribute(GetType(EditorFactory), _  
          ".myext", 32, NameResourceID:=101 )> _  
    ```  
  
    ```csharp  
    [ProvideEditorFactory(typeof(EditorFactory), 101)]  
    [ProvideEditorExtension(typeof(EditorFactory),   
          ".myext", 32, NameResourceID = 101)]   
    ```  
  
     <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute>屬性關聯.myext 副檔名編輯器 factory，以便在任何時候，在載入延伸模組，會叫用編輯器 factory 的檔案。  
  
6.  加入私用變數，以`MyPackage`類別之前建構函式，, 並提供它的類型`EditorFactory`。  
  
    ```vb  
    Private editorFactory As EditorFactory  
    ```  
  
    ```csharp  
    private EditorFactory editorFactory;  
    ```  
  
7.  尋找`Initialize`方法 (您可能需要開啟`Package Members`隱藏的區域) 並加入下列程式碼的呼叫後方`base.Initialize()`。  
  
    ```vb  
    'Create our editor factory and register it.   
    Me.editorFactory = New EditorFactory(Me)  
    MyBase.RegisterEditorFactory(Me.editorFactory)  
    ```  
  
    ```csharp  
    // Create our editor factory and register it.  
    this.editorFactory = new EditorFactory(this);  
    base.RegisterEditorFactory(this.editorFactory);  
  
    ```  
  
8.  編譯程式，並確定沒有任何錯誤。  
  
     此步驟中的實驗登錄區中登錄 editor factory [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 如果提示您覆寫 resource.h 檔案時，請按一下**確定**。  
  
9. 建立名為 TextFile1.myext 範例檔案。  
  
10. 按**F5**若要開啟的實驗性執行個體[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
11. 在實驗性[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]上**檔案**功能表上，指向**開啟**，然後按一下 **檔案**。  
  
12. 尋找 TextFile1.myext 並按一下**開啟**。  
  
     現在應該載入的檔案。  
  
## <a name="robust-programming"></a>穩固程式設計  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]核心編輯器處理各種不同的文字為基礎的檔案類型和適用於緊密語言服務，以提供一組豐富的功能，例如語法反白顯示，比對括號和 IntelliSense 文字自動完成及成員完成清單。 如果您正在使用以文字為基礎的檔案，您可以使用核心編輯器，以及支援您的特定檔案類型的自訂語言服務。  
  
 VSPackage 可以叫用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]核心編輯器，藉由提供編輯器 factory。 載入與它相關聯的檔案時，會使用這個編輯器 factory。 如果檔案是專案的一部分，然後核心編輯器會自動叫用除非覆寫您的 VSPackage。 不過，如果在專案外載入該檔案，然後核心編輯器必須明確地叫用您的 VSPackage。  
  
 如需有關核心編輯器的詳細資訊，請參閱[核心編輯器內](../extensibility/inside-the-core-editor.md)。  
  
## <a name="see-also"></a>請參閱  
 [核心編輯器內](../extensibility/inside-the-core-editor.md)   
 [執行個體化使用舊版 API 的核心編輯器](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)