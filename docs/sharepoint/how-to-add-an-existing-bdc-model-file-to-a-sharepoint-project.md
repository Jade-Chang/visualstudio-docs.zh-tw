---
title: 如何： 將現有的 BDC 模型檔案新增至 SharePoint 專案 |Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.BDC.ImportDialog
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], import a model
- Business Data Connectivity service [SharePoint development in Visual Studio], reuse a model
- BDC [SharePoint development in Visual Studio], import a model
- BDC [SharePoint development in Visual Studio], remove a model
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8f7508cf8c66343894c16da7ff840bd275abb65c
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755894"
---
# <a name="how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project"></a>如何： 將現有的 BDC 模型檔案新增至 SharePoint 專案
  您可以自訂、 封裝和重新部署的商務資料連接 (BDC) 模型，可以使用 Visual Studio 將模型檔案 (*.bdcm*) 至任何 SharePoint 伺服器陣列的專案。 如需詳細資訊，請參閱 <<c0> [ 建立 business data connectivity 模型](../sharepoint/creating-a-business-data-connectivity-model.md)。  
  
### <a name="to-add-a-bdc-model-file-to-a-sharepoint-project"></a>若要將 BDC 模型檔案新增至 SharePoint 專案  
  
1.  在 [**方案總管] 中**，選擇 SharePoint 專案的資料夾。  
  
2.  在功能表列上選擇 **專案** > **加入現有項目**。  
  
3.  在 **加入現有項目** 對話方塊中，瀏覽至您想要新增至您的專案，選擇 檔案，然後選擇的模型定義檔的位置**新增** 按鈕。  
  
     如果模型未定義*類型的.NET 組件的企業營運 (LOB) 系統*，則**新增.NET 組件 LobSystem**對話方塊隨即開啟。  
  
4.  如果出現對話方塊，請執行下列步驟：  
  
    -   如果您想要撰寫自訂程式碼，並使用設計工具定義匯入模型的中繼資料、 選擇**是**按鈕、 命名系統，然後選擇**確定** 按鈕。  
  
    -   否則，請選擇**No**按鈕，然後再選擇**確定** 按鈕。  
  
     **Business Data Connectivity 模型**項目加入至專案。  
  
## <a name="see-also"></a>另請參閱
 [建立 business data connectivity 模型](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [如何： 建立 BDC 模型](../sharepoint/how-to-create-a-bdc-model.md)   
 [如何： 使用資源檔來指定當地語系化的名稱、 屬性和權限](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [如何： 在 BDC 功能中包含自訂組件](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [將商務資料整合至 SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
 
