---
title: 控制色彩、線條樣式和其他圖形屬性
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 710e4a20d0b9cc60a32786836fda7716a70f86e5
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="controlling-color-line-style-and-other-shape-properties"></a>控制色彩、線條樣式和其他圖形屬性
某些圖形屬性例如色彩可以 '公開'-也就被連結至圖形的網域屬性。 其他人也不必直接控制。

## <a name="exposing-a-property"></a>公開屬性
 某些圖形屬性，例如色彩可以連結到網域屬性的值。

 DSL 定義中，選取形狀、 連接器或圖表的類別。 其內容功能表上，選擇**新增公開**，然後選擇您要填滿色彩等的屬性。

 圖形現在有網域屬性，您可以在程式碼中或以使用者設定。

## <a name="dynamically-updating-an-exposed-property"></a>以動態方式更新公開的屬性
 通常您會想要讓公開的屬性相依於另一個屬性。 例如，您可以小於零的圖形以特定的網域屬性時變成紅色。 若要讓此相依性，建立[規則](../modeling/rules-propagate-changes-within-the-model.md)。 例如: 

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
namespace ExampleNamespace
{
 // Attribute associates the rule with class:
 [RuleOn(typeof(CarShape), FireTime = TimeToFire.TopLevelCommit)]
 // The rule is a class derived from one of the abstract rules:
 class CarShapeAddRule : AddRule
 {
 // Override the abstract method:
 public override void ElementAdded(ElementAddedEventArgs e)
 {
 base.ElementAdded(e);
 CarShape shape = e.ModelElement as CarShape;
 Store store = shape.Store;
 // Ignore this call if we're currently loading a model:
 if (store.TransactionManager.CurrentTransaction.IsSerializing)
  return;
 Car car = shape.ModelElement as Car;
 // Code here propagates change as required - for example:
 shape.FillColor = car.Somebool ? System.Drawing.Color.Red : System.Drawing.Color.Green;
 }
}
 // The rule must be registered:
 public partial class ExampleDomainModel
 {
 protected override Type[] GetCustomDomainModelTypes()
 {
  List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
  types.Add(typeof(CarShapeAddRule));
  // If you add more rules, list them here.
  return types.ToArray();
 }
 }
}
```