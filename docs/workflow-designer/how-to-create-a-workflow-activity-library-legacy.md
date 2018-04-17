---
title: 如何： 建立工作流程活動程式庫 （舊版） |Microsoft 文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- workflows, activity library projects
- workflow activity libraries
- projects, workflow activity libraries
ms.assetid: fb5aa940-2ae8-4b52-b52c-51c20861a7b4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 18fa570f732f71336ce5a2f5e8e56d1185366afa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-a-workflow-activity-library-legacy"></a>HOW TO：建立工作流程活動程式庫 (舊版)

請遵循下列步驟來建立工作流程活動程式庫專案使用舊版所提供的 Windows 工作流程設計工具[!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]。 當您需要以 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] 或 [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] 為目標時，請使用舊版 [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)]。

### <a name="to-create-a-workflow-activity-library-project"></a>若要建立工作流程活動程式庫專案

1.  啟動 Visual Studio。

2.  在 [檔案] 功能表上，指向 [新增]，然後選取 [專案]。

     [ **新增專案** ] 對話方塊隨即開啟。

3.  選取 [ **.NET Framework 3.0**選項或**.NET Framework 3.5**在清單頂端的下拉式選項**新專案**存取舊版設計工具] 視窗。

    > [!NOTE]
    > 中的預設選項[!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]是**.NET Framework 4**。 這個選項是用來建立以 [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] 為目標的 [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] 應用程式，而不會使用舊版設計工具。

4.  在**專案類型**窗格中，選取 Visual C# 或 Visual Basic (在**其他語言**)，然後選取 **工作流程**。

5.  在**範本**窗格中，選取**Workflow Activity Library**。

6.  在**名稱**方塊中，輸入您的專案讓您輕鬆識別的描述性名稱。

7.  在**位置**方塊中，輸入您要儲存您的專案，或按一下的目錄**瀏覽**來巡覽找到它。

     如果您想要建立專案的方案目錄，選取**為方案建立目錄**核取方塊，然後輸入中的名稱**方案名稱**方塊。

8.  按一下 [確定 **Deploying Office Solutions**]。

## <a name="see-also"></a>另請參閱

- [建立舊版工作流程專案](../workflow-designer/creating-legacy-workflow-projects.md)
- [使用舊版活動設計工具](../workflow-designer/using-the-legacy-activity-designer.md)
- [舊版工作流程活動](../workflow-designer/legacy-workflow-activities.md)
- [開發工作流程活動](http://msdn.microsoft.com/en-us/19876dfc-dfa5-4d52-b1f5-1d087474cc52)
- [Windows Workflow Foundation 活動](http://msdn.microsoft.com/en-us/192c4c1e-afb6-4f58-ab11-2b5bbbc2d2c0)