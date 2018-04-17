---
title: 如何： 實作 Windows Communication Foundation 合約作業 （舊版） |Microsoft 文件
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: d6aeb20e-fac8-4a9d-bd26-ae78bef96b41
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 71bf4e4e6f5abc1d2984362396f21f3c613de795
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-implement-a-windows-communication-foundation-contract-operation-legacy"></a>HOW TO：實作 Windows Communication Foundation 合約作業 (舊版)
本主題描述如何實作[!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)]合約作業為目標的舊版 Windows 工作流程設計工具[!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)]或[!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)]。

 拖曳之後**ReceiveActivity**活動從工具箱拖曳至工作流程設計介面，您將建立新[!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)]合約或匯入現有合約並實作這些作業。 您選取及/或建立您的合約和其作業透過[選擇作業對話方塊 （舊版）](../workflow-designer/choose-operation-dialog-box-legacy.md)。

### <a name="to-implement-a-wcf-contract-operation"></a>若要實作 WCF 合約作業

1.  按兩下**ReceiveActivity**活動設計工具中的，或按一下省略符號旁**ServiceOperationInfo**屬性**屬性**窗格。

2.  執行下列任一步驟：

    -   按一下**新增合約**對話方塊右上角。 這將為您建立新的 [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] 合約與作業。

         -或-

    -   按一下**匯入**對話方塊右上角。 [瀏覽並選取.NET 類型對話方塊 （舊版）](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md)隨即開啟。 搜尋含有您所要之合約的組件或專案。 選取合約，然後按一下 **確定**。

     建立或匯入合約之後，您可以將新作業加入至該建立或匯入的合約。 若要加入新的作業，請選取合約，然後按一下  **Add 作業**對話方塊右上角。 完成新增作業時，請繼續進行步驟 3。

3.  選取您想要與關聯的作業**ReceiveActivity**活動。 您可以變更作業的名稱、參數、屬性和權限設定，藉此操作作業的定義。

     若要變更名稱，請輸入中的新名稱**作業名稱**文字方塊。

     按一下**參數** 索引標籤存取作業的參數。 您可以變更參數的名稱、型別或方向，以及從作業新增或刪除參數。

     按一下**屬性** 索引標籤存取作業保護層級和支援的訊息交換 」 功能的操作。

     按一下**權限**索引標籤可指定允許哪個群組實作作業。

4.  按一下**確定**和**ReceiveActivity**活動將會顯示它所實作之作業的作業名稱。

5.  將您要使用的實作，該作業內的工作流程活動**ReceiveActivity**活動。

## <a name="see-also"></a>另請參閱

- [選擇作業對話方塊 (舊版)](../workflow-designer/choose-operation-dialog-box-legacy.md)
- [如何： 叫用 WCF 合約作業 （舊版）](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)
- [舊版工作流程活動](../workflow-designer/legacy-workflow-activities.md)