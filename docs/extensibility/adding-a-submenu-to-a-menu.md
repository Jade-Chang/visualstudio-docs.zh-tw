---
title: 加入功能表的子功能表 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- context menus
- submenus, cascading
- cascading submenus
- menus, creating cascading submenus
ms.assetid: 692600cb-d052-40e2-bdae-4354ae7c6c84
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f6998c275aead7b12b107f700e699f5a82edd84e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31102417"
---
# <a name="adding-a-submenu-to-a-menu"></a>加入功能表的子功能表
本逐步解說是根據在示範[功能表加入 Visual Studio 功能表列](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)，以顯示如何新增至子功能表**TestMenu**功能表。  
  
 子功能表，就是第二個功能表會出現在另一個功能表。 子功能表可以識別其名稱會遵循的箭頭。 按一下名稱，會讓子功能表和它所要顯示的命令。  
  
 本逐步解說在 Visual Studio 功能表列上的功能表中建立子功能表，並將新的命令放在子功能表。 本逐步解說也會實作新的命令。  
  
## <a name="prerequisites"></a>必要條件  
 啟動 Visual Studio 2015 中，請勿從 「 下載中心 」 未安裝 Visual Studio SDK。 它是包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱[安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="adding-a-submenu-to-a-menu"></a>加入功能表的子功能表  
  
1.  請依照[功能表加入 Visual Studio 功能表列](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)建立專案和功能表項目。 在本逐步解說的步驟假設 VSIX 專案的名稱是`TopLevelMenu`。  
  
2.  開啟 TestCommandPackage.vsct。 在`<Symbols>`區段中，新增`<IDSymbol>`元素的子功能表，一個是針對子群組，其中一個命令中，所有在`<GuidSymbol>`節點名為"guidTopLevelMenuCmdSet。 」 這是包含的相同節點`<IDSymbol>`最上層功能表項目。  
  
    ```xml  
    <IDSymbol name="SubMenu" value="0x1100"/>  
    <IDSymbol name="SubMenuGroup" value="0x1150"/>  
    <IDSymbol name="cmdidTestSubCommand" value="0x0105"/>  
    ```  
  
3.  加入新建立的子功能表`<Menus>`> 一節。  
  
    ```xml  
    <Menu guid="guidTestCommandPackageCmdSet" id="SubMenu" priority="0x0100" type="Menu">  
        <Parent guid="guidTestCommandPackageCmdSet" id="MyMenuGroup"/>  
        <Strings>  
            <ButtonText>Sub Menu</ButtonText>  
            <CommandName>Sub Menu</CommandName>  
        </Strings>  
    </Menu>  
    ```  
  
     父代的 GUID/識別碼組指定的功能表群組中所產生[功能表加入 Visual Studio 功能表列](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)，和子系的最上層的功能表。  
  
4.  加入在步驟 2 中定義的功能表群組`<Groups>`區段，並讓子功能表的子系。  
  
    ```xml  
    <Group guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" priority="0x0000">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>  
    </Group>  
    ```  
  
5.  加入新`<Button>`元素`<Buttons>`區段，以定義在步驟 2 中建立子功能表上的項目為命令。  
  
    ```xml  
    <Button guid="guidTestCommandPackageCmdSet" id="cmdidTestSubCommand" priority="0x0000" type="Button">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" />  
        <Icon guid="guidImages" id="bmpPic2" />  
        <Strings>  
           <CommandName>cmdidTestSubCommand</CommandName>  
           <ButtonText>Test Sub Command</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
6.  建置方案並開始偵錯。 您應該會看到實驗執行個體。  
  
7.  按一下**TestMenu**以查看新的子功能表，名為**子功能表**。 按一下**子功能表**開啟子功能表，並查看新的命令**測試子命令**。 請注意，按一下**測試子命令**不做任何動作。  
  
## <a name="adding-a-command"></a>加入命令  
  
1.  開啟 TestCommand.cs 和現有的命令 id。 之後加入下列的命令 ID  
  
    ```csharp  
    public const int cmdidTestSubCmd = 0x105;  
    ```  
  
2.  加入子命令。 尋找命令的建構函式。 只在呼叫之後加入下列行`AddCommand`方法。  
  
    ```csharp  
    CommandID subCommandID = new CommandID(CommandSet, cmdidTestSubCmd);  
    MenuCommand subItem = new MenuCommand(  
        new EventHandler(SubItemCallback), subCommandID);  
    commandService.AddCommand(subItem);  
  
    ```  
  
     `SubItemCallback`稍後將會定義命令處理常式。 建構函式現在看起來應該像這樣：  
  
    ```csharp  
    private TestCommand(Package package)  
            {  
                if (package == null)  
                {  
                    throw new ArgumentNullException("package");  
                }  
  
                this.package = package;  
  
                OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
                if (commandService != null)  
                {  
                    var menuCommandID = new CommandID(CommandSet, CommandId);  
                    var menuItem = new MenuCommand(this.MenuItemCallback, menuCommandID);  
                    commandService.AddCommand(menuItem);  
                    CommandID subCommandID = new CommandID(CommandSet, cmdidTestSubCmd);  
                    MenuCommand subItem = new MenuCommand(  
                        new EventHandler(SubItemCallback), subCommandID);  
                    commandService.AddCommand(subItem);  
                }  
    ```  
  
3.  加入 SubItemCallback()。 這是新的命令 子功能表中按一下時呼叫的方法。  
  
    ```csharp  
    private void SubItemCallback(object sender, EventArgs e)  
    {  
        IVsUIShell uiShell = (IVsUIShell)this.ServiceProvider.GetService(  
            typeof(SVsUIShell));  
        Guid clsid = Guid.Empty;  
        int result;  
        uiShell.ShowMessageBox(  
            0,  
            ref clsid,  
            "TestCommand",  
            string.Format(CultureInfo.CurrentCulture,  
            "Inside TestCommand.SubItemCallback()",  
            this.ToString()),  
            string.Empty,  
            0,  
            OLEMSGBUTTON.OLEMSGBUTTON_OK,  
            OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,  
            OLEMSGICON.OLEMSGICON_INFO,  
            0,  
            out result);  
    }  
    ```  
  
4.  建置此專案並開始偵錯。 實驗執行個體應該會出現。  
  
5.  在**TestMenu**功能表上，按一下 **子功能表**，然後按一下 **測試子命令**。 訊息方塊應該會出現並顯示文字，也就是 「 第命令頁，內部 TestCommand.SubItemCallback() 測試 」。  
  
## <a name="see-also"></a>另請參閱  
 [將功能表加入至 Visual Studio 功能表列](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)   
 [命令、功能表及工具列](../extensibility/internals/commands-menus-and-toolbars.md)
