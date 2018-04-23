---
title: IDebugDisassemblyStream2::Read |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDisassemblyStream2::Read
helpviewer_keywords:
- IDebugDisassemblyStream2::Read
ms.assetid: 7db5f6bb-73ee-45bc-b187-c1b6aa2dfdd5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d9143abac4ce10a2b7305889e1d1a5236c1e9b07
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugdisassemblystream2read"></a>IDebugDisassemblyStream2::Read
讀取從反組譯碼資料流中目前位置開始的指示。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Read(   
   DWORD                     dwInstructions,  
   DISASSEMBLY_STREAM_FIELDS dwFields,  
   DWORD*                    pdwInstructionsRead,  
   DisassemblyData*          prgDisassembly  
);  
```  
  
```csharp  
int Read(   
   uint                           dwInstructions,  
   enum_DISASSEMBLY_STREAM_FIELDS dwFields,  
   out uint                       pdwInstructionsRead,  
   DisassemblyData[]              prgDisassembly  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwInstructions`  
 [in]反組譯的指令數目。 此值也是最大長度`prgDisassembly`陣列。  
  
 `dwFields`  
 [in]從旗標的組合[DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)列舉型別，以指出哪些欄位的`prgDisassembly`會填入。  
  
 `pdwInstructionsRead`  
 [out]傳回實際反組譯的指令的數目。  
  
 `prgDisassembly`  
 [out]陣列[DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)填寫反組譯程式碼中，反組譯指示每一個結構的結構。 這個陣列的長度取決於`dwInstructions`參數。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 可取得指示目前領域中可用的最大數目，藉由呼叫[GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)方法。  
  
 可以藉由呼叫變更目前位置的下一個指令會從讀取[搜尋](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)方法。  
  
 `DSF_OPERANDS_SYMBOLS`旗標可以加入至`DSF_OPERANDS`加上旗標`dwFields`參數，以指出當解譯指示應該使用的符號名稱。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)   
 [GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)   
 [搜尋](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)