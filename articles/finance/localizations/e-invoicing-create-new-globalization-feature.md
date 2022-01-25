---
# required metadata

title: Create a new Globalization feature
description: This topic provides information about how to create a new Globalization feature.
author: dkalyuzh
ms.date: 01/24/2022
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
ms.custom: 
ms.author: dkalyuzh
ms.search.validFrom: 
ms.dyn365.ops.version: 

---

# Create a new Globalization feature

[!include [banner](../includes/banner.md)]


You can create a new **Electronic invoicing feature** on it's own, or you can create a new feature based on an existing feature.
When you create a new **Electronic invoicing feature**, you must manually add Electronic reporting (ER)configurations and other components, such as the **Feature setup** and **Application setup** details. When you create a feature based on another feature, the new feature inherits all of the configurations and parameters from the base feature. You can review what is copied from the base to the new feature.

## Create new feature 

This topic explains how to create a new Electronic invoicing feature when no Globalization feature is available in Global repository for your business scenarios out of the box.

To create a new Electronic invoicing feature, complete the following steps.
 
 1. Sign in to your Regulatory configuration service (RCS) account.
 2. In the **Globalization feature** workspace, in the **Features** section, select the **Electronic invoicing** tile.
 3. Select **Add**, and then select **New** feature.
 4. Enter a name and description for the Electronic invoicing feature.
 5. Select **Create feature**.
 6. On the right side of the page, you will see the first version of your feature in **Draft** status. Next, add Electronic reporting configurations and feature setups. Before you add new or existing Electronic reporting format configurations, make sure that the configurations exist in your local RCS repository.
 7. Select the Electronic invoicing feature that you're working on, and on the **Configurations** tab, select **Add**.
 8. In the **Configurations** grid, browse to and select the format configurations that required for the processing pipeline. For example, to generate the electronic invoice file or process a response from external Web services.
 9. Select **OK**. Now you can use this configuration in actions of the processing pipeline. For more details, see [Work with configurations](e-invoicing-work-configurations.md).  

    To add a new Electronic invoicing feature setup, on the **Setups** tab of the **New feature** page, create a new feature setup. For more information, see [Work with feature setup](e-invoicing-feature-setup.md).

10. Complete the setup and deploy the Electronic invoicing feature to the Service environment. For more information, see [Complete, publish, and deploy a Globalization feature](e-invoicing-complete-publish-deploy-globalization-feature).

### Create new file format configurations derived from the existing invoice model

You can skip this section if you don't need to create Electronic reporting configurations and can simply reuse existing versions as a base.

Create the file format configurations that are required for the new Electronic invoicing feature that you want to create. Create the electronic invoice file format configuration and any other file format configurations that your new Electronic invoicing feature might require.

 1. Sign in to your RCS account and go to the **Electronic reporting** workspace.
 2. Select the **Reporting configurations** tile, and then select the **Invoice model** of **Fiscal model** (for Brazilian scenarios).
 3. Select **Create configuration** and then select **Format based on data model Invoice**/.
 4. Enter a name and description for the format configuration.
 5. In the **Format type** field, select the file extension type.
 6. In the **Data model definition**, select the root structure to map your format to. For example, **InvoiceCustomer** is used for the customer invoice formats .
 7. Select **Create configuration**, and then select the format configuration that you created.
 8. Select **Designer**, and use the **Format designer tool** to configure the file layout so that it meets the file format specifications.
 9. Close the page.
 10. On the **Versions** tab, select **Change status** > **Complete**.
 11. Select **Change status** > **Share** to publish the format configuration to the Global repository.

The new file format configuration must be shared with the Microsoft domain before the configuration can be consumed by the Electronic invoicing service.
 1. Select the format configuration that you're working on. The status of the configuration must be **Shared**.
 2. On the **Versions** tab, select **Advanced sharing** > **Global repository**.
 3. On the **Shared with** tab, select **Organization**.
 4. In the **Parameters** field, enter **`microsoft.com`** to share the format configuration with the Microsoft domain.
 5. Select **OK**.
	

## Create a new feature from an existing feature

 1. In the **Electronic reporting** workspace, make sure that you have selected your active configuration provider in **Configuration provider** field. You will see the new Electronic invoicing feature in the list when it is created. If you don't have your active configuration provider selected, the new feature will be filtered out which might cause confusion.
 2. Select **Add** > **Based on existing version**.
 3. Enter a name and description for the feature.
 4. In the list of available features, select the base version of the feature, and then select **Create feature**. The feature that you added is created and has a status of **Draft**.
 5. Review the feature components to determine whether updates are required:
 
    - Review the configurations, in case you need to customize the Electronic reporting (ER) formats and their binding with format mappings for the feature version.
    - Review the setup, in case you need to customize the **Actions** tab, **Applicability rules** tab, or **Variables** tab for the feature version.

Complete and deploy the Electronic invoicing feature to the Service environment. For more information, see [Complete, publish and deploy](e-invoicing-complete-publish-deploy-globalization-feature).
