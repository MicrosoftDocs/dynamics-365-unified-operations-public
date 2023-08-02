---
# required metadata

title: Manage product categories and products
description: This article describes how merchandising managers can use product categories to manage relationships between the product hierarchies and released product details in Microsoft Dynamics 365 Commerce.
author: ashishmsft
ms.date: 07/18/2023
ms.topic: article
ms.search.form: EcoResCategorySearchList, EcoResAttribute, COODualUseCategories, EcoResProductCategory, EcoResCategoryAddProduct, EcoResAttributeValue
audience: Application User, Developer, IT Pro
ms.reviewer: josaw
ms.assetid: c7ed2ba5-87c6-4d99-9728-2a83e6d95ca9
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2017-09-01

---

# Manage product categories and products

[!include [banner](./includes/banner.md)]

This article describes how merchandising managers can use product categories to manage relationships between the product hierarchies and released product details in Microsoft Dynamics 365 Commerce.

Dynamics 365 Commerce allows merchandising managers view a structure of product properties that is shared between the product hierarchy and released product details.

To learn more about how to manage product categories, in the **Category and product management** workspace of Commerce headquarters, select the **Commerce product hierarchy** tile.

Notice the enhanced structure of the **Commerce product hierarchy** page that appears. In previous versions of the app, product properties were divided into *basic product properties* and *Retail product properties*, based on the scope of their applicability. Retail product properties are *global* in their scope of applicability. In other words, for a given product property, the same value is shared across all legal entities. By contrast, basic product properties are *legal entity–specific*. In other words, for a given basic product property, the value can differ across legal entities, depending on the individual business requirements of each legal entity.

In the enhanced product category structure, product properties are logically separated based on their applicability in a group, to reflect the structure of the released product details form structure.

![Fields grouped based on the properties' scope of applicability.](media/NoticeGroupingOfFieldsBasedOnTheirScope.PNG)

You can switch between managing legal entity–specific properties across all legal entities and managing them for a specific legal entity.

To manage properties across all legal entities, select **View for all legal entities** (or **Edit for all legal entities**).

![View/Edit for all legal entities.](media/ToggleBackToEditForSpecificLegalEntity.PNG)

To manage properties for a specific legal entity, select **View for a specific legal entity** (or **Edit for a specific legal entity**).

![View/Edit for a specific legal entity.](media/ToggleToEditForAllLegalEntities.PNG)

Additionally, in the enhanced product category structure, a merchandising manager can now define default values for an additional set of product properties at the level of the individual category. Then, when products are created, they inherit default values for their product properties, based on the association of those properties with an individual category in the product hierarchy. These inherited product properties can also be modified for each product to meet individual business requirements.

## Selecting properties to update products on the Commerce product hierarchy page

You can use the new enhanced structure for product properties to select updated product properties that must be pushed to the associated products. On the **Commerce product hierarchy** page, on the Action Pane, select **Category**, and then select **Update products** to open the **Update products** dialog box.

![Update products dialog box.](media/NewUpdateProductsEnhancedView.PNG)

> [!NOTE]
> When you select **Schedule batch job** in the **Update products** dialog box, you can find the log on the **System administration \> Inquiries \> Batch jobs** form. For the **Update products** batch job, select **Batch job history \> Log**, and then select **Message details** on the top right to view the log to check if there are any warnings or errors.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
