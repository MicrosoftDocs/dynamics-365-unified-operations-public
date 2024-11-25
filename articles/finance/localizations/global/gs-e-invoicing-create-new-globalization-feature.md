---
title: Create Globalization features
description: Learn how to create a Globalization feature, including outlines on creating a feature based on an existing feature and creating a feature from scratch.
author: ilikond
ms.author: ikondratenko
ms.topic: article
ms.date: 01/29/2024
ms.custom: 
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2024-01-29
ms.search.form:
ms.dyn365.ops.version: 10.0.39
---

# Create Globalization features

[!INCLUDE[banner](../../includes/banner.md)]

You can create an Electronic invoicing feature from scratch, or you can base it on an existing feature. When you create a feature from scratch, you must manually add Electronic reporting (ER) configurations and other components, such as the feature setup and application setup details. When you create a feature that's based on an existing feature, the new feature inherits all the base feature's configurations and parameters. You can review what's copied from the base feature to the new feature.

## Create a feature based on an existing feature

1. In the **Globalization Studio** workspace, select the **Electronic invoicing** tile.
1. In the **Configuration provider** field, make sure that your active configuration provider is selected. In this way, the new Electronic invoicing feature will appear in the list after it's created. If your active configuration provider isn't selected, the new feature will be filtered out of the list.
1. Select **Add**, and then, in the dropdown dialog box, select the **Based on existing version** option.
1. Enter a name and description for the feature.
1. In the **Base feature** field, select the base version of the feature.
1. Select **Create feature**. The feature is created and has a status of **Draft**.
1. Review the feature components to determine whether updates are required:

    - Review the configurations in case you must customize the ER formats and their binding with format mappings for the feature version.
    - Review the setup in case you must customize the **Actions** tab, **Applicability rules** tab, or **Variables** tab for the feature version.

1. Complete the setup, and deploy the Electronic invoicing feature. For more information, see [Complete and deploy a Globalization feature](gs-e-invoicing-complete-publish-deploy-globalization-feature.md).

## Create a feature from scratch

This section explains how to create an Electronic invoicing feature when the Global repository includes no Globalization feature for your business scenarios out of the box.

To create an Electronic invoicing feature, follow these steps.

1. In the **Globalization Studio** workspace, select the **Electronic invoicing** tile.
1. Select **Add**, and then, in the dropdown dialog box, select the **New feature** option.
1. Enter a name and description for the Electronic invoicing feature.
1. Select **Create feature**. The first version of the new feature appears on the right side of the page and has a status of **Draft**.

    Next, you must add ER configurations and feature setups. Before you add new or existing ER format configurations, make sure that they exist in your Microsoft Dynamics 365 Finance or Dynamics 365 Supply Chain Management environment.

1. Select the Electronic invoicing feature that you're working on.
1. On the **Configurations** tab, select **Add**.
1. In the **Configurations** grid, browse to and select the format configurations that are required for the processing pipeline (for example, to generate electronic invoice files or process responses from external web services).
1. Select **OK**. You can now use the configurations in actions of the processing pipeline. For more information, see [Work with configurations](gs-e-invoicing-work-configurations.md).
1. To add an Electronic invoicing feature setup, create it on the **Setups** tab of the **New feature** page. For more information, see [Work with feature setups](gs-e-invoicing-feature-setup.md).
1. Complete the setup, and deploy the Electronic invoicing feature to the service environment. For more information, see [Complete and deploy a Globalization feature](gs-e-invoicing-complete-publish-deploy-globalization-feature.md).

### Create file format configurations that are derived from the existing invoice model

You can skip this section if you don't have to create ER configurations but can reuse existing versions as a base.

This procedure shows how to create the file format configurations that are required for the new Electronic invoicing feature that you want to create. Create the electronic invoice file format configuration and any other file format configurations that your new Electronic invoicing feature requires.

1. In the **Globalization Studio** workspace, select the **Electronic invoicing** tile.
1. Select **Invoice model** or, for Brazilian scenarios, **Fiscal model**.
1. Select **Create configuration**, and then, in the dropdown dialog box, select the **Format based on data model Invoice** option.
1. Enter a name and description for the format configuration.
1. In the **Format type** field, select the file extension type.
1. In the **Data model definition** field, select the root structure to map your format to. For example, **InvoiceCustomer** is used for the customer invoice formats.
1. Select **Create configuration**.
1. Select the new format configuration.
1. Select **Designer**, and use the Format designer tool to configure the file layout so that it meets the file format specifications.
1. Close the page.
1. On the **Versions** tab, select **Change status** \> **Complete**.
