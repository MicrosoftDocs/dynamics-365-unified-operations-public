---
# required metadata

title: Manage product categories and products
description: Learn how merchandising managers can use product categories to manage relationships between the product hierarchies and released product details in Microsoft Dynamics 365 Commerce.
author: ashishmsft
ms.date: 01/16/2026
ms.topic: how-to
ms.search.form: EcoResCategorySearchList, EcoResAttribute, COODualUseCategories, EcoResProductCategory, EcoResCategoryAddProduct, EcoResAttributeValue
ms.reviewer: v-cgriffinc
ms.assetid: c7ed2ba5-87c6-4d99-9728-2a83e6d95ca9
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2017-09-01
ms.custom: 
  - bap-template
---

# Manage product categories and products

[!include [banner](./includes/banner.md)]

This article describes how merchandising managers can use product categories to manage relationships between the product hierarchies and released product details in Microsoft Dynamics 365 Commerce.

Dynamics 365 Commerce allows merchandising managers to view a structure of product properties that the product hierarchy and released product details share.

To learn more about managing product categories, in the **Category and product management** workspace of Commerce headquarters, select the **Commerce product hierarchy** tile.

Notice the enhanced structure of the **Commerce product hierarchy** page. In previous versions of the app, product properties were divided into *basic product properties* and *Retail product properties*, based on the scope of their applicability. Retail product properties are *global* in their scope of applicability. In other words, for a given product property, all legal entities share the same value. By contrast, basic product properties are *legal entity–specific*. In other words, for a given basic product property, the value can differ across legal entities, depending on the individual business requirements of each legal entity.

In the enhanced product category structure, product properties are logically separated into groups based on their applicability to reflect the structure of the released product details form.

:::image type="content" source="media/NoticeGroupingOfFieldsBasedOnTheirScope.PNG" alt-text="Screenshot of fields grouped based on the properties' scope of applicability.":::

You can switch between managing legal entity–specific properties across all legal entities and managing them for a specific legal entity.

To manage properties across all legal entities, select **View for all legal entities** (or **Edit for all legal entities**).

:::image type="content" source="media/ToggleBackToEditForSpecificLegalEntity.PNG" alt-text="Screenshot of the View/Edit for all legal entities option.":::

To manage properties for a specific legal entity, select **View for a specific legal entity** (or **Edit for a specific legal entity**).

:::image type="content" source="media/ToggleToEditForAllLegalEntities.PNG" alt-text="Screenshot of the View/Edit for a specific legal entity option.":::

Additionally, in the enhanced product category structure, a merchandising manager can now define default values for an additional set of product properties at the level of the individual category. Then, when you create products, they inherit default values for their product properties, based on the association of those properties with an individual category in the product hierarchy. You can also modify these inherited product properties for each product to meet individual business requirements.

## Select properties to update products on the Commerce product hierarchy page

Use the new enhanced structure for product properties to select updated product properties that you want to push to the associated products. On the **Commerce product hierarchy** page, select **Category** on the Action Pane, and then select **Update products** to open the **Update products** dialog box.

:::image type="content" source="media/NewUpdateProductsEnhancedView.PNG" alt-text="Screenshot of the Update products dialog box.":::

> [!NOTE]
> When you select **Schedule batch job** in the **Update products** dialog box, you can find the batch job history log on the **System administration > Inquiries > Batch jobs** form. For the **Update products** batch job, select **Batch job history > Log**, and then select **Message details** in the upper right to view the log and check if there are any warnings or errors.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
