---
title: Enable and set up product bundles 
description: This article describes how to set up product bundles.
author: henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form: Customer
ms.topic: how-to
ms.date: 07/31/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Enable and set up product bundles

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

## Turn on the product bundle feature for your system

To make product bundle functionality available, you must turn it on for your system.

1. Go to **System administration \> Workspaces \> Feature management**. (For more information, see [Feature management overview](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).)
1. On the **All** tab, use the **Filter** field to search for the feature that is named *Revenue recognition*.
1. If the *Revenue recognition* feature is enabled on your system, select it in the list, and then select **Disable** to disable it. You can't use this feature together with the product bundle feature that you will enable in the next step.
1. Use the **Filter** field to search for the feature that is named *Product bundle*.
1. Select the feature in the list, and then select **Enable now** to enable it.

> [!NOTE]
> When you first turn on the *Product bundle* feature, the system checks to see whether any released products in the system have the **Revenue recognition bundle** setting set to *Yes*. If so, the system will create a batch job that will automatically upgrade those records to work with the *Product bundle* feature. Likewise, if your system includes any uncanceled sales orders that have lines containing revenue recognition bundle items, then those sales order lines will also be upgraded to work with the *Product bundle* feature. This should provide a seamless experience as you transition from using revenue-recognition bundles to using product bundles. The upgrade is done as part of a Data maintenance portal action <!--KFM: What is the implication of this detail? What do we need to do about it? -->.

## Set up product bundles

Bundle items are unique released products that include components. You set up bundle items using the bill of materials (BOM) functionality. When a product bundle item is entered on a sales order, revenue is posted for the individual components, not the product bundle item. Documents printed for the customer (such as sales order confirmations and invoices) show only the product bundle item and not the components, while documents printed for internal use (such as sales order picking lists and packing slips) show only the components and not the product bundle item.

### Set up product bundle components

The components that are included in the product bundle must be set up on the **Released products** page (**Product information management \> Products \> Released products**). These components are released products, and they must be set up in the same manner as products that are included in a BOM. For example, a released product can be an item of either the *Item* type or the *Service* type, but it must be assigned to an item model group where the **Stocked product** option is set to *Yes*. For more information, see the setup documentation for BOM items.

The components must must also be set up with a base sales price. The product bundle revenue price will be distributed to the components, based on their revenue contribution percentages, which is calculated from the base sales price of each.

### Set up product bundle items

When you set up a product bundle item, you must set two fields on the **Released products** page (**Product information management \> Products \> Released products**):

- On the **Engineer** FastTab, in the **Production type** field, the item must be set up as a BOM item.
- On the **General** FastTab, in the **Product Bundle** field, the item must be marked as a product bundle item.

The components must be then assigned to the product bundle/BOM parent item on the **BOM versions** page (go to **Product information management \> Products \> Released products**, and then, on the Action Pane, on the **Engineer** tab, in the **BOM** group, select **BOM versions**). For more information, see [Bills of materials and formulas](../production-control/bill-of-material-bom.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
