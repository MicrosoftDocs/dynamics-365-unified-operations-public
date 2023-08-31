---
title: Over-pick materials for production and batch orders
description: This article explains how to enable and use over-picking for production and batch orders.
author: JohanHoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form: WHSRFMenuItem
ms.topic: how-to
ms.date: 09/01/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Over-pick materials for production and batch orders

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

<!-- KFM: Preview until 10.0.37 GA -->

This article explains how warehouse managers can configure Dynamics 365 Supply Chain Management to permit over-picking of raw materials and set limits on over-picking. Over-picking occurs when a worker picks slightly more material than specified for a production order. This feature allows workers using the Warehouse Management mobile app to over-pick raw materials for production orders when needed.  Workers are notified if they exceed the over-picking thresholds set by the warehouse manager. Over-picking can be relevant in situations where it's more efficient for workers to over-pick by rounding up to the nearest packing unit, or in situations where it's efficient to pick the full content of nearly empty locations to free up space.

## Prerequisites

To use this feature, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management 10.0.37 or later.
- The feature that is named *Over-pick materials for production orders and batch orders* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
- All products for which you'll use this feature must be enabled for warehouse management processes (WMS).

## Set up over-picking for production and batch orders

Use the following procedures to set up over-picking for production and batch orders.

### Enable over-picking for a worker

Follow these steps to enable over-picking for a worker.

1. Go to **Warehouse management \> Setup \> Worker**.
1. Select the worker you want to enable the feature for.
1. On the **Users** FastTab, select the user account that should be allowed to over-pick.
1. On the **Work** FastTab, set **Allow production over picking** to *Yes*.

### Enable over-picking for a mobile device menu item

Follow these steps to enable over-picking for a mobile device menu item.

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**.
1. From the list pane, select a mobile device menu item or create a new one. For your new or selected item, on the **Work classes** FastTab, there must be a row that has a **Work order type** of *Raw material picking*. (If you're working with USMF [demo data](../../fin-ops-core/fin-ops/get-started/demo-data.md), you can select the mobile device menu item named *Production pick*.)
1. On the **General** FastTab, set the **Allow over pick** field to *Yes*.

## Set an allowed threshold for over-picking

For each product, you can set an over-pick threshold, which controls the extent to which a worker is permitted to over-pick that product. You can override that threshold for products included in a bill of materials (BOM). When you create a production order for a product, the over-pick threshold for each item in that product's BOM is copied either from the item itself or (if set) from the override value set in the product BOM. The threshold is defined as a percentage of the quantity designated for the production order.

### Set the over-picking threshold for a product

Follow these steps to set the over-picking threshold for a product.

1. Go to **Product Information management \> Products \> Released products**.
1. Open the product you want to set the over-picking threshold for.
1. On the **Warehouse** FastTab, set **Material over picking (%)** to the over-picking threshold you want to allow.

### Override the over-picking threshold on a BOM line

When you add a product to a BOM line, the system will initially copy that product's over-picking threshold to the BOM line. Follow these steps to override that over-picking threshold for a specific BOM line.

1. Go to **Product Information management \> Bill of materials and formulas \> Bill of materials**.
1. Open the bill of materials you want to set the over-picking threshold override for.
1. On the **Bill of material lines** FastTab, select the BOM line you want to set the over-picking threshold override for.
1. On the **Line details** FastTab, open the **Setup** tab and make the following settings:
    - **Override** – Set to *Yes*.
    - **Material over-picking (%)** – Enter the new over-picking threshold, which overrides the default threshold set on the product when this BOM line is used in a production order.

## Set policies for staging and over-picking

Warehouse managers can set up policies for how material should be allocated when picked from license plate controlled and non-license plate controlled locations.

### Set the policy for over-picking in license plate controlled locations

Follow these steps to set the policy for over-picking in license plate controlled locations.

1. Go to **Product Information management \> Products \> Released products**.
1. Select the product you want to set up.
1. On the **Warehouse** FastTab, set **Material picking in license plate controlled locations** to one of the following values:

    - *Staging* – The full quantity of the scanned license plate is staged to the production input location. The original estimated quantity is allocated to the production order and the quantity remaining on the license plate is left unallocated at the production input location. When you use policy, the over-picking option isn't available in the workflow for raw material picking on the Warehouse Management mobile app.
    - *Order picking* – The full picked quantity is allocated to the production order.

### Set the policy for over-picking in non-license plate controlled locations

Follow these steps to set the policy for over-picking in non-license plate controlled locations.

1. Go to **Product Information management \> Products \> Released products**.
1. Select the product you want to set up.
1. In the **Warehouse** FastTab, set **Material picking in non-license plate controlled locations** to one of the following values:

    - *Staging* – The original estimated quantity is allocated the production order and the remaining quantity is left unallocated at the production input location.
    - *Order picking* – The full picked quantity is allocated to the production order.
