---
title: DBGPROP_INFO_FLAGS |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DBGPROP_INFO_FLAGS
apilocation:
- scrobj.dll
f1_keywords:
- DBGPROP_INFO_FLAGS
helpviewer_keywords:
- DBGPROP_INFO_FLAGS
ms.assetid: e9450a21-a802-4c3e-8b3d-8e202f555de1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9821cde6c159712ff44438b74eea0f8e01247155
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641048"
---
# <a name="dbgpropinfoflags"></a>DBGPROP_INFO_FLAGS
用來指定`DebugPropertyInfo`欄位  
  
## <a name="syntax"></a>語法  
  
```  
enum {  
   DBGPROP_INFO_NAME  =0x001,  
   DBGPROP_INFO_TYPE  =0x002,  
   DBGPROP_INFO_VALUE  =0x004,  
   DBGPROP_INFO_FULLNAME  =0x020,  
   DBGPROP_INFO_ATTRIBUTES  =0x008,  
   DBGPROP_INFO_DEBUGPROP  =0x010,  
   DBGPROP_INFO_AUTOEXPAND  =0x8000000  
};  
```  
  
## <a name="members"></a>成員  
 DBGPROP_INFO_NAME  
 初始化`bstrName`欄位。  
  
 DBGPROP_INFO_TYPE  
 初始化`bstrType`欄位。  
  
 DBGPROP_INFO_VALUE  
 初始化`bstrValue`欄位。  
  
 DBGPROP_INFO_FULLNAME  
 初始化`bstrFullName`欄位。  
  
 DBGPROP_INFO_ATTRIBUTES  
 初始化`dwAttrib`欄位。  
  
 DBGPROP_INFO_DEBUGPROP  
 初始化`pDebugProp`包含欄位`IDebugProperty`介面。  
  
 DBGPROP_INFO_AUTOEXPAND  
 指定 [值] 欄位應包含的自動展開的值，是否有的話，這種類型的物件。  
  
## <a name="see-also"></a>另請參閱  
 [DebugPropertyInfo 結構](../../winscript/reference/debugpropertyinfo-structure.md)   
 [IDebugProperty 介面](../../winscript/reference/idebugproperty-interface.md)