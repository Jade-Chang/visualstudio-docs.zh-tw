---
title: IApplicationDebugger::QueryAlive |Microsoft 文件
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebugger.QueryAlive
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebugger::QueryAlive
ms.assetid: 41181ebb-a3bf-4e41-82af-d6c7348dc706
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 48571476407c29b9af949bd6f626d14ea822f2e8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
ms.locfileid: "24725318"
---
# <a name="iapplicationdebuggerqueryalive"></a>IApplicationDebugger::QueryAlive
表示偵錯工具是否有回應。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT QueryAlive();  
```  
  
#### <a name="parameters"></a>參數  
 這個方法會採用任何參數。  
  
## <a name="return-value"></a>傳回值  
 方法會傳回 `HRESULT`。 可能的值包括 (但不限於) 下表中的這些值。  
  
|值|說明|  
|-----------|-----------------|  
|`S_OK`|方法成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會指示偵錯工具是否有回應。 這個方法的實作應該會一律傳回`S_OK`。  
  
 如果偵錯工具處理序意外終止，COM 會從呼叫此方法的封送處理 proxy 傳回錯誤。  
  
## <a name="see-also"></a>另請參閱  
 [IApplicationDebugger 介面](../../winscript/reference/iapplicationdebugger-interface.md)