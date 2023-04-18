---
# required metadata

title: Expired subscriptions and data deletion
description: This article provides information about data deletion that occurs after a finance and operations apps subscription expires. It also explains how to clean up cloud-hosted environments deployed to an Azure subscription after a project is deleted.
author: LaneSwenka
ms.date: 02/17/2023
ms.topic: article
audience: IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: laswenka
ms.search.validFrom: 2021-08-16
---

# Expired subscriptions and data deletion

[!include[banner](../includes/banner.md)]

This article provides a brief overview of licenses for finance and operations apps. These licenses are also referred to as subscriptions. The article describes how subscriptions are related to projects in Microsoft Dynamics Lifecycle Services, and what happens when your license subscriptions expire.

## Dynamics 365 license subscriptions

Dynamics 365 applications are licensed by subscription in two broad categories:

- **Assigned licenses** – There are two types:

    - **User licenses** – These licenses grant access for a named user, regardless of the device that's used. For products that offer licenses for both enterprise and professional levels of functionality (for example, Dynamics 365 Finance and Dynamics 365 Customer Service), user licenses might be referred to as enterprise or base licenses, and attach licenses.
    - **Device licenses** – These licenses grant access via specific devices, through either assigned or shared sign-ins.

- **Unassigned licenses** – These licenses provide access to a feature or service at the tenant level, regardless of the user or device that's involved. Options include additional capacity for storage or files, or add-on sandboxes, based on tiers for performance requirements or other user acceptance testing (UAT) requirements.

An organization can have both assigned and unassigned licenses. Licenses grant users non-perpetual rights (with no buy-out rights) to the use of one or more specific Dynamics 365 products in the cloud (not on-premises). If your subscription payments are up to date, and you adhere to the product terms, you'll have access to the current licensed Dynamics 365 product.

Admins don't require any license to configure and administer Dynamics 365 applications.

### Base licenses vs. attach licenses

Microsoft provides a cost-effective way for a single Dynamics 365 user to obtain full user licensing for multiple Dynamics 365 products. Licenses for products that provide core business functionality qualify as base licenses. Examples are Finance, Dynamics 365 Supply Chain Management, Dynamics 365 Commerce, Dynamics 365 Project Operations, and Dynamics 365 Human Resources. Each has one or more additional applications that are frequently used by people in the same roles and that qualify as attach licenses for that user. (These applications are sometimes referred to as subsequent qualifying applications.) For more information about attach licenses and how to save them, see [Dynamics 365 Licensing Guide](https://aka.ms/dynamicslicensingguide).

### Licenses required to create an implementation project

Admins use an implementation project to do most of their work in Lifecycle Services. Inside these types of projects, an admin can deploy a sandbox environment and a production environment, and can also deploy additional add-on sandboxes (a type of unassigned license) they've purchased. A minimum of 20 base licenses for Finance, Supply Chain Management, Commerce, Project Operations, or Human Resources is required to create an implementation project.

If you require multiple projects, you can create more by using the information in this documentation. The number of projects that you can create is a factor of 20. Therefore, if you require two projects, for example, you need 40 licenses.

## What happens when my license subscriptions expire?

Customers adjust the number of licenses that they have on a regular basis. As was mentioned previously, a minimum of 20 base licenses is required to create a project. If the number of paid base licenses falls below 20, several automated actions are performed for implementation projects, as described in this section.  

### Banners are shown and notifications are sent

First, banners will be shown on difference pages in your Lifecycle Services project. These banners indicate that you're working in a project that Microsoft has detected falls below the minimum number of license subscriptions required to use it.

Second, email communications and/or message center posts will be sent to your tenant admins. These notifications indicate that Microsoft has detected a project that doesn't have enough paid license subscriptions.

### Sandboxes are disabled

The next action is to disable sandbox environments.  This will be performed 4 business days after communications are sent from the previous step. Because these environments are used for testing, training, and debugging purposes, they'll be targeted first for deallocation. This approach helps protect against non-compliance but doesn't affect customer production environments that host mission-critical workloads.

Disabled environments aren't yet deleted.  These can be recovered if your licenses are renewed or if you provide proof of intent following the steps outlined in section *Manual renewal process* below.

### Production is disabled

Three business days after sandboxes are disabled, the production environment will be disabled. This action will begin a downtime for mission-critical workloads for the customer, because there will be an inactive or insufficient number of paid license subscriptions to operate the applications.

Disabled environments aren't yet deleted.  These can be recovered if your licenses are renewed or if you provide proof of intent following the steps outlined in section *Manual renewal process* below.

### Sandboxes are deleted

Three business days after Production is disabled, the sandbox environments will be deleted.  This is a non-recoverable action.  

### The project and Production environment are deleted

Two business days after the sandboxes are deleted, the project will be deleted along with the Production environment. This is a non-recoverable action.  This action will remove all users, project data such as uploaded software assets, Azure connectors for deployment of cloud-hosted developer environments, and all associated sandbox and production environments.

## Manual renewal process for long purchasing processes

Sometimes purchasing licenses or renewing them can be a lengthy process for some customer organizations.  If you can show proof of your intent to renew your licenses, Microsoft can prevent the automated actions that were described earlier from occurring and will re-enable the environments. To communicate that you've started the renewal process with your license vendor, create a support ticket that includes those details, and submit it to Microsoft Support.

## Clean up your Azure subscription

After your implementation project is deleted, if you deployed cloud-hosted environments in it via a customer-owned Azure subscription, Lifecycle Services will no longer have access to the Azure subscription or any of the cloud-hosted environments. However, some resources might remain in your Azure subscription.

Follow these steps to free up the resources, and to remove application permissions in your Azure Active Directory (Azure AD) tenant and each Azure subscription that you previously added to Lifecycle Services so that you could deploy the cloud-hosted environments.

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
