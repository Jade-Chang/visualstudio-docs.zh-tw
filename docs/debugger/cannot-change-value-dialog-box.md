---
title: 無法變更值對話方塊 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.variables.failededit
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Cannot Change Value dialog box
- variables [debugger], editing
ms.assetid: 19e930c2-5fbf-4c83-aae8-a1dc3f8fcae8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 23a6eb8059d9780e3b7343c6a7864896a0c529c6
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="cannot-change-value-dialog-box"></a>無法變更值對話方塊
## <a name="error"></a>錯誤  
 `The value of this variable cannot be changed` &#124;`The name` *名稱* `does not exist in the current context` &#124; *各種其他訊息*  
  
 當您在偵錯工具視窗 ([自動變數]、[監看式] 或 [區域變數] 視窗) 或 [快速監看式] 對話方塊中嘗試將變數內容變更為無效值時，這個訊息方塊就會出現。 例如，如果您將整數變數的值設定成字元字串，這個訊息方塊就會出現。  
  
## <a name="solution"></a>方案  
 確認您輸入偵錯工具視窗或 [快速監看式] 對話方塊內的輸入內容，對於您嘗試設定的變數而言是有效的值。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯工具中的運算式](../debugger/expressions-in-the-debugger.md)