---
title: ER Upgrade your format by adopting a new, base version of that format
description: This article describes how to maintain an Electronic reporting (ER) format configuration.
author: kfend
ms.date: 08/29/2018
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: ERWorkspace, ERVendorPart, ERSolutionTable, ERSolutionCreateDropDialog, EROperationDesigner, ERComponentTypeDropDialog
---
# ER Upgrade your format by adopting a new, base version of that format

[!include [banner](../../includes/banner.md)]

The following steps explain how a user in the System Administrator or Electronic Reporting Developer role can maintain an Electronic reporting (ER) format configuration. This procedure explains how a custom version of a format can be created based on the format received from a configuration provider (CP). It also explains how to adopt a new, base version of that format.

To complete these steps, you must first complete the steps in the "Create a configuration provider and mark it as active" and "Use created format to generate electronic documents for payments" procedures. These steps can be performed in the GBSI company.

## Select format configuration for customization
1. Go to Organization administration > Workspaces > Electronic reporting.

    In this example, sample company Litware, Inc. (https://www.litware.com) will act as a configuration provider that supports format configurations for electronic payments for a particular country/region.    Sample company Proseware, Inc. (http://www.proseware.com) will act as a consumer of the format configuration that Litware, Inc. provided. Proseware, Inc. uses formats in certain regions of that country/region.  
2. Click Reporting configurations.
3. Click Show filters.
4. Apply the following filters: Enter a filter value of "BACS (UK fictitious)" on the "Name" field using the "begins with" filter operator.
  
    The selected format configuration BACS (UK fictitious) is owned by provider Litware, Inc.  

5. Click Show filters.
6. In the list, find and select the desired record.

    The version of the format with the status of Completed will be used by Proseware, Inc. for customization.  

## Create a new configuration for your custom format of electronic document
Proseware, Inc. received version 1.1 of BACS (UK fictitious) configuration that contains the initial format to generate electronic payment documents from Litware, Inc. in accordance to their service subscription. Proseware, Inc. wants to start using this as a standard for their country/region but some customization is required to support specific regional requirements. Proseware, Inc. also wants to keep the ability to upgrade a custom format as soon as a new version of it (with changes to support new country/region-specific requirements) comes from Litware, Inc. and they want to perform this upgrade with the lowest cost.  

To do this, Proseware, Inc. needs to create a configuration using the Litware, Inc. configuration BACS (UK fictitious) as a base.  

1. Close the page.
2. Select Proseware, Inc. to make it an active provider.
3. Click Set active.
4. Click Reporting configurations.
5. In the tree, expand 'Payments (simplified model)'.
6. In the tree, select 'Payments (simplified model)\BACS (UK fictitious)'.

    Select the BACS (UK fictitious) configuration from Litware, Inc. Proseware, Inc. will use version 1.1 as a base for the custom version.  

7. Click Create configuration to open the drop dialog.

    This lets you create a new configuration for a custom payment format.  

8. In the New field, enter 'Derive from Name: BACS (UK fictitious), Litware, Inc.'.

    Select the Derive option to confirm the usage of BACS (UK fictitious) as the base for creating the custom version.  

9. In the Name field, type 'BACS (UK fictitious custom)'.
10. In the Description field, type 'BACS vendor payment (UK fictitious custom)'.

    The active configuration provider (Proseware, Inc.) is automatically entered here. This provider will be able to maintain this configuration. Other providers can use this configuration, but will not be able to maintain it.  

11. Click Create configuration.

## Customize your format for the electronic document
1. Click Designer.
2. Click Expand/collapse.
3. Click Expand/collapse.
4. In the tree, select 'Xml\Message\Payments\Item\Vendor\Bank'.
5. Click Add to open the drop dialog.
6. In the tree, select 'XML\Element'.
7. In the Name field, type 'IBAN'.
8. Click OK.
9. In the tree, select 'Xml\Message\Payments\Item\Vendor\Bank\IBAN'.
10. Click Add to open the drop dialog.
11. In the tree, select 'Text\String'.
12. Click OK.
13. In the tree, select 'Xml\Message\Payments\Item\Vendor\Name\String'.
14. In the Maximum length field, enter '60'.
15. Click the Mapping tab.
16. In the tree, expand 'model'.
17. In the tree, expand 'model\Payments'.
18. In the tree, expand 'model\Payments\Creditor'.
19. In the tree, expand 'model\Payments\Creditor\Account'.
20. In the tree, select 'model\Payments\Creditor\Account\IBAN'.
21. In the tree, select 'Xml\Message\Payments\Item =  model.Payments\Vendor\Bank\IBAN\String'.
22. Click Bind.
23. Click Save.

## Validate the customized format
1. Click Validate.

    Validate the customized format layout and data mapping changes to make sure that all bindings are okay.  

2. Close the page.

## Change the status of the current version of the custom format configuration
Change the status of the designed format configuration from Draft to Completed to make it available for payment document generation.  

1. Click Change status.

    Note that the current version of the selected configuration is in Draft status.  

2. Click Complete.
3. In the Description field, type a value.
4. Click OK.
5. In the list, find and select the desired record.

    Note that the created configuration is saved as completed version 1.1.1. This means it is version 1 of the custom BACS (UK fictitious custom) format, which is based on version 1 of the BACS (UK fictitious) format, which is based on version 1 of the Payments (simplified model) data model.  

## Test the customized format to generate payment files
Complete the steps in the "Use created format to generate electronic documents for payments" procedure in a parallel finance and operations session. Select the BACS (UK fictitious custom) format in electronic payment method parameters. Make sure that the created payment file contains the recently introduced XML node presenting IBAN code in accordance to regional requirements.  

## Update the existing country/region-specific configuration
Litware, Inc. needs to update the BACS (UK fictitious) configuration and adopt new country/region requirements for managing the format of the electronic document. Later, this will be enclosed in a new version of this configuration that will be offered for service subscribers, including Proseware, Inc.  

In real service provision related processes, each new version of BACS (UK fictitious) can be imported by Proseware, Inc. from Litware, Inc. configurations' LCS repository. In this procedure we will simulate this by updating BACS (UK fictitious) on behalf of a service provider.  

1. Close the page.
2. Select Litware, inc. provider.
3. Click Set active.
4. Click Reporting configurations.
5. In the tree, expand 'Payments (simplified model)'.
6. In the tree, select 'Payments (simplified model)\BACS (UK fictitious)'.

    The draft version owned by Litware, Inc. provider BACS (UK fictitious) is selected to bring in changes to support new country/region-specific requirements.  

## Localize the base format of the electronic document
Assume that there are new country/region-specific requirements to be supported by Litware, Inc.:  

- A value for the creditor's bank SWIFT code in each payment transaction.
- A limit of 100 characters for the length of text for the vendor's name in a generating file.  
- New country/region-specific requirements  
- Select the draft version of the desired configuration to introduce required changes.  


1. Click Designer.
2. Click Expand/collapse.
3. Click Expand/collapse.
4. In the tree, select 'Xml\Message\Payments\Item\Vendor\Bank'.
5. Click Add to open the drop dialog.
6. In the tree, select 'XML\Element'.
7. In the Name field, type 'SWIFT'.
8. Click OK.
9. In the tree, select 'Xml\Message\Payments\Item\Vendor\Bank\SWIFT'.
10. Click Add to open the drop dialog.
11. In the tree, select 'Text\String'.
12. Click OK.
13. In the tree, select 'Xml\Message\Payments\Item\Vendor\Name\String'.
14. In the Maximum length field, enter '100'.
15. Click the Mapping tab.
16. In the tree, expand 'model'.
17. In the tree, expand 'model\Payments'.
18. In the tree, expand 'model\Payments\Creditor'.
19. In the tree, expand 'model\Payments\Creditor\Agent'.
20. In the tree, select 'model\Payments\Creditor\Agent\SWIFT'.
21. In the tree, select 'Xml\Message\Payments\Item =  model.Payments\Vendor\Bank\SWIFT\String'.
22. Click Bind.
23. Click Save.

## Validate the localized format
1. Click Validate.
2. Close the page.

## Change the status of the current version of the base format configuration
Change the status of the updated base format configuration from Draft to Completed to make it available for generation of payment documents and updates of format configurations derived from it.  

1. Click Change status.

    Note that the current version of the selected configuration is in Draft status.  

2. Click Complete.
3. In the Description field, type a value.
4. Click OK.
5. In the list, find and select the desired record.

## Change the base version for the custom format configuration

Proseware, Inc. is informed that a new version 1.2 of BACS (UK fictitious) configuration is available to generate electronic payment documents in accordance to recently announced country/region-specific requirements. Proseware, Inc. wants to start using it as a standard for the country/region.  

To do this, Proseware, Inc. needs to change the base configuration version for the custom configuration BACS (UK fictitious custom). Instead of version 1.1 of BACS (UK fictitious) use new version 1.2.  

1. Go to Organization administration > Workspaces > Electronic reporting.
2. Select the Proseware, Inc. provider to mark it as active.
3. Click Set active.
4. Click Reporting configurations.
5. In the tree, expand 'Payments (simplified model)'.
6. In the tree, expand 'Payments (simplified model)\BACS (UK fictitious)'.
7. In the tree, select 'Payments (simplified model)\BACS (UK fictitious)\BACS (UK fictitious custom)'.

    Select the BACS (UK fictitious custom) configuration, which is owned by Proseware, Inc.  

    Use the draft version of the selected configuration to introduce required changes.  

8. Click Rebase.

    Select the new version 1.2 of the base configuration to be applied as a new base for updating the configuration.  

9. Click OK.

    Note that some conflicts have been discovered between merging the custom version and a new base version representing some format changes that can't be merged automatically.  

## Resolve rebase conflicts
1. Click Designer.
    
    Note that changes to the vendor's name text length limit couldn't be resolved automatically. Therefore, this is presented in a conflicts list. For each conflict of type Update, the following options are available:  - Apply a prior base value (button on top of the grid) to bring in the previous base version value (0 in our case).  - Apply a base value (button on top of the grid) to bring in the new base version value (100 in our case).  - Keep your own (custom) value (60 in our case).  Click Apply base value to apply a country/region-specific limit of 100 characters for vendor's name text length.  

    Note that Proseware, Inc. and Litware, Inc. have custom and local versions of this format using IBAN and SWIFT codes with related components that are automatically merged in the managing format.  

2. Click Apply base value.

    Click Apply base value to apply the country/region-specific limit of 100 characters for vendor names.  

3. Click Save.

    Saving the format will remove resolved conflicts from the conflicts list.  

4. Close the page.

## Change the status of the new version of the custom format configuration
1. Click Change status.

    Change the status of the updated, custom format configuration from Draft to Completed. This will make the format configuration available for generating payment documents. Note that the current version of the selected configuration is in Draft status.  

2. Click Complete.
3. In the Description field, type a value.
4. Click OK.

    Note that the created configuration is saved as completed version 1.2.2: version 2 of base BACS (UK fictitious custom) format, which is based on version 2 of base BACS (UK fictitious) format, which is based on version 1 of Payments (simplified model) data model.  

## Test the customized format for payment files generation
Complete the steps in the "Use created format to generate electronic documents for payments" procedure in parallel finance and operations session. Select the created 'BACS (UK fictitious custom)' format in electronic payment method parameters. Make sure that the created payment file contains recently introduced by Proseware, Inc. XML node presenting IBAN account code in accordance to regional requirements. The file also should contain the recently introduced by Litware, Inc. XML node presenting SWIFT bank code in accordance to country/region requirements.  



[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
