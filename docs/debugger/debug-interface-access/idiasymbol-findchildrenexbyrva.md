---
title: "IDiaSymbol::findChildrenExByRVA | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaSymbol::findChildrenExByRVA"
ms.assetid: cbc57c6c-7d64-4469-a114-1dd6671e5ec5
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::findChildrenExByRVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取在指定的相對虛擬位址 \(RVA\) 是有效的符號的子系。  
  
## 語法  
  
```cpp#  
HRESULT findChildrenExByRVA (   
   enum SymTagEnum   symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   DWORD             address,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### 參數  
 `symtag`  
 \[in\]指定要擷取的子系的符號標記所定義的[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)。  設定成`SymTagNull`為要擷取的所有子系。  
  
 `name`  
 \[in\]指定要擷取的子系的名稱。  設定成`NULL`為要擷取的所有子系。  
  
 `compareFlags`  
 \[in\]指定要套用到名稱比對的比較選項。  從數值[NameSearchOptions 列舉](../../debugger/debug-interface-access/namesearchoptions.md)列舉型別可以單獨使用或一起使用。  
  
 `address`  
 \[in\]指定的 RVA。  
  
 `ppResult`  
 \[\] out傳回[IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)擷取包含的子系符號清單的物件。  
  
## 傳回值  
 傳回`S_OK`若至少一個子節點的符號已經找到，或是傳回`S_FALSE`如果找不到沒有子系。 否則，會傳回錯誤碼。  
  
## 備註  
 傳回本機符號包含即時範圍的資訊。  
  
## 需求  
 標頭: Dia2.h  
  
 媒體櫃： diaguids.lib  
  
 DLL： msdia100.dll  
  
## 請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [NameSearchOptions 列舉](../../debugger/debug-interface-access/namesearchoptions.md)