---
title: 檢查 XML 結構描述設計工具中使用內容模型檢視節點的內容模型
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: c42ddac8-b0e3-48d6-9832-112a19d6c104
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 650478a92ea2dabc9aeef239a68bdff428429cd7
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/25/2018
ms.locfileid: "34548592"
---
# <a name="how-to-examine-the-content-model-of-nodes-using-the-content-model-view"></a>如何： 檢查使用內容模型檢視節點的內容模型

本主題描述如何瀏覽您使用的節點[內容模型檢視](../xml-tools/content-model-view.md)。

## <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>建立新的 XSD 檔案，並且在內容模型檢視中顯示根項目

1.  建立新的 XML 結構描述檔案。

2.  按一下**使用 XML 編輯器檢視與編輯基礎 XML 結構描述檔案**開始檢視上。

3.  XML 結構描述範例程式碼複製[範例 XML 結構描述： 採購單結構描述](../xml-tools/sample-xsd-file-purchase-order-schema.md)並貼上取代依預設加入至新 XSD 檔案的程式碼。

4.  選取`purchaseOrder`在結構描述總管 中，以滑鼠右鍵按一下項目`purchaseOrder`XML 編輯器中的項目，然後選取**XML 總管中顯示**。

5.  以滑鼠右鍵按一下`purchaseOrder`XML 總管 中選取**在內容模型檢視中顯示**。

     內容模型檢視的設計介面上會顯示 `purchaseOrder` 項目。

6.  在每個節點上按兩下，或按一下每個節點右邊的雙箭頭，展開 `shipTo`、`billTo` 和 `items` 節點。

     `purchaseOrder` 項目的節點已展開，您可以查看該項目的內容模型。

7.  按一下 `purchaseOrder` 項目下的任何節點並查看階層連結列，以查看所選節點在結構描述集中的位置。

8.  按一下**顯示文件**XSD 工具列切換文件中的按鈕。 您也可以以滑鼠右鍵按一下設計介面來切換文件。

9. 滑鼠右鍵按一下`purchaseOrder`節點，然後選取**產生範例 XML**查看 XML 執行個體文件。