---
title: Create a Globalization feature
description: This article explains how to create a Globalization feature.
author: ilikond
ms.date: 01/29/2024
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: ikondratenko
ms.search.validFrom: 2024-01-29
ms.dyn365.ops.version: 10.0.39 
ms.custom: 
ms.assetid: 
ms.search.form: 
---

# Create a Globalization feature

[!include [banner](../../includes/banner.md)]

You can create an electronic invoicing feature from scratch, or you can base it on an existing feature. When you create a feature from scratch, you must manually add Electronic reporting (ER) configurations and other components, such as the feature setup and application setup details. When you create a feature that is based on an existing feature, the new feature inherits all the base feature's configurations and parameters. You can review what is copied from the base feature to the new feature.

## Create a feature that is based on an existing feature

1. In the **Globalization studio** workspace, select the **Electronic invoicing** tile.
2. In the **Configuration provider** field, make sure that your active configuration provider is selected. In this way, the new electronic invoicing feature will appear in the list after it's created. If your active configuration provider isn't selected, the new feature will be filtered out of the list.
3. Select **Add**, and then, in the drop-down dialog box, select the **Based on existing version** option.
4. Enter a name and description for the feature.
5. In the **Base feature** field, select the base version of the feature.
6. Select **Create feature**. The feature is created and has a status of **Draft**.
7. Review the feature components to determine whether updates are required:

    - Review the configurations, in case you must customize the ER formats and their binding with format mappings for the feature version.
    - Review the setup, in case you must customize the **Actions** tab, **Applicability rules** tab, or **Variables** tab for the feature version.

8. Complete the setup, and deploy the electronic invoicing feature. For more information, see [Complete and deploy a Globalization feature](e-invoicing-complete-publish-deploy-globalization-feature.md).

## Create a feature from scratch

This section explains how to create an electronic invoicing feature when no Globalization feature is available in the Global repository for your business scenarios out of the box.

To create an electronic invoicing feature, follow these steps.

1. In the **Globalization studio** workspace, select the **Electronic invoicing** tile.
2. Select **Add**, and then, in the drop-down dialog box, select the **New feature** option.
3. Enter a name and description for the electronic invoicing feature.
4. Select **Create feature**. The first version of the new feature appears on the right side of the page and has a status of **Draft**.

    Next, you must add ER configurations and feature setups. Before you add new or existing ER format configurations, make sure that they exist in your Microsoft Dynamics 365 Finance or Dynamics 365 Supply Chain Management environment.

5. Select the electronic invoicing feature that you're working on.
6. On the **Configurations** tab, select **Add**.
7. In the **Configurations** grid, browse to and select the format configurations that are required for the processing pipeline (for example, to generate electronic invoice files or process responses from external web services).
8. Select **OK**. You can now use the configurations in actions of the processing pipeline. For more information, see [Work with configurations](GS-e-invoicing-work-configurations.md).
9. To add an electronic invoicing feature setup, create it on the **Setups** tab of the **New feature** page. For more information, see [Work with feature setups](GS-e-invoicing-feature-setup.md).
10. Complete the setup, and deploy the electronic invoicing feature to the service environment. For more information, see [Complete and deploy a Globalization feature](e-invoicing-complete-publish-deploy-globalization-feature.md).

### Create file format configurations that are derived from the existing invoice model

You can skip this section if you don't have to create ER configurations but can reuse existing versions as a base.

This procedure shows how to create the file format configurations that are required for the new electronic invoicing feature that you want to create. Create the electronic invoice file format configuration and any other file format configurations that your new electronic invoicing feature requires.

1. In the **Globalization studio** workspace, select the **Electronic invoicing** tile.
2. Select the **Invoice model** or, for Brazilian scenarios, select the **Fiscal model**.
3. Select **Create configuration**, and then, in the drop-down dialog box, select the **Format based on data model Invoice** option.
4. Enter a name and description for the format configuration.
5. In the **Format type** field, select the file extension type.
6. In the **Data model definition** field, select the root structure to map your format to. For example, **InvoiceCustomer** is used for the customer invoice formats.
7. Select **Create configuration**.
8. Select the new format configuration.
9. Select **Designer**, and use the Format designer tool to configure the file layout so that it meets the file format specifications.
10. Close the page.
11. On the **Versions** tab, select **Change status** \> **Complete**.
12. **!!!CLARIFY - DO WE NEED TO SHARE NOW?!!!** Select **Change status** \> **Share** to publish the format configuration to the Global repository.

The new file format configurations must be shared with the Microsoft domain before they can be consumed by the Electronic invoicing service.

1. Select the format configuration that you're working on. The status of the configuration must be **Shared**.
2. On the **Versions** tab, select **Advanced sharing** \> **Global repository**.
3. On the **Shared with** tab, select **Organization**.
4. In the **Parameters** field, enter **microsoft.com** to share the format configuration with the Microsoft domain.
5. Select **OK**.

