---
title: Expired subscriptions and data deletion
description: Learn about data deletion that occurs after a finance and operations apps subscription expires, including cleaning up environments deployed to Azure subscriptions.
author: LaneSwenka
ms.author: laswenka
ms.topic: article
ms.date: 03/06/2026
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2021-08-16
---

# Expired subscriptions and data deletion

[!include[banner](../includes/banner.md)]
[!include [LCS freeze](../../../includes/lcs-freeze-banner.md)]

This article provides a brief overview of licenses for finance and operations apps. These licenses are also referred to as subscriptions. The article describes how subscriptions relate to projects in Microsoft Dynamics Lifecycle Services, and what happens when your license subscriptions expire.

## Dynamics 365 license subscriptions

Subscribe to Dynamics 365 applications in two broad categories:

- **Assigned licenses** – There are two types:

    - **User licenses** – These licenses grant access for a named user, regardless of the device that's used. For products that offer licenses for both enterprise and professional levels of functionality (for example, Dynamics 365 Finance and Dynamics 365 Customer Service), user licenses might be referred to as enterprise or base licenses, and attach licenses.
    - **Device licenses** – These licenses grant access through specific devices, by using either assigned or shared sign-ins.

- **Unassigned licenses** – These licenses provide access to a feature or service at the tenant level, regardless of the user or device that's involved. Options include additional capacity for storage or files, or add-on sandboxes, based on tiers for performance requirements or other user acceptance testing (UAT) requirements.

An organization can have both assigned and unassigned licenses. Licenses grant users non-perpetual rights (with no buy-out rights) to use one or more specific Dynamics 365 products in the cloud (not on-premises). If your subscription payments are up to date, and you adhere to the product terms, you have access to the current licensed Dynamics 365 product.

Admins don't require any license to configure and administer Dynamics 365 applications.

### Base licenses vs. attach licenses

Microsoft provides a cost-effective way for a single Dynamics 365 user to obtain full user licensing for multiple Dynamics 365 products. Licenses for products that provide core business functionality qualify as base licenses. Examples are Finance, Dynamics 365 Supply Chain Management, Dynamics 365 Commerce, Dynamics 365 Project Operations, and Dynamics 365 Human Resources. Each product has one or more additional applications that people in the same roles frequently use and that qualify as attach licenses for that user. (These applications are sometimes referred to as subsequent qualifying applications.) For more information about attach licenses and how to save them, see [Dynamics 365 Licensing Guide](https://aka.ms/dynamicslicensingguide).

### Licenses required to create an implementation project

Admins use an implementation project to do most of their work in Lifecycle Services. Inside these types of projects, an admin can deploy a sandbox environment and a production environment, and can also deploy extra add-on sandboxes (a type of unassigned license) they purchase. You need at least 20 base licenses for Finance, Supply Chain Management, Commerce, Project Operations, or Human Resources to create an implementation project.

If you need multiple projects, you can create more by using the information in this documentation. The number of projects that you can create is a factor of 20. Therefore, if you need two projects, for example, you need 40 licenses.

## What happens when my license subscriptions expire?

Customers regularly adjust the number of licenses that they have. As mentioned earlier, you need at least 20 base licenses to create a project. If the number of paid base licenses falls below 20, Lifecycle Services performs several automated actions for implementation projects, as described in this section.  

### Banners are shown and notifications are sent

First, Lifecycle Services shows banners on different pages in your Lifecycle Services project. These banners indicate that you're working in a project that Microsoft detected falls below the minimum number of license subscriptions required to use it.

Second, Lifecycle Services sends email communications and message center posts to your tenant admins. These notifications indicate that Microsoft detected a project that doesn't have enough paid license subscriptions.

### Sandboxes are disabled

The next action is to disable sandbox environments. Lifecycle Services performs this action four business days after it sends communications in the previous step. Because these environments are used for testing, training, and debugging purposes, Lifecycle Services targets them first for deallocation. This approach helps protect against noncompliance but doesn't affect customer production environments that host mission-critical workloads.

Disabled environments aren't yet deleted. You can recover these environments if you renew your licenses or if you provide proof of intent by following the steps outlined in the *Manual renewal process* section.

### Production is disabled

Three business days after Lifecycle Services disables sandboxes, it disables the production environment. This action begins downtime for mission-critical workloads for the customer, because there are inactive or insufficient paid license subscriptions to operate the applications.

Disabled environments aren't yet deleted. You can recover these environments if you renew your licenses or if you provide proof of intent by following the steps outlined in the *Manual renewal process* section.

### Sandboxes are deleted

Three business days after you disable Production, the system deletes the sandbox environments.  This action is non-recoverable.  

### The project and Production environment are deleted

Two business days after the system deletes the sandboxes, it deletes the project along with the Production environment. This action is non-recoverable. This action removes all users, project data such as uploaded software assets, Azure connectors for deployment of cloud-hosted developer environments, and all associated sandbox and production environments.

## Manual renewal process for long purchasing processes

Sometimes purchasing licenses or renewing them can be a lengthy process for some customer organizations. If you show proof of your intent to renew your licenses, Microsoft can prevent the earlier automated actions and re-enable the environments. To communicate that you started the renewal process with your license vendor, create a support ticket that includes those details, and submit it to Microsoft Support.

## Clean up your Azure subscription

After you delete your implementation project, if you deployed cloud-hosted environments by using a customer-owned Azure subscription, Lifecycle Services no longer has access to the Azure subscription or any of the cloud-hosted environments. However, some resources might remain in your Azure subscription.

Follow these steps to free up the resources and remove application permissions in your Microsoft Entra tenant and each Azure subscription that you previously added to Lifecycle Services so that you could deploy the cloud-hosted environments.

1. Delete the Azure resources:

    1. In the [Azure portal](https://portal.azure.com), go to your Azure subscription.
    1. When you create a cloud-hosted environment, it creates a resource group in your Azure subscription. This resource group represents the resources that are created as part of your deployment of the cloud-hosted environment. It has the same name as the deployment. Therefore, it should be easy to find in the list of resource groups. Delete any resource groups that have the prefix **DynamicsDeployments-**.

    > [!IMPORTANT]
    > If you deployed cloud-hosted environments to more than one Azure region, you might have created multiple resource groups. Be sure to delete all related resource groups.

1. Remove the deployment service application from the subscription:

    1. Sign in to Microsoft Entra by using the PowerShell cmdlet.

        ```powershell
        Connect-AzureAD (Using Tenant Administrator account)
        ```

    1. Check whether the app is still enabled on the Microsoft Entra tenant.

        ```powershell
        Get-AzureADServicePrincipal -Filter "AppId eq '00001111-aaaa-2222-bbbb-3333cccc4444'"
        ```

    1. If the preceding command returns an object, the app is currently enabled on the tenant, and it might still have access to the subscription. Remove the app from the tenant.

        ```powershell
        $DDSObjectId=$(Get-AzureADServicePrincipal -Filter "AppId eq '00001111-aaaa-2222-bbbb-3333cccc4444'").ObjectId
        ```

        ```powershell
        Remove-AzureADServicePrincipal -ObjectId $DDSObjectId
        ```

    1. Verify that you removed the app.

        ```powershell
        Get-AzureADServicePrincipal -Filter "AppId eq ' 00001111-aaaa-2222-bbbb-3333cccc4444'"
        ```

## Related topics

[Data retention, deletion, and destruction in Microsoft 365](/compliance/assurance/assurance-data-retention-deletion-and-destruction-overview)

[Subscriptions, LCS projects, and Microsoft Entra tenants FAQ](../../fin-ops/get-started/subscription-overview.md)
