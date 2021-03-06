---
title: "永久性延遲 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 220ec240-b958-430c-81ff-b734a6aa97ae
caps.latest.revision: 11
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 11
---
# 永久性延遲
這個範例示範如何使用永久性延遲，此延遲會在延遲期間將工作流程保存至永久性裝置。範例工作流程包含兩個主控台訊息，兩者之間會以延遲區隔。當延遲觸發時，工作流程便會卸載，並且在工作流程執行個體存放區中等待 5 秒鐘，再重新載入記憶體中。  
  
## 工作流程詳細資料  
 工作流程服務主機會透過載入和卸載的方式裝載工作流程，並且管理工作流程執行個體。為了啟動工作流程定義的執行個體，範例會設定一個 Proxy，以便將訊息傳送至工作流程中的 <xref:System.ServiceModel.Activities.Receive> 活動。<xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> 屬性會設為 `true`，以便在收到訊息時，建立新的工作流程執行個體。  
  
 下列清單詳細描述工作流程服務主機在初始化期間的設定內容。  
  
1.  建立具有位址的服務主機 \(http:\/\/localhost:8080\/Client\)。  
  
2.  在服務主機中建立端點，以便在工作流程內與 <xref:System.ServiceModel.Activities.Receive> 活動進行通訊。  
  
3.  設定 SQL 執行個體存放區。  
  
4.  加入卸載執行個體的行為，該行為會指定工作流程服務主機應將工作流程執行個體卸載至 SQL 持續性存放區的情況。在這個範例中，它會在工作流程閒置後 \(觸發延遲時\) 立即卸載執行個體。  
  
5.  建立 Proxy，將訊息傳送至工作流程中的 <xref:System.ServiceModel.Activities.Receive> 活動。  
  
#### 若要使用這個範例  
  
1.  設定持續性資料庫。  
  
    1.  開啟 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 命令提示字元。  
  
    2.  巡覽至 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 目錄 \(C:\\Windows\\Microsoft.NET\\Framework\\v4.X\\\)。  
  
    3.  編輯 WorkflowManagementService.exe.config 檔案，並將下列連接字串加入至 \<`database`\> 項目內。  
  
        ```  
        <database connectionString="Data Source=localhost\SQLEXPRESS;Initial Catalog=DefaultSampleStore;Integrated Security=True;Asynchronous Processing=True" />  
  
        ```  
  
    4.  巡覽至 DurableDelay\\CS 目錄。  
  
    5.  執行 Setup.cmd。  
  
2.  以滑鼠右鍵按一下 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 圖示並選取 \[**以系統管理員身分執行**\]，藉此使用更高的權限執行 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]。  
  
3.  開啟 \[Delay.sln\] 方案檔案。  
  
4.  按下 CTRL\+SHIFT\+B 建置方案。  
  
5.  按 CTRL\+F5 執行方案。  
  
#### 若要解除安裝這個範例  
  
1.  開啟 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 命令提示字元。  
  
2.  巡覽至 DurableDelay\\CS 目錄。  
  
3.  執行 Cleanup.cmd。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDelay`  
  
## 請參閱