--- 
# required metadata 
 
title: Create predefined product variants
description: This procedure walks through creating product variants for a product master using the combinations of product dimensions. 
author: t-benebo 
ms.date: 04/22/2021

ms.topic: business-process 
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

This example scenario shows how to create product variants for a product master using a combinations of product dimensions.

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

- **Deferred generation of variant suggestions:** The **Variant suggestions** page no longer shows suggestions when you first open it. Instead, you must explicitly choose which values you will need and then select the **Suggest** button to generate the combinations. This makes the process more visible and interactive.
- **Selection of dimensions values:** When you have many dimension values, you are typically interested in generating variant suggestions that include just a few of them (such as when introducing a new set of colors or styles). With the improved design, you can select the dimension values for which you want to generate product variant suggestions. This greatly increases the relevance of the suggested variants and improves both system performance and user productivity.

### Turn on the Variant suggestions page improvements feature

Before you can use *Variant suggestions page improvements* feature, it must be turned on in your system. Admins can use the [feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the status of the feature and turn it on. In the **Feature management** workspace, the feature is listed in the following way:

- **Module:** *Product information management*
- **Feature name:** *Variant suggestions page improvements*

### Work with the improved variant suggestions

To generate product variant suggestions when the *Variant suggestions page improvements* feature is enabled:

1. Open or create a product master and add the required product dimensions to it, as described in the previous section.
1. With the product master open, select **Product variants** on the Action Pane.
1. Select **Variant suggestions** on the Action Pane.
1. Select the values that you want to use for each of the dimensions.
1. On the top toolbar, select **Suggest**.
1. The system generates a list with all possible combinations of the sizes and colors you selected. On the **Suggested variants** FastTab, select the check box for each product dimension combination that you want to use, or select **Select all** on the toolbar to select all of them.  
1. Select **Create** to add the variants to the current product master.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
