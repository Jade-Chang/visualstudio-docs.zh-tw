---
title: 'Idiatable:: Item |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable::Item method
ms.assetid: eae11b26-4807-400c-be25-e85bbc0c6b20
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cd734d287a4740a25840d93b4724b45396c7dd87
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
ms.locfileid: "31470071"
---
# <a name="idiatableitem"></a>IDiaTable::Item
擷取指定的項目資料表中的參考。  
  
## <a name="syntax"></a>語法  
  
```C++  
HRESULT Item (   
   DWORD      index,  
   IUnknown** element  
);  
```  
  
#### <a name="parameters"></a>參數  
 `index`  
 [in]索引的資料表中的項目介於範圍 0 到`count`-1，其中`count`傳回[idiatable:: Get_count](../../debugger/debug-interface-access/idiatable-get-count.md)方法。  
  
 `element`  
 [out]傳回`IUnknown`物件，代表指定之資料表的項目。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 資料表代表物件的集合。 根據這些物件中，項目參數可轉換成適當的介面。 例如，如果資料表包含[IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)物件，則項目參數可轉換成`IDiaSegment`介面。  
  
 它是更常見的方法呼叫`QueryInterface`方法中的[IDiaTable](../../debugger/debug-interface-access/idiatable.md)適當的列舉程式介面的介面，並透過列舉值的特定方式來存取資料表內容。 請參閱[IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)介面的範例。  
  
## <a name="see-also"></a>另請參閱  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [Idiatable:: Get_count](../../debugger/debug-interface-access/idiatable-get-count.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)   
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)