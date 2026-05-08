---
title: ER Upgrade your format by adopting a new, base version of that format
description: This article describes how to maintain an Electronic reporting (ER) format configuration.
author: kfend
ms.date: 04/09/2026
ms.topic: how-to
audience: Developer, IT Pro
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: ERWorkspace, ERVendorPart, ERSolutionTable, ERSolutionCreateDropDialog, EROperationDesigner, ERComponentTypeDropDialog
---

# ER Upgrade your format by adopting a new, base version of that format

[!include [banner](../../includes/banner.md)]

The following steps explain how a user in the System Administrator or Electronic Reporting Developer role can maintain an Electronic reporting (ER) format configuration. This procedure explains how to create a custom version of a format based on the format received from a configuration provider (CP). It also explains how to adopt a new, base version of that format.

To complete these steps, you must first complete the steps in the "Create a configuration provider and mark it as active" and "Use created format to generate electronic documents for payments" procedures. You can perform these steps in the GBSI company.

## Select format configuration for customization

1. Go to **Organization administration** > **Workspaces** > **Electronic reporting**.

    In this example, sample company Litware, Inc. (<https://www.litware.com>) acts as a configuration provider that supports format configurations for electronic payments for a particular country/region. Sample company Proseware, Inc. (<https://www.proseware.com>) acts as a consumer of the format configuration that Litware, Inc. provided. Proseware, Inc. uses formats in certain regions of that country/region.  
1. Select **Reporting configurations**.
1. Select **Show filters**.
1. Apply the following filters: Enter a filter value of **BACS (UK fictitious)** on the **Name** field by using the **begins with** filter operator.
  
    The selected format configuration **BACS (UK fictitious)** is owned by provider Litware, Inc.  

1. Select **Show filters**.
1. In the list, find and select the desired record.

    Proseware, Inc. uses the version of the format with the status of **Completed** for customization.  

## Create a new configuration for your custom format of electronic document

Proseware, Inc. receives version 1.1 of BACS (UK fictitious) configuration that contains the initial format to generate electronic payment documents from Litware, Inc. in accordance with their service subscription. Proseware, Inc. wants to start using this format as a standard for their country/region but some customization is required to support specific regional requirements. Proseware, Inc. also wants to keep the ability to upgrade a custom format as soon as a new version of it (with changes to support new country/region-specific requirements) comes from Litware, Inc. They want to perform this upgrade with the lowest cost.  

To do this upgrade, Proseware, Inc. needs to create a configuration by using the Litware, Inc. configuration BACS (UK fictitious) as a base.  

1. Close the page.
1. Select Proseware, Inc. to make it an active provider.
1. Select **Set active**.
1. Select **Reporting configurations**.
1. In the tree, expand **Payments (simplified model)**.
1. In the tree, select **Payments (simplified model)\BACS (UK fictitious)**.

    Select the BACS (UK fictitious) configuration from Litware, Inc. Proseware, Inc. uses version 1.1 as a base for the custom version.  

1. Select **Create configuration** to open the drop dialog.

    This step lets you create a new configuration for a custom payment format.  

1. In the **New** field, enter `Derive from Name: BACS (UK fictitious), Litware, Inc.`.

    Select the **Derive** option to confirm the usage of BACS (UK fictitious) as the base for creating the custom version.  

1. In the **Name** field, type `BACS (UK fictious custom)`.
1. In the **Description** field, type `BACS vendor payment (UK fictitious custom)`.

    The active configuration provider (Proseware, Inc.) is automatically entered here. This provider can maintain this configuration. Other providers can use this configuration, but can't maintain it.  

1. Select **Create configuration**.

## Customize your format for the electronic document

1. Select **Designer**.
1. Select **Expand/collapse**.
1. Select **Expand/collapse**.
1. In the tree, select `Xml\Message\Payments\Item\Vendor\Bank`.
1. Select **Add** to open the drop dialog.
1. In the tree, select `XML\Element`.
1. In the **Name** field, type `IBAN`.
1. Select **OK**.
1. In the tree, select `Xml\Message\Payments\Item\Vendor\Bank\IBAN`.
1. Select **Add** to open the drop dialog.
1. In the tree, select `Text\String`.
1. Select **OK**.
1. In the tree, select `Xml\Message\Payments\Item\Vendor\Name\String`.
1. In the **Maximum length** field, enter `60`.
1. Select the **Mapping** tab.
1. In the tree, expand `model`.
1. In the tree, expand `model\Payments`.
1. In the tree, expand `model\Payments\Creditor`.
1. In the tree, expand `model\Payments\Creditor\Account`.
1. In the tree, select `model\Payments\Creditor\Account\IBAN`.
1. In the tree, select `Xml\Message\Payments\Item =  model.Payments\Vendor\Bank\IBAN\String`.
1. Select **Bind**.
1. Select **Save**.

## Validate the customized format

1. Select **Validate**.

    Validate the customized format layout and data mapping changes to make sure that all bindings are correct.  

1. Close the page.

## Change the status of the current version of the custom format configuration

Change the status of the designed format configuration from **Draft** to **Completed** to make it available for payment document generation.  

1. Select **Change status**.

    The current version of the selected configuration is in **Draft** status.  

1. Select **Complete**.
1. In the **Description** field, enter a value.
1. Select **OK**.
1. In the list, find and select the desired record.

    The created configuration is saved as **completed version 1.1.1**. This version means it's version 1 of the custom BACS (UK fictitious custom) format, which is based on version 1 of the BACS (UK fictitious) format, which is based on version 1 of the Payments (simplified model) data model.    

## Test the customized format to generate payment files

Complete the steps in the "Use created format to generate electronic documents for payments" procedure in a parallel finance and operations session. Select the BACS (UK fictitious custom) format in electronic payment method parameters. Make sure that the created payment file contains the recently introduced XML node presenting IBAN code in accordance to regional requirements.  

## Update the existing country/region-specific configuration

Litware, Inc. needs to update the BACS (UK fictitious) configuration and adopt new country/region requirements for managing the format of the electronic document. Later, Litware, Inc. encloses this configuration in a new version that it offers to service subscribers, including Proseware, Inc.  

In real service provision related processes, Proseware, Inc. can import each new version of BACS (UK fictitious) from Litware, Inc. configurations' LCS repository. In this procedure, you simulate this process by updating BACS (UK fictitious) on behalf of a service provider.  

1. Close the page.
1. Select Litware, inc. provider.
1. Select **Set active**.
1. Select **Reporting configurations**.
1. In the tree, expand **Payments (simplified model)**.
1. In the tree, select **Payments (simplified model)\BACS (UK fictitious)**.

    The draft version owned by Litware, Inc. provider BACS (UK fictitious) is selected to bring in changes to support new country/region-specific requirements.  

## Localize the base format of the electronic document

Assume that Litware, Inc. needs to support new country or region-specific requirements:  

- A value for the creditor's bank SWIFT code in each payment transaction.
- A limit of 100 characters for the length of text for the vendor's name in a generating file.  
- New country or region-specific requirements.  
- Select the draft version of the desired configuration to introduce required changes.  

1. Select **Designer**.
1. Select **Expand/collapse**.
1. Select **Expand/collapse**.
1. In the tree, select `Xml\Message\Payments\Item\Vendor\Bank`.
1. Select **Add** to open the drop dialog.
1. In the tree, select `XML\Element`.
1. In the **Name** field, type `SWIFT`.
1. Select **OK**.
1. In the tree, select `Xml\Message\Payments\Item\Vendor\Bank\SWIFT`.
1. Select **Add** to open the drop dialog.
1. In the tree, select `Text\String`.
1. Select **OK**.
1. In the tree, select `Xml\Message\Payments\Item\Vendor\Name\String`.
1. In the **Maximum length** field, enter `100`.
1. Select the **Mapping** tab.
1. In the tree, expand `model`.
1. In the tree, expand `model\Payments`.
1. In the tree, expand `model\Payments\Creditor`.
1. In the tree, expand `model\Payments\Creditor\Agent`.
1. In the tree, select `model\Payments\Creditor\Agent\SWIFT`.
1. In the tree, select `Xml\Message\Payments\Item =  model.Payments\Vendor\Bank\SWIFT\String`.
1. Select **Bind**.
1. Select **Save**.

## Validate the localized format

1. Select **Validate**.
1. Close the page.

## Change the status of the current version of the base format configuration

Change the status of the updated base format configuration from **Draft** to **Completed** to make it available for generating payment documents and updating format configurations derived from it.  

1. Select **Change status**.

    The current version of the selected configuration is in **Draft** status.  

1. Select **Complete**.
1. In the **Description** field, enter a value.
1. Select **OK**.
1. In the list, find and select the desired record.

## Change the base version for the custom format configuration

Proseware, Inc. is informed that a new version 1.2 of BACS (UK fictitious) configuration is available to generate electronic payment documents in accordance with recently announced country/region-specific requirements. Proseware, Inc. wants to start using it as a standard for the country/region.  

To do this, Proseware, Inc. needs to change the base configuration version for the custom configuration BACS (UK fictitious custom). Instead of version 1.1 of BACS (UK fictitious), use new version 1.2.  

1. Go to **Organization administration** > **Workspaces** > **Electronic reporting**.
1. Select the Proseware, Inc. provider to mark it as active.
1. Select **Set active**.
1. Select **Reporting configurations**.
1. In the tree, expand **Payments (simplified model)**.
1. In the tree, expand **Payments (simplified model)\BACS (UK fictitious)**.
1. In the tree, select **Payments (simplified model)\BACS (UK fictitious)\BACS (UK fictitious custom)**.

    Select the BACS (UK fictitious custom) configuration, which Proseware, Inc. owns.  

    Use the draft version of the selected configuration to introduce required changes.  

1. Select **Rebase**.

    Select the new version 1.2 of the base configuration to apply as a new base for updating the configuration.  

1. Select **OK**.

    The system discovers some conflicts between merging the custom version and a new base version. These conflicts represent some format changes that can't be merged automatically.  

## Resolve rebase conflicts

1. Select **Designer**.

    The system can't automatically resolve changes to the vendor's name text length limit. Therefore, the system presents this change in a conflicts list. For each conflict of type **Update**, you see the following options:  

    - **Apply a prior base value** (button on top of the grid): Bring in the previous base version value (0 in this case).  

- **Apply a base value** (button on top of the grid): Bring in the new base version value (100 in this case).

    - **Keep your own (custom) value** (60 in this case).  

1. Select **Save**.

    Saving the format will remove resolved conflicts from the conflicts list.  

1. Close the page.

## Change the status of the new version of the custom format configuration

1. Select **Change status**.

    Change the status of the updated custom format configuration from **Draft** to **Completed**. This change makes the format configuration available for generating payment documents. The current version of the selected configuration is in **Draft** status.  

1. Select **Complete**.
1. In the **Description** field, enter a value.
1. Select **OK**.

    The created configuration is saved as completed version 1.2.2: version 2 of base BACS (UK fictitious custom) format, which is based on version 2 of base BACS (UK fictitious) format, which is based on version 1 of Payments (simplified model) data model.    

## Test the customized format for payment files generation

Complete the steps in the "Use created format to generate electronic documents for payments" procedure in parallel finance and operations session. Select the created **BACS (UK fictitious custom)** format in electronic payment method parameters. Make sure that the created payment file contains recently introduced by Proseware, Inc. XML node presenting IBAN account code in accordance to regional requirements. The file also should contain the recently introduced by Litware, Inc. XML node presenting SWIFT bank code in accordance to country/region requirements.  

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
