---
title: Exclude purchase, production, or inbound transfer supply from ATP calculations (preview)
description: Learn how to exclude purchase, production, and inbound transfer supply from available-to-promise calculations to control customer promise dates.
author: AditiPattanaik
ms.author: adpattanaik
ms.reviewer: kamaybac
ms.search.form: CustParameters
ms.topic: how-to
ms.date: 10/23/2026
ai-usage: ai-assisted
ms.custom:
  - bap-template
---

# Exclude purchase, production, or inbound transfer supply from ATP calculations (preview)

[!INCLUDE [banner](../includes/banner.md)]

[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

*Available-to-promise* (ATP) calculations use on-hand inventory, expected receipts, and demand to determine when you can promise inventory to a customer. You can exclude purchase, production, or inbound transfer supply when your order-promising policy shouldn't rely on those receipts. These exclusions can reduce the quantity available to promise or move the promise date later.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## Prerequisites

To use the features described in this article, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.50 or later.
- The feature named *Configurable ATP with Receipt Control* must be turned on in feature management. Learn more in [Feature management overview](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

The feature is turned off by default. While it's off, the three supply-exclusion settings aren't available, and ATP uses its existing supply-selection rules.

## Applicable sales lines

The exclusions described in this article apply to sales order lines that use *ATP* or *ATP + Issue margin* as the **Delivery date control** method. Learn more in [Order promising](delivery-dates-available-promise-calculations.md).

Supply-exclusion settings apply across the current legal entity, not to individual items or sales order lines. Product-specific overrides for other ATP settings don't override these exclusions.

## Configure supply exclusions

Choose which supply types ATP can use for the current legal entity. Each exclusion is independent, so you can exclude one, two, or all three supply types. Follow these steps:

1. Go to **Accounts receivable** > **Setup** > **Accounts receivable parameters**.
1. Open the **Shipments** tab.
1. Expand the **Delivery control** FastTab.
1. In the **ATP** field group, set the following fields:

    - **ATP excl. purchase orders** – Set this field to *Yes* to exclude purchase order supply. This exclusion includes open, arrived, and overdue receipts and planned purchase orders.
    - **ATP excl. production orders** – Set this field to *Yes* to exclude production order receipts and planned production supply. This exclusion includes process co-products and by-products.
    - **ATP excl. inbound transfer orders** – Set this field to *Yes* to exclude expected receipts from open inbound transfer orders and planned transfer orders.

Set a field to *No* to keep that supply type eligible for ATP, subject to the other ATP settings and filters. When all three fields are *No*, this feature doesn't change the existing supply-selection rules.

## How exclusions affect ATP

When you turn on an exclusion, ATP doesn't count the matching supply as a receipt when it calculates availability and promise dates. This setting doesn't delete or change the underlying purchase, production, or transfer orders.

The exclusions apply to both actual and planned receipts for the selected supply types. However, planned supply participates only when **ATP incl. planned orders** is turned on in the ATP settings used for the product. Check any product-specific overrides on the **Default order settings** page, rather than relying only on the legal entity's default value.

Planned Kanban supply remains eligible even when **ATP excl. production orders** is *Yes*, provided that planned orders are included. Existing ATP time fences, inventory dimensions, and other eligibility rules still apply.

The exclusions don't remove on-hand inventory from ATP. Once a receipt becomes on-hand inventory, the supply-exclusion settings don't remove it from the starting inventory balance. Other on-hand settings and filters continue to apply.

Demand also remains in the calculation, including customer demand, production component requirements, and outbound transfer demand. Turning on all three exclusions doesn't create an on-hand-only calculation: other eligible receipt types and planned Kanban supply can still contribute.

## Example: Exclude supply from a promise date

An item has 10 units on hand, and a customer requests 25 units today. The following open receipts fall within the ATP time fence:

| Supply source | Quantity | Expected date |
| --- | --- | --- |
| Purchase order | 15 | Tomorrow |
| Production order | 10 | In two days |
| Inbound transfer order | 10 | In three days |

All receipts match the item's inventory dimensions and meet the other ATP eligibility rules. There are no other issues or receipts. Transport and warehouse calendars don't add days.

The exclusion settings change when the available quantity reaches the requested 25 units:

| Exclusion settings | Quantity available over time | Earliest promise date for 25 units |
| --- | --- | --- |
| All three fields are *No*. | The purchase order receipt increases availability from 10 to 25 units tomorrow. | Tomorrow |
| **ATP excl. purchase orders** is *Yes*; the other two fields are *No*. | Availability reaches 20 units in two days and 30 units in three days. | In three days |
| All three fields are *Yes*. | Availability stays at the 10 units on hand because this example has no other eligible receipts. | None within the example's ATP time fence |

## Related information

- [Order promising](delivery-dates-available-promise-calculations.md)
- [Delivery alternatives](delivery-alternatives.md)
- [Calculate sales order delivery dates using CTP](../master-planning/planning-optimization/calculate-delivery-dates-using-ctp.md)
