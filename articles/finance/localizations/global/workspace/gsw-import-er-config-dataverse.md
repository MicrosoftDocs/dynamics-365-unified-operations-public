---
title: Import Electronic reporting (ER) configurations from Dataverse
description: Learn how to import Electronic reporting (ER) configurations from Microsoft Dataverse, including an overview on importing the Globalization solution.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.date: 05/14/2026
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak

---

# Import Electronic reporting (ER) configurations from Dataverse

[!INCLUDE[banner](../../../includes/banner.md)]

[!INCLUDE[banner](../../../includes/rsc-to-gsw-banner.md)]

This article explains how to import Electronic reporting (ER) configurations from Microsoft Dataverse.

## Set up integration with Dataverse

To use this functionality, you need a Dataverse environment that's connected to your Dynamics 365 Finance environment. For more information, see the following articles:

- [Enable Power Platform Integration](../../../../fin-ops-core/dev-itpro/power-platform/enable-power-platform-integration.md)
- [Connect finance and operations apps with a new Microsoft Dataverse instance](../../../../fin-ops-core/dev-itpro/power-platform/environment-lifecycle-connect-finops-new-dv.md)
- [Connect finance and operations apps with an existing Microsoft Dataverse instance](../../../../fin-ops-core/dev-itpro/power-platform/environment-lifecycle-connect-finops-existing-dv.md)

You should also add a security role to access tables in Dataverse by following these steps:

1. Create a new security role as described in [Create or edit a security role](/power-platform/admin/create-edit-security-role).
1. In that security role, add **Create, Read, Write, Delete, Append, Append to, Assign, Share** permissions for **Organization** to the following tables: **Electronic Reporting Configuration File, Electronic Reporting Configurations Index File, Globalization Feature File, and Globalization Features Index File**. 
1. Assign the created security role to users as described in [Assign security roles](/power-platform/admin/assign-security-roles).

## Import the Globalization solution

This functionality uses the [Microsoft Dataverse Web API](/power-apps/developer/data-platform/webapi/overview).

Import the Globalization solution by following these steps:

1. Go to [Globalization Solution for Microsoft Dynamics 365 Finance](https://aka.ms/GlobalizationSolution) on Marketplace.
1. Select **Get it now**.
1. Fill in the required data.
1. Select an environment, and then select **Install**.

## Import configurations from Dataverse

This solution adds a new type of repository for getting ER configurations in Dynamics 365 Finance. This repository is known as the Dataverse configuration repository. It provides the same user interface (UI) that Dataverse provides. Therefore, you can import single and filtered configurations.

> [!NOTE]
> To use the Dataverse configuration repository, make sure that the **Dataverse repository** feature is enabled in the **Feature management** workspace of the Dynamics 365 Finance app. The feature is enabled by default since the service update 10.0.39. However, it might be disabled in your environment.

### Open the Dataverse configuration repository

To open the Dataverse configuration repository, follow these steps:

1. Sign in to the Dynamics 365 Finance app by using one of the following roles:

    - Electronic reporting developer
    - Electronic reporting functional consultant
    - System administrator

1. Go to **Organization administration** > **Workspaces** > **Globalization studio**.
1. In the **Configuration providers** section, select the **Microsoft** tile.
1. On the **Microsoft** tile, select **Repositories**.

    :::image type="content" source="media/gsw-repositories.png" alt-text="Screenshot that shows the tile for the Microsoft configuration provider in the Globalization Studio workspace.":::

1. On the **Configuration repositories** page, in the grid, select the existing repository of the **Dataverse** type. If this repository doesn't appear in the grid, follow these steps:

    1. Select **Add** to add a repository.
    1. Select **Dataverse** as the repository type, and then select **Create repository**.
    1. If you're prompted for authorization, follow the on-screen instructions.
    1. Enter a name and description for the repository, and then select **OK** to confirm the new repository entry.
    1. In the grid, select the new repository of the **Dataverse** type.

1. Select **Open** to view the list of ER configurations for the selected repository.

## Import a single configuration

> [!NOTE]
> It can take up to two weeks for a new ER configuration released by Microsoft or a new version of an ER configuration released by Microsoft to appear in the Dataverse configuration repository. If you expect a configuration update but don't see it in the Dataverse configuration repository, or if auto-updates are disabled in your environment, you can manually trigger the update of the Globalization solution package in your Power Platform admin center portal. To learn more about updating solutions in Power Platform admin center, see [Manage Dynamics 365 apps](/power-platform/admin/manage-apps#environment-level-view-of-apps).

To import a single configuration, follow these steps:

1. On **Configuration repository**, in the configurations tree, select the ER configuration that you want.
1. On the **Versions** FastTab, select the required version of the selected ER configuration.
1. Select **Import** to download the selected version from the Dataverse to the current Dynamics 365 Finance instance.

    > [!NOTE]
    > The **Import** button is unavailable for ER configuration versions that are already present in the current Dynamics 365 Finance instance.

:::image type="content" source="media/gsw-config-repo.png" alt-text="Screenshot of the Configuration repository page, where a version of a configuration is selected for import.":::

## Review configuration prerequisites before import

Starting in version 10.0.47 of Dynamics 365 Finance apps, before you import an ER configuration version, you can review its prerequisites and verify that your environment meets all requirements. This process helps you identify potential issues, such as missing dependent configurations or an incompatible application version, before you start the import.

### View prerequisites for a configuration version

To view the prerequisites for a specific configuration version, follow these steps:

1. On **Configuration repository**, in the configurations tree, select the ER configuration that you want.
1. On the **Versions** FastTab, select the required version of the selected ER configuration.
1. On the **Prerequisites** FastTab, review the list of prerequisites for the selected configuration version.

    The **Prerequisites** FastTab shows the following types of requirements:

    - **Configuration** – Other ER configurations that must be present in the current Dynamics 365 Finance instance before you can import the selected version. Prerequisites might be organized into groups:
        - **All of** – All configurations in the group must be available.
        - **One of** – At least one configuration in the group must be available.
    - **Product** – The minimum Dynamics 365 Finance application version that is required.

:::image type="content" source="media/gsw-config-repo-prerequisites.png" alt-text="Screenshot of the Prerequisites FastTab.":::

### Check prerequisites before import

To proactively validate that your environment meets all prerequisites for a configuration version, follow these steps:

1. On **Configuration repository**, in the configurations tree, select the ER configuration that you want.
1. On the **Versions** FastTab, select the required version of the selected ER configuration.
1. Select **Check prerequisites**.

    The system validates the following requirements:

    1. The required Dynamics 365 Finance application version is installed.
    1. All required ER configuration dependencies are available in the current instance.

    If any prerequisite isn't met, the validation results show the specific gaps and provide guidance about how to resolve them.

> [!TIP]
> By checking prerequisites before you import, you can avoid failed imports and reduce troubleshooting time, especially in environments where configuration updates are applied regularly.

### Error messages for failed imports

If you import a configuration version that has unmet prerequisites, the system provides an error message that explicitly identifies the missing prerequisites. The error message includes:

- The name and version of the missing prerequisite configuration.
- The required application version or platform build, if applicable.

## Import filtered configurations

To import filtered configurations, follow these steps:

1. On **Configuration repository**, on the **Filter** FastTab, in the **Tags** grid, add any needed tags.
1. In the **Country/region applicability** field, select the appropriate country/region codes.
1. Select **Apply filter**.
1. The **Configurations** FastTab shows all the configurations that satisfy the specified selection conditions. Select **Import** to download the filtered configurations from Dataverse to the current Dynamics 365 Finance instance.
1. Select **Reset filter** to remove the specified selection conditions.

:::image type="content" source="media/gsw-config-repo-reset-filter.png" alt-text="Screenshot of the Configuration repository page, where a Country/region applicability filter is applied.":::

> [!NOTE]
> - Depending on the ER settings, the system validates configurations after you import them. You might see a notification about any inconsistency problems that it finds. You must fix these problems before you can use the imported configuration version. For more information, see the list of related resources for this article.
> - You can configure ER configurations as dependent on other configurations. Therefore, when you import a selected configuration, the system might automatically import other configurations. For more information about configuration dependencies, see [Define the dependency of ER configurations on other components](../../../../fin-ops-core/dev-itpro/analytics/tasks/er-define-dependency-er-configurations-from-other-components-july-2017.md).

## Additional resources

[Get started with Tax Calculation - High-level configuration](../global-get-started-with-tax-calculation-service.md#high-level-configuration)

[Globalization feature components](../gs-e-invoicing-working-globalization-features.md)

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
