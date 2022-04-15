---
# required metadata

title: Create a Globalization feature
description: This topic explains how to create a Globalization feature.
author: dkalyuzh
ms.date: 02/14/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: dkalyuzh
ms.search.validFrom: 
ms.dyn365.ops.version: 

---

# Create a Globalization feature

[!include [banner](../includes/banner.md)]

You can create an electronic invoicing feature from scratch, or you can base it on an existing feature. When you create a feature from scratch, you must manually add Electronic reporting (ER) configurations and other components, such as the feature setup and application setup details. When you create a feature that is based on an existing feature, the new feature inherits all the base feature's configurations and parameters. You can review what is copied from the base feature to the new feature.

## Create a feature from scratch

This section explains how to create an electronic invoicing feature when no Globalization feature is available in the Global repository for your business scenarios out of the box.

To create an electronic invoicing feature, follow these steps.

1. Sign in to your Regulatory Configuration Service (RCS) account.
2. In the **Globalization feature** workspace, in the **Features** section, select the **Electronic invoicing** tile.
3. Select **Add**, and then, in the drop-down dialog box, select the **New feature** option.
4. Enter a name and description for the electronic invoicing feature.
5. Select **Create feature**. The first version of the new feature appears on the right side of the page and has a status of **Draft**.

    Next, you must add ER configurations and feature setups. Before you add new or existing ER format configurations, make sure that they exist in your local RCS repository.

6. Select the electronic invoicing feature that you're working on.
7. On the **Configurations** tab, select **Add**.
8. In the **Configurations** grid, browse to and select the format configurations that are required for the processing pipeline (for example, to generate electronic invoice files or process responses from external web services).
9. Select **OK**. You can now use the configurations in actions of the processing pipeline. For more information, see [Work with configurations](e-invoicing-work-configurations.md).
10. To add an electronic invoicing feature setup, create it on the **Setups** tab of the **New feature** page. For more information, see [Work with feature setups](e-invoicing-feature-setup.md).
11. Complete the setup, and deploy the electronic invoicing feature to the service environment. For more information, see [Complete, publish, and deploy a Globalization feature](e-invoicing-complete-publish-deploy-globalization-feature.md).

### Create file format configurations that are derived from the existing invoice model

You can skip this section if you don't have to create ER configurations but can reuse existing versions as a base.

This procedure shows how to create the file format configurations that are required for the new electronic invoicing feature that you want to create. Create the electronic invoice file format configuration and any other file format configurations that your new electronic invoicing feature requires.

1. Sign in to your RCS account.
2. In the **Electronic reporting** workspace, select the **Reporting configurations** tile.
3. Select the **Invoice model** or, for Brazilian scenarios, select the **Fiscal model**.
4. Select **Create configuration**, and then, in the drop-down dialog box, select the **Format based on data model Invoice** option.
5. Enter a name and description for the format configuration.
6. In the **Format type** field, select the file extension type.
7. In the **Data model definition** field, select the root structure to map your format to. For example, **InvoiceCustomer** is used for the customer invoice formats.
8. Select **Create configuration**.
9. Select the new format configuration.
10. Select **Designer**, and use the Format designer tool to configure the file layout so that it meets the file format specifications.
11. Close the page.
12. On the **Versions** tab, select **Change status** \> **Complete**.
13. Select **Change status** \> **Share** to publish the format configuration to the Global repository.

The new file format configurations must be shared with the Microsoft domain before they can be consumed by the Electronic invoicing service.

1. Select the format configuration that you're working on. The status of the configuration must be **Shared**.
2. On the **Versions** tab, select **Advanced sharing** \> **Global repository**.
3. On the **Shared with** tab, select **Organization**.
4. In the **Parameters** field, enter **microsoft.com** to share the format configuration with the Microsoft domain.
5. Select **OK**.

## Create a feature that is based on an existing feature

1. Sign in to your RCS account.
2. In the **Globalization feature** workspace, in the **Features** section, select the **Electronic invoicing** tile.
3. In the **Configuration provider** field, make sure that your active configuration provider is selected. In this way, the new electronic invoicing feature will appear in the list after it's created. If your active configuration provider isn't selected, the new feature will be filtered out of the list.
4. Select **Add**, and then, in the drop-down dialog box, select the **Based on existing version** option.
5. Enter a name and description for the feature.
6. In the **Base feature** field, select the base version of the feature.
7. Select **Create feature**. The feature is created and has a status of **Draft**.
8. Review the feature components to determine whether updates are required:

    - Review the configurations, in case you must customize the ER formats and their binding with format mappings for the feature version.
    - Review the setup, in case you must customize the **Actions** tab, **Applicability rules** tab, or **Variables** tab for the feature version.

9. Complete the setup, and deploy the electronic invoicing feature to the service environment. For more information, see [Complete, publish, and deploy a Globalization feature](e-invoicing-complete-publish-deploy-globalization-feature.md).
