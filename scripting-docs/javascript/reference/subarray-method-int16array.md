---
title: "subarray 方法 (Int16Array) | Microsoft Docs"
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
ms.assetid: 8a7437c2-8c4e-41eb-a3d5-ec4f7399b81d
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# subarray 方法 (Int16Array)
指定子陣列的第一個和最後一個成員，為這個陣列取得 [ArrayBuffer 物件](../../javascript/reference/arraybuffer-object.md) 存放區的新 Int16Array 檢視。  
  
## 語法  
  
```javascript  
var newInt16Array = int16Array.subarray(begin, end);  
```  
  
## 參數  
 `newInt16Array`  
 這個方法所傳回的子陣列。  
  
 `begin`  
 陣列開頭的索引。  
  
 `end`  
 陣列結尾的索引。  這個索引為非內含。  
  
## 備註  
 如果 `begin` 或 `end` 是負值，則是指從陣列結尾起算的索引，而非從開頭起算。  如果未指定 `end`，子陣列就會包含從類型陣列的開始到結尾的所有元素。  `begin` 和 `end` 值所指定的範圍僅限於目前陣列的有效索引範圍。  如果新的類型陣列的長度計算後為負值，則會限於零。  傳回的陣列與叫用這個方法的陣列會屬於相同類型。  
  
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
            var intArr = new Int16Array(buffer.byteLength / 2);  
            var subArr = intArr.subarray(0, 2);  
        }  
    }  
  
```  
  
## 需求  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]