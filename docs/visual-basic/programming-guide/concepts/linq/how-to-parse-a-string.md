---
title: "如何︰ 剖析字串 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 896e1b4b-f9bd-4975-8bc1-55b6badce1ac
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: d062efd2e207f5db39e3be044450fd3f9a5d9e11
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-parse-a-string-visual-basic"></a>如何︰ 剖析字串 (Visual Basic)
本主題說明如何在 C# 中建立 XML 樹狀結構。  
  
## <a name="example"></a>範例  
 您可以在字串中的剖析[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]使用`XElement.Parse`方法。 不過，它是使用 XML 常值，如下列程式碼所示，因為 XML 常值不會遭受相同的效能低落，從字串剖析 XML 更有效率。  
  
 藉由使用 XML 常值，您只可以將您的 XML 複製並貼入您的 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 程式中。  
  
> [!NOTE]
>  從文字檔剖析文字或載入 XML 文件比功能結構沒有效率。 如果您要從程式碼初始化 XML 樹狀結構，使用功能結構比剖析文字所花的處理器時間少。  
  
```vb  
Dim contacts as XElement = _  
    <Contacts>  
        <Contact>  
            <Name>Patrick Hines</Name>  
            <Phone Type="home">206-555-0144</Phone>  
            <Phone Type="work">425-555-0145</Phone>  
            <Address>  
            <Street1>123 Main St</Street1>  
            <City>Mercer Island</City>  
            <State>WA</State>  
            <Postal>68042</Postal>  
            </Address>  
            <NetWorth>10</NetWorth>  
        </Contact>  
        <Contact>  
            <Name>Gretchen Rivas</Name>  
            <Phone Type="mobile">206-555-0163</Phone>  
            <Address>  
            <Street1>123 Main St</Street1>  
            <City>Mercer Island</City>  
            <State>WA</State>  
            <Postal>68042</Postal>  
            </Address>  
            <NetWorth>11</NetWorth>  
        </Contact>  
    </Contacts>  
```  
  
## <a name="see-also"></a>另請參閱  
 [剖析 XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
