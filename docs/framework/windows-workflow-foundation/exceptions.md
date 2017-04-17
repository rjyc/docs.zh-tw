---
title: "例外狀況 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 065205cc-52dd-4f30-9578-b17d8d113136
caps.latest.revision: 26
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 26
---
# 例外狀況
工作流程可以利用 <xref:System.Activities.Statements.TryCatch> 活動處理在工作流程執行期間引發的例外狀況。工作流程可以處理這些例外狀況，也可以利用 <xref:System.Activities.Statements.Rethrow> 活動重新擲回。<xref:System.Activities.Statements.TryCatch.Finally%2A> 區段中的活動是在 <xref:System.Activities.Statements.TryCatch.Try%2A> 區段或 <xref:System.Activities.Statements.TryCatch.Catches%2A> 區段完成時執行的。<xref:System.Activities.WorkflowApplication> 執行個體所裝載的工作流程也可以利用 <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> 事件處理常式來處理未經 <xref:System.Activities.Statements.TryCatch> 活動處理的例外狀況。  
  
## 例外狀況的原因  
 在工作流程中，可以透過下列方式產生例外狀況：  
  
-   <xref:System.Activities.Statements.TransactionScope> 中的交易逾時。  
  
-   工作流程使用 <xref:System.Activities.Statements.Throw> 活動擲回明確的例外狀況。  
  
-   活動擲回 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 例外狀況。  
  
-   從外部程式碼 \(例如程式庫、元件或工作流程中使用的服務\) 擲回例外狀況。  
  
## 處理例外狀況  
 如果活動擲回例外狀況，且該例外狀況未經處理，預設的行為是終止該工作流程執行個體。如果自訂的 <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> 處理常式存在，即可覆寫這個預設行為。這個處理常式可讓工作流程主機作者提供適當的處理，例如自訂登入、中止工作流程、取消工作流程，或者終止工作流程。如果工作流程引發未處理的例外狀況，則會叫用 <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> 處理常式。<xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> 會傳回三種可能的動作，這些動作決定工作流程最終的結果。  
  
-   **Cancel** \-取消的工作流程執行個體是非失誤性結束分支執行。你可以建立取消行為模型 （例如使用 CancellationScope 活動）。取消流程完成時，將叫用 Completed 處理常式。取消的工作流程處於 Cancelled 狀態。  
  
-   **終止** \-無法恢復或重新啟動已終止的工作流程執行個體。 這個動作會觸發 Completed 事件，您可在其中提供例外狀況說明終止原因。終止流程完成時，將叫用 Terminated 處理常式。終止的工作流程處於 Faulted 狀態。  
  
-   **Abort** \-中止的工作流程設定為持續性後，才能繼續。沒有持續性就不能恢復工作流程。工作流程中止時，會失去上一個持續點以來 \(在記憶體中\) 完成的所有工作。若為中止的工作流程，會在中止程序完成時使用例外狀況叫用 Aborted 處理常式說明原因。不過，Completed 不同於 Cancelled 和 Terminated 之處在於它不會被叫用。中止的工作流程處於 Aborted 狀態。  
  
 下列範例會叫用擲回例外狀況的工作流程。此例外狀況未由工作流程處理，而且叫用了 <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> 處理常式。系統會檢查 <xref:System.Activities.WorkflowApplicationUnhandledExceptionEventArgs> 以提供例外狀況的相關資訊，並且終止工作流程。  
  
 [!code-csharp[CFX_WorkflowApplicationExample#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#1)]  
  
### 利用 TryCatch 活動處理例外狀況  
 工作流程內部的例外狀況是利用 <xref:System.Activities.Statements.TryCatch> 活動進行處理。<xref:System.Activities.Statements.TryCatch> 活動包含 <xref:System.Activities.Statements.Catch> 活動的 <xref:System.Activities.Statements.TryCatch.Catches%2A> 集合，其中每個活動各與一個特定的 <xref:System.Exception> 型別相關聯。如果活動包含在 <xref:System.Activities.Statements.TryCatch> 活動的 <xref:System.Activities.Statements.TryCatch.Try%2A> 區段中，當此活動擲回的例外狀況符合 <xref:System.Activities.Statements.TryCatch.Catches%2A> 集合中 <xref:System.Activities.Statements.Catch%601> 活動的例外狀況時，該例外狀況就會受到處理。如果例外狀況遭到明確重新擲回，或者擲回了新的例外狀況，則會將這個例外狀況向上傳遞父活動。下列程式碼範例示範 <xref:System.Activities.Statements.TryCatch> 活動，此活動會處理 <xref:System.Activities.Statements.Throw> 活動在 <xref:System.Activities.Statements.TryCatch.Try%2A> 區段中擲回的 <xref:System.ApplicationException>。<xref:System.Activities.Statements.Catch%601> 活動會將例外狀況的訊息寫入至主控台，然後將訊息寫入至主控台的 <xref:System.Activities.Statements.TryCatch.Finally%2A> 區段中。  
  
 [!code-csharp[CFX_WorkflowApplicationExample#33](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#33)]  
  
 <xref:System.Activities.Statements.TryCatch.Finally%2A> 區段中的活動會在 <xref:System.Activities.Statements.TryCatch.Try%2A> 區段或 <xref:System.Activities.Statements.TryCatch.Catches%2A> 區段順利完成時執行。如果 <xref:System.Activities.Statements.TryCatch.Try%2A> 區段未擲回任何例外狀況，就會順利完成，如果未擲回或重新擲回任何例外狀況，則 <xref:System.Activities.Statements.TryCatch.Catches%2A> 也會順利完成。如果 <xref:System.Activities.Statements.TryCatch> 的 <xref:System.Activities.Statements.TryCatch.Try%2A> 區段執回例外狀況，且未經 <xref:System.Activities.Statements.TryCatch.Catches%2A> 區段中的 <xref:System.Activities.Statements.Catch%601> 處理，或由 <xref:System.Activities.Statements.TryCatch.Catches%2A> 重新擲回，則不會執行 <xref:System.Activities.Statements.TryCatch.Finally%2A> 中的活動，除非發生下列其中任一情況。  
  
-   工作流程中層級較高的 <xref:System.Activities.Statements.TryCatch> 擷取該例外狀況，而不論該例外狀況是否由該層級較高的 <xref:System.Activities.Statements.TryCatch> 重新擲回。  
  
-   該例外狀況未經層級較高的 <xref:System.Activities.Statements.TryCatch> 處理、溢出工作流程的根目錄，且該工作流程設定為取消而非終止或中止。 。使用 <xref:System.Activities.WorkflowApplication> 裝載的工作流程可以透過處理　<xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> 及傳回 <xref:System.Activities.UnhandledExceptionAction> 進行此設定。本主題前文亦提供處理 <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> 的範例。工作流服務可以使用 <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> 並指定 <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction> 來進行此設定。如需設定 <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> 的範例，請參閱 [工作流程服務主機擴充性](../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)。  
  
## 例外狀況處理與補償  
 例外狀況處理與補償之間的不同在於，例外狀況處理會發生於活動執行期間。補償則是發生於活動順利完成後。例外狀況處理可讓您在活動引發例外狀況後進行清理，而補償則提供一種機制，利用這種機制即可復原先前完成之活動順利完成的工作。[!INCLUDE[crdefault](../../../includes/crdefault-md.md)][補償](../../../docs/framework/windows-workflow-foundation//compensation.md).  
  
## 請參閱  
 <xref:System.Activities.Statements.TryCatch>   
 <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>   
 <xref:System.Activities.Statements.CompensableActivity>