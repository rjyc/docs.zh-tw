---
title: "泛型和反映 (C# 程式設計手冊) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- generics [C#], reflection
- reflection [C#], generic types
ms.assetid: 162fd9b4-dd5b-4abb-8c9b-e44e21e2f451
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: cea1f48f336e4c73fa317d1cbbab3d06ceb6045f
ms.lasthandoff: 03/13/2017

---
# <a name="generics-and-reflection-c-programming-guide"></a>泛型和反映 (C# 程式設計手冊)
由於 Common Language Runtime (CLR) 可在執行階段存取泛型型別資訊，因此您可以使用反映取得泛型型別的相關資訊，方法和取得非泛型型別的資訊相同。 如需詳細資訊，請參閱[執行階段中的泛型](../../../csharp/programming-guide/generics/generics-in-the-run-time.md)。  
  
 在 [!INCLUDE[dnprdnlong](../../../csharp/programming-guide/events/includes/dnprdnlong_md.md)] 中，<xref:System.Type> 類別新增了幾個成員，以允許泛型型別的執行階段資訊。 如需使用這些方法和屬性的詳細資訊，請參閱這些類別的文件。 <xref:System.Reflection.Emit> 命名空間也包含支援泛型的新成員。 請參閱[如何：使用反映發出定義泛型型別](http://msdn.microsoft.com/library/07d5f01a-7b5b-40ea-9b15-f21561098fe4)。  
  
 如需泛型反映中所使用之規範的恆成立條件清單，請參閱 <xref:System.Type.IsGenericType%2A> 屬性的備註。  
  
|System.Type 成員名稱|描述|  
|-----------------------------|-----------------|  
|<xref:System.Type.IsGenericType%2A>|如果類型是泛型，則傳回 true。|  
|<xref:System.Type.GetGenericArguments%2A>|傳回 `Type` 物件的陣列，代表提供給建構類型的型別引數，或泛型型別定義的型別參數。|  
|<xref:System.Type.GetGenericTypeDefinition%2A>|傳回目前建構類型的基礎泛型型別定義。|  
|<xref:System.Type.GetGenericParameterConstraints%2A>|傳回由 `Type` 物件組成的陣列，這些物件代表對目前泛型類型參數所設下的條件約束。|  
|<xref:System.Type.ContainsGenericParameters%2A>|如果類型或是其封入之任何類型或方法中，包含尚未提供其特定類型的型別參數，則傳回 true。|  
|<xref:System.Type.GenericParameterAttributes%2A>|取得一組 `GenericParameterAttributes` 旗標，描述目前泛型型別參數的特殊條件約束。|  
|<xref:System.Type.GenericParameterPosition%2A>|針對代表型別參數的 `Type` 物件，取得宣告型別參數之泛型型別定義或泛型方法定義中，型別參數清單內的型別參數位置。|  
|<xref:System.Type.IsGenericParameter%2A>|取得值，指出目前的 `Type` 是否表示泛型型別或方法定義的型別參數。|  
|<xref:System.Type.IsGenericTypeDefinition%2A>|取得值，指出目前的 <xref:System.Type> 是否表示可從中建構其他泛型型別的泛型型別定義。 如果類型表示泛型型別的定義，則傳回 true。|  
|<xref:System.Type.DeclaringMethod%2A>|傳回定義目前泛型型別參數的泛型方法；如果泛型方法未定義型別參數，則為 Null。|  
|<xref:System.Type.MakeGenericType%2A>|用類型陣列的元素取代目前泛型型別定義的型別參數，並傳回代表所產生之建構類型的 <xref:System.Type> 物件。|  
  
 此外，<xref:System.Reflection.MethodInfo> 類別新增了成員，以允許泛型方法的執行階段資訊。 如需反映在泛型方法所使用之規範的恆成立條件清單，請參閱 <xref:System.Reflection.MethodInfo.IsGenericMethod%2A> 屬性的備註。  
  
|System.Reflection.MemberInfo 成員名稱|說明|  
|----------------------------------------------|-----------------|  
|<xref:System.Reflection.MethodInfo.IsGenericMethod%2A>|如果方法是泛型，則傳回 true。|  
|<xref:System.Reflection.MethodInfo.GetGenericArguments%2A>|傳回 Type 物件的陣列，這些物件代表所建構泛型方法的型別引數，或泛型方法定義的型別參數。|  
|<xref:System.Reflection.MethodInfo.GetGenericMethodDefinition%2A>|傳回目前建構方法的基礎泛型方法定義。|  
|<xref:System.Reflection.MethodInfo.ContainsGenericParameters%2A>|如果方法或是其封入之任何類型中，包含尚未提供其特定類型的任何型別參數，則傳回 true。|  
|<xref:System.Reflection.MethodInfo.IsGenericMethodDefinition%2A>|如果目前的 <xref:System.Reflection.MethodInfo> 表示泛型方法的定義，則傳回 true。|  
|<xref:System.Reflection.MethodInfo.MakeGenericMethod%2A>|使用類型陣列的元素取代目前泛型方法定義的型別參數，並傳回代表所產生之建構方法的 <xref:System.Reflection.MethodInfo> 物件。|  
  
## <a name="see-also"></a>另請參閱  
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [泛型](../../../csharp/programming-guide/generics/index.md)   
 [反映和泛型型別](http://msdn.microsoft.com/library/f7180fc5-dd41-42d4-8a8e-1b34288e06de)   
 [泛型](https://msdn.microsoft.com/library/ms172192)
