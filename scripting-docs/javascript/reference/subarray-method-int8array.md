---
title: "subarray 方法 (Int8Array) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 46271ed6-a3c3-41fb-bd6f-81efa9e8dedc
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# subarray 方法 (Int8Array)
為這個陣列取得 ArrayBuffer 存放區的新 Int8Array 檢視，並參考從 begin \(內含\) 到 end \(不含\) 的元素。  
  
## 語法  
  
```javascript  
var newInt8Array = int8Array.subset(begin, end);  
```  
  
## 參數  
 `newInt8Array`  
 這個方法所傳回的子陣列。  
  
 `begin`  
 陣列開頭的索引。  
  
 `end`  
 陣列結尾的索引。  這個索引為非內含。  
  
## 備註  
 如果 begin 或 end 是負值，則是指從陣列結尾起算的索引，而非從開頭起算。  如果未指定 end，子陣列就會包含從 TypedArray 的開始到結尾的所有元素。  begin 和 end 值所指定的範圍僅限於目前陣列的有效索引範圍。  如果新的 TypedArray 長度計算後為負值，則會限於零。  傳回的 TypedArray 與叫用這個方法的陣列會屬於相同類型。  
  
## 範例  
 下列範例將示範如何從來源陣列的第一個元素開始，取得長度為兩個元素的子陣列。  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var intArr = new Int8Array(buffer.byteLength);  
            var subArr = intArr.subarray(0, 2);  
        }  
    }  
  
```  
  
## 需求  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]