---
title: "HOW TO：移轉 XslTransform 程式碼 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: 910beb2f-cfb3-4e8e-9936-f7e0c5f4064a
caps.latest.revision: 2
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 2
---
# HOW TO：移轉 XslTransform 程式碼
設計的新版 XSLT 類別與現有類別非常類似。  <xref:System.Xml.Xsl.XslCompiledTransform> 類別取代了 <xref:System.Xml.Xsl.XslTransform> 類別。  使用 <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> 方法編譯樣式表。  使用 <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> 方法執行轉換。  下列程序顯示常見的 XSLT 工作，並比較使用 <xref:System.Xml.Xsl.XslTransform> 類別的程式碼與使用 <xref:System.Xml.Xsl.XslCompiledTransform> 類別的程式碼。  
  
### 轉換檔案及輸出為 URI  
  
-   使用 <xref:System.Xml.Xsl.XslTransform> 類別的程式碼。  
  
     [!code-csharp[XML_Migration#9](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#9)]
     [!code-vb[XML_Migration#9](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#9)]  
  
-   使用 <xref:System.Xml.Xsl.XslCompiledTransform> 類別的程式碼。  
  
     [!code-csharp[XML_Migration#10](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#10)]
     [!code-vb[XML_Migration#10](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#10)]  
  
### 編譯樣式表並使用具有預設認證的解析程式  
  
-   使用 <xref:System.Xml.Xsl.XslTransform> 類別的程式碼。  
  
     [!code-csharp[XML_Migration#11](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#11)]
     [!code-vb[XML_Migration#11](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#11)]  
  
-   使用 <xref:System.Xml.Xsl.XslCompiledTransform> 類別的程式碼。  
  
     [!code-csharp[XML_Migration#12](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#12)]
     [!code-vb[XML_Migration#12](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#12)]  
  
### 使用 XSLT 參數  
  
-   使用 <xref:System.Xml.Xsl.XslTransform> 類別的程式碼。  
  
     [!code-csharp[XML_Migration#13](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#13)]
     [!code-vb[XML_Migration#13](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#13)]  
  
-   使用 <xref:System.Xml.Xsl.XslCompiledTransform> 類別的程式碼。  
  
     [!code-csharp[XML_Migration#14](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#14)]
     [!code-vb[XML_Migration#14](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#14)]  
  
### 啟用 XSLT 指令碼  
  
-   使用 <xref:System.Xml.Xsl.XslTransform> 類別的程式碼。  
  
     [!code-csharp[XML_Migration#15](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#15)]
     [!code-vb[XML_Migration#15](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#15)]  
  
-   使用 <xref:System.Xml.Xsl.XslCompiledTransform> 類別的程式碼。  
  
     [!code-csharp[XML_Migration#16](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#16)]
     [!code-vb[XML_Migration#16](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#16)]  
  
### 將結果載入至 DOM 物件  
  
-   使用 <xref:System.Xml.Xsl.XslTransform> 類別的程式碼。  
  
     [!code-csharp[XML_Migration#19](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#19)]
     [!code-vb[XML_Migration#19](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#19)]  
  
-   使用 <xref:System.Xml.Xsl.XslCompiledTransform> 類別的程式碼。  
  
    > [!NOTE]
    >  <xref:System.Xml.Xsl.XslCompiledTransform> 類別不具有將 XSLT 轉換結果當做 <xref:System.Xml.XmlReader> 物件傳回的方法。  但是，您可以輸出至 XML 檔案，並將 XML 檔案載入到其他物件中。  
  
     [!code-csharp[XML_Migration#20](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#20)]
     [!code-vb[XML_Migration#20](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#20)]  
  
### 以資料流方式傳送結果至其他資料存放區  
  
-   使用 <xref:System.Xml.Xsl.XslTransform> 類別的程式碼。  
  
     [!code-csharp[XML_Migration#17](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#17)]
     [!code-vb[XML_Migration#17](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#17)]  
  
-   使用 <xref:System.Xml.Xsl.XslCompiledTransform> 類別的程式碼。  
  
     [!code-csharp[XML_Migration#18](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#18)]
     [!code-vb[XML_Migration#18](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#18)]  
  
## 請參閱  
 [從 XslTransform 類別移轉](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)   
 [使用 XslCompiledTransform 類別](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)