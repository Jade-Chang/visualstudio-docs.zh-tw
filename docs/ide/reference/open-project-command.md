---
title: 開啟專案命令
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.openproject
- file.opensolution
helpviewer_keywords:
- op command
- File.OpenProject command
- Open Project command
ms.assetid: baa85f86-041b-49f4-9ced-0c397dc180e1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0ff848ded38b0f59d3894ec4f78dd79ec9d182b8
ms.sourcegitcommit: db680e8fa8066f905e7f9240342ece7ab9259308
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2018
ms.locfileid: "37924144"
---
# <a name="open-project-command"></a>開啟專案命令

開啟現有的專案或方案。

## <a name="syntax"></a>語法

```cmd
File.OpenProject filename
```

## <a name="arguments"></a>引數

`filename`

必要。 要開啟之專案或方案的完整路徑和檔名。

> [!NOTE]
> `filename` 引數的語法需要包含空格的路徑使用引號。

## <a name="remarks"></a>備註

自動完成會在您鍵入時嘗試找出正確的路徑和檔名。

偵錯時，無法使用此命令。

## <a name="example"></a>範例

下列範例會開啟 Visual Basic 專案 **Test1**：

```cmd
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"
```

## <a name="see-also"></a>另請參閱

- [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)
- [命令視窗](../../ide/reference/command-window.md)
- [尋找/命令方塊](../../ide/find-command-box.md)
- [Visual Studio 命令別名](../../ide/reference/visual-studio-command-aliases.md)