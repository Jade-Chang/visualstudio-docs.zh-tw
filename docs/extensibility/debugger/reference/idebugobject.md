---
title: "IDebugObject |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugObject
helpviewer_keywords:
- IDebugObject interface
ms.assetid: 05cd8bf4-c9ee-4b49-b782-2263c33067d6
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 4707784dcccfa85f0edee277bc40ed19013509b5
ms.lasthandoff: 04/05/2017

---
# <a name="idebugobject"></a>IDebugObject
> [!IMPORTANT]
>  在 Visual Studio 2015 中，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱[CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 此介面代表繫結器建立封裝的符號和運算式值的物件。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugObject : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 運算式評估工具會實作這個介面來代表的物件。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 這個介面是運算式評估工具會使用已剖析的運算式中的所有物件的基底類別。 它由呼叫[繫結](../../../extensibility/debugger/reference/idebugbinder-bind.md)方法。 [QueryInterface](/cpp/atl/queryinterface)從這個介面取得更具特製化的介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugObject`。  
  
|方法|描述|  
|------------|-----------------|  
|[GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md)|取得物件的大小。|  
|[GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)|取得物件的值做為一系列連續的位元組。|  
|[SetValue](../../../extensibility/debugger/reference/idebugobject-setvalue.md)|設定物件的值從一系列連續的位元組。|  
|[SetReferenceValue](../../../extensibility/debugger/reference/idebugobject-setreferencevalue.md)|設定此物件的參考值。|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugobject-getmemorycontext.md)|取得代表值的物件位址的記憶體內容。|  
|[GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md)|偵錯引擎的位址空間中建立受管理物件的複本。|  
|[IsNullReference](../../../extensibility/debugger/reference/idebugobject-isnullreference.md)|測試此物件是否為 null 參考。|  
|[IsEqual](../../../extensibility/debugger/reference/idebugobject-isequal.md)|比較這個物件。|  
|[IsReadOnly](../../../extensibility/debugger/reference/idebugobject-isreadonly.md)|判斷此物件是否為唯讀。|  
|[IsProxy](../../../extensibility/debugger/reference/idebugobject-isproxy.md)|判斷物件是否為透明的 proxy。|  
  
## <a name="remarks"></a>備註  
 運算式評估工具會使用此介面的基底類別來表示剖析樹狀目錄中的物件。  
  
## <a name="requirements"></a>需求  
 標頭︰ ee.h  
  
 命名空間︰ Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰ Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [運算式評估介面](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)   
 [繫結](../../../extensibility/debugger/reference/idebugbinder-bind.md)