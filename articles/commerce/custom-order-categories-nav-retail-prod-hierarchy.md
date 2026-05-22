---
title: Change the sort order for merchandising entities
description: Learn how to control the display order for various merchandising-related entities in Dynamics 365 Commerce.
author: josaw1
ms.date: 01/21/2026
ms.topic: how-to
ms.search.form: Category, Retail product hierarchy, Navigation hierarchy
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2016-11-30
ms.custom: 
  - bap-template
---

# Change the sort order for merchandising entities


[!Include [banner](includes/banner.md)]

This article explains how to control the display order for various merchandising-related entities in Dynamics 365 Commerce.

Retailers consider product discovery a primary tool for customer interaction across all channels. Several features help customers easily discover products. For example, customers can browse categories, search, and filter.

In Commerce, sorting various merchandising-related entities aligns with existing customer scenarios and no longer requires extensions from implementation partners.

In Commerce versions 10.0.5 and earlier, the sort order for categories in the navigation hierarchy was alphabetical. The current custom sort order functionality enables merchandising managers to configure the sort order for various merchandising-related entities across all end-user clients. These clients include headquarters (HQ) and call centers.

## Configure the display order for categories in the product hierarchy

Before you can complete this procedure, you must install demo data in your environment.

1. Go to **Retail and Commerce > Products and categories > Commerce product hierarchy**.
1. Select **Edit category hierarchy**.
1. Select **Edit**.
1. In the tree, expand **ALL > Action Sports**.
1. In the tree, expand **ALL > Team Sports**.
1. In the **Display order** field, enter a number. You can use a negative number.
1. Repeat steps 4 through 6 for any additional categories that you want to change the order of.

The display order for the channel navigation hierarchy appears in HQ for the commerce product hierarchy and released products by category.

:::image type="content" source="./media/RetailProductHierarchyCustomSortedWithNegativeValues.png" alt-text="Screenshot of product hierarchy custom sorted with negative values.":::

:::image type="content" source="./media/ReleasedProductsByCategoryCustomSortedBasedOnRetailProductHierarchy.png" alt-text="Screenshot of released products by category custom sorted based on the product hierarchy.":::

## Configure the display order for categories in the channel navigation hierarchy

Before you can complete this procedure, you must install demo data in your environment.

1. Go to **Retail and Commerce > Products and categories > Channel navigation categories**.
1. In the list, select the **Fashion navigation** hierarchy.
1. Select **Edit category hierarchy**.
1. Select **Edit**.
1. In the tree, select **Fashion > Womenswear > Women's Shoes**.
1. In the **Display order** field, enter a number.
1. In the tree, select **Fashion > Womenswear > Tops**.

You can also define the sort order for the subcategories.

1. In the tree, select **Fashion > Menswear > Casual Shirts**.
1. In the **Display order** field, enter a number.
1. In the tree, select **Fashion > Menswear > Coats & Jackets**.
1. In the **Display order** field, enter a number.
1. Repeat for any additional categories that you want to change the order of.

The display order for the channel navigation hierarchy appears in HQ, catalog, and channels.

:::image type="content" source="./media/ChannelNavCustomSorted.png" alt-text="Screenshot of channel navigation hierarchy custom sorted.":::

:::image type="content" source="./media/CatalogNavHierarchyCustomSortedBasedOnChannelNav.png" alt-text="Screenshot of catalog navigation hierarchy custom sorted based on the channel navigation hierarchy.":::

:::image type="content" source="./media/POSChannelCategoriesCustomSorted.png" alt-text="Screenshot of POS with custom sorted categories.":::

> [!NOTE]
> By default, the **Enable display order for merchandising entities** feature is turned off. Use [Feature management](../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) to turn it on. After you turn on the feature, run **Global configuration -1110** CDX job from the distribution schedule.
> If your categories order in POS aren't updated, reactivate the device. Category information is fetched when device activation occurs, so the device might need to refetch the category information with updated display orders.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
