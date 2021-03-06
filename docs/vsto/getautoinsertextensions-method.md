---
title: GetAutoInsertExtensions 方法
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f8573576b40afabb5ec568a0c471e7b1d79560ba
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2018
---
# <a name="getautoinsertextensions-method"></a>GetAutoInsertExtensions 方法
  取得要在偵錯期間自動插入的 Office 應用程式的相關資訊。  
  
 這個方法是保留供日後使用。  
  
## <a name="syntax"></a>語法  
  
```c  
HRESULT GetAutoInsertExtensions(  
    [out, retval] SAFEARRAY(BSTR)* psaExtensionNames  
);  
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|*psaExtensionNames*|適用於 Office 的應用程式的延伸模組名稱。|  
  
## <a name="return-value"></a>傳回值  
 HRESULT 值，表示此方法是否已順利完成。  
  
## <a name="remarks"></a>備註  
 適用於 Office 插入每個應用程式會以 Office 應用程式擴充功能名稱，對應於底下的值傳回**HKEY_CURRENT_USER\Software\Microsoft\Office\WEF\Developer**。 主機必須查閱登錄中的這些值，並自動插入擴充功能。  
  
  