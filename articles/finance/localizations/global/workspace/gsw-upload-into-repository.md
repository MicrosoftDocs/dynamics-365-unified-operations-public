---
title: Create a Dataverse solution using upload into repository 
description: Learn how to create a Dataverse solution using upload into repository.
author: filatovm
ms.author: filatovm
ms.topic: how-to 
ms.date: 05/30/2024
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
---

# Create a Dataverse solution using upload into repository

[!INCLUDE[banner](../includes/banner.md)]

Instead of manual Dataverse creation described here in [Upload ER configurations and Globalization features as a Dataverse solution](gsw-upload-er-config.md), you can now leverage the Upload into repository functionality to upload one or all of you custom electronic reporting configurations and globalization features. 

There are three phases you must follow to create a Dataverse solution using upload into repository:

- Create a Dataverse configuration repository.
- Export configurations to Dataverse.
- View configurations as a Dataverse solution.

Each phase is described in the following sections.

## Create a Dataverse configuration repository

You should create a Dataverse configuration repository for your active configuration provider. 

To create a Dataverse configuration repository, follow these steps.

1. Sign in to the Dynamics 365 Finance app by using one of the following roles:
   - Electronic reporting developer
   - Electronic reporting functional consultant
   - System administrator
1. Go to **Organization administration** > **Workspaces** > **Globalization studio**.
1. In the **Configuration providers** section, select the tile with your provider. For example, Contoso.
1. On the Contoso tile, select **Repositories**.
1. Select **Add**.
1. In the dialog, setup parameters for **Dataverse solution**, associated with this repository.

If you enable the checkbox **Automatically create solution**, the system creates the solution for you. You can leave the **Publisher** field empty, and a default publisher is used.

:::image type="content" source="media/configuration-repository-properties.png" alt-text="Screenshot of the Configuration repository properties page."::: 

## Export configurations to Dataverse

After creating the repository, you can export configurations to Dataverse.

To export configurations to Dataverse, follow these steps.

1. Upload a single configuration version in Status “Completed”, using the **Upload into repository** button in the Versions grid of the **Electronic reporting Configurations** form. The system uploads all parent configuration versions to make this solution independently deployable. 
1. Upload all latest “Completed” versions configurations with active provider, using **Configurations** > **Upload all configurations into repository**.

:::image type="content" source="media/upload-all configurations.png" alt-text="Screenshot of Upload into repository."::: 


## View configurations as a Dataverse solution

If you chose the **Automatically create solution** option while creating a Dataverse repository for your configuration provider, after uploading your configurations, you see a new solution in the PowerApps Maker portal. 

The system adds the new configuration versions to the same solution as the files when you upload additional configuration versions. 


:::image type="content" source="media/configuration-versions.png" alt-text="Screenshot of the configuration versions."::: 


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
