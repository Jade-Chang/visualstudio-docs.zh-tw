---
title: DEBUG_CUSTOM_VIEWER |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- DEBUG_CUSTOM_VIEWER
helpviewer_keywords:
- DEBUG_CUSTOM_VIEWER structure
ms.assetid: 8e0ef3f0-0107-48e8-a037-6e52b4c4ed9d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 84d8bdc7a4ea9ac59ee0956226618402b397844b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31109986"
---
# <a name="debugcustomviewer"></a>DEBUG_CUSTOM_VIEWER
識別自訂的檢視器的結構，或輸入視覺化檢視。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct tagDEBUG_CUSTOM_VIEWER {  
   DWORD dwID;  
   BSTR  bstrMenuName;  
   BSTR  bstrDescription;  
   GUID  guidLang;  
   GUID  guidVendor;  
   BSTR  bstrMetric;  
} DEBUG_CUSTOM_VIEWER;  
```  
  
```csharp  
public struct DEBUG_CUSTOM_VIEWER {  
   public uint   dwID;  
   public string bstrMenuName;  
   public string bstrDescription;  
   public Guid   guidLang;  
   public Guid   guidVendor;  
   public string bstrMetric;  
};  
```  
  
## <a name="members"></a>成員  
 dwID  
 若要區別多個檢視器或其中一個所實作的視覺化檢視的識別碼`GUID`。  
  
 bstrMenuName  
 文字會出現在下拉式選單。  
  
 bstrDescription  
 自訂檢視器或 （必須是 null 的值如果不使用） 的類型視覺化檢視的描述。  
  
 guidLang  
 提供的運算式評估工具的語言。  
  
 guidVendor  
 廠商提供的運算式評估工具。  
  
 bstrMetric  
 度量的自訂檢視器或類型的視覺化檢視`CLSID`儲存。  
  
## <a name="remarks"></a>備註  
 此結構的清單由呼叫[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)方法 (以及依擴充而[GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)方法)。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)