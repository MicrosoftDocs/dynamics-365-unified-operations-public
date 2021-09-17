---
title: Install the Inventory Visibility Add-in
description: This topic describes how to install the Inventory Visibility Add-in for Microsoft Dynamics 365 Supply Chain Management.
author: yufeihuang
ms.date: 08/02/2021
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: yufeihuang
ms.search.validFrom: 2021-08-02
ms.dyn365.ops.version: 10.0.21
---

# Install and set up Inventory Visibility

[!include [banner](../includes/banner.md)]
[!INCLUDE [cc-data-platform-banner](../../includes/cc-data-platform-banner.md)]

This topic describes how to install the Inventory Visibility Add-in for Microsoft Dynamics 365 Supply Chain Management.

You must use Microsoft Dynamics Lifecycle Services (LCS) to install the Inventory Visibility Add-in. LCS is a collaboration portal that provides an environment and a set of regularly updated services that help you manage the application lifecycle of your finance and operations apps.

For more information, see [Lifecycle Services resources](../../fin-ops-core/dev-itpro/lifecycle-services/lcs.md).

## Inventory Visibility prerequisites

Before you install the Inventory Visibility, you must complete the following tasks:

- Obtain an LCS implementation project where at least one environment is deployed.
- Make sure that the prerequisites for setting up add-ins have been completed. For information about these prerequisites, see [Add-ins overview](../../fin-ops-core/dev-itpro/power-platform/add-ins-overview.md). Inventory Visibility doesn't require dual-write linking.
- Contact the Inventory Visibility product team at [inventvisibilitysupp@microsoft.com](mailto:inventvisibilitysupp@microsoft.com) to get the following required files:

    - `InventoryServiceApplication.PackageDeployer.zip`
    - `Inventory Visibility Integration.zip` (if the version of Supply Chain Management that you're running is earlier than version 10.0.18)

> [!NOTE]
> The countries and regions that are currently supported include Canada (CCA, ECA), the United States (WUS, EUS), the European Union (NEU, WEU), the United Kingdom (SUK, WUK), Australia (EAU, SEAU), Japan (EJP, WJP), and Brazil (SBR, SCUS).

If you have any questions about these prerequisites, contact the Inventory Visibility product team.

## <a name="setup-microsoft-dataverse"></a>Set up Dataverse

To set up Dataverse so that it can be used with Inventory Visibility, use the package deployer tool to deploy the Inventory Visibility package. The following subsections describe how to complete each task.

> [!NOTE]
> Currently, only Dataverse environments that were created by using LCS are supported. If your Dataverse environment was created in some other way (for example, by using the Power Apps admin center), and if it's linked to your Supply Chain Management environment, you must first contact the Inventory Visibility product team to fix the mapping issue. You can then install Inventory Visibility.

### Migrate from an old version of the Dataverse solution

If you've installed an older version of the Inventory Visibility Dataverse solution, use these instructions to update your version. There are two cases:

- **Case 1:** If you manually set up Dataverse by importing the `Inventory Visibility Dataverse Solution_1_0_0_2_managed.zip` solution, follow these steps:

    1. Download the following three files:

        - `Inventory Visibility Dataverse Solution_1_0_0_3_managed.zip`
        - `InventoryServiceBase_managed.cab`
        - `InventoryServiceApplication.PackageDeployer.zip`

    1. Manually import `Inventory Visibility Dataverse Solution_1_0_0_3_managed.zip` and `InventoryServiceBase_managed.cab` into Dataverse by following these steps:

        1. Open the URL of your Dataverse environment.
        1. Open the **Solutions** page.
        1. Select **Import**.

    1. Use the package deployer tool to deploy the `InventoryServiceApplication.PackageDeployer.zip` package. For instructions, see the [Use the package deployer tool to deploy the package](#deploy-package) section later in this topic.

- **Case 2:** If you set up Dataverse by using the package deployer tool before you installed the older `.*PackageDeployer.zip` package, download `InventoryServiceApplication.PackageDeployer.zip`, and do an update. For instructions, see the [Use the package deployer tool to deploy the package](#deploy-package) section.

### <a name="deploy-package"></a>Use the package deployer tool to deploy the package

1. Install the developer tools as described in [Download tools from NuGet](/dynamics365/customerengagement/on-premises/developer/download-tools-nuget).
1. Unblock the `InventoryServiceApplication.PackageDeployer.zip` file that you downloaded from the Teams group by following these steps:

    1. Select and hold (or right-click) the file, and then select **Properties**.
    1. In the **Properties** dialog box, on the **General** tab, find the **Security** section, select **Unblock**, and apply the change. If there is no **Security** section on the **General** tab, the file isn't blocked. In this case, move on to the next step.

    ![Unblocking the downloaded file](media/unblock-file.png "Unblocking the downloaded file")

1. Unzip `InventoryServiceApplication.PackageDeployer.zip` to find the following items:

    - `InventoryServiceApplication` folder
    - `[Content_Types].xml` file
    - `Microsoft.Dynamics.InventoryServiceApplication.PackageExtension.dll` file

1. Copy each of those items to the `.\Tools\PackageDeployment` directory. (This directory was created when you installed the developer tools.)
1. Run `.\Tools\PackageDeployment\PackageDeployer.exe`, and follow the on-screen instructions to import the solutions.

## <a name="install-add-in"></a>Install the Inventory Visibility Add-in

Before you install the add-in, register an application and add a client secret to Azure Active Directory (Azure AD) under your Azure subscription. For instructions, see [Register an application](/azure/active-directory/develop/quickstart-register-app) and [Add a client secret](/azure/active-directory/develop/quickstart-register-app#add-a-certificate). Be sure to make a note of the **Application (client) ID**, **Client secret**, and **Tenant ID** values, because you will need them later.

After you register an application and add a client secret to Azure AD, follow these steps to install the Inventory Visibility Add-in.

1. Sign in to [LCS](https://lcs.dynamics.com/Logon/Index).
1. On the home page, select the project where your environment is deployed.
1. On the project page, select the environment where you want to install the add-in.
1. On the environment page, scroll down until you find the **Environment add-ins** section in the **Power Platform integration** section. There, you can find the Dataverse environment name.
1. In the **Environment add-ins** section, select **Install a new add-in**.

    ![Environment page in LCS](media/inventory-visibility-environment.png "Environment page in LCS")

1. Select the **Install a new add-in** link. A list of available add-ins appears.
1. In the list, select **Inventory Visibility**.
1. Set the following fields for your environment:

    - **AAD application (client) ID** – Enter the Azure AD application ID that you created and made a note of earlier.
    - **AAD tenant ID** – Enter the tenant ID that you made a note of earlier.

    ![Setup add-in page](media/inventory-visibility-setup.png "Setup add-in page")

1. Agree to the terms and condition by selecting the **Terms and conditions** checkbox.
1. Select **Install**. The status of the add-in is shown as **Installing**. When the installation is completed, refresh the page. The status should change to **Installed**.

> [!IMPORTANT]
> If you have more than one LCS environment, create a different Azure AD application for each environment. If you use same application ID and tenant ID to install the Inventory Visibility Add-in for different environments, a token issue will occur for older environments. Only the last one that was installed will be valid.

## <a name="uninstall-add-in"></a>Uninstall the Inventory Visibility Add-in

To uninstall the Inventory Visibility Add-in, select **Uninstall** on the LCS page. The uninstallation process terminates the Inventory Visibility Add-in, unregisters the add-in from LCS, and deletes any temporary data that is stored in the Inventory Visibility Add-in data cache. However, the primary inventory data that is stored in your Dataverse subscription isn't deleted.

To uninstall inventory data that is stored in your Dataverse subscription, open [Power Apps](https://make.powerapps.com), select **Environment** on the navigation bar, and select the Dataverse environment that is bonded with your LCS environment. Then go to **Solutions**, and delete the following five solutions:

- Anchor solution for Inventory Visibility application in Dynamics 365 solutions
- Dynamics 365 FNO SCM Inventory Visibility Applications Solution
- Inventory Service Configuration
- Inventory Visibility Standalone
- Dynamics 365 FNO SCM Inventory Visibility Base Solution

After you delete these solutions, the data that is stored in tables will also be deleted.

## <a name="setup-dynamics-scm"></a>Set up Inventory Visibility in Supply Chain Management

### <a name="deploy-inventory-visibility-package"></a>Deploy the Inventory Visibility integration package

If you're running Supply Chain Management version 10.0.17 or earlier, contact the Inventory Visibility on-board support team at [inventvisibilitysupp@microsoft.com](mailto:inventvisibilitysupp@microsoft.com) to get the package file. Then deploy the package in LCS.

> [!NOTE]
> If a version mismatch error occurs during deployment, you must manually import the X++ project into your development environment. Then create the deployable package in your development environment, and deploy it in your production environment.
>
> The code is included with Supply Chain Management version 10.0.18. If you're running that version or later, deployment isn't required.

Make sure that the following features are turned on in your Supply Chain Management environment. (By default, they are turned on.)

| Feature description | Code version | Toggle class |
|---|---|---|
| Enable or disable using inventory dimensions on InventSum table      | 10.0.11 | InventUseDimOfInventSumToggle      |
| Enable or disable using inventory dimensions on InventSumDelta table | 10.0.12 | InventUseDimOfInventSumDeltaToggle |

### <a name="setup-inventory-visibility-integration"></a>Set up Inventory Visibility integration

Once you have installed the add-in, prepare your Supply Chain Management system to work with it by doing the following steps.

1. In Supply Chain Management, open the **[Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md)** workspace, and turn on the following features:
    - *Inventory Visibility Integration* – Required.
    - *Inventory Visibility integration with reservation offset* – Recommended but optional. Requires version 10.0.22 or later. For more information, see [Inventory Visibility reservations](inventory-visibility-reservations.md).

1. Go to **Inventory Management \> Set up \> Inventory Visibility Integration parameters**.
1. Open the **General** tab and make the following settings:
    - **Inventory Visibility endpoint** – Enter the URL of the environment where you're running Inventory Visibility. For more information, see [Find the service endpoint](inventory-visibility-configuration.md#get-service-endpoint).
    - **Maximum number of records in a single request** – Set to the maximum number of records to include in a single request. You must enter a positive integer less than or equal to 1000. The default value is 512. We strongly recommend keeping the default value unless you have received advice from Microsoft Support or are otherwise certain that you need to change it.

1. If you enabled the optional *Inventory Visibility integration with reservation offset* feature, open the **Reservation offset** tab and make the following settings:
    - **Enable reservation offset** – Set to *Yes* to enable this functionality.
    - **Reservation offset modifier** – Select the inventory transaction status that will offset reservations made on Inventory Visibility. This setting determines the order processing stage that triggers offsets. The stage is traced by the order's inventory transaction status. Choose one of the following:
        - *On order* – For the *On transaction* status, an order will send an offset request when it's created. The offset quantity will be the quantity of the created order.
        - *Reserve* – For the *Reserve ordered transaction* status, an order will send an offset request when it's reserved, picked, packing-slip posted, or invoiced. The request will be triggered only once, for the first step when the mentioned process occurs. The offset quantity will be the quantity where the inventory transaction status changed from *On order* to *Reserved ordered* (or later status) on the corresponding order line.

1. Go to **Inventory Management \> Periodic \> Inventory Visibility Integration**, and enable the job. All inventory change events from Supply Chain Management will now be posted to Inventory Visibility.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
