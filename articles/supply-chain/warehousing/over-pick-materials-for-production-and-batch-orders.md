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

This article explains how warehouse managers can configure Microsoft Dynamics 365 Supply Chain Management to allow and set limits on over-picking of raw materials. Over-picking occurs when a worker picks slightly more material than is specified for a production order. Over-picking can be relevant in situations where it's more efficient for workers to over-pick by rounding up to the nearest packing unit, or where it's more efficient to pick the full content of nearly empty locations to free up space.

This feature lets workers who use the Warehouse Management mobile app over-pick raw materials for production orders when they must. Workers are notified if they exceed the over-picking thresholds that the warehouse manager sets.

## Prerequisites

Before you can use this feature, your system must meet the following requirements:

- You must be running Supply Chain Management version 10.0.37 or later.
- The feature that's named *Over-pick materials for production orders and batch orders* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
- All products that you'll use this feature for must be enabled for warehouse management processes (WMS).

## Set up over-picking for production and batch orders

Use the following procedures to set up over-picking for production and batch orders.

### Enable over-picking for a worker

Follow these steps to enable over-picking for a worker.

1. Go to **Warehouse management \> Setup \> Worker**.
1. Select the worker that you want to enable the feature for.
1. On the **Users** FastTab, select the user account that should be allowed to over-pick.
1. On the **Work** FastTab, set the **Allow production over picking** option to *Yes*.

### Enable over-picking for a mobile device menu item

Follow these steps to enable over-picking for a mobile device menu item.

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**.
1. Select a mobile device menu item in the list pane, or create a new one. For the new or selected item, the grid on the **Work classes** FastTab must include a row where the **Work order type** field is set to *Raw material picking*. (If you're working with USMF [demo data](../../fin-ops-core/fin-ops/get-started/demo-data.md), you can select the mobile device menu item that's named *Production pick*.)
1. On the **General** FastTab, set the **Allow over pick** option to *Yes*.

## Set an allowed threshold for over-picking

For each product, you can define an over-picking threshold to control the extent to which a worker is allowed to over-pick the product. You can override the threshold for products that are included in a bill of materials (BOM). When you create a production order for a product, the over-picking threshold for each item on that product's BOM is copied either from the item itself or from the override value that's set in the product BOM (if any value is set there). The threshold is defined as a percentage of the quantity that's designated for the production order.

### Set the over-picking threshold for a product

Follow these steps to set the over-picking threshold for a product.

1. Go to **Product Information management \> Products \> Released products**.
1. Open the product that you want to set the over-picking threshold for.
1. On the **Warehouse** FastTab, set the **Material over picking (%)** field to the over-picking threshold that you want to allow.

### Override the over-picking threshold on a BOM line

When you add a product to a BOM line, the system initially copies that product's over-picking threshold to the BOM line. Follow these steps to override the over-picking threshold for a specific BOM line.

1. Go to **Product Information management \> Bill of materials and formulas \> Bill of materials**.
1. Open the BOM where you want to override the over-picking threshold.
1. On the **Bill of material lines** FastTab, select the BOM line that you want to override the over-picking threshold for.
1. On the **Line details** FastTab, on the **Setup** tab, set the following fields:

    - **Override** – Set this option to *Yes*.
    - **Material over-picking (%)** – Enter the new over-picking threshold. When this BOM line is used in a production order, the threshold that you set here overrides the default threshold that's set on the product.

## Set policies for staging and over-picking

Warehouse managers can set up policies that define how material should be allocated when it's picked from license-plate-controlled and non-license-plate-controlled locations.

### Set the policy for over-picking in license-plate-controlled locations

Follow these steps to set the policy for over-picking in license-plate-controlled locations.

1. Go to **Product Information management \> Products \> Released products**.
1. Select the product that you want to set up.
1. On the **Warehouse** FastTab, set the **Material picking in license plate controlled locations** field to one of the following values:

    - *Staging* – The full quantity of the scanned license plate is staged to the production input location. The original estimated quantity is allocated to the production order, and the remaining quantity on the license plate is left unallocated at the production input location. When you use policy, the over-picking option isn't available in the workflow for raw material picking on the Warehouse Management mobile app.
    - *Order picking* – The full picked quantity is allocated to the production order.

### Set the policy for over-picking in non-license-plate-controlled locations

Follow these steps to set the policy for over-picking in non-license-plate-controlled locations.

1. Go to **Product Information management \> Products \> Released products**.
1. Select the product that you want to set up.
1. On the **Warehouse** FastTab, set the **Material picking in non-license plate controlled locations** field to one of the following values:

    - *Staging* – The original estimated quantity is allocated to the production order, and the remaining quantity is left unallocated at the production input location.
    - *Order picking* – The full picked quantity is allocated to the production order.
