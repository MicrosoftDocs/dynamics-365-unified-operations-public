---
title: Define the dependency of ER configurations on other components
description: This article describes how to design an Electronic reporting (ER) configuration and specify its dependency from other software components.
author: kfend
ms.date: 04/10/2026
ms.topic: how-to
audience: Developer, IT Pro
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: AX 7.0.0
---

# Define the dependency of ER configurations on other components

[!include [banner](../../includes/banner.md)]

To complete these steps, you must first complete the steps in the task guide, **ER Manage model mapping configurations**, and you must have access to Microsoft Dynamics Lifecycle Services.

This procedure shows how to design an Electronic reporting (ER) configuration and specify its dependency on other software components. By specifying these dependencies, you help guarantee that the configuration is correctly downloaded to a specific version of finance and operations. In this example, you create required ER configurations for the sample company Litware, Inc.

This procedure is intended for users who have the **System administrator** or **Electronic reporting developer** role assigned to them. You can perform the steps in any company, because ER configurations are shared among companies.

1. Go to **Organization administration** > **Electronic reporting** > **Configurations**.
    * Make sure that the configurations tree contains the **Sample data model** configuration and subordinate items. Otherwise, complete the steps in the task guide, **ER Manage model mapping configurations**, and then start this guide again.

## Define the dependency of ER configurations on other components

1. In the tree, expand **Sample data model**.
1. In the tree, select **Sample data model\Sample mapping**.
    * You selected the draft version of the **Sample mapping** model mapping configuration. You can now define its dependency on other software components. This step is a prerequisite for controlling the download of this configuration version from an ER repository and any further use of this version.
1. Expand the Prerequisites section.
    * The **Implementations** prerequisites group is added automatically at this stage. This group contains the prerequisite component that refers to the data model configuration and has the Implementation flag turned on. This flag indicates that the **Sample mapping** mapping configuration is considered the implementation of the **Sample data model** data model. This component forces ER to download the **Sample mapping** mapping configuration from an ER repository whenever the **Sample data model** model configuration is downloaded.
1. Select **Edit**.
    * You can specify a single dependency of the current version of a configuration on a software component by using the definition of the component's type, and either the component version or a range of component versions.  
    * You can group desired dependencies together. When you select the **All of** grouping type, the dependency condition of this group is considered satisfied when each dependency condition from this group and subordinate group is satisfied. When you select the **One of** grouping type, the dependency condition of this group is considered satisfied when at least one dependency condition from this group is satisfied.
1. Select **New**.
1. Select **Product prerequisite component**.
1. Select **Microsoft Dynamics 365 for Operations (1611)**.
1. In the **Version** field, type `[7.1.1541.3036,8)`.
    * [7.1.1541.3036,8)  
    * Dependencies that you enter are evaluated when this configuration is downloaded from any ER repository. This configuration version is downloaded from the ER repository when version 1 of the **Sample data model** configuration is either already in place or downloaded in advance. If it's downloaded in advance, it must be completed in finance and operations version 7.1.1541.3036 or later, but must not exceed major version 8.
1. Select **Save**.
1. Close the page.
1. Select **Change status**.
1. Select **Complete**.
1. Select **OK**.
1. In the tree, select **Sample data model\Sample mapping (alternative)**.
1. Select **Edit**.
1. Select **New**.
1. Select **Product prerequisite component**.
1. Select **Microsoft Dynamics AX 7.0 RTW**.
1. In the **Version** field, type `[7.0.1265.3015,7.1)`.
    * [7.0.1265.3015,7.1)  
    * Dependencies are evaluated when the configuration is downloaded from any ER repository. This configuration version is downloaded from the ER repository when version 1 of the **Sample data model** configuration is either already in place or downloaded in advance. If it's downloaded in advance, it must be completed in Microsoft Dynamics 365 Finance, Enterprise edition, the version of which must be 7.0.1265.3015 or later, but must not exceed minor version 1.
1. Select **Save**.
1. Close the page.
1. Select **Change status**.
1. Select **Complete**.
1. Select **OK**.

## Configure the ER repository

1. Close the page.
1. Go to **Organization administration** > **Workspaces** > **Electronic reporting**.
    * Open the list of ER repositories for the current ER provider, Litware, Inc.  
1. In the list, select the row.
1. Select **Repositories**.
1. Select **Show filters**.
1. Enter a filter value of **LCS** in the **Type name** field by using the **contains** filter operator.
    * If the Lifecycle Services repository is already registered for the current ER provider, you can skip the remaining steps in this sub-task. If the Lifecycle Services repository isn't already registered, complete the remaining steps.
1. Select **Add** to open the drop dialog.
1. In the **Configuration repository type** field, enter **LCS**.
1. Select **Create repository**.
1. In the **Project** field, enter or select a value.
    * Select the desired Lifecycle Services project from the lookup of the **Project** field.  
1. Select **OK**.
1. Close the page.

## Upload configurations to Lifecycle Services

1. Select **Reporting configurations**.
1. In the tree, select **Sample data model**.
1. Select the completed version of this configuration.
1. Select **Change status**.
1. Select **Share**.
1. Select **OK**.
    * Version 1 of this model configuration is uploaded to Lifecycle Services by using the Lifecycle Services project for the ER repository that you previously configured.
1. In the tree, expand **Sample data model**.
1. In the tree, select **Sample data model\Sample mapping**.
1. Select the completed version of this configuration.
1. Select **Change status**.
1. Select **Share**.
1. Select **OK**.
    * Version 1.1 of this model mapping configuration is uploaded to Lifecycle Services by using the Lifecycle Services project for the ER repository that you previously configured.
1. In the tree, select **Sample data model\Sample mapping (alternative)**.
1. Select the completed version of this configuration.
1. Select **Change status**.
1. Select **Share**.
1. Select **OK**.
    * Version 1.1 of this model mapping configuration is uploaded to Lifecycle Services by using the Lifecycle Services project for the ER repository that you previously configured.

## Evaluate ER configuration dependencies

You delete created configurations from the system and download them back from the Lifecycle Services repository.  

1. In the tree, select **Sample data model\Sample mapping**.
1. Select **Delete**.
1. Select **Yes**.
1. In the tree, select **Sample data model\Sample mapping (alternative)**.
1. Select **Delete**.
1. Select **Yes**.
1. In the tree, select **Sample data model\Sample format**.
1. Select **Delete**.
1. Select **Yes**.
1. In the tree, select **Sample data model**.
1. Select **Delete**.
1. Select **Yes**.
1. Close the page.
    * Open the list of ER repositories for the current ER provider, Litware, Inc.  
1. Select **Repositories**.
1. Select **Show filters**.
1. Enter a filter value of **LCS** in the **Type name** field by using the **contains** filter operator.
1. Select **Open**.
1. In the tree, select **Sample data model**.
    * You can view an evaluation of whether prerequisite conditions are satisfied for each version of the ER configurations for the current repository. To view this evaluation, select **Check prerequisites**.
1. Select **Check prerequisites**.
1. Select **Import**.
1. Select **Yes**.
1. Close the page.
1. Close the page.
1. Close the page.
1. Go to **Organization administration** > **Electronic reporting** > **Configurations**.
1. In the tree, expand **Sample data model**.
    * The model **Sample mapping** mapping configuration is downloaded together with the selected data model configuration. You download the two files together because **Sample mapping** is defined as implementing the selected data model, and because it's applicable for the application. The **Sample mapping (alternative)** configuration isn't downloaded because the condition for the required application version isn't satisfied.
    * If you sign in to finance and operations, register the same provider, access the same Lifecycle Services project, and download the same data model configuration, the **Sample mapping (alternative)** configuration downloads, whereas the **Sample mapping** configuration is skipped.

## Additional resources

[Manage the Electronic reporting (ER) configuration lifecycle](../general-electronic-reporting-manage-configuration-lifecycle.md)

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
