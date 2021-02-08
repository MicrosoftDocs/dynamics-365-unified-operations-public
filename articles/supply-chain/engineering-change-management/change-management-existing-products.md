---
# required metadata

title: Enable change management on existing products
description: This topic explains how you can enable change management on existing products and the restrictions on the cases where you are able to do so
author: t-benebo
manager: tfehr
ms.date: 02/05/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form:  EngChgProductAttributeSearch, EngChgMaintainAttributeInheritance, EngChgAttribute
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: benebotg
ms.search.validFrom: 2021-05-02
ms.dyn365.ops.version: Release 10.0.17
---

# Enable change management on existing products

[!include [banner](../includes/banner.md)]

This topic explains how to enable change management on existing products and the restrictions that apply to your ability to do so.

When you enable change management on an existing product, you will be able to version that product and trace its changes throughout its life so you will be able to track those change with change orders. To enable this, you must convert the relevant products to *engineering items* (which are products that are versioned and managed with change management). A wizard is provided to help guide you through the process.

## Enable this feature on your system

To use this capability, you must do the following:

1. Enable the Engineering change management feature and its configuration key as described in the [Engineering change management overview](product-engineering-overview.md).
1. Turn on the *Enable change management on existing products* feature in feature management. (See also the [Feature management overview](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md)).

## Restrictions and limitations

<!-- KFM: I think customers will be concerned about this. If possible, we should be specific and complete, not just give examples. -->

Some restrictions apply in terms of which types of product can be converted to which other types. For example, if changing a product, the product will remain a product <!-- KFM: I don't understand this -->. In the case of a product master with a specific set of dimensions, those dimensions will be maintained after the change.

This means that if you have a distinct product, you will be able to change it to an engineering product that does not track the product dimension in transactions (the version dimension isn't used).

Another example is that if you want to change a product master with the size dimension <!-- KFM: I think something is missing here. -->

## Prepare for conversion by creating all required engineering product categories

Each engineering product must be assigned an *engineering product category*. You will assign this when you run the convert to engineering product wizard. The engineering product category provides a basis for creating an engineering product and establishes a set of default values and policies. The engineering category must match the product you assign it to. For example, the product type and dimension group must match both the product and its engineering category. More information: [Engineering versions and engineering product categories](engineering-versions-product-category.md)

Therefore, a engineering categories must exist for each relevant standard product *before* you can convert those products. 

> [!IMPORTANT]
> Because the wizard can only convert to engineering products where the version is not tracked in transactions, the engineering categories that you create for converting existing products must have their **Track version in transactions** option set to *No*.

For instructions about how to create engineering product categories, see [Engineering versions and engineering product categories](engineering-versions-product-category.md).

## Run the convert to engineering product wizard

The *convert to engineering product wizard* helps you convert one or more existing products into engineering products. Once converted, you'll be able to manage these products using Engineering Change Management. This conversion is permanent, so you won't be able to revert it later. The wizard will convert the product into an engineering product (a versioned product) where the version is not tracked in transactions (the version dimension isn't used).

After the conversion, each converted engineering product will still be released in the same companies as the original product was. However, the engineering bill of materials (BOM) and routes won't automatically be released to those companies. 

To convert a product to an engineering item, you must run the convert to engineering product wizard as follows:

1. Go to **Product information management \> Products \> Released products**.
1. On the grid, select the check box for each product that you want to convert for now.
1. On the Action Pane, open the **Engineer** tab and then, from the **Engineering change management** group, select **Convert to engineering product**.
1. The **Convert to engineering product** wizard launches, open to the **Welcome** page. If you aren't already familiar with the process, then read the information shown here carefully. Select **Next** to continue.
1. The **Select details for the products to be converted** page opens, showing each of the products you had selected before launching the wizard. Inspect the list and, if necessary, use the **New** and/or **Delete** commands in the toolbar to add or remove a product.
1. Use the fields at the top of the grid to establish default values for each listed item (you'll be able to change these for each specific item as needed afterwards). Defaults will not be applied to products where a relevant value has already been assigned. See the next step for more information about each of these settings. The following fields are available for establishing defaults in the grid:
    - **Default engineering category** - Select an initial engineering category to assign to each listed product. The category you choose here will only be applied to those products that are compatible with it.
    - **Default version** - Enter an initial product version to assign to each listed product. When you use engineering products, each product has at least one engineering version.
    - **Default lifecycle state** - Select an initial product lifecycle state to assign to each listed product.
    - **Current BOM will be part of the engineering product** - Select this check box if each product should use its current bill of materials (BOM) as a BOM for the engineering product.

1. Review each product listed in the grid and consider whether the default values you selected (if any) really do apply to each product. For each row, review the following information and make relevant settings:
    - **Product number** - Shows the product number.
    - **Product name** - Shows the name of the product.
    - **Engineering category** - Select the engineering category that the product should belong to after being converted. An appropriate category must already exist for each product (see the previous section for details). You must assign this for each product.
    - **Version** - Enter the product version to assign to the product after being converted. For example, you might select a number that fits with the number sequence already used by your category. The default will not be applied if a value has already been specified. <!-- KFM: Typically start with 1.0? Any advice? --> When you use engineering products, each product has at least one engineering version. Each engineering version stores the engineering-relevant data that is specific to that version. More information: [Engineering versions and engineering product categories](engineering-versions-product-category.md)
    - **Product lifecycle state** - Select the product lifecycle state that the product should be in after being converted.  The product lifecycle state enables you to control which transactions are allowed for a given engineering version. More information: [Product lifecycle states and transactions](product-lifecycle-state-transactions.md).
    - **Has BOM** - Shows a check mark if the product has a BOM. This will help you decide how to set the **Current BOM will be part of the engineering product** option.
    - **Current BOM will be part of the engineering product** - Select this check box if the product should use its current bill of materials (BOM) as a BOM for the engineering product. This BOM will then be managed by Engineering Change Management. Clear this check box for products that don't have a BOM, or if you prefer to manually create a BOM for the converted product later.
    - **Has errors** - Shows a check mark if the product setup has one or more errors (for example, if the product type or the dimension group don't match in the category). Products that have errors will be skipped and won't be converted.

1. When you are done making settings, select **Validate** from the toolbar to check them. For each row, the **Has errors** check box will update to indicate its status. Adjust your settings until all products are free of errors.
1. When all of your products are set up correctly, select Next to continue.
1. The **Confirm selection** page opens. Here you can read how many products are ready to be converted (and therefore show no errors) and how many were skipped (due to errors). Set **Run in batch** to *Yes* to perform the conversion using the batch engine; set it to *No* to perform the conversion right away. <!-- KFM: Please confirm this description of **Run in batch** -->
1. Select **Finish** to apply your settings and start converting the products.

> [!NOTE]
> If your system is set up to manually accept products before they are released, you must accept each converted product using the **Open product releases** page in the respective companies. See also [Review and accept the product before you release it in the local company](engineering-scenarios.md#accept).
