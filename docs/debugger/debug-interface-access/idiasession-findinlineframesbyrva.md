---
title: "IDiaSession::findInlineFramesByRVA |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: ddb3ff0e-cb3d-4fa0-af56-f064b218b264
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 418aac1a1b45d9c81909f2673d0a31d54b22d31d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idiasessionfindinlineframesbyrva"></a>IDiaSession::findInlineFramesByRVA
擷取列舉，可讓用戶端來逐一查看所有指定相對虛擬位址 (RVA) 上的內嵌框架。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT findInlineFramesByRVA (   
   IDiaSymbol*       parent,   DWORD             rva,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### <a name="parameters"></a>參數  
 `parent`  
 [in]`IDiaSymbol`表示父物件。  
  
 `rva`  
 [in]指定的位址為 RVA。  
  
 `ppResult`  
 [out]保存`IDiaEnumSymbols`物件，其中包含所擷取的畫面格的清單。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="see-also"></a>請參閱  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)