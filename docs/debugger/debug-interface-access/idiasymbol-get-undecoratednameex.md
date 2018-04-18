---
title: 'Idiasymbol:: Get_undecoratednameex |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_undecoratedNameEx method
ms.assetid: 579aed0b-c57d-41a1-a94a-3bf665fd4a9d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d737ccfe9dbbcdf7a205fb847bb81344cd18ff0c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idiasymbolgetundecoratednameex"></a>IDiaSymbol::get_undecoratedNameEx
擷取部分或全部的 c + + 未裝飾名稱裝飾 （連結） 名稱。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_undecoratedNameEx(   
   DWORD undecorateOptions,  
   BSTR* pRetval  
);  
```  
  
#### <a name="parameters"></a>參數  
 `undecoratedOptions`  
 [in]指定旗標的組合傳回該控制項。 請參閱 < 備註 > 一節的特定值和它們的功用。  
  
 `pRetVal`  
 [out]傳回的未裝飾的名稱的 c + + 裝飾名稱。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示屬性不適用於符號。  
  
## <a name="remarks"></a>備註  
 `undecorateOptions`可以是下列旗標的組合。  
  
> [!NOTE]
>  旗標名稱未定義在 DIA SDK 中，因此您需要將宣告加入至您的程式碼，或使用未經處理的值。  
  
|旗標|值|描述|  
|----------|-----------|-----------------|  
|UNDNAME_COMPLETE|0x0000|啟用完整 undecoration。|  
|UNDNAME_NO_LEADING_UNDERSCORES|0x0001|移除 Microsoft 擴充關鍵字前置底線。|  
|UNDNAME_NO_MS_KEYWORDS|0x0002|停用擴充的 Microsoft 擴充關鍵字。|  
|UNDNAME_NO_FUNCTION_RETURNS|0x0004|停用擴充的主要宣告傳回型別。|  
|UNDNAME_NO_ALLOCATION_MODEL|0x0008|停用擴充的宣告模型。|  
|UNDNAME_NO_ALLOCATION_LANGUAGE|0x0010|停用擴充的宣告語言規範。|  
|UNDNAME_RESERVED1|0x0020|保留。|  
|UNDNAME_RESERVED2|0x0040|保留。|  
|UNDNAME_NO_THISTYPE|0x0060|停用上的所有修飾詞`this`型別。|  
|UNDNAME_NO_ACCESS_SPECIFIERS|0x0080|停用擴充成員的存取規範。|  
|UNDNAME_NO_THROW_SIGNATURES|0x0100|停用擴充 」 throw-簽章中的 「 函式和函式的指標。|  
|UNDNAME_NO_MEMBER_TYPE|0x0200|停用擴充`static`或`virtual`成員。|  
|UNDNAME_NO_RETURN_UDT_MODEL|0x0400|針對 UDT 傳回，會停用擴充的 Microsoft 模型。|  
|UNDNAME_32_BIT_DECODE|0x0800|Undecorates 32 位元的裝飾的名稱。|  
|UNDNAME_NAME_ONLY|0x1000|取得主要宣告; 的名稱只會傳回 [範圍::] 名稱。  展開 範本參數。|  
|UNDNAME_TYPE_ONLY|0x2000|輸入是只要類型的編碼。撰寫抽象宣告子。|  
|UNDNAME_HAVE_PARAMETERS|0x4000|使用真實的樣板參數。|  
|UNDNAME_NO_ECSU|0x8000|會隱藏列舉/類別/結構/等位。|  
|UNDNAME_NO_IDENT_CHAR_CHECK|0x10000|隱藏檢查有效的識別項字元。|  
|UNDNAME_NO_PTR64|0x20000|不包含 ptr64 輸出中。|  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)