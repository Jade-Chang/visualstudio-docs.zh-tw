---
title: "Visual Studio 中的 Python 混和模式偵錯 | Microsoft Docs"
ms.custom: 
ms.date: 5/8/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4ca86a87-e254-4ab7-b3ba-a0ab99c1da93
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 90b2481b0ec4f9387fe3a2c0b733a103e8c03845
ms.openlocfilehash: 9e8ac0cbafe296223de68eb5b4f1b89680f61088
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017

---

# <a name="debugging-python-and-c-together"></a>同時對 Python 和 C++ 進行偵錯

多數的標準 Python 偵錯工具都僅支援對 Python 程式碼進行偵錯。 不過，實際上在需要高效能或是需要能直接叫用平台 API 的情況下，會將 Python 搭配 C 或 C++ 使用 (範例請參閱[建立適用於 Python 的 C++ 延伸模組](cpp-and-python.md))。 載入 Python 專案之後，Visual Studio 為 Python 和原生 (C/C++) 提供整合式的同步混合模式偵錯，包含合併的呼叫堆疊、可在 Python 和原生程式碼及任一類型的程式碼中斷點之間逐步執行、可在原生框架查看物件的 Python 表示法，反之亦然︰

![混合模式偵錯](media/mixed-mode-debugging.png) 

如需使用 Visual Studio 建置、測試原生 C 模組並進行偵錯的簡介，請參閱[深入探討︰建立原生模組 (英文)](https://youtu.be/D9RlT06a1EI) (youtube.com，9 分 9 秒)。

> [!VIDEO https://www.youtube.com/embed/D9RlT06a1EI]

> [!Note]
> 適用於 Visual Studio 1.x 的 Python 工具不提供混合模式偵錯。

## <a name="enabling-mixed-mode-debugging"></a>啟用混合模式偵錯

1. 在 [方案總管 (Solution Explorer)] 中以滑鼠右鍵按一下專案，選取 [屬性 (Properties)]，選取 [偵錯 (Debug)] 索引標籤，然後開啟 [啟用原生程式碼偵錯 (Enable native code debugging)] 的選項。 這樣會啟用所有偵錯工作階段的混合模式。

    ![啟用原生程式碼偵錯](media/mixed-mode-debugging-enable-native.png)

    > [!Tip]    
    > 當您啟用機器碼偵錯時，Python 的輸出視窗可能會在程式完成時立即消失，而不給您平常的「按任意鍵繼續...」暫停。 若要強制暫停，當您啟用機器碼偵錯時，請將 `-i` 選項加入 [偵錯] 索引標籤上的 [執行] > [解譯器引數] 欄位。 這會讓 Python 解譯器在程式碼完成之後進入互動模式，等候您按下 Ctrl + Z、Enter 以結束。

1. 將混合模式偵錯工具附加至現有的處理序 ([偵錯 (Debug)] > [附加至處理序 (Attach to Process)]) 時，選取 [選取 (Select)] 按鈕以開啟 [選取程式碼類型 (Select Code Type)] 對話方塊、設定 [偵錯這些程式碼類型 (Debug these code types)] 選項，然後同時選取清單中的 [原生 (Native)] 和 [Python]︰

    ![選取原生和 Python 程式碼類型](media/mixed-mode-debugging-code-type.png)

    程式碼類型設定為持續性；因此，如果您之後附加至其他處理序時想停用混合模式偵錯，您將需要重複這些步驟，並清除 Python 程式碼類型。

    除了選取 (或不選取) [原生 (Native)] 以外，您還可以選取其他程式碼類型。 例如，如果某個受管理的應用程式裝載 CPython，而 CPython 又使用原生延伸模組，您想對這三個進行偵錯，您可以同時核取 [Python]、[原生 (Native)] 及 [受管理 (Managed)**] 以提供整合的偵錯體驗，包括合併的呼叫堆疊，以及在這三個執行階段之間逐步執行。

1. 當您首次在混合模式開始偵錯時，您可能會看到 [需要 Python 符號] 對話方塊。 如需詳細資訊，請參閱[混合模式偵錯的符號](debugging-symbols-for-mixed-mode.md)。 針對任何指定的 Python 環境，符號只需安裝一次。 請注意，如果您透過 Visual Studio 2017 安裝程式安裝 Python 支援，會自動包含符號。

1. 您可能也想要手邊擁有 Python 原始碼本身。 對於標準的 Python，這可以取自 [https://www.python.org/downloads/source/](https://www.python.org/downloads/source/)。 下載適用於您版本的封存檔，並將它解壓縮到資料夾。 每當提示您時，請將 Visual Studio 指向該資料夾中的特定檔案。

> [!Note]
> 只有當 Python 專案已經載入到 Visual Studio 時，才會啟用這裡所述的混合模式偵錯。 該專案會決定 Visual Studio 偵錯模式，此模式會讓混合模式選項成為可用。 不過，如果您載入了 C++ 專案 (如同 [python.org 上所述，在另一個應用程式中內嵌 Python](https://docs.python.org/3/extending/embedding.html) 時會做的)，則 Visual Studio 會使用原生 C++ 偵錯工具，它並不支援混合模式偵錯。
>
> 在此情況下，請啟動 C++ 專案但不進行偵錯 ([偵錯] > [啟動但不偵錯] 或 Ctrl + F5)，然後使用 [偵錯] > [附加至處理序]。 在出現的對話方塊中，選取適當的處理序，然後使用 [選取] 按鈕來開啟 [選取程式碼類型] 對話方塊，在其中您可以選取 [Python]，如下所示。 選取 [確定] 關閉該對話方塊，然後選取 [附加] 啟動偵錯工具。 請注意，您可能需要在 C++ 應用程式中加入適合的暫停或延遲，以確保它不會在您可以附加偵錯工具之前就呼叫您要偵錯的 Python。
>
> ![附加偵錯工具時，選取 Python 作為偵錯類型](media/mixed-mode-debugging-attach-type.png)

## <a name="mixed-mode-specific-features"></a>混和模式的特定功能

- [合併的呼叫堆疊](#combined-call-stack)
- [在 Python 和原生程式碼之間逐步執行](#stepping-between-python-and-native-code)
- [原生程式碼中的 PyObject 值檢視](#pyobject-values-view-in-native-code)
- [Python 程式碼中的原生值檢視](#native-values-view-in-python-code)

### <a name="combined-call-stack"></a>合併的呼叫堆疊

[呼叫堆疊 (Call Stack)] 視窗會穿插顯示原生和 Python 堆疊框架，而兩者間會標示轉換︰

![合併的呼叫堆疊](media/mixed-mode-debugging-call-stack.png)

> [!Note]
> 如果設定 [工具] > [選項] > [偵錯] > [一般] > [啟用 Just My Code] 選項，轉換會顯示為「外部程式碼」，而不指定轉換的方向。

按兩下任一呼叫框架會讓它成為使用中，可能的話，會開啟適當的原始程式碼。 如果沒有原始程式碼，框架仍會是使用中，並可檢查區域變數。

### <a name="stepping-between-python-and-native-code"></a>在 Python 和原生程式碼之間逐步執行

使用逐步執行 (F11) 或跳離 (Shift+F11) 命令時，混合模式偵錯工具可正確處理程式碼類型之間的變更。 例如，當 Python 呼叫某個在 C 中實作之類型的方法時，在該方法的呼叫中逐步執行時，會停在實作該方法的原生函式開頭。 同樣地，當原生程式碼呼叫一些 Python API 函式時，會叫用 Python 程式碼。 例如，在原先定義於 Python 中的某個函式值上逐步執行到 `PyObject_CallObject`，會停在 Python 函式的開頭。 對於透過 [ctypes](http://docs.python.org/3/library/ctypes.html) 從 Python 叫用的原生函式，也支援從 Python 逐步執行到原生函式。

### <a name="pyobject-values-view-in-native-code"></a>原生程式碼中的 PyObject 值檢視

當原生 (C 或 C++) 框架為使用中時，其區域變數會顯示在偵錯工具的 [區域變數 (Locals)] 視窗。 在原生 Python 延伸模組中，其中有許多都是`PyObject` 類型 (即 `_object` 的 typedef)，或是一些其他基本 Python 類型 (請參閱下方清單)。 在混合模式偵錯中，這些值會出現一個標示為「Python 檢視 (Python view)」的額外子節點。 展開時，此節點會顯示變數的 Python 表示法，您所看到的一切，會與參考相同物件的本機變數出現在 Python 框架時相同。 此節點的子系是可編輯的。

![Python 檢視](media/mixed-mode-debugging-python-view.png)

若要停用這項功能，請在 [區域變數 (Locals)] 視窗的任意處按一下滑鼠右鍵，然後切換 [Python (Python)] > [顯示 Python 檢視節點 (Show Python View Nodes)] 功能表選項︰

![啟用 Python 檢視中](media/mixed-mode-debugging-enable-python-view.png)

會顯示 [Python 檢視 (Python View)] 節點 (如果啟用) 的 C 類型：

- `PyObject `
- `PyVarObject`
- `PyTypeObject`
- `PyByteArrayObject`
- `PyBytesObject`
- `PyTupleObject`
- `PyListObject`
- `PyDictObject`
- `PySetObject`
- `PyIntObject`
- `PyLongObject`
- `PyFloatObject`
- `PyStringObject`
- `PyUnicodeObject`

針對您自行撰寫的類型，不會自動顯示 [Python 檢視 (Python View)]。 撰寫 Python 3.x 的延伸模組時，這通常不是問題，因為所有物件最終都會有上述其中一個類型的 `ob_base` 欄位，因而導致 [Python 檢視 (Python View)] 顯示。 

不過，針對 Python 2.x，每個物件類型通常會將其標頭宣告為內嵌欄位的集合，而且自訂的撰寫類型和 C/C++ 程式碼中類型系統層級的 `PyObject` 之間沒有關聯。 若要啟用這種自訂類型的 [Python 檢視 (Python View)] 節點，請編輯 [Python 工具安裝目錄](installation.md#install-locations)中的 `PythonDkm.natvis`，然後直接在 C 結構或 C++ 類別的 XML 中新增另一個元素。

有一個替代 (也是更好) 的選項是依循 [PEP 3123 (英文)](http://www.python.org/dev/peps/pep-3123/) 並使用明確的 `PyObject ob_base;` 欄位 (而非`PyObject_HEAD`)，然而基於回溯相容性的理由，不一定總是可行。


### <a name="native-values-view-in-python-code"></a>Python 程式碼中的原生值檢視

如同上一節，當 Python 框架為使用中時，您可以在 [區域變數 (Locals)] 視窗中為原生值啟用 [C++ 檢視 (C++ View)]。 此功能預設為未啟用，請在 [區域變數 (Locals)] 視窗中按一下滑鼠右鍵並切換 [Python] > [顯示 C++ 檢視節點 (Show C++ View Nodes)]  功能表選項來開啟它。

![啟用 C++ 檢視中](media/mixed-mode-debugging-enable-cpp-view.png)

[C++ 檢視 (C++ View)] 節點提供值的基礎 C/C++ 結構的表示法，如在原生框架中所見。 比方說，它會顯示 Python 長整數的 `_longobject`(`PyLongObject` 是其 typedef) 執行個體，而且會嘗試推斷您自行撰寫之原生類別的類型。 此節點的子系是可編輯的。

![C++ 檢視](media/mixed-mode-debugging-cpp-view.png)

如果物件的子欄位為 `PyObject` 類型或其他支援的類型之一，它將包含一個 [Python 檢視 (Python View)] 表示法節點 (如果已啟用)，您就可以瀏覽物件圖形，其中的連結不會直接向 Python 公開。

不同於 [Python 檢視 (Python View)] 節點使用 Python 物件中繼資料來判斷物件的類型，[C++ 檢視 (C++ View)] 沒有類似的可靠機制。 一般而言，憑藉一個 Python 值 (也就是 `PyObject` 參考) 是無法可靠地判斷支援它的 C/C++ 結構。 混合模式偵錯工具會透過查看具有函式指標類型的物件類型 (例如其 `ob_type` 欄位參考的 `PyTypeObject`) 的各個欄位，以嘗試猜測該類型 。 如果這些函式指標之一參考的函式可以解析，而且該函式具有類型比 `PyObject*` 更明確的 `self` 參數，則會假設該類型為支援的類型。 例如，如果是下列函式中指定物件點的 `ob_type->tp_init`︰

```c
static int FobObject_init(FobObject* self, PyObject* args, PyObject* kwds) {
    return 0;
}
```

則偵錯工具可以正確地推論出物件的 C 類型是 `FobObject`。 如果無法從 `tp_init` 判斷更精確的類型，它會繼續嘗試其他欄位。 如果無法從這些欄位的任一個推論出類型，[C++ 檢視 (C++ View)] 節點會將物件顯示為 `PyObject` 執行個體。

為了始終能夠取得自訂撰寫類型最有用的表示法，註冊類型時最好註冊至少一個特殊函式，並使用強型別 `self` 參數。 大多數類型都能自然地滿足該需求；若非如此，`tp_init` 通常是針對此用途最方便使用的項目。 虛構的 `tp_init` 實作只能立即傳回零，它適用於為啟用偵錯工具類型推斷而存在的類型，如上面的程式碼範例所示。

## <a name="differences-from-standard-python-debugging"></a>與標準 Python偵錯的差異

混合模式偵錯工具與[標準 Python 偵錯工具](debugging.md)的不同之處在於它導入一些額外功能，但缺少一些 Python 相關功能︰

- 不支援的功能︰條件式中斷點、偵錯互動式視窗及跨平台遠端偵錯。
- 即時運算視窗︰可以使用，但僅有其中一小部分的功能，包括此處所列的所有限制。
- 支援的 Python 版本︰僅限 CPython 2.7 和 3.3 及更新版本。
- Visual Studio Shell︰搭配使用 Python 和 Visual Studio Shell 時 (例如使用整合式安裝程式進行安裝時)，Visual Studio 無法開啟 C++ 專案，且針對 C++ 檔案的編輯體驗僅如同使用基本文字編輯器。 不過，Shell 搭配偵錯工具視窗中的原始程式碼、逐步執行到原生程式碼及 C++ 運算式評估，可完整支援 C/C++ 偵錯和混合模式偵錯。
- 檢視和擴充物件︰在 [區域變數 (Locals)] 和 [監看式 (Watch)] 偵錯工具的工具視窗中檢視 Python 物件時，混合模式偵錯工具只會顯示物件的結構。 它不會自動評估屬性，或顯示計算的屬性。 對於集合，它只會顯示內建集合類型的元素 (`tuple`、`list``dict``set`)。 自訂集合類型不會視覺化為集合，除非它們繼承自某些內建的集合類型。
- 運算式評估：請參閱下文。

### <a name="expression-evaluation"></a>運算式評估

當偵錯的處理序在程式碼的任一處暫停時，標準 Python 偵錯工具可允許監看式和即時運算視窗中的任意 Python 運算式評估，只要它在 I/O 作業或其他類似的系統呼叫中不會被封鎖。 在混合模式偵錯中，任意運算式只有在 Python 程式碼中停止 (中斷點或逐步執行到程式碼之後 ) 時才能進行評估，且運算式只有在發生中斷點或逐步執行作業的執行緒上才能進行評估。

在原生程式碼或在 Python 程式碼 (當上述條件不適用時) 中停止時 (例如，在跳離作業之後，或在不同的執行緒上)，運算式評估僅限於存取目前所選框架範圍中的區域和全域變數、存取其欄位，及為含有常值的內建集合類型編製索引。 例如，下列運算式可在任何內容中評估 (前提是所有識別項參考適當類型的現有變數和欄位)︰

```python
foo.bar[0].baz['key']
```

混合模式偵錯工具也會以不同方式解析這類運算式。 所有成員存取作業都只會查閱直屬於物件的欄位 (例如在其 `__dict__` 或 `__slots__` 中的項目，或透過 `tp_members` 向 Python 公開的原生結構的欄位)，並忽略任何 `__getattr__`、`__getattribute__` 或描述元邏輯。 同樣地，所有編制索引作業會忽略 `__getitem__`，而直接存取集合的內部資料結構。

為保持一致性，此名稱解析配置會使用在所有符合限制的運算式評估條件約束的運算式，不論目前的停止點是否允許任意運算式。 若要在有功能完整的評估工具時強制適當的 Python 語意，請將運算式括在括號中︰

```python
(foo.bar[0].baz['key'])
```