---
title: IDebugDocumentPosition2 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDocumentPosition2
helpviewer_keywords:
- IDebugDocumentPosition2 interface
ms.assetid: 0e838ced-12bb-4efc-b811-2b7c034b77b0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d685a59dd9404f48cfbdf9ae72e1fa07ba0d0625
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugdocumentposition2"></a>IDebugDocumentPosition2
此介面代表來源檔案中的抽象位置。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugDocumentPosition2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 Visual Studio 通常會實作這個介面。 如果它必須提供自己原始程式碼，偵錯引擎 (DE) 也會實作這個介面 (做為當 DE 實作[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)介面)。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 這個介面會做為引數傳入[EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)。 它也提供一部分[BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)聯集 (具體而言， [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)結構)，接著是一部分[BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)結構，會用於建立暫止中斷點。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugDocumentPosition2`。  
  
|方法|描述|  
|------------|-----------------|  
|[GetFileName](../../../extensibility/debugger/reference/idebugdocumentposition2-getfilename.md)|取得包含此文件位置的來源檔案的檔案名稱。|  
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)|取得包含文件。|  
|[IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)|判斷這個位置是否包含指定的文件中。|  
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)|取得這個文件位置的範圍。|  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)