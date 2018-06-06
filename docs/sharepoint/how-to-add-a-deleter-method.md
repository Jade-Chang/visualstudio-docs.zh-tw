---
title: 如何： 加入刪除者方法 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], deleting data
- Business Data Connectivity service [SharePoint development in Visual Studio], Deleter
- BDC [SharePoint development in Visual Studio], Deleter
- BDC [SharePoint development in Visual Studio], removing data
- BDC [SharePoint development in Visual Studio], deleting entity instances
- Business Data Connectivity service [SharePoint development in Visual Studio], deleting entity instances
- Business Data Connectivity service [SharePoint development in Visual Studio], deleting data
- Business Data Connectivity service [SharePoint development in Visual Studio], removing data
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 02a6daf7a3155113ecd06d991b337b54fb0d7cd4
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2018
ms.locfileid: "34768127"
---
# <a name="how-to-add-a-deleter-method"></a>如何： 加入刪除者方法
  您可以讓使用者從 SharePoint 網站上的一個外部清單刪除的資料記錄，將刪除者方法新增至模型。 如需詳細資訊，請參閱[設計商務資料連接模型](../sharepoint/designing-a-business-data-connectivity-model.md)。  
  
### <a name="to-create-a-deleter-method"></a>若要建立的刪除者方法  
  
1.  在**BDC 設計工具**，選擇實體。  
  
2.  在功能表列上選擇 **檢視** > **其他視窗** > **BDC 方法詳細資料**。  
  
     **BDC 方法詳細資料**視窗隨即開啟。 如需此視窗的詳細資訊，請參閱[BDC 模型設計工具概觀](../sharepoint/bdc-model-design-tools-overview.md)。  
  
3.  在**將方法加入**清單中，選擇**建立刪除者方法**。  
  
     Visual Studio 會將下列項目加入至模型。 這些項目會出現在**BDC 方法詳細資料**視窗。  
  
    -   方法，名為**刪除**。  
  
    -   方法的輸入的參數。  
  
    -   參數型別描述項。  
  
    -   方法執行個體方法。  
  
     如需詳細資訊，請參閱[設計商務資料連接模型](../sharepoint/designing-a-business-data-connectivity-model.md)。  
  
4.  在**方案總管 中**，開啟實體的已產生的服務程式碼檔案的捷徑功能表，然後選擇**檢視程式碼**。  
  
     實體服務程式碼檔隨即開啟 程式碼編輯器。 如需有關實體服務程式碼檔的詳細資訊，請參閱[建立商務資料連接模型](../sharepoint/creating-a-business-data-connectivity-model.md)。  
  
5.  將程式碼加入至刪除者方法，以刪除記錄。 下列範例會刪除從銷售訂單中行項目，透過 AdventureWorks 範例資料庫的 SQL Server。  
  
    > [!NOTE]  
    >  在此範例中的方法會使用兩個輸入的參數。  
  
    > [!NOTE]  
    >  取代的值`ServerName`欄位與您的伺服器名稱。  
  
     [!code-csharp[SP_BDC#6](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderdetailservice.cs#6)]
     [!code-vb[SP_BDC#6](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderdetailservice.vb#6)]  
  
## <a name="see-also"></a>另請參閱
 [設計商務資料連接模型](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [如何： 加入搜尋方法](../sharepoint/how-to-add-a-finder-method.md)   
 [如何： 加入特定搜尋方法](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [如何： 加入建立者方法](../sharepoint/how-to-add-a-creator-method.md)   
 [如何： 加入 Updater 方法](../sharepoint/how-to-add-an-updater-method.md)   
 [BDC 模型設計工具概觀](../sharepoint/bdc-model-design-tools-overview.md)   
 [如何： 將參數加入至方法](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [如何：定義方法執行個體](../sharepoint/how-to-define-a-method-instance.md)  
  
  