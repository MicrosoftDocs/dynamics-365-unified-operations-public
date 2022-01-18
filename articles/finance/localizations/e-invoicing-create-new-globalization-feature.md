---
# required metadata

title: Create new Globalization feature
description: This topic provides description of the process of new Globalization feature creation.
author: dkalyuzh
ms.date: 12/15/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata
---

# Create new Globalization feature

[!include [banner](../includes/banner.md)]


You can create an **Electronic invoicing feature** from scratch, or you can create it based on another existing feature.
When you create an **Electronic invoicing feature** from scratch, you must manually add ER configurations and other components, such as the **Feature setup** and **Application setup** details. When you create a feature as based from another feature, the new feature inherits all configurations and parameters from the base one as copies. You can review what is the Base feature for the current one.


## Create new feature from scratch

This topic explains how to create a new Electronic invoicing feature when no Globalization feature is available in Global repository for your business scenarios out of the box.

To create a new Electronic invoicing feature, follow the steps:
 1. Sign in to your RCS account.
 2. In the **Globalization feature** workspace, in the **Features** section, select the **Electronic invoicing** tile.
 3. Select **Add**, and then select **New** feature.
 4. Enter a name and description for the Electronic invoicing feature.
 5. Select **Create feature**.
 6. On the right side of the form you will see the first version of your feature in Draft status. Next, you need to add Electronic reporting configurations and Feature setups.

To add a new or existing Electronic reporting format configurations, make sure that the configurations exist in your local RCS repository.
 1. Select the Electronic invoicing feature that you're working on.
 2. On the **Configurations** tab, select **Add**.
 3. In the **Configurations** grid, browse and select format configurations that your Electronic invoicing feature requires to use in Processing pipeline (for example, to generate the electronic invoice file, or process response from external Web services).
 4. Select **OK**.
For more details see [Work with Configurations](e-inv_tut-setup-electronic-invoicing_global-feature_configurations.md). Now you can use this configuration in actions of the Processing pipeline. 

To add a new Electronic invoicing feature setups go to Setups tab and create a new Feature setup as described in the article: [Work with Feature setup](e-inv_tut-setup-electronic-invoicing_global-feature_setup.md).

Complete and deploy the Electronic invoicing feature to the Service environment. For information about how to complete this task, see [Complete, publish and deploy](e-inv_tut-setup-electronic-invoicing_global-feature_complete-publish.md).


### Create new file format configurations that are derived from the existing invoice model

Skip this step if you don't need to create Electronic reporting configuration, but can reuse existing versions as a base.

In this procedure, you will create the file format configurations that are required for the new Electronic invoicing feature that you want to create. You can create the electronic invoice file format configuration and any other file format configurations that your new Electronic invoicing feature might require.

 1. Sign in to your RCS account.
 2. Go to **Electronic reporting** workspace.
 3. Select the **Reporting configurations** tile, and then select the ***Invoice model*** of ***Fiscal model*** (for Brazilian scenarios).
 4. Select **Create configuration**.
 5. Select **Format based on data model Invoice** option.
 6. Enter a name and description for the format configuration.
 7. In the **Format type** field, select the file extension type.
 8. In the **Data model definition** select root structure you will be using for mapping your format to. For example, InvoiceCustomer is used for the formats for customer invoices.
 9. Select **Create configuration**, and then select the format configuration that you created.
 10. Select **Designer**, and use the Format designer tool to configure the file layout so that it meets the file format specifications.
 11. Close the page.
 12. On the **Versions** tab, select **Change status** > **Complete**.
 13. Select **Change status** > **Share** to publish the format configuration to the Global repository.

The new file format configuration must be shared with the Microsoft domain before the configuration can be consumed by the Electronic invoicing service.
 1. Select the format configuration that you're working on. The status of the configuration must be Shared.
 2. On the **Versions** tab, select **Advanced sharing** > **Global repository**.
 3. On the **Shared with** tab, select **Organization**.
 4. In the **Parameters** field, enter **`microsoft.com`** to share the format configuration with the Microsoft domain.
 5. Select **OK**.
	

## Create new feature based on existing one

 1. Make sure that in **Configuration provider** field you have selected your active Configuration provider. In this case you will see new Electronic invoicing feature in the list as soon as it is created, otherwise, it will be filtered out that can confuse you.
 2. Select **Add**, and then, in the drop-down dialog box, select the **Based on existing version** option.
 3. Enter a name and description for the feature.
 4. In the list of available features, select the base version of the feature, and then select Create feature.

	  The feature that you added is created and has a status of Draft.
	
 5. Review the feature components to determine whether updates are required:
   - Review the configurations, in case you need to customize the Electronic reporting (ER) formats and their binding with format mappings for the feature version.
   - Review the setup, in case you need to customize the Actions tab, Applicability rules tab, or Variables tab for the feature version.

Complete and deploy the Electronic invoicing feature to the Service environment. For information about how to complete this task, see [Complete, publish and deploy](e-inv_tut-setup-electronic-invoicing_global-feature_complete-publish.md).
