---
title: "服務：安全性驗證和驗證失敗數 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 55c98268-b1ad-459d-851b-25ef52248187
caps.latest.revision: 7
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 7
---
# 服務：安全性驗證和驗證失敗數
計數器名稱：安全性驗證和驗證失敗數  
  
## 描述  
 每當因為「未授權的安全性呼叫數」計數器所未涵蓋的安全性問題而拒絕訊息時，這個計數器就會遞增。這類問題包括：  
  
-   無法從訊息中讀取用戶端權杖。  
  
-   用戶端權杖已經驗證失敗 \(例如密碼錯誤\)。  
  
-   簽章驗證已經失敗 \(例如訊息遭到竄改\)。  
  
-   此訊息與之前的訊息重複，這可能會在重新執行攻擊時發生。  
  
-   發生解密失敗。  
  
-   訊息中遺漏某些必要的項目 \(例如遺漏時間戳記或加密的資料區塊\)。  
  
-   在 TLSNEGO\/SPNEGO 交換期間發生錯誤。