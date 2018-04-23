---
title: SccRunScc 函式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccRunScc
helpviewer_keywords:
- SccRunScc function
ms.assetid: bbe7c931-b17a-4779-9cf6-59e5f9f0c172
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 322ebe148144260106fb895273b66e1b9f5696f8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="sccrunscc-function"></a>SccRunScc 函式
此函式會叫用的原始檔控制系統管理工具。  
  
## <a name="syntax"></a>語法  
  
```cpp  
SCCRTN SccRunScc(  
   LPVOID  pvContext,  
   HWND    hWnd,  
   LONG    nFiles,  
   LPCSTR* lpFileNames  
);  
```  
  
#### <a name="parameters"></a>參數  
 pvContext  
 [in]原始檔控制外掛程式的內容結構。  
  
 hWnd  
 [in]原始檔控制外掛程式之任何它所提供的對話方塊，可以使用為父代 IDE 視窗的控制代碼。  
  
 nFiles  
 [in]中指定的檔案數目`lpFileNames`陣列。  
  
 lpFileNames  
 [in]選取的檔案名稱的陣列。  
  
## <a name="return-value"></a>傳回值  
 此函式的原始檔控制外掛程式實作預期會傳回下列值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|原始檔控制系統管理工具已順利叫用。|  
|SCC_I_OPERATIONCANCELED|作業已取消。|  
|SCC_E_INITIALIZEFAILED|無法初始化原始檔控制系統。|  
|SCC_E_ACCESSFAILURE|無法存取原始檔控制系統，可能是因為網路或競爭問題。|  
|SCC_E_CONNECTIONFAILURE|無法連線至原始檔控制系統。|  
|SCC_E_FILENOTCONTROLLED|選取的檔案不在原始檔控制中。|  
|SCC_E_NONSPECIFICERROR|不明確的失敗。|  
  
## <a name="remarks"></a>備註  
 此函式可讓呼叫者存取透過外部管理工具功能的原始檔控制系統的完整範圍。 如果原始檔控制系統沒有使用者介面，原始檔控制外掛程式可以實作的介面來執行必要的管理功能。  
  
 此函式呼叫計數與目前所選檔案的檔案名稱的陣列。 如果系統管理工具支援它，檔案清單可用來預先在管理介面中的檔案否則，您可以忽略清單。  
  
 此函式通常叫用使用者選取時**啟動\<原始檔控制伺服器 >**從**檔案** -> **原始檔控制**功能表。 這**啟動**功能表選項可一律停用，或甚至隱藏設定登錄項目。 請參閱[如何： 安裝原始檔控制外掛程式](../extensibility/internals/how-to-install-a-source-control-plug-in.md)如需詳細資訊。 只有當呼叫此函式[SccInitialize](../extensibility/sccinitialize-function.md)傳回`SCC_CAP_RUNSCC`功能位元 (請參閱[功能旗標](../extensibility/capability-flags.md)如需詳細資訊，這和其他功能的位元)。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)   
 [如何： 安裝原始檔控制外掛程式](../extensibility/internals/how-to-install-a-source-control-plug-in.md)   
 [功能旗標](../extensibility/capability-flags.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)