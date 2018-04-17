---
title: IManagedAddin::Load |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords: ''
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 545560c5f02437925c2f93e9c6dc3113e1cddd0b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="imanagedaddinload"></a>IManagedAddin::Load
  載入 Managed VSTO 增益集時呼叫。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT Load([in] BSTR bstrManifestURL,   
             [in] IDispatch *pdispApplication);  
```  
  
#### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|*bstrManifestURL*|VSTO 增益集之資訊清單的完整路徑。|  
|*pdispApplication*|代表載入 VSTO 增益集的主應用程式 IDispatch 指標。|  
  
## <a name="return-value"></a>傳回值  
 HRESULT 值，表示此方法是否已順利完成。  
  
## <a name="remarks"></a>備註  
 資訊清單是一種檔案 (通常是 XML 檔案)，可提供協助載入 VSTO 增益集的資訊。 例如，資訊清單可以指定 VSTO 增益集組件的位置，以及載入 VSTO 增益集時要具現化的進入點類別。  
  
 *BstrManifestURL*參數包含的值`Manifest`HKEY_CURRENT_USER\Software\Microsoft\Office 下的項目\\*\<應用程式名稱 >*\Addins\\*\<增益集識別碼 >* VSTO 增益集的登錄機碼。 如需詳細資訊，請參閱 [IManagedAddin Interface](../vsto/imanagedaddin-interface.md)。  
  
 實作 [IManagedAddIn::Load](../vsto/imanagedaddin-load.md) 方法可針對所要載入之 VSTO 增益集執行工作，例如設定增益集的應用程式定義域和安全性原則。  
  
## <a name="see-also"></a>另請參閱  
 [IManagedAddin Interface](../vsto/imanagedaddin-interface.md)   
 [IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)  
  
  