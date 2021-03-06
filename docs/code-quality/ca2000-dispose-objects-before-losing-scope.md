---
title: CA2000：必須在超出範圍前處置物件
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2000
- Dispose objects before losing scope
- DisposeObjectsBeforeLosingScope
helpviewer_keywords:
- CA2000
- DisposeObjectsBeforeLosingScope
ms.assetid: 0c3d7d8d-b94d-46e8-aa4c-38df632c1463
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6b492324b87bfc25741492669b7c659c43fc9765
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31920401"
---
# <a name="ca2000-dispose-objects-before-losing-scope"></a>CA2000：必須在超出範圍前處置物件
|||
|-|-|
|TypeName|DisposeObjectsBeforeLosingScope|
|CheckId|CA2000|
|分類|Microsoft.Reliability|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 本機物件<xref:System.IDisposable>型別建立，但是物件的所有參考都都超出範圍之前，無法處置物件。

## <a name="rule-description"></a>規則描述
 如果所有參考都都超出範圍之前，不會明確處置可處置的物件，物件會處置記憶體回收行程執行物件的完成項時的時間不確定。 因為發生例外事件可能會導致無法完成項執行物件的物件應該改以明確處置。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，呼叫<xref:System.IDisposable.Dispose%2A>上的所有參考都都超出範圍之前的物件。

 請注意，您可以使用`using`陳述式 (`Using`中[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) 來包裝實作物件`IDisposable`。 物件會包裝在這種方式，會自動在結束時的處置`using`區塊。

 以下是某些情況下，使用陳述式，以防止 IDisposable 物件並不可能會導致發生 CA2000。

-   傳回可處置的物件需要物件的建構在 try/finally 區塊外部的 using 區塊。

-   初始化可處置的物件的成員不應該在執行中的建構函式的 using 陳述式。

-   巢狀結構只能有一個例外狀況處理常式所保護的建構函式。 例如，套用至物件的

    ```csharp
    using (StreamReader sr = new StreamReader(new FileStream("C:\myfile.txt", FileMode.Create)))
    { ... }
    ```

     會導致 CA2000 發生因為 StreamReader 物件的建構中的失敗可能導致 FileStream 物件永遠不會關閉。

-   動態物件應該使用陰影物件來實作 Dispose 模式的 IDisposable 物件。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 除非您已在呼叫 `Dispose` 的物件上呼叫方法，例如 <xref:System.IO.Stream.Close%2A>，或是引發警告的方法傳回的 IDisposable 物件會包裝您的物件，否則請勿隱藏這項規則的警告。

## <a name="related-rules"></a>相關的規則
 [CA2213：可處置的欄位應該受到處置](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

 [CA2202：不要多次處置物件](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)

## <a name="example"></a>範例
 如果您要實作的方法，傳回可處置的物件，使用 try/finally 區塊沒有 catch 區塊來確定物件已處置。 藉由使用 try/finally 區塊，您可以允許例外狀況會在錯誤點引發，並確定該物件已處置。

 在 OpenPort1 方法中，以開啟 ISerializable 物件 SerialPort 呼叫或 SomeMethod 呼叫可能會失敗。 CA2000 警告會在此實作中引發。

 在 OpenPort2 方法中，兩個序列連接埠物件都可以宣告和設定為 null:

-   `tempPort`用來測試方法作業都成功。

-   `port`用於方法的傳回值。

 `tempPort`建構，並在中開啟`try`區塊，以及任何其他需要在同一個執行工作`try`區塊。 在結尾`try`區塊中，開啟連接埠指派給`port`將傳回的物件和`tempPort`物件設定為`null`。

 `finally`值區塊檢查`tempPort`。 如果不是 null，方法中的作業失敗，並`tempPort`關閉並確定已釋放任何資源。 如果方法的作業成功，或如果作業失敗，將會是 null，傳回的連接埠物件將包含開啟的 SerialPort 物件。

```csharp
public SerialPort OpenPort1(string portName)
{
   SerialPort port = new SerialPort(portName);
   port.Open();  //CA2000 fires because this might throw
   SomeMethod(); //Other method operations can fail
   return port;
}

public SerialPort OpenPort2(string portName)
{
   SerialPort tempPort = null;
   SerialPort port = null;
   try
   {
      tempPort = new SerialPort(portName);
      tempPort.Open();
      SomeMethod();
      //Add any other methods above this line
      port = tempPort;
      tempPort = null;

   }
   finally
   {
      if (tempPort != null)
      {
         tempPort.Close();
      }
   }
   return port;
}
```

```vb
Public Function OpenPort1(ByVal PortName As String) As SerialPort

   Dim port As New SerialPort(PortName)
   port.Open()    'CA2000 fires because this might throw
   SomeMethod()   'Other method operations can fail
   Return port

End Function


Public Function OpenPort2(ByVal PortName As String) As SerialPort

   Dim tempPort As SerialPort = Nothing
   Dim port As SerialPort = Nothing

   Try
      tempPort = New SerialPort(PortName)
      tempPort.Open()
      SomeMethod()
      'Add any other methods above this line
      port = tempPort
      tempPort = Nothing

   Finally
      If Not tempPort Is Nothing Then
         tempPort.Close()
      End If


   End Try

   Return port

End Function
```

## <a name="example"></a>範例
 根據預設，[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]編譯器有溢位檢查的所有算術運算子。 因此，任何 Visual Basic 的算術運算可能會擲回<xref:System.OverflowException>。 這可能會導致非預期規則，例如 CA2000 違規。 例如，下列 CreateReader1 函式會產生 CA2000 違規，因為 Visual Basic 編譯器會發出溢位檢查可能會擲回例外狀況，可能導致不要處置 StreamReader 加法的指示。

 若要修正此問題，您可以停用的溢位檢查發出 Visual Basic 編譯器在您的專案中，或您可以修改您的程式碼，如下列 CreateReader2 函式所示。

 要停用發出的溢位檢查，以滑鼠右鍵按一下方案總管] 中的專案名稱，然後按一下 [**屬性**。 按一下**編譯**，按一下 **進階編譯選項**，然後檢查**移除整數溢位檢查**。

  [!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../code-quality/codesnippet/VisualBasic/ca2000-dispose-objects-before-losing-scope-vboverflow_1.vb)]

## <a name="see-also"></a>另請參閱
 <xref:System.IDisposable> [處置模式](/dotnet/standard/design-guidelines/dispose-pattern)