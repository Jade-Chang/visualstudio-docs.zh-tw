---
title: CaptureCurrentFrame |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 41169494424310427e5a8ae6a0af533bdf4be834
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
ms.locfileid: "31471229"
---
# <a name="capturecurrentframe"></a>CaptureCurrentFrame
擷取目前畫面的圖形記錄檔的其餘部分。  
  
## <a name="syntax"></a>語法  
  
```C++  
void CaptureCurrentFrame();  
```  
  
## <a name="remarks"></a>備註  
 如果另一個擷取作業目前正在進行，例如由啟動擷取`BeginCapture`函式 — 該擷取會完成，且要為不同的畫面格的圖形記錄檔記錄。 立即之後，圖形診斷會開始擷取目前的框架，也會記錄為不同的畫面格的其餘部分。 目前畫面格的結束是由呼叫呈現標記。  
  
 若要擷取的畫面格，您必須準備您的應用程式來擷取和記錄的圖形資訊 — 也就是您必須先呼叫[Init](init.md)的執行個體透過`VsgDbg`類別才能呼叫`CaptureCurrentFrame`。  
  
## <a name="see-also"></a>另請參閱  
 [初始化](init.md)   
 [BeginCapture](begincapture.md)