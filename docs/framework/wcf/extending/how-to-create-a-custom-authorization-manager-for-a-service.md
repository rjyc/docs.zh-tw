---
title: "HOW TO：為服務建立自訂授權管理員 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "OperationRequirement 類別"
  - "Windows Communication Foundation, 擴充"
ms.assetid: 6214afde-44c1-4bf5-ba07-5ad6493620ea
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 15
---
# HOW TO：為服務建立自訂授權管理員
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 中的「身分識別模型」基礎結構支援可延伸的宣告授權模型。從語彙基元擷取的宣告可以選擇性地由自訂授權原則進行處理並放入 <xref:System.IdentityModel.Policy.AuthorizationContext>。授權管理員會檢查 <xref:System.IdentityModel.Policy.AuthorizationContext> 中的宣告來做出授權決策。  
  
 根據預設，<xref:System.ServiceModel.ServiceAuthorizationManager> 類別會做出授權決策，不過，您也可以建立自訂的授權管理員來覆寫這些決策。若要建立自訂的授權管理員，請建立衍生自 <xref:System.ServiceModel.ServiceAuthorizationManager> 的類別，然後實作 <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> 方法。授權決策會在 <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> 方法中進行，並在授與存取權時傳回 `true`，在拒絕存取權時傳回 `false`。  
  
 如果授權決策取決於訊息本文的內容，則使用 <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> 方法。  
  
 基於效能考量，如果可以，您應該重新設計應用程式，讓授權決策不需要存取訊息本文。  
  
 您也可以透過程式碼或組態，為服務註冊自訂授權管理員。  
  
### 若要建立自訂授權管理員  
  
1.  從 <xref:System.ServiceModel.ServiceAuthorizationManager> 類別衍生類別。  
  
     [!code-csharp[c_CustomAuthMgr#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#5)]
     [!code-vb[c_CustomAuthMgr#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#5)]  
  
2.  覆寫 <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> 方法。  
  
     使用傳遞至 <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> 方法的 <xref:System.ServiceModel.OperationContext> 來做出授權決策。  
  
     下列程式碼範例使用 <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%28System.String%2CSystem.String%29> 方法來找出自訂宣告 `http://www.contoso.com/claims/allowedoperation`，以便做出授權決策。  
  
     [!code-csharp[c_CustomAuthMgr#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#6)]
     [!code-vb[c_CustomAuthMgr#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#6)]  
  
### 若要使用程式碼來註冊自訂授權管理員  
  
1.  建立自訂授權管理員的執行個體，然後將它指派給 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ServiceAuthorizationManager%2A> 屬性。  
  
     <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> 可以透過使用 <xref:System.ServiceModel.ServiceHostBase.Authorization%2A> 屬性來存取。  
  
     下列程式碼範例會註冊 `MyServiceAuthorizationManager` 自訂授權管理員。  
  
     [!code-csharp[c_CustomAuthMgr#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#4)]
     [!code-vb[c_CustomAuthMgr#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#4)]  
  
### 若要使用組態來註冊自訂授權管理員  
  
1.  開啟服務的組態檔。  
  
2.  將 [\<serviceAuthorization\>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) 新增至 [\<行為\>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)。  
  
     針對 [\<serviceAuthorization\>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) 新增 `serviceAuthorizationManagerType` 屬性，並將它的值設定為代表自訂授權管理員的型別。  
  
3.  新增繫結，以便保護用戶端與服務之間的通訊安全。  
  
     選定用在此通訊上的繫結會決定新增至 <xref:System.IdentityModel.Policy.AuthorizationContext> 的宣告，而自訂授權管理員會使用此宣告來做出授權決策。如需系統提供之繫結的詳細資訊，請參閱[系統提供的繫結](../../../../docs/framework/wcf/system-provided-bindings.md)。  
  
4.  藉由新增 [\<服務\>](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) 項目，建立行為與服務端點的關聯，然後將 `behaviorConfiguration` 屬性的值設定為 [\<行為\>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) 項目的名稱屬性值。  
  
     如需設定服務端點的詳細資訊，請參閱 [HOW TO：在組態中建立服務端點](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)。  
  
     下列程式碼範例會註冊自訂授權管理員 `Samples.MyServiceAuthorizationManager`。  
  
    ```  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service   
              name="Microsoft.ServiceModel.Samples.CalculatorService"  
              behaviorConfiguration="CalculatorServiceBehavior">  
            <host>  
              <baseAddresses>  
                <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
              </baseAddresses>  
            </host>  
            <endpoint address=""  
                      binding="wsHttpBinding_Calculator"  
                      contract="Microsoft.ServiceModel.Samples.ICalculator" />  
          </service>  
        </services>  
        <bindings>  
          <WSHttpBinding>  
           <binding name = "wsHttpBinding_Calculator">  
             <security mode="Message">  
               <message clientCredentialType="Windows"/>  
             </security>  
            </binding>  
          </WSHttpBinding>  
    </bindings>  
        <behaviors>  
          <serviceBehaviors>  
            <behavior name="CalculatorServiceBehavior">  
              <serviceAuthorization serviceAuthorizationManagerType="Samples.MyServiceAuthorizationManager,MyAssembly" />  
             </behavior>  
         </serviceBehaviors>  
       </behaviors>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
    > [!WARNING]
    >  請注意，當您指定 serviceAuthorizationManagerType 時，字串必須包含完整限定的型別名稱。逗號和定義該型別之組件的名稱。如果您省略組件名稱，WCF 會嘗試從 System.ServiceModel.dll 載入型別。  
  
## 範例  
 下列程式碼範例示範包含覆寫 <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> 方法的基本 <xref:System.ServiceModel.ServiceAuthorizationManager> 類別實作。此範例程式碼會檢查自訂宣告的 <xref:System.IdentityModel.Policy.AuthorizationContext>，並在該自訂宣告符合來自 <xref:System.ServiceModel.OperationContext> 的動作值時傳回 `true`。如需更完整的 <xref:System.ServiceModel.ServiceAuthorizationManager> 類別實作，請參閱[授權原則](../../../../docs/framework/wcf/samples/authorization-policy.md)。  
  
 [!code-csharp[c_CustomAuthMgr#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#2)]
 [!code-vb[c_CustomAuthMgr#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#2)]  
  
## 請參閱  
 <xref:System.ServiceModel.ServiceAuthorizationManager>   
 [授權原則](../../../../docs/framework/wcf/samples/authorization-policy.md)   
 [授權原則](../../../../docs/framework/wcf/samples/authorization-policy.md)