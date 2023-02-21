---
# required metadata

title: Expired subscriptions and data deletion
description: This article provides information about data deletion that occurs after a Dynamics 365 finance and operations subscription expires. It also explains how to clean up cloud-hosted environments deployed to an Azure subscription after a project is deleted.
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

This article will cover a brief overview of Microsoft Dynamics 365 finance and operations licenses (also referred to as subscriptions). It describes how they relate to Projects in Microsoft Dynamics 365 Lifecycle Services, and what happens when your license subscriptions expire.

## Dynamics 365 license subscriptions
Dynamics 365 applications are licensed by subscription in two broad categories outlined below.

**Assigned licenses**, which include:
- User licenses, which grant access for a named user, regardless of the device used. For products that offer licenses for both enterprise and professional levels of functionality (such as  Microsoft Dynamics 365 Finance or Microsoft Dynamics 365 Customer Service), user licenses may be referred to as Enterprise or Base licenses, and Attach licenses.
- Device licenses, which grant access via certain devices, using either assigned or shared logins.

**Unassigned licenses** that provide access to a feature or service at the tenant level, regardless of the user or device involved.
- Options include additional capacity for storage or files, add-on Sandboxes based on tiers for performance or other user acceptance testing needs.

An organization may have both assigned and unassigned licenses. Licenses grant users non-perpetual rights (with no buy-out rights) to the use of one or more specific Dynamics 365 products in the cloud (not on-premises). If your subscription payments are up to date and you adhere to the Product Terms, you'll have access to the current licensed Dynamics 365 product.

Admins don't need any license to configure and administer Dynamics 365 applications.

### Base licenses vs attach licenses
Microsoft provides a cost-effective way for a single Dynamics 365 user to obtain full user licensing for multiple Dynamics 365 products. Licenses for products that provide core business functionality qualify as base licenses. Examples are Finance, Microsoft Dynamics 365 Supply Chain Management, Microsoft Dynamics 365 Commerce, Microsoft Dynamics 365 Project Operations, or Microsoft Dynamics 365 Human Resources. Each has one or more additional applications that are frequently used by people in the same roles and that qualify as attach licenses for that user. (These are sometimes referred to as subsequent qualifying applications.) To learn more about attach licenses and ways to save, see [Dynamics 365 Licensing Guide](https://aka.ms/dynamicslicensingguide).

### Licenses required to create an Implementation Project
Administrators use an Implementation Project to do most of their work in Lifecycle Services. Inside these types of projects, the admin may deploy a Sandbox and a Production environment, as well as deploy additional add-on sandboxes (a type of unassigned license) that they've purchased. A minimum of 20 base licenses for Finance, Supply Chain Management, Commerce, Project Operations, or Human Resources are required to create an Implementation Project.

If you require multiple projects, you can create more following this documentation. The number of projects you can create is a factor of 20, so if you require two projects then you would need 40 licenses as an example.

## What happens when my license subscriptions expire
Customers adjust the number of licenses they've on a regular basis. As mentioned previously, a minimum of 20 base licenses is required to create a project. If the number of paid base licenses falls below 20 then a number of automated actions will be performed.

### Banners and notifications
First, banners will be shown across various pages in your Lifecycle Services project. These will indicate that you're operating in a project that Microsoft has detected falls below the minimum number of license subscriptions required to use it.

Second, email communications and/or message center posts will be sent to your tenant administrators indicating that we've detected a project that doesn't have sufficient paid license subscriptions.

### Sandboxes will be disabled
The next course of action is to disable Sandbox environments. These environments are used for testing, training, and debugging purposes and as such will be targeted first for deallocation. This helps protect against non-compliance, however, doesn't impact customer Production environments which are hosting mission critical workloads.

### Production will be disabled
After 3 days of disabling Sandboxes, the Production environment will be disabled. This will begin a downtime for mission critical workloads for the customer, due to an inactive or insufficient number of paid license subscriptions to operate the applications.

### Project deletion
After 15 days of disabling Production, the project will be deleted. This will remove all users, project data such as uploaded software assets, Azure connectors for deployment of cloud-hosted developer environments, and all of the Sandbox and Production environments associated.

## I have begun renewing my licenses, but that is a longer process due to Enterprise Agreements
If you can show proof of intent to renew your licenses, Microsoft can prevent the automated actions listed above from taking place and will re-enable the environments. To share that you've started the renewal process with your license vendor, please create a support ticket to Microsoft Support with those details.

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
