---
title: Import Electronic reporting (ER) configurations from Dataverse (preview)
description: This article explains how to import Electronic reporting (ER) configurations from Microsoft Dataverse (preview).
author: filatovm
ms.author: filatovm
ms.topic: how-to
ms.date: 01/29/2023
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak

---

# Import Electronic reporting (ER) configurations from Dataverse (preview)

[!INCLUDE[banner](../../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
[!INCLUDE[banner](../../../includes/rsc-to-gsw-banner.md)]

This article explains how to import Electronic reporting (ER) configurations from Microsoft Dataverse.

## Set up integration with Dataverse and import the Globalization solution

To use this functionality, you should have a Dataverse environment that's connected to your Dynamics 365 Finance environment. To validate that this setup is in place, follow these steps.

1. In [Power Platform admin center](https://admin.powerplatform.microsoft.com/), go to the environment.
1. Select **Settings**.
1. On the **Product** tab, select **Features**.
1. Set the **Enable Finance and Operations User Impersonation in Dataverse** option to **On** if it isn't already.
1. Select **Save**.

You can now import the Globalization solution by following these steps.

1. Go to [Globalization Solution for Microsoft Dynamics 365 Finance](https://appsource.microsoft.com/product/dynamics-crm/mscrm.d365-globalizationartifacts-preview?flightCodes=a0bc3ba0711a4558bf3a2932a66dc11d) on AppSource.
1. Select **Get it now**.
1. Fill in the required data.
1. Select an environment, and then select **Install**.

## Import configurations from Dataverse

A new type of repository for getting ER configurations in Dynamics 365 Finance is added. This repository is known as the Dataverse configuration repository. It enables the same user interface (UI) that the Global repository enables. Therefore, you can import single and filtered configurations.

### Open the Dataverse configuration repository

To open the Dataverse configuration repository, follow these steps.

1. Sign in to the Dynamics 365 Finance app by using one of the following roles:

    - Electronic reporting developer
    - Electronic reporting functional consultant
    - System administrator

1. Go to **Organization administration** \> **Workspaces** \> **Globalization studio**.
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

To import a single configuration, follow these steps.

1. On the **Configuration repository** page, in the configurations tree, select the ER configuration that you want.
1. On the **Versions** FastTab, select the required version of the selected ER configuration.
1. Select **Import** to download the selected version from the Dataverse repository to the current Dynamics 365 Finance instance.

    > [!NOTE]
    > The **Import** button is unavailable for ER configuration versions that are already present in the current Dynamics 365 Finance instance.

:::image type="content" source="media/gsw-config-repo.png" alt-text="Screenshot of the Configuration repository page, where a version of a configuration is selected for import.":::

## Import filtered configurations

To import filtered configurations, follow these steps.

1. On the **Configuration repository** page, on the **Filter** FastTab, in the **Tags** grid, add any tags that are needed.
1. In the **Country/region applicability** field, select the appropriate country/region codes.
1. Select **Apply filter**.
1. The **Configurations** FastTab shows all the configurations that satisfy the specified selection conditions. Select **Import** to download the filtered configurations from the Dataverse repository to the current Dynamics 365 Finance instance.
1. Select **Reset filter** to clean up the specified selection conditions.

:::image type="content" source="media/gsw-config-repo-reset-filter.png" alt-text="Screenshot of the Configuration repository page, where a Country/region applicability filter is applied.":::

> [!NOTE]
> Depending on the ER settings, configurations are validated after they're imported. You might be notified about any inconsistency issues that are found. Before you can use the imported configuration version, you must fix the issues. For more information, see the list of related resources for this article.
>
> ER configurations can be configured as dependent on other configurations. Therefore, when you import a selected configuration, other configurations might be automatically imported. For more information about configuration dependencies, see [Define the dependency of ER configurations on other components](../../../../fin-ops-core/dev-itpro/analytics/tasks/er-define-dependency-er-configurations-from-other-components-july-2017.md).

## Related resources

- [Get started with Tax Calculation - High-level configuration](../global-get-started-with-tax-calculation-service.md#high-level-configuration)
- [Globalization feature components](../e-invoicing-working-globalization-features.md)

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
