---
# required metadata

title: Expired subscription and data deletion
description: This template contains examples of Markdown syntax, as well as guidance on setting the metadata.
author: AngelMarshall
ms.date: 08/16/2021
ms.topic: article
audience: IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: tsmarsha
ms.search.validFrom: 2021-08-16
---

# Expired subscription and data deletion

[!include[banner](../includes/banner.md)]

**NEED: Introductory paragraph**

## Expired subscription and data deletion

After your subscription expires beyond the 90 days retention period, Microsoft will disable the accounts and delete customer data. Your LCS implementation project will be deleted and any Microsoft-managed environments will be deprovisioned and deleted. 

## Clean up Azure subscription 

If you have deployed cloud-hosted environments in your LCS implementation project via a customer-owned Azure subscription, after the project is deleted, LCS will no longer have access to your Azure subscription or any of the cloud-hosted environments. However, certain resources may remain in your Azure subscription. 

You will need to take the following steps to free up the resources and remove application permissions in your AAD (Azure Active Directory) tenant and each of the Azure subscriptions previously added to LCS to deploy the cloud-hosted environments. 

1. Delete the Azure resources: 
   1. Go to Azure subscription in Portal. 
   1. When a cloud-hosted environment is created, it creates a resource group in your Azure subscription. This resource group represents the resources created as part of your cloud-hosted environment deployment, and will carry the same name as that of the deployment. This should be easy to identify in the resource group name list.  
   1. Delete any resource groups with the prefix of **DynamicsDeployments-*** .
        > [!Note] 
        > If you have deployed cloud-hosted environments to more than one Azure region, there may be multiple resource groups created, make sure to delete all related resource groups. 
1. Remove app from the subscription:  
   1. Login to via AuzreAD PowerShell cmdlet.     
      1. **Connect-AzureAD** (Using Tenant Administrator account)  
   1. Check if Dynamics Deployment Service application is still enabled on the AAD tenant.    
       1. **Get-AzureADServicePrincipal -Filter "AppId eq 'b96b7e94-b82e-4e71-99a0-cf7fb188acea'"**  
   1. If the above command returns an object, then the app is currently enabled on this tenant, and it may still have access to the subscription. Remove this application from this tenant:  
      1. **$DDSObjectId=$(Get-AzureADServicePrincipal -Filter "AppId eq 'b96b7e94-b82e-4e71-99a0-cf7fb188acea'").ObjectId    
      1. **Remove-AzureADServicePrincipal -ObjectId $DDSObjectId**  
    1. Verify the application has been removed successfully: 
       1. Get-AzureADServicePrincipal -Filter "AppId eq ' b96b7e94-b82e-4e71-99a0-cf7fb188acea'" 

## Related topics
[Data retention, deletion, and destruction in Microsoft 365](/compliance/assurance/assurance-data-retention-deletion-and-destruction-overview?view=o365-worldwide)

[Subscriptions, LCS projects, and Azure Active Directory tenants FAQ](../../fin-ops/get-started/subscription-overview.md)
