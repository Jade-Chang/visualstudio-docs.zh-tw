---
title: 如何： 搜尋執行緒 檢視中執行緒 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- threads, searching
ms.assetid: 5609a9b3-c279-4426-9e2e-dd87896a6d6f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b5eee67e195821f89dbd820f930288eb24f20a11
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
ms.locfileid: "31479802"
---
# <a name="how-to-search-for-a-thread-in-threads-view"></a>如何：在執行緒檢視中搜尋執行緒
您可以使用它的執行緒 ID 或模組字串做為搜尋準則來搜尋特定執行緒 檢視中的執行緒。 您也可以指定搜尋的初始方向。 在對話方塊中的欄位會顯示所選取之執行緒的屬性中的執行緒樹狀結構。  
  
### <a name="to-search-for-a-thread-in-threads-view"></a>若要搜尋的執行緒 檢視中的執行緒  
  
1.  排列的視窗，因此該 Spy + + 和作用中[執行緒檢視](../debugger/threads-view.md)視窗會顯示。  
  
2.  從**搜尋**功能表上，選擇**尋找執行緒**。  
  
     [執行緒搜尋對話方塊](../debugger/thread-search-dialog-box.md)隨即開啟。  
  
3.  輸入執行緒 ID 或模組字串做為搜尋準則。  
  
4.  清除所有的欄位，您不想指定值。  
  
    > [!TIP]
    >  若要尋找模組所擁有的所有執行緒，請清除**執行緒**文字方塊並輸入模組中的名稱**模組**方塊。 然後使用**找下一個**繼續搜尋執行緒。  
  
5.  選擇**向上**或**向**搜尋初始方向。  
  
6.  按一下 [確定 **Deploying Office Solutions**]。  
  
 如果找到符合的執行緒，它會反白顯示 [執行緒檢視] 視窗中。