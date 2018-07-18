---
title: IDebugContainerField::EnumFields |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugContainerField::EnumFields
helpviewer_keywords:
- IDebugContainerField::EnumFields method
ms.assetid: 9e5e681b-ad49-4c62-bd95-4afa11d61a57
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0af939253de7b592e7c0ec35be9ea2b9bbff2b0f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31106961"
---
# <a name="idebugcontainerfieldenumfields"></a>IDebugContainerField::EnumFields
建立容器的欄位的列舉值。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumFields(   
   FIELD_KIND         dwKindFilter,  
   FIELD_MODIFIERS    dwModifiersFilter,  
   LPCOLESTR          pszNameFilter,  
   NAME_MATCH         nameMatch,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int EnumFields(  
   enum_ FIELD_KIND      dwKindFilter,   
   enum_ FIELD_MODIFIERS dwModifiersFilter,   
   string                pszNameFilter,   
   NAME_MATCH            nameMatch,   
   out IEnumDebugFields  ppEnum  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwKindFilter`  
 [in]組合[FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)常數，選取要列舉的欄位。 欄位類型可以儲存類型，例如類別或基本類型，或特定的資訊，例如本機、 參數或"this"指標，說明。  
  
 `dwModifiersFilter`  
 [in]組合[FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)常數，選取要列舉的欄位。 欄位修飾詞可存取的權限，例如公用或私用或儲存體的資訊，例如虛擬、 靜態，或最後一個。  
  
 `pszNameFilter`  
 [in]要列舉的欄位名稱。 如果要傳回所有的欄位，這可以是 null 值。  
  
 `nameMatch`  
 [in]中的值[NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)列舉，用於控制是否搜尋是否區分大小寫。  
  
 `ppEnum`  
 [out]傳回[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)物件，代表欄位的清單。 如果沒有任何欄位，則傳回 null 值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回 S_OK 或 S_FALSE，如果沒有任何欄位。 反之則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 `dwKindFilter`， `dwModifiersFilter`，和`pszNameFilter`參數可以結合，例如，若要選取所有公用虛擬方法名為"MyMethod"。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)   
 [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)   
 [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)