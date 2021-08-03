---
title: Inventory Visibility Setup
description: This topic describes how to install the Inventory Visibility Add-in for Dynamics 365 Supply Chain Management.
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

# Inventory Visibility Setup

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]
[!INCLUDE [cc-data-platform-banner](../../includes/cc-data-platform-banner.md)]

This topic describes how to install the Inventory Visibility Add-in for Dynamics 365 Supply Chain Management.

You need to install the Inventory Visibility Add-in using Microsoft Dynamics Lifecycle Services (LCS). LCS is a collaboration portal that provides an environment and a set of regularly updated services that help you manage the application lifecycle of your Dynamics 365 Finance and Operations apps.

For more information, see [Lifecycle Services resources](../../fin-ops-core/dev-itpro/lifecycle-services/lcs.md).

## Inventory Visibility prerequisites

Before you install the Inventory Visibility, you must do the following:

- Obtain an LCS implementation project with at least one environment deployed.
- Make sure that the prerequisites for setting up add-ins provided in the [Add-ins overview](../../fin-ops-core/dev-itpro/power-platform/add-ins-overview.md) have been completed. Inventory Visibility doesn't require dual-write linking.
- Contact the Inventory Visibility Team at [inventvisibilitysupp@microsoft.com](mailto:inventvisibilitysupp@microsoft.com) to get the following three required files:
  - `InventoryServiceApplication.PackageDeployer.zip`
  - `Inventory Visibility Integration.zip` (if the version of Supply Chain Management that you're running is earlier than version 10.0.18)

> [!NOTE]
> The currently supported countries and regions include Canada(CCA, ECA), the United States(WUS, EUS), the European Union (NEU, WEU), the United Kingdom(SUK, WUK), Australia(EAU, SEAU).

If you have any questions about these prerequisites, please contact the Inventory Visibility product team.

## <a id="setup-microsoft-dataverse"></a>Set up Dataverse

To set up Dataverse for use with Inventory Visibility, use package deployer tool to deploy Inventory Visibility package. The following subsections describe how to complete each of these tasks.

> [!NOTE]
> Currently we only support you use the Dataverse environment created from LCS page, if your Dataverse environment is created in other ways(such as PowerAppsAdminCenter) and link to the FO environment, please contact the Inventory Visibility product team to resolve the mapping issue first and then install Inventory Visibility.

### Migrate from old version of Dataverse solution

If you are a user has installed Inventory Visibility Dataverse solution with older version, please check which case you choose to install the Inventory Visibility, and follow the below instruction to update your version. There are two cases:

- Case 1: If you set up Dataverse manually by importing solution `Inventory Visibility Dataverse Solution_1_0_0_2_managed.zip`, please download these three files.

  - `Inventory Visibility Dataverse Solution_1_0_0_3_managed.zip`
  - `InventoryServiceBase_managed.cab`
  - `InventoryServiceApplication.PackageDeployer.zip`

    1. Manully import `Inventory Visibility Dataverse Solution_1_0_0_3_managed.zip` and `InventoryServiceBase_managed.cab` to the Dataverse.
       1. Open the URL of your Dataverse environment.
       1. Go to the **Solutions** page.
       1. Select **Import**.
    2. Use the package deployer tool deploy `InventoryServiceApplication.PackageDeployer.zip` package. Please follow the [Using the package deployer tool to deploy package](#deploy-package) section to update.

- Case 2: If you set up Dataverse using the package deployer tool before to install the older version `.*PackageDeployer.zip` package, please download `InventoryServiceApplication.PackageDeployer.zip` and follow the [Using the package deployer tool to deploy package](#deploy-package) section to update.

### <a name="Using the package deployer tool to deploy package" id="deploy-package"></a>Using the package deployer tool to deploy package

1. Install developer tools as described in [Download tools from NuGet](/dynamics365/customerengagement/on-premises/developer/download-tools-nuget).

1. Unblock `InventoryServiceApplication.PackageDeployer.zip` that you download from the Teams Group.

   Right click the file and find **Properties** -> **General** -> **Security**, check **Unblock** and apply. If there is no **Security** section in **General** tab, the file is not blocked, go to next step.

   ![Unblock downloaded file.](media/unblock-file.png "Unblock downloaded file")

1. Unzip `InventoryServiceApplication.PackageDeployer.zip`:

   - folder `InventoryServiceApplication`
   - file `[Content_Types].xml`
   - file `Microsoft.Dynamics.InventoryServiceApplication.PackageExtension.dll`

1. Copy each of these folders and files to the `.\Tools\PackageDeployment` directory, which was created when you installed the developer tools.

1. Execute `.\Tools\PackageDeployment\PackageDeployer.exe`. Follow the instructions on your screen to import the solutions.

## <a id="install-add-in"></a>Install the Inventory Visibility Add-in

Before you install the add-in, please follow the instructions given in [Quickstart: Register an application with the Microsoft identity platform](/azure/active-directory/develop/quickstart-register-app) to register an application and add a client secret to AAD under your azure subscription.<a id="RegisterApp"></a>

- [Register an application](/azure/active-directory/develop/quickstart-register-app)
- [Add a client secret](/azure/active-directory/develop/quickstart-register-app#add-a-certificate)
- The **Application(Client) Id**, **Client Secret**, and **Tenant ID** will be used in the following steps.

After you register an application and add a client secret to AAD, do the following to install the Inventory Visibility Add-in:

1. Sign in to the [Lifecycle Services (LCS)](https://lcs.dynamics.com/Logon/Index) portal.
1. On the home page, select the project where your environment is deployed.
1. On the project page, select the environment where you want to install the add-in.
1. On the environment page, scroll down until you see the **Environment add-ins** section in the **Power Platform integration** section, where you can find the Dataverse environment name.
1. In the **Environment add-ins** section, select **Install a new add-in**.

   ![The environment page in LCS.](media/inventory-visibility-environment.png "The environment page in LCS")

1. Select the **Install a new add-in** link. A list of available add-ins opens.
1. Select **Inventory Visibility** in the list.
1. Enter values for the following fields for your environment, the AAD application ID is the one you created in [previous step](#RegisterApp):

   - **AAD application (client) ID**
   - **AAD tenant ID**

   ![Add in setup page.](media/inventory-visibility-setup.png "Add-in setup page")

1. Agree to the terms and condition by selecting the **Terms and conditions** check box.
1. Select **Install**. The status of the add-in will show as **Installing**. When it's done, refresh the page to see the status change to **Installed**.

## <a id="uninstall-add-in"></a>Uninstall the Inventory Visibility Add-in

To uninstall the Inventory Visibility Add-in, select **Uninstall** from LCS page. The uninstallation will terminate the Inventory Visibility Add-in, unregister the Inventory Add-in from LCS and delete any temporal data stored within the Inventory Visibility Add-in data cache. The primary inventory data stored in your Dataverse subscription will not be deleted by the uninstall process.

To uninstall inventory data stored in your Dataverse subscription, go to https://make.powerapps.com, click **Environment** from the navigation bar and select the Dataverse environment bonded with your LCS environment. Then go to **Solutions** and delete these 5 solutions:

- Anchor solution for Inventory Visibility application in Dynamics 365 solutions
- Dynamics 365 FNO SCM Inventory Visibility Applications Solution
- Inventory Service Configuration
- Inventory Visibility Standalone
- Dynamics 365 FNO SCM Inventory Visibility Base Solution

After deletion of these Solutions, the data stored in tables will also be deleted.

## <a id="setup-dynamics-scm"></a>Set up Dynamics 365 Supply Chain Management

### <a id="deploy-inventory-visibility-package"></a>Deploy the Inventory Visibility integration package

If you're running Supply Chain Management version 10.0.17 or earlier, contact the Inventory Visibility on-board support team at [inventvisibilitysupp@microsoft.com](mailto:inventvisibilitysupp@microsoft.com) to get the package file. Then deploy the package in LCS.

> [!NOTE]
> If a version mismatch error occurs during deployment, you must manually import the X++ project into your development environment. Then create the deployable package in your development environment, and deploy it in your production environment.
>
> The code is included with Supply Chain Management version 10.0.18. If you're running that version or later, deployment isn't required.

Make sure that the following features are turned on in your Supply Chain Management environment. (By default, they are turned on.)

| Feature description | Code version | Toggle class |
| --- | --- | --- |
| Enable or disable using inventory dimensions on InventSum table      | 10.0.11      | InventUseDimOfInventSumToggle      |
| Enable or disable using inventory dimensions on InventSumDelta table | 10.0.12      | InventUseDimOfInventSumDeltaToggle |

### <a id="setup-inventory-visibility-integration"></a>Set up Inventory Visibility integration

1. In Dynamics 365 Supply Chain Management, open the **[Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md)** workspace, and turn on the **Inventory Visibility Integration** feature.
1. Go to **Inventory Management \> Set up \> Inventory Visibility Integration parameters**, and enter the URL of the environment where you're running Inventory Visibility, see [Find endpoint according to your LCS environment](./inventory-visibility-power-platform.md#get-service-endpoint) for more details.
1. Go to **Inventory Management \> Periodic \> Inventory Visibility Integration**, and enable the job. All inventory change events from Supply Chain Management will now be posted to Inventory Visibility.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]