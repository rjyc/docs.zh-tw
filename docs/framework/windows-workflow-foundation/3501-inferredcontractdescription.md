---
title: "3501 - InferredContractDescription | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 21a70849-4fc0-41d2-b9a4-db5aa2acdf1a
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 3501 - InferredContractDescription
## 屬性  
  
|||  
|-|-|  
|ID|3501|  
|關鍵字|WFServices|  
|層級|資訊|  
|通道|Microsoft\-Windows\-Application Server\-Applications\/Analytic|  
  
## 描述  
 表示已從 WorkflowService 推斷出 ContractDescription。  
  
## 訊息  
 已從 WorkflowService 推斷出 Name\='%1' 且 Namespace\='%2' 的 ContractDescription。  
  
## 詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|------------|------------|--------|  
|名稱|xs:string|ContractDescription 的名稱。|  
|命名空間|xs:string|ContractDescription 的命名空間。|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|