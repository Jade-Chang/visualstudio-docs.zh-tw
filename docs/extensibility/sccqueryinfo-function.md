---
title: "SccQueryInfo 函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccQueryInfo
helpviewer_keywords:
- SccQueryInfo function
ms.assetid: 3973d336-a9b7-41a2-a4e6-bb8184a96aaf
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 7bda59c3bf674354e38fa306abe1fbb673f40e19
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="sccqueryinfo-function"></a>SccQueryInfo 函式
此函式會取得一組選取原始檔控制下的檔案狀態資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
SCCRTN SccQueryInfo(  
   LPVOID  pvContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LPLONG  lpStatus  
);  
```  
  
#### <a name="parameters"></a>參數  
 pvContext  
 [in]原始檔控制外掛程式的內容結構。  
  
 nFiles  
 [in]中指定的檔案數目`lpFileNames`陣列長度和`lpStatus`陣列。  
  
 lpFileNames  
 [in]要查詢的檔案名稱陣列。  
  
 lpStatus  
 [in、 out]陣列，其中原始檔控制外掛程式傳回每個檔案的狀態旗標。 如需詳細資訊，請參閱[檔案狀態碼](../extensibility/file-status-code-enumerator.md)。  
  
## <a name="return-value"></a>傳回值  
 此函式的原始檔控制外掛程式實作預期會傳回下列值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|查詢已成功。|  
|SCC_E_ACCESSFAILURE|發生問題，以存取原始檔控制系統，可能因網路或競爭問題。 建議使用重試。|  
|SCC_E_PROJNOTOPEN|無法在原始檔控制開啟專案。|  
|SCC_E_NONSPECIFICERROR|不明確的失敗。|  
  
## <a name="remarks"></a>備註  
 如果`lpFileName`為空字串，目前沒有更新狀態資訊。 否則，它是可能的狀態資訊已變更的檔案的完整路徑名稱。  
  
 傳回陣列可以是位元遮罩`SCC_STATUS_xxxx`位元。 如需詳細資訊，請參閱[檔案狀態碼](../extensibility/file-status-code-enumerator.md)。 原始檔控制系統可能不支援所有的位元類型。 例如，如果`SCC_STATUS_OUTOFDATE`不提供，只是無法設定位元。  
  
 使用這個函數時簽出檔案，請注意下列`MSSCCI`狀態需求：  
  
-   `SCC_STATUS_OUTBYUSER`目前的使用者已簽出檔案時設定。  
  
-   `SCC_STATUS_CHECKEDOUT`無法設定，除非`SCC_STATUS_OUTBYUSER`設定。  
  
-   `SCC_STATUS_CHECKEDOUT`時才會設定檔案已簽出到指定的工作目錄。  
  
-   如果檔案已簽出目前的使用者所到工作目錄，以外的目錄`SCC_STATUS_OUTBYUSER`設定但`SCC_STATUS_CHECKEDOUT`不是。  
  
## <a name="see-also"></a>請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [檔案狀態碼](../extensibility/file-status-code-enumerator.md)