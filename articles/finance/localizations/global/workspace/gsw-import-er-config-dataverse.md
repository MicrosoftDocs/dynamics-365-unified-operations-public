---
title: Import Electronic reporting (ER) configurations from Dataverse
description: This article explains the how to import Electronic reporting (ER) configurations from Dataverse
author: filatovm
ms.author: filatovm
ms.topic: how-to
ms.date: 01/29/2023
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak

---

# Import Electronic reporting (ER) configurations from Dataverse

[!INCLUDE[banner](../../../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
[!INCLUDE[banner](../../../../includes/rsc-to-gsw-banner.md)]

This article explains the how to import Electronic reporting (ER) configurations from Dataverse.

## Set up integration with Dataverse and import Globalization solution

In order to use this functionality you should have Dataverse environment connected to your Finance environment. To validate this, follow these steps.

1. Go to environment in **Power Platform admin center**.
1. Select **Settings**.
1. Go to **Features** under **Product** tab.
1. Set **Enable Finance and Operations User Impersonation in Dataverse** to **On,** if it is not and select **Save**.

After this, you can **import** Globalization Solution. To import Globalization Solution, follow these steps.

1. Navigate to [solution AppSource link](https://appsource.microsoft.com/en-us/product/dynamics-crm/mscrm.d365-globalizationartifacts-preview?flightCodes=a0bc3ba0711a4558bf3a2932a66dc11d).
1. Select **Get it now**.
1. Fill out required data.
1. Select an environment and select **Install**.

## Import configurations from Dataverse

A new type of repository for getting ER configurations in Dynamics 365 Finance is added. The new repository is called the **Dataverse configuration** repository. This repository enables the same user interface as for the Global repo, allowing you to import single and filtered configurations.

### Open the configurations repository

To open the configurations repository, follow these steps.

1. Sign in to the Dynamics 365 Finance application using one of the following roles.
   - Electronic reporting developer
   - Electronic reporting functional consultant
   - System administrator
1. Go to **Organization administration** \> **Workspaces** \> **Globalization studio**.
1. In the **Configuration providers** section, select the **Microsoft** tile.
1. On the **Microsoft** tile, select **Repositories**.

   :::image type="content" source="media/gsw-repositories.png" alt-text="Screenshot of repositories in Globalization studio."::: 

1. On the **Configuration repositories** page, in the grid, select the existing repository of the **Dataverse** type. If this repository doesn't appear in the grid, follow these steps:
   1. Select **Add** to add a new repository.
   1. Select **Dataverse** as the repository type, and then select **Create repository**.
   1. If prompted, follow the authorization instructions.
   1. Enter a name and description for the repository and then select **OK** to confirm the new repository entry.
   1. In the grid, select the new repository of the **Dataverse** type.
1. Select **Open** to view the list of ER configurations for the selected repository.

## Import a single configuration

To import a single configureation, follow these steps.

1. On the **Configuration repositories** page, in the configurations tree, select the ER configuration that you want.
1. On the **Versions** FastTab, select the required version of the selected ER configuration.
1. Select **Import** to download the selected version from Global repository to the current Finance instance.

   > [!NOTE]
   > The **Import** button is unavailable for ER configuration versions that are already present in the current Finance instance.

   :::image type="content" source="media/gsw-config-repo.png" alt-text="Screenshot of the Configuration repository."::: 

## Import filtered configurations

To import filtered configurations, follow these steps.

1. On the **Configuration repositories** page, in the configurations tree, expand the **Filter** FastTab.
1. In the **Tags** grid, add any tags that are needed.
1. In the **Country/region applicability** field, select the appropriate country/region codes, and then select **Apply filter**.

   > [!NOTE]
   > The **Configurations** FastTab shows all the configurations that satisfy the specified selection conditions.

1. On the **Configurations** FastTab, select **Import** to download the filtered configurations from the Global repository to the current instance.
1. On the **Configurations** FastTab, select **Reset filter** to clean up the specified selection conditions.

   :::image type="content" source="media/gsw-config-repo-reset-filter.png" alt-text="Screenshot of the Configuration repository Reset filter.":::
   
> [!NOTE]
> Depending on the ER settings, configurations are validated after they are imported. You might be notified about any inconsistency issues that are discovered. Before you can use the imported configuration version, you must resolve the issues. For more information, see the list of related resources for this article.

> [!NOTE]
> ER configurations can be configured as being dependent on other configurations. Therefore, along with a selected configuration, other configurations might be automatically imported. For more about configuration dependencies, see [**Define the dependency of ER configurations on other components**](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/analytics/tasks/er-define-dependency-er-configurations-from-other-components-july-2017).
