--- 
# required metadata 
 
title: Create predefined product variants
description: This procedure walks through creating product variants for a product master using the combinations of product dimensions. 
author: t-benebo 
ms.date: 08/09/2022

ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: EcoResProductListPage, EcoResProductCreate, EcoResProductDetails, EcoResProductMasterDimension, EcoResProductVariants, EcoResProductVariantSuggestions, EcoResProductVariantsPendingReleaseFormPart, EcoResProductVariantSuggestionsEnhanced 
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: benebotg
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: 10.0.19
---
# Predefined product variants

[!include [banner](../../includes/banner.md)]

## Example scenario: Create predefined product variants

This example scenario shows how to create product variants for a product master using a combination of product dimensions.

### Make demo data available

To follow this scenario using the values suggested here, you must have demo data installed, and you must select the *USMF* legal entity.

### Step 1: Create a product master

To create a product master:

1. Go to **Product information management > Products > Product masters**.
1. Select **New**.
1. If the **Product number** field doesn't already show a number, then enter a value. This is only required if no number sequence has been set for this field.
1. Enter a name in the **Product name** field.
1. In the **Product dimension group** field, select the product dimension group *SizeCol* (Size and Color).
1. Select **OK** to create and open the new product master.

### Step 2: Add product dimensions

This example shows how to manually enter product dimensions. You can also choose to select a size, color, or style group that includes the product dimension values you want to use.

To add product dimensions:

1. With your new product master still open, select **Product dimensions** on the Action Pane.
1. Open the **Size** tab and select **New** on the toolbar to add a row to the grid. Make the following settings for the new row:
    - **Size:** Select a size value.
    - **Name:** Enter a name for the size.
1. Select **New** on the toolbar and add a second size to the grid with a new **Size** and **Name**.
1. Open the **Colors** tab and select **New** on the toolbar to add a row to the grid. Make the following settings for the new row:
    - **Color:** Select a color value.
    - **Name:** Enter a name for the color.
1. Select **New** on the toolbar and add a second color to the grid with a new **Color** and **Name**.
1. Select **Save**.
1. Close the page to return to your new product master.

### Step 3: Generate product variants

> [!NOTE]
> This section describes how to generate product variants when the *Variant suggestions page improvements* feature isn't enabled. See the next section for details about how to generate product variants when that feature is available.

To generate product variants:

1. With your new product master still open, select **Product variants** on the Action Pane.
1. Select **Variant suggestions** on the Action Pane.
1. The system generates a list with all possible combinations of the sizes and colors you defined for the product. Select **Select all** on the toolbar.
    - In this example, select all of the possible variants. If you only want to use a subset of the possible product dimension combinations, select only the required check boxes as needed.  
1. Select **Create**.
1. Select **Save**.

## Improved variant suggestions

The *Variant suggestions page improvements* feature improves the **Variant suggestions** page to address performance and usability issues for companies that have a high number of product dimension combinations. The enhanced process for selecting the product dimension values for which to generate variant suggestions makes it faster and easier to identify and release the relevant set of product variants.

The following improvements are added by this feature:

- **Deferred generation of variant suggestions:** The **Variant suggestions** page no longer shows suggestions when you first open it. Instead, you must explicitly choose which values you'll need and then select the **Suggest** button to generate the combinations. This makes the process more visible and interactive.
- **Selection of dimensions values:** When you have many dimension values, you're typically interested in generating variant suggestions that include just a few of them (such as when introducing a new set of colors or styles). With the improved design, you can select the dimension values for which you want to generate product variant suggestions. This greatly increases the relevance of the suggested variants and improves both system performance and user productivity.

### Turn the Variant suggestions page improvements feature on or off

To use this feature, it must be turned on for your system. As of Supply Chain Management version 10.0.25, the feature is turned on by default. As of Supply Chain Management version 10.0.29, the feature is mandatory and can't be turned off. If you're running a version older than 10.0.29, then admins can turn this functionality on or off by searching for the *Variant suggestions page improvements* feature in the [Feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace.

### Work with the improved variant suggestions

To generate product variant suggestions when the *Variant suggestions page improvements* feature is enabled:

1. Open or create a product master and add the required product dimensions to it, as described in the previous section.
1. With the product master open, select **Product variants** on the Action Pane.
1. Select **Variant suggestions** on the Action Pane.
1. Select the values that you want to use for each of the dimensions.
1. On the top toolbar, select **Suggest**.
1. The system generates a list with all possible combinations of the sizes and colors you selected. On the **Suggested variants** FastTab, select the check box for each product dimension combination that you want to use, or select **Select all** on the toolbar to select all of them.  
1. Select **Create** to add the variants to the current product master.

## Set up variant-specific sales tax groups for sales and/or procurement

[!INCLUDE [preview-banner-section](../../../includes/preview-banner-section.md)]

The *Apply sales tax group for product variants in sales and procurement* feature lets you assign variant-specific item sales tax groups both for sales and for procurement. The feature applies the following rules:

- If a specific item sales tax group is assigned to a released product variant for sales, that group is used by default when a sales quotation or sales order line is created.
- If no specific item sales tax group is assigned to a released product variant for sales, the item sales tax group that's assigned to the released product master is used by default when a sales quotation or sales order line is created.
- In a similar way, for purchase orders, purchase requisitions, and requests for quotation, if a specific item sales tax group is assigned to a released product variant for procurement, that group is used by default. If no specific item sales tax group is assigned to a released product variant, the item sales tax group that's assigned to the product master is used by default.

This functionality allows for a setup where most released product variants use the item sales tax groups of the product master setup, but a few variants instead use an alternative item sales tax group by default. Therefore, this functionality helps eliminate the cost, pain, and risk that can occur when incorrect taxation is applied to an order line for a product variant.

### Turn the Apply sales tax group for product variants in sales and procurement feature on or off

This feature requires Supply Chain Management version 10.0.34 or later.

To use this feature, it must be enabled for your system. Admins can turn this functionality on or off by searching for the *Apply sales tax group for product variants in sales and procurement* feature in the [Feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) workspace.

### Assign an item sales tax group to a released product variant

To assign variant-specific item sales tax groups, follow these steps.

1. Go to **Product information management \> Products \> Released products**.
1. Open the product that you want to set up variant-specific item sales tax groups for.
1. On the **Released product details** page, you can view the default item sales tax groups for the master product and edit them as required. These default groups will apply to all variants that you don't assign a variant-specific item sales tax group to for sales and/or procurement.

    - To specify the default item sales tax group that's used when product variants for this master are purchased, set the **Item sales tax group** field on the **Purchase** FastTab.
    - To specify the default item sales tax group that's used when product variants for this master are sold, set the **Item sales tax group** field on the **Sell** FastTab.

1. On the Action Pane, on the **Product** tab, select **Released product variants**.
1. On the **Released products variants** page, find the variant that you want to set up, and open it by selecting the link in the **Product number** column.

    - To specify the default item sales tax group that's used when the selected variant is purchased, set the **Item sales tax group** field on the **Purchase** FastTab.
    - To specify the default item sales tax group that's used when the selected variant is sold, set the **Item sales tax group** field on the **Sell** FastTab.

You can now create a sales order line, sales quotation line, purchase requisition line, purchase order line, or request for quotation line. Notice that the default item sales tax group for the product variant is entered from the variant setup, not from the product master setup.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
