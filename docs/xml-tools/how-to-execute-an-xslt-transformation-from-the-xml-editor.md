---
title: "HOW TO：從 XML 編輯器執行 XSLT 轉換 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 56a0fe82-5231-487d-8b6e-a08a9b04e0fc
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# HOW TO：從 XML 編輯器執行 XSLT 轉換
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

XML 編輯器可讓您將 XSLT 樣式表與 XML 文件相關聯、執行轉換，以及檢視輸出。XSLT 轉換的結果輸出會顯示在新文件視窗中。  
  
 **Output** 屬性指定輸出的檔名。如果 **Output** 屬性是空白，則暫存目錄中會產生檔名。副檔名以樣式表中的 `xsl:output` 項目為基礎，可以是 .xml、.txt 或 .htm。  
  
 如果 **Output** 屬性指定副檔名為 htm 或 .html 的檔名，則會使用 [!INCLUDE[msCoName](../xml-tools/includes/msconame_md.md)] Internet Explorer 預覽 XSLT 輸出。所有其他副檔名都使用 [!INCLUDE[msCoName](../xml-tools/includes/msconame_md.md)] Visual Studio 所選擇的預設編輯器來開啟。例如，如果副檔名為 .xml，則 Visual Studio 使用 XML 編輯器。  
  
### 從 XML 文件執行 XSLT 轉換  
  
1.  在 XML 編輯器中開啟 XML 文件。  
  
2.  將 XSLT 樣式表與 XML 文件產生關聯。  
  
    -   將 `xml-stylesheet` 處理指示加入 XML 文件。例如，加入下列行 `<?xml-stylesheet type='text/xsl' href='filename.xsl'?>` 至文件初構。  
  
         \- 或 \-  
  
    -   使用 \[屬性\] 視窗加入 XSLT 樣式表。在文件 \[屬性視窗\] 中，按一下 \[樣式表\] 欄位的 \[瀏覽\] 按鈕，選取 XSLT 樣式表，並按一下 \[開啟\]。  
  
3.  在 \[XML 編輯器\] 工具列上，按一下 \[顯示 XSL 輸出\] 按鈕。  
  
    > [!NOTE]
    >  如果沒有與 XML 文件相關聯的樣式表，則會出現一個對話方塊，提示您提供要使用的樣式表。  
    >   
    >  XSLT 轉換的結果輸出會顯示在新文件視窗中。  
  
### 從 XSLT 樣式表執行 XSLT 轉換  
  
1.  在 \[XML 編輯器\] 中開啟 XSLT 樣式表。  
  
2.  在文件 \[屬性\] 視窗的 \[輸入\] 欄位中指定 XML 文件。  
  
    > [!NOTE]
    >  XML 文件為用於轉換的輸入文件。如果在啟動 XSLT 轉換時未指定文件，則當 \[開啟檔案\] 對話方塊出現時您便可指定文件。  
  
3.  在 \[XML 編輯器\] 工具列上，按一下 \[顯示 XSLT 輸出\] 按鈕。  
  
     XSLT 轉換的結果輸出會顯示在新文件視窗中。  
  
### 提供不同的輸出檔案名稱  
  
1.  在文件 \[屬性\] 視窗的 \[輸出\] 欄位中指定檔名。  
  
2.  在 \[XML 編輯器\] 工具列上，按一下 \[顯示 XSLT 輸出\] 按鈕。  
  
     XSLT 轉換的結果輸出會顯示在新文件視窗中，輸出視窗中使用的編輯器取決於 **Output** 文件屬性的副檔名。  
  
## 請參閱  
 [XML 編輯器](../xml-tools/xml-editor.md)