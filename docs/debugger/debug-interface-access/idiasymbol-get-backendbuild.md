---
title: "Idiasymbol:: Get_backendbuild |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_backEndBuild method
ms.assetid: 423af497-9294-438e-92b4-456c6f56dc56
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dc1d06aa488335c8a7d551d59d9ecf3d3beea9f2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetbackendbuild"></a>IDiaSymbol::get_backEndBuild
擷取編譯器的後端組建編號。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT get_backEndBuild (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pRetVal`  
 [out]傳回的後端組建編號。 請參閱＜備註＞。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回`S_FALSE`或錯誤碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示屬性不是使用符號。  
  
## <a name="remarks"></a>備註  
 編譯器通常由兩個主要項目所組成： 前端 （剖析器），用來處理來源的程式碼剖析為中繼格式，以及的後端 （程式碼產生器），它會將中繼格式轉換成組件。 是很常見的前端有後端的版本不同的位置。  
  
 前端或後端版本號碼是三個部分組成：\<主要 >。\<次要 >。\<建置 >，其中\<主要 > 是主要版本號碼，\<次要 > 是次要版本號碼，和\<建置 > 是的組建編號。 例如，13.10.3077。  
  
## <a name="requirements"></a>需求  
  
|需求|描述|  
|-----------------|-----------------|  
|Header:|dia2.h|  
|版本:|DIA SDK v7.0|  
  
## <a name="see-also"></a>另請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)