---
title: "IDebugMethodField |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugMethodField
helpviewer_keywords:
- IDebugMethodField interface
ms.assetid: a7dc9030-fc98-4cf1-b943-37a4003300b6
caps.latest.revision: 12
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
ms.openlocfilehash: 46d6173d2c015dc783bac0778b93419101d4c553
ms.lasthandoff: 04/05/2017

---
# <a name="idebugmethodfield"></a>IDebugMethodField
此介面描述的方法。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugMethodField : IDebugContainerField  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 符號提供者會實作此介面實作在相同物件上[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)介面。 這個介面是特製化，呈現的方法。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 使用[QueryInterface](/cpp/atl/queryinterface)獲得從這個介面[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)介面[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)傳回`FIELD_TYPE_METHOD`。 此外，方法[GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)， [GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)，和[EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md)、 所有傳回`IDebugMethodField`介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 除了上[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)和[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)介面，這個介面會實作下列方法︰  
  
|方法|描述|  
|------------|-----------------|  
|[EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)|建立方法的參數的列舉值。|  
|[GetThis](../../../extensibility/debugger/reference/idebugmethodfield-getthis.md)|取得物件，包含方法的"this"指標。|  
|[EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)|建立方法的所有區域變數的列舉值。|  
|[EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)|建立選取的本機變數之方法的列舉值。|  
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugmethodfield-iscustomattributedefined.md)|判斷是否已定義特定的自訂屬性。|  
|[EnumStaticLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumstaticlocals.md)|建立方法的靜態區域變數的列舉值。|  
|[GetGlobalContainer](../../../extensibility/debugger/reference/idebugmethodfield-getglobalcontainer.md)|取得全域方法的容器。|  
|[EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)|建立的每個呼叫的方法所需的引數類型的列舉值。|  
  
## <a name="remarks"></a>備註  
 方法可以包含參數，以及本機變數。  
  
## <a name="requirements"></a>需求  
 標頭︰ sh.h  
  
 命名空間︰ Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰ Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [符號提供者介面](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)