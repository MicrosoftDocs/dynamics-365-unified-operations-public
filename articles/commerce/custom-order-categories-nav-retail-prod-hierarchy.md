---
title: Change the sort order for merchandising entities
description: This article explains the concepts that are related to controlling the display order for various merchandising-related entities in Dynamics 365 Commerce.
author: josaw1
ms.date: 08/01/2024
ms.topic: how-to
ms.search.form: Category, Retail product hierarchy, Navigation hierarchy
audience: Application User
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2016-11-30
ms.custom: 
  - bap-template
---

# Change the sort order for merchandising entities


[!Include [banner](includes/banner.md)]

Retailers consider product discovery a primary tool for customer interaction across all channels. There are several features that can help customers easily discover products. For example, customers can browse categories, search, and filter.

This article explains the concepts that are related to controlling the display order for various merchandising-related entities. It also explains how to change the sort order.

## Overview

In Commerce, sorting various merchadising-relating entities is aligned with existing customer scenarios and no longer requires extensions from implementation partners.

In Commerce versions 10.0.5 and earlier, the sort order for categories in the navigation hierarchy was alphabetical. The current custom sort order functionality enables merchandising managers to configure the sort order for various merchandising-related entities across all end-user clients. These clients include headquarters (HQ) and call centers.

## Configure the display order for categories in the product hierarchy

Before you can complete this procedure, demo data must be installed in your environment.

1. Go to **Retail and Commerce \> Products and categories \> Commerce product hierarchy**.
2. Click **Edit category hierarchy**.
3. Click **Edit**.
4. In the tree, expand **ALL \> Action Sports**.
5. In the tree, expand **ALL \> Team Sports**.
6. In the **Display order** field, enter a number. (The number can be negative.)
7. Repeat steps 4 through 6 for any additional categories that you want to change the order of.

The display order for the channel navigation hierarchy will be reflected in HQ for the commerce product hierarchy and released products by category.

![Product hierarchy custom sorted with negative values.](./media/RetailProductHierarchyCustomSortedWithNegativeValues.png)

![Released products by category custom sorted based on the product hierarchy.](./media/ReleasedProductsByCategoryCustomSortedBasedOnRetailProductHierarchy.png)

## Configure the display order for categories in the channel navigation hierarchy

Before you can complete this procedure, demo data must be installed in your environment.

1. Go to **Retail and Commerce \> Products and categories \> Channel navigation categories**.
2. In the list, select the **Fashion navigation** hierarchy.
3. Click **Edit category hierarchy**.
4. Click **Edit**.
5. In the tree, select **Fashion \> Womenswear \> Women's Shoes**.
6. In the **Display order** field, enter a number.
7. In the tree, select **Fashion \> Womenswear \> Tops**.

Likewise, you can define the sort order for the subcategories.

8. In the tree, select **Fashion \> Menswear \> Casual Shirts**.
9. In the **Display order** field, enter a number.
10. In the tree, select **Fashion \> Menswear \> Coats & Jackets**.
11. In the **Display order** field, enter a number.
12. Repeat for any additional categories that you want to change the order of.

The display order for the channel navigation hierarchy is reflected in HQ, catalog, and channels.

![Channel navigation hierarchy custom sorted.](./media/ChannelNavCustomSorted.png)

![Catalog navigation hierarchy custom sorted based on the channel navigation hierarchy.](./media/CatalogNavHierarchyCustomSortedBasedOnChannelNav.png)

![POS with custom sorted categories.](./media/POSChannelCategoriesCustomSorted.png)

> [!NOTE]
> By default, the **Enable display order for merchandising entities** feature is turned off. Use [Feature management](../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) to turn it on. After you tun the feature on, run **Global configuration -1110** CDX job from the distribution schedule.
> If your categories order in POS aren't updated, reactivate the device. Category information is fetched when device activation occurs, so the device may need to refetch the category information with updated display orders. 

[!INCLUDE[footer-include](../includes/footer-banner.md)]
