---
title: Enable and set up product bundles 
description: Learn how to set up product bundles, including prerequisites and an outline on toggling product bundle features for your system.
author: henrikan
ms.author: henrikan
ms.topic: how-to
ms.date: 04/29/2024
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form: Customer
---

# Enable and set up product bundles

[!include [banner](../includes/banner.md)]

## Prerequisites

Before you can use the features that are described in this article, your system must meet the following requirements:

- To use the *Product bundle* feature, you must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.36 or later.
- To use the *Product bundles in journals* feature, which extends the *Product bundle* feature, you must be running Supply Chain Management version 10.0.40 or later.

## Turn on the product bundle features for your system

### Turn on the product bundle feature

To make product bundle functionality available, you must turn it on for your system.

1. Go to **System administration \> Workspaces \> Feature management**. (Learn more in [Feature management overview](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).)
1. On the **All** tab, use the **Filter** field to search for the feature that's named *Revenue recognition*.
1. If the *Revenue recognition* feature is enabled in your system, select it in the list, and then select **Disable** to disable it. You can't use this feature together with the *Product bundle* feature.
1. Use the **Filter** field to search for the feature that's named *Product bundles*.
1. Select the feature in the list, and then select **Enable now** to enable it.

> [!NOTE]
> When you first turn on the *Product bundle* feature, the system checks whether it includes any released products where the **Revenue recognition bundle** option is set to *Yes*. If it does, the system creates a batch job that automatically upgrades the records for those products so that they will work with the *Product bundle* feature. Likewise, if the system includes any uncanceled sales orders that have lines that contain revenue recognition bundle items, those sales order lines are also upgraded so that they will work with the *Product bundle* feature. This behavior should provide a seamless experience as you transition from using revenue recognition bundles to using product bundles. The upgrade is done as part of a Data maintenance portal action.

### Turn on the product bundles in journals feature

The *Product bundles in journals* feature extends the *Product bundle* feature. It enables the system to preserve detailed product bundle information in its database. Therefore, you can reprint original sales order confirmations and invoices even after the related sales order is deleted or archived and purged. This feature also improves the ability to exchange order confirmations and invoices electronically. Because product bundles are now represented in journals, you can electronically exchange order confirmations and invoices that include product bundles.

To make the *Product bundles in journals* feature available, you must turn it on for your system.

1. Go to **System administration** \> **Workspaces** \> **Feature management**. (Learn more in [Feature management overview](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).)
1. On the **All** tab, use the **Filter** field to search for the feature that's named *Product bundles in journals*.
1. Select the feature in the list, and then select **Enable now** to enable it.

> [!NOTE]
> When you turn on the *Product bundles in journals* feature, the system creates a batch job that automatically upgrades sales confirmation journal lines, sales packing slip journal lines, and sales invoice journal lines that contain product bundles and that sales order lines exist for. As a result of this upgrade, sales confirmations and sales invoices can be reprinted correctly after sales order lines are deleted. The upgrade is done as part of a data maintenance portal action.

## Set up product bundles

Bundle items are released products that include components. You set up bundle items by using the bill of materials (BOM) functionality. When a product bundle item is entered on a sales order, revenue is posted for the individual components, not for the product bundle item.

Documents that are printed for the customer (such as sales order confirmations and invoices) show only the product bundle item, not the components. However, documents that are printed for internal use (such as sales order picking lists and packing slips) show only the components, not the product bundle item. Learn more in [Sell and allocate product bundles](product-bundles-use.md).

### Set up product bundle components

Each component item of a product bundle must be set up as a released product on the **Released products** page (**Product information management \> Products \> Released products**). The released products are set up in the same way as products that are included on a BOM. For example, a released product can be an item of either the *Item* type or the *Service* type, but it must be assigned to an item model group where the **Stocked product** option is set to *Yes*. Learn more in [Bills of materials and formulas](../production-control/bill-of-material-bom.md).

In addition, a base sales price must be set for each component. The base sales price is used to calculate the component's revenue contribution percentage. The product bundle's revenue price is then distributed to the components based on their revenue contribution percentages. Learn more in [Sell and allocate product bundles](product-bundles-use.md).

### Set up product bundle items

Each product bundle item must be set up as a released product on the **Released products** page (**Product information management \> Products \> Released products**). To identify a released product as a bundle item, you must set the following two fields on the released product record:

- On the **General** FastTab, set the **Product Bundle** option to *Yes*.
- On the **Engineer** FastTab, set the **Production type** field to *BOM*.

The component items must be then assigned to the product bundle (BOM parent) item on the **BOM versions** page. To open this page, open the product bundle item on the **Released products** page. Then, on the Action Pane, on the **Engineer** tab, select **BOM versions**. Learn more in [Bills of materials and formulas](../production-control/bill-of-material-bom.md).

## Related information

- [Product bundles overview](product-bundles-overview.md)
- [Sell and allocate product bundles](product-bundles-use.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
