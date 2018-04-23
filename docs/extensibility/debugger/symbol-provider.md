---
title: 符號提供者 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a98a5b80126bcb11109acedc2d24f226cde3714a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="symbol-provider"></a>符號提供者
運算式評估工具實作必須存取以便評估變數和運算式語言編譯器所產生的符號偵錯資訊。 它會使用介面的符號提供者 (SP)，也稱為符號處理常式。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] managed 程式碼，以及使用的程式資料庫 (PDB) 符號檔案格式的原生程式碼會提供預存程序。 除非沒有強式需要的程式以使用儲存在自訂格式的符號，它是建議使用所提供的預存程序[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
## <a name="implementation-notes"></a>實作注意事項  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]偵錯引擎預期要與預存程序，使用 Common Language Runtime (CLR) 介面。 如此一來，Visual Studio 偵錯引擎會使用預存程序必須支援的 CLR。 所有 CLR 偵錯介面的完整清單位於 debugref.doc 屬於的[!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)]。  
  
 如果您的預存程序只會使用您的自訂偵錯引擎，您可以在根據的偵錯引擎需求適當地實作預存程序。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯工具元件](../../extensibility/debugger/debugger-components.md)