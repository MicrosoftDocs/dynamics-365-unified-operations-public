---
title: Create a Dataverse solution using Upload into repository
description: Learn how to create a Microsoft Dataverse solution by using the Upload into repository functionality.
author: filatovm
ms.author: filatovm
ms.topic: how-to 
ms.date: 07/02/2024
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
---

# Create a Dataverse solution using Upload into repository

[!INCLUDE[banner](../../../includes/banner.md)]

Starting from version 10.0.40, instead of manually creating a Dataverse solution as described in [Upload ER configurations and Globalization features as a Dataverse solution](gsw-upload-er-config.md), you can now use the Upload into repository functionality to upload one or all of your custom Electronic reporting (ER) configurations and Globalization features.

To use this functionality, you should have a Dataverse environment that's connected to your Dynamics 365 Finance environment and add a security role to access tables in Dataverse by following these steps:

1. Create a new security role as described in [Create or edit a security role](/power-platform/admin/create-edit-security-role).
2. In that security role add **Create, Read, Write, Delete, Append, Append to, Assign, Share** permissions for the **Organization** to the following tables: **Solution, Publisher, Electronic Reporting Configuration File, Electronic Reporting Configurations Index File, Globalization Feature File, and Globalization Features Index File**. 
3. Assign the created security role to users as described in [Assign security roles](/power-platform/admin/assign-security-roles). 

The process of creating a Dataverse solution by using Upload into repository has three phases:

1. Create a Dataverse configuration repository.
2. Export configurations to Dataverse.
3. View configurations as a Dataverse solution.

The following sections describe each phase.

## Create a Dataverse configuration repository

You should create a Dataverse configuration repository for your active configuration provider.

To create a Dataverse configuration repository, follow these steps.

1. Sign in to the Dynamics 365 Finance app by using one of the following roles:

    - Electronic reporting developer
    - Electronic reporting functional consultant
    - System administrator

1. Go to **Organization administration** \> **Workspaces** \> **Globalization studio**.
1. In the **Configuration providers** section, select the tile that has your provider (for example, Contoso).
1. On the **Contoso** tile, select **Repositories**.
1. Select **Add**.
1. In the **Configuration repository properties** dialog box, set up parameters for the Dataverse solution that is associated with the new repository.

    If you set the **Automatically create solution** option to **Yes**, the system creates the solution for you. If you leave the **Publisher** field blank, a default publisher is used.

:::image type="content" source="media/configuration-repository-properties.png" alt-text="Screenshot of the Configuration repository properties dialog box.":::

## Export configurations to Dataverse

After you create the repository, you can export configurations to Dataverse.

To export configurations to Dataverse, follow these steps.

1. To upload a single configuration version that has a status of **Completed**, use the **Upload into repository** button on the **Versions** FastTab of the **Electronic reporting Configurations** page. The system uploads all parent configuration versions to make the solution independently deployable.
1. To upload all the latest **Completed** configuration versions with the active provider, select **Upload all configurations into repository** on the **Configurations** tab on the Action Pane of the **Electronic reporting Configurations** page. Then use the **Upload into repository** dropdown dialog box.


## View configurations as a Dataverse solution

If you set the **Automatically create solution** option to **Yes** when you created a Dataverse repository for your configuration provider, after you upload your configurations, a new solution appears in the Power Apps maker portal.

When you upload additional configuration versions, the system adds the new configuration versions to the same solution as the files.

:::image type="content" source="media/configuration-versions.png" alt-text="Screenshot of the configuration versions.":::

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
