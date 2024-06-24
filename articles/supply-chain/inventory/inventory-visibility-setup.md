---
title: Install the Inventory Visibility Add-in
description: Learn how to install the Inventory Visibility Add-in for Microsoft Dynamics 365 Supply Chain Management, including Inventory Visibility prerequisites.
author: yufei-huang
ms.author: yufeihuang
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 06/24/2024
audience: Application User
ms.custom: 
  - bap-template
---

# Install and set up Inventory Visibility

[!include [banner](../includes/banner.md)]
[!INCLUDE [azure-ad-to-microsoft-entra-id](../../includes/azure-ad-to-microsoft-entra-id.md)]

This article describes how to install the Inventory Visibility Add-in for Microsoft Dynamics 365 Supply Chain Management.

> [!TIP]
> If you're a feature consultant or solution consultant, we recommend that you join the [Inventory Visibility Add-in Yammer group](https://www.yammer.com/dynamicsaxfeedbackprograms/#/threads/inGroup?type=in_group&feedId=46697168896), where you can read about the latest developments, exchange tips with other consultants and developers, and discuss features.
>
> If you're experiencing technical issues or running into exceptions, you can get help by sending email directly to the Inventory Visibility product team at [inventvisibilitysupp@microsoft.com](mailto:inventvisibilitysupp@microsoft.com) (please be sure to include your Supply Chain Management environment ID).
>
> For useful code samples and troubleshooting guides, visit the [Inventory Visibility GitHub repo](https://github.com/microsoft/Inventory-Visibility-Add-in-Examples).

## Inventory Visibility prerequisites

Before you install the Inventory Visibility, you must complete the following tasks:

- Obtain a Supply Chain Management environment that is linked to a Microsoft Dataverse environment.
- Make sure that the prerequisites for setting up add-ins have been completed. For information about these prerequisites, see [Add-ins overview](../../fin-ops-core/dev-itpro/power-platform/add-ins-overview.md). Inventory Visibility doesn't require dual-write linking.

The following table lists the countries/regions where Inventory Visibility is currently supported.

| Azure region | Region short name |
|---|---|
| Asia East | eas |
| Asia Southeast | seas |
| Australia East | eau |
| Australia Southeast | seau |
| Brazil South | sbr |
| Canada Central | cca |
| Canada East | eca |
| China East 2 | cne2 |
| China North 2 | cnn2 |
| Europe North | neu |
| Europe West | weu |
| France Central | cfr |
| France South | sfr |
| India Central | cin |
| India South | sin |
| Japan East | ejp |
| Japan West | wjp |
| Norway East | eno |
| Norway West | wno |
| South Africa West | wza |
| South Africa North | nza |
| Switzerland North | nch |
| Switzerland West | wch |
| UAE North | nae |
| UK South | suk |
| UK West | wuk |
| US East | eus |
| US West | wus |

If you have any questions about these prerequisites, contact the Inventory Visibility product team at [inventvisibilitysupp@microsoft.com](mailto:inventvisibilitysupp@microsoft.com).

## <a name="install-add-in"></a>Install the Inventory Visibility Add-in

Before you install the add-in, register an application and add a client secret to Microsoft Entra under your Azure subscription. For instructions, see [Register an application](/azure/active-directory/develop/quickstart-register-app) and [Add a client secret](/azure/active-directory/develop/quickstart-register-app#add-a-certificate). Be sure to make a note of the **Application (client) ID**, **Client secret**, and **Tenant ID** values, because you'll need them later.

> [!IMPORTANT]
> If you have more than one environment, create a different Microsoft Entra application for each of them. If you use the same application ID and tenant ID to install the Inventory Visibility Add-in for different environments, a token issue will occur for older environments. As a result, only the latest installation will be valid.

Two options are available to install the Inventory Visibility Add-in. One is from [Lifecycle Services](../../fin-ops-core/dev-itpro/lifecycle-services/lcs.md), which is a collaboration portal that provides a unifying, collaborative environment along with a set of regularly updated services that help you manage the application lifecycle of your implementations. The other is from [Power Platform Admin Center](/power-platform/admin/admin-documentation), which provides a unified portal for administrators to manage environments and settings for Power Apps, Power Automate, Power Pages, and Microsoft Copilot Studio.

### Install the Inventory Visibility Add-in from Lifecycle Services

After you register an application and add a client secret to Microsoft Entra ID, follow these steps to install the Inventory Visibility Add-in.

1. Sign in to [Lifecycle Services](https://lcs.dynamics.com/Logon/Index).
1. On the home page, select the project where your environment is deployed.
1. On the project page, select the environment where you want to install the add-in.
1. On the environment page, scroll down until you find the **Environment add-ins** section in the **Power Platform integration** section. There, you can find the Dataverse environment name. Confirm that the Dataverse environment name is the one that you want to use for Inventory Visibility.

    > [!IMPORTANT]
    > If *all* of the following are true for your installation, then you must fix the mapping issue before installing the Inventory Visibility Add-in:
    >
    > - You installed the Inventory Visibility Add-in using Lifecycle Services.
    > - Your Dataverse environment wasn't created by Lifecycle Services (for example, because it was created using the Power Platform admin center).
    > - Your Dataverse environment is linked to your Supply Chain Management environment.
    >
    > It's possible that your dual-write environment is linked to a Dataverse instance while Lifecycle Services isn't set up for Power Platform integration. This linking mismatch can cause unexpected behavior. We recommend that your Lifecycle Services environment details match what you're connected to in dual-write so that the same connection can be used by business events, virtual tables, and add-ins. See [Linking mismatch](../../fin-ops-core/dev-itpro/data-entities/dual-write/lcs-setup.md#linking-mismatch) for information about how to fix the mapping issue. Once the mapping issue is resolved, you can then proceed to install Inventory Visibility.

1. In the **Environment add-ins** section, select **Install a new add-in**.

    :::image type="content" source="media/inventory-visibility-environment.png" alt-text="Environment page in Lifecycle Services." lightbox="media/inventory-visibility-environment.png":::

1. Select the **Install a new add-in** link. A list of available add-ins appears.
1. In the list, select **Inventory Visibility**.
1. Set the following fields for your environment:

    - **Microsoft Entra application (client) ID** – Enter the Microsoft Entra application ID that you created and made a note of earlier.
    - **Microsoft Entra tenant ID** – Enter the tenant ID that you made a note of earlier.

    :::image type="content" source="media/inventory-visibility-setup.png" alt-text="Setup add-in page." lightbox="media/inventory-visibility-setup.png":::

1. Agree to the terms and conditions by selecting the **Terms and conditions** checkbox.
1. Select **Install**. The status of the add-in is shown as **Installing**. When the installation is completed, refresh the page. The status should change to **Installed**.
1. In Dataverse, select the **Apps** section in the left navigation, and verify that the **Inventory Visibility** Power Apps is installed successfully. If the **Apps** section doesn't exist, contact the Inventory Visibility product team at [inventvisibilitysupp@microsoft.com](mailto:inventvisibilitysupp@microsoft.com).

> [!NOTE]
> If the system warns you that you don't have permission to install Inventory Visibility on Lifecycle Services, you must contact the administrator to modify your permission.
>
> If it takes more than an hour to install from the Lifecycle Services page, then your user account probably lacks permission to install solutions in the Dataverse environment. Follow these steps to resolve the issue:
>
> 1. Cancel the Inventory Visibility Add-in installation process from the Lifecycle Services page.
> 1. [Install the Inventory Visibility Add-in from Power Platform admin center](#install-from-power-platform).
> 1. After the installation is complete, go back to the Lifecycle Services page and check the status of the Inventory Visibility Add-in.

### <a name="install-from-power-platform"></a>Install the Inventory Visibility Add-in from Power Platform admin center

After you register an application and add a client secret to Microsoft Entra ID, you must install the Inventory Visibility Add-in.

> [!IMPORTANT]
> If your environment isn't a [unified environment](/power-platform/developer/unified-experience/finance-operations-dev-overview) and your Dataverse environment wasn't created by Lifecycle Services (for example, because you created it using the Power Platform admin center), then you must fix the mapping issue before installing Inventory Visibility Add-in. See [Linking mismatch](../../fin-ops-core/dev-itpro/data-entities/dual-write/lcs-setup.md#linking-mismatch) for instructions.

Follow these steps to install the Inventory Visibility Add-in.

1. Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) and make sure that the user account you want to use to install the add-in has the *Dynamics 365 Unified Operations Plan* license assigned to it. Assign the license if needed.
1. Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com) using the same user account.
1. Select the environment where you want to install the add-in.
1. On the top bar, select **Resources** \> **Dynamics 365 apps**.

    :::image type="content" source="media/inventory-visibility-environment-ppac.png" alt-text="Environment page in PPAC." lightbox="media/inventory-visibility-environment-ppac.png":::

1. Select **Install App**. Find *Dynamics 365 Inventory Visibility* in the list and select **Next**.
1. Set the following fields for your environment:

    - **Enter application id of service** – Enter the Microsoft Entra application ID that you created and made a note of earlier.
    - **Enter tenant id of service** – Enter the tenant ID that you made a note of earlier.

    :::image type="content" source="media/inventory-visibility-setup-ppac.png" alt-text="Setup add-in page in PPAC." lightbox="media/inventory-visibility-setup-ppac.png":::

1. Agree to the terms of service.
1. Select **Install**. During the installation, the status of the add-in is shown as *Installing*. After the installation completes, refresh the page and the status should change to *Installed*.

> [!NOTE]
> If the installation failed, please contact the Inventory Visibility product team at [inventvisibilitysupp@microsoft.com](mailto:inventvisibilitysupp@microsoft.com).

## <a name="setup-dynamics-scm"></a>Set up Inventory Visibility in Supply Chain Management

### <a name="deploy-inventory-visibility-package"></a>Deploy the Inventory Visibility integration package

If you're running Supply Chain Management version 10.0.18 or later, you can skip this deployment session and jump to [set up Inventory Visibility integration](#setup-inventory-visibility-integration).

If you're running Supply Chain Management version 10.0.17 or earlier, contact the Inventory Visibility on-board support team at [inventvisibilitysupp@microsoft.com](mailto:inventvisibilitysupp@microsoft.com) to get the package file. Then deploy the package in Lifecycle Services.

> [!NOTE]
> If a version mismatch error occurs during deployment, you must manually import the X++ project into your development environment. Then create the deployable package in your development environment, and deploy it in your production environment.

Make sure that the following features are turned on in your Supply Chain Management environment. (By default, they're turned on.)

| Feature description | Code version | Toggle class |
|---|---|---|
| Enable or disable using inventory dimensions on InventSum table      | 10.0.11 | InventUseDimOfInventSumToggle      |
| Enable or disable using inventory dimensions on InventSumDelta table | 10.0.12 | InventUseDimOfInventSumDeltaToggle |

### <a name="setup-inventory-visibility-integration"></a>Set up Inventory Visibility integration

Once you've installed the add-in, prepare your Supply Chain Management system to work with it by doing the following steps.

1. In Supply Chain Management, open the **[Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md)** workspace, and turn on the *Inventory Visibility integration* feature.
1. Go to **Inventory Management** \> **Set up** \> **Inventory Visibility Integration parameters**.
1. Open the **General** tab and make the following settings:

    - **Inventory Visibility endpoint** – Enter the URL of the environment where you're running Inventory Visibility. For more information, see [Find your service endpoint and read the configuration](inventory-visibility-power-platform.md#endpoint).
    - **Maximum number of records in a single request** – Set to the maximum number of records to include in a single request. You must enter a positive integer less than or equal to 1000. The default value is 512. We strongly recommend keeping the default value unless you've received advice from Microsoft Support or are otherwise certain that you need to change it.

1. The following optional features enhance the functionality of Inventory Visibility. Decide whether you want to use one or both of these features. If you do, set them up. (You can also set them up later.)

    - **Soft reservations and offsets** – Soft reservations help organizations achieve a single source of truth for available inventory, especially during the order fulfillment process. For information about how to enable and set up this feature, see [Inventory Visibility reservations](inventory-visibility-reservations.md).
    - **Support for warehouse management processes (WMS) items** – This feature lets you use WMS items with Inventory Visibility. For information about how to enable and set up this feature, see [Inventory Visibility support for WMS items](inventory-visibility-whs-support.md).
    - **Inventory summary** – This feature provides an inventory summary for products together with all dimensions. For information about how to enable and set up this feature, see [Inventory summary](inventory-visibility-inventory-summary.md).
    - **Preload a streamlined on-hand query** – This feature provides an aggregated inventory summary for products by configured dimensions. For information about how to enable and set up this feature, see [Preload a streamlined on-hand query](inventory-visibility-preload-on-hand.md).

1. After you finish setting up the optional features you selected, go to **Inventory Management** \> **Periodic** \> **Inventory Visibility Integration** and enable the job. All inventory change events from Supply Chain Management will now be posted to Inventory Visibility.

> [!NOTE]
> When you enable the Inventory Visibility integration job, if you receive an error that states that you must update the partition schema, see the [Update partition schema to two if you get an error when enabling the Inventory Visibility integration job](#update-partition-two) section of this article for instructions.

### <a name="setup-inventory-visibility-integration-hotfixes-link"></a>Inventory Visibility integration hotfixes

For a list of the latest hotfixes available for Inventory Visibility integration features in Supply Chain Management, see [Recent Dynamics 365 SCM hotfixes](https://github.com/microsoft/Inventory-Visibility-Add-in-Examples/blob/main/Troubleshooting%20Guide/Recent%20Dynamics%20365%20SCM%20hotfixes.md).

### <a name="update-partition-two"></a>Update partition schema to two if you get an error when enabling the Inventory Visibility integration job

When you try to enable the Inventory Visibility integration batch job from Supply Chain Management, you might receive the following error:

> Cannot sync more than 500000 records in the same warehouse. To mitigate this issue, update partition schema to 2 in Inventory Visibility Add-in. Contact Inventory Visibility Support Team at `inventvisibilitysupp@microsoft.com` for more info.

If you receive this error, follow these steps to update your [partition schema](inventory-visibility-power-platform.md#data-partition) to help prevent out-of-memory issues. If you don't receive this error, you can skip this procedure.

1. In Power Apps, [delete all inventory data](inventory-visibility-power-platform.md#delete-data).
1. Set up a system to send [API requests](inventory-visibility-api.md) to Inventory Visibility.
1. After data is deleted, call the `Get` API with a body of `none` to get all partition IDs (by using `/api/environment/{environmentId}/allpartitionids`). Review the response to confirm that data has been completely cleared. The result should be empty.
1. Call the `Post` API with a body of `none` to change the partition schema (by using `/api/environment/{environmentId}/updatePartitionSchema?newversion=2`).
1. In Power Apps, enable the [advanced warehouse inventory](inventory-visibility-whs-support.md) feature, and [update the configuration](inventory-visibility-power-platform.md#update-configuration).
1. In Power Apps, [review the runtime configuration](inventory-visibility-power-platform.md#endpoint). The `CachePartitonIdVersion` field should show a value of `ByLocationAndProductIdMod64`.
1. In Supply Chain Management, go to **Inventory Management** \> **Periodic** \> **Inventory Visibility Integration**, and enable the job.

## <a name="update-add-in"></a>Update the Inventory Visibility Add-in

To update an installed version of the Inventory Visibility Add-in to the latest version, follow these steps:

1. Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com).
1. On the navigation pane, select **Environments**.
1. Open the environment where you want to update the Inventory Visibility Add-in.
1. In the **Resources** section, select **Dynamics 365 apps**.
1. In the list, find the row where **Name** is *Dynamics 365 Inventory Visibility*. Check the value in the **Status** column for this row.
    - If the **Status** is *Installed*, then you're already running the latest version so you can skip the rest of this procedure.
    - If the **Status** is *Update available*, then an update is available. Continue with the next step.

    > [!TIP]
    > To see which version of the add-in you are currently running, regardless of the status, open the **More application actions** menu (ellipsis button) and then select **Details**.

1. If the page shows that an update is available, open the **More application actions** menu (ellipsis button) and then select **Update**.
1. A dialog opens. Select the **I agree to the terms of service** check box and then select **Update**.
1. A pop-up window opens asking you to confirm the action. To proceed, enter the name of your environment in the field provided and then select **Update**.

## <a name="uninstall-add-in"></a>Uninstall the Inventory Visibility Add-in

To uninstall the Inventory Visibility Add-in, follow these steps:

1. Sign in to Supply Chain Management.
1. Go to **Inventory Management** \> **Periodic** \> **Inventory Visibility Integration** and disable the job.
1. Go to Lifecycle Services and open the page for the environment where you want to uninstall the add-in (see also the [Install the Inventory Visibility Add-in](#install-add-in) section).
1. Select **Uninstall**.

    > [!NOTE]
    > Uninstalling from the Power Platform admin center is not officially supported.

The uninstall process terminates the Inventory Visibility Add-in, unregisters the add-in from Lifecycle Services, and deletes any temporary data that's stored in the Inventory Visibility Add-in data cache. Primary inventory data that was synced to your Dataverse subscription won't be deleted.

> [!IMPORTANT]
> If you want to continue using Inventory Visibility in the current environment, we advise against deleting all solutions from your Dataverse environment. If you want to delete all inventory data in Dataverse, we recommend using the [delete all inventory data](inventory-visibility-power-platform.md#delete-data) option. Please contact [inventvisibilitysupp@microsoft.com](mailto:inventvisibilitysupp@microsoft.com) for assistance if you are not sure about your scenario.

> [!NOTE]
> If it's necessary to delete all solutions related to Inventory Visibility, follow these steps.
>
> 1. Open [Power Apps](https://make.powerapps.com).
> 1. Select **Environment** on the navigation bar.
> 1. Select the target Dataverse environment.
> 1. Go to **Solutions** and delete solutions in the following order:
>    1. Dynamics 365 Inventory Visibility – Anchor
>    1. Dynamics 365 Inventory Visibility – Copilot
>    1. Dynamics 365 Inventory Visibility – Application
>    1. Dynamics 365 Inventory Visibility – Controls
>    1. Dynamics 365 Inventory Visibility – Plugins
>    1. Dynamics 365 Inventory Visibility – Base
>    1. Dynamics 365 Product Search - Anchor
>    1. Dynamics 365 Product Search Core
>
> Inventory Visibility data that is stored in tables will also be deleted along with the solutions.

## Supply Chain Management Database and Dataverse Movement

There are several ways to migrate data between Supply Chain Management databases and Dataverse environments. For instructions, see the [Inventory Visibility GitHub repo](https://github.com/microsoft/Inventory-Visibility-Add-in-Examples/blob/main/Troubleshooting%20Guide/Database%20and%20Dataverse%20Movement.md). If the target environment of your movement operation is a production environment, or if your scenario isn't listed in the guide, please contact [inventvisibilitysupp@microsoft.com](mailto:inventvisibilitysupp@microsoft.com) for assistance.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
