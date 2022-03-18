---
# required metadata

title: Expired subscriptions and data deletion
description: This topic provides information about data deletion that occurs after an Azure subscription expires. It also explains how to clean up an expired Azure subscription.
author: AngelMarshall
ms.date: 08/16/2021
ms.topic: article
audience: IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: tsmarsha
ms.search.validFrom: 2021-08-16
---

# Expired subscriptions and data deletion

[!include[banner](../includes/banner.md)]

After your subscription has been expired for longer than the 90-day retention period, Microsoft disables the accounts and deletes customer data. Your implementation project in Microsoft Dynamics Lifecycle Services (LCS) is deleted, and any Microsoft-managed environments are deprovisioned and deleted.

## Clean up your Azure subscription

After your LCS implementation project is deleted, if you deployed cloud-hosted environments in it via a customer-owned Azure subscription, LCS will no longer have access to the Azure subscription or any of the cloud-hosted environments. However, some resources might remain in your Azure subscription.

Follow these steps to free up the resources, and to remove application permissions in your Azure Active Directory (Azure AD) tenant and each Azure subscription that you previously added to LCS so that you could deploy the cloud-hosted environments.

1. Delete the Azure resources:

    1. In the [Azure portal](https://portal.azure.com), go to your Azure subscription.
    1. When a cloud-hosted environment is created, it creates a resource group in your Azure subscription. This resource group represents the resources that are created as part of your deployment of the cloud-hosted environment. It has the same name as the deployment. Therefore, it should be easy to find in the list of resource groups. Delete any resource groups that have the prefix **DynamicsDeployments-**.

    > [!IMPORTANT]
    > If you deployed cloud-hosted environments to more than one Azure region, multiple resource groups might have been created. Be sure to delete all related resource groups.

1. Remove the deployment service application from the subscription:

    1. Sign in to Azure AD via the PowerShell cmdlet.

        ```powershell
        Connect-AzureAD (Using Tenant Administrator account)
        ```

    1. Determine whether the app is still enabled on the Azure AD tenant.

        ```powershell
        Get-AzureADServicePrincipal -Filter "AppId eq 'b96b7e94-b82e-4e71-99a0-cf7fb188acea'"
        ```

    1. If the preceding command returns an object, the app is currently enabled on the tenant, and it might still have access to the subscription. Remove the app from the tenant.

        ```powershell
        $DDSObjectId=$(Get-AzureADServicePrincipal -Filter "AppId eq 'b96b7e94-b82e-4e71-99a0-cf7fb188acea'").ObjectId
        ```

        ```powershell
        Remove-AzureADServicePrincipal -ObjectId $DDSObjectId
        ```

    1. Verify that the app has been removed.

        ```powershell
        Get-AzureADServicePrincipal -Filter "AppId eq ' b96b7e94-b82e-4e71-99a0-cf7fb188acea'"
        ```

## Related topics

[Data retention, deletion, and destruction in Microsoft 365](/compliance/assurance/assurance-data-retention-deletion-and-destruction-overview)

[Subscriptions, LCS projects, and Azure Active Directory tenants FAQ](../../fin-ops/get-started/subscription-overview.md)
