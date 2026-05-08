---
title: Optimize confirmed dates for CTP line changes (preview)
description: Optimize confirmed dates for CTP line changes feature ensures that confirmed ship and receipt dates on sales order lines remain accurate when fields that affect transport days are modified.
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form: SalesAvailableDlvDates, SalesTable, CustParameters, InventItemOrderSetup
ms.topic: how-to
ms.date: 05/05/2026
ms.custom:
  - bap-template
---

# Optimize confirmed dates for CTP line changes (preview)

[!include [banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: preview until 10.0.49 -->

The *Optimize confirmed dates for CTP line changes* feature ensures that confirmed ship and receipt dates on sales order lines stay accurate when you modify fields that affect transport days. When you use capable-to-promise (CTP) with Planning Optimization, this feature automatically adjusts the confirmed dates to optimize delivery without requiring user action.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## When the feature applies

This feature applies when you modify a sales order line in a way that changes the calculated transport days. Changes to any of the following fields can affect transport days:

- **Mode of delivery**
- **Warehouse**
- **Delivery address**

Transport days can either increase (for example, when the delivery mode adds more days, or when the destination or warehouse changes to a more distant location) or decrease (for example, when the delivery mode is faster).

## How the feature works

When you modify a field on a sales order line that impacts transport days, the system automatically recalculates the requested and confirmed dates to reflect the new transport days.

The system optimizes the confirmed dates as follows:

- If the confirmed receipt date equals the requested receipt date and no past shipment is needed, the ship date moves closer to the receipt date.
- If the confirmed receipt date is later than the requested receipt date, the system optimizes toward the requested date within shipping constraints.
- If the change would cause the ship date to fall in the past, the confirmed receipt date is scheduled forward from the first feasible ship date.

## Enable Optimize confirmed dates for CTP line changes

Before you can use the **Optimize confirmed dates for CTP line changes** feature, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.48 or later.
- You must use Planning Optimization.
- You must use capable-to-promise (CTP) delivery date control on the sales order line. You can use either *Near real-time CTP* or *Batch CTP*.
- The *(Preview) Optimize confirmed dates for CTP line changes* feature must be turned on in [Feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Example scenario 1: changing to a faster mode of delivery

This example shows how the feature adjusts confirmed dates when you change the mode of delivery to one with fewer transport days.

### Example scenario 1 setup

The following modes of delivery are configured:

- **Air** - 1 transport day
- **Truck** - 10 transport days

### Initial sales order line with truck

The user creates a sales order line with **Mode of delivery** set to *Truck*. CTP returns the following dates:

| Field | Value |
|---|---|
| Requested ship date | 1.11.2025 |
| Confirmed ship date | 1.11.2025 |
| Requested receipt date | 10.11.2025 |
| Confirmed receipt date | 10.11.2025 |

### Change the mode of delivery to air

The user changes **Mode of delivery** to *Air*. When the **Optimize confirmed dates for CTP line changes** feature is enabled, the system automatically adjusts the dates to reflect the shorter transport time. The result is:

| Field | Value |
|---|---|
| Requested ship date | 9.11.2025 |
| Confirmed ship date | 9.11.2025 |
| Requested receipt date | 10.11.2025 |
| Confirmed receipt date | 10.11.2025 |

Without this feature, the requested and confirmed ship dates stay 1.11.2025 even though only one transport day is required.

## Example scenario 2: changing to a slower mode of delivery

This example shows how the feature adjusts confirmed dates when the user changes the mode of delivery to one with more transport days.

### Example scenario 2 setup

The following modes of delivery are configured:

- **Air** - 1 transport day
- **Truck** - 10 transport days

### Initial sales order line with air

You create a sales order line with **Mode of delivery** set to *Air*. CTP returns the following dates:

| Field | Value |
|---|---|
| Requested ship date | 9.11.2025 |
| Confirmed ship date | 9.11.2025 |
| Requested receipt date | 10.11.2025 |
| Confirmed receipt date | 10.11.2025 |

### Change the mode of delivery to truck

You change **Mode of delivery** to *Truck*. When you the *Optimize confirmed dates for CTP line changes* feature is enabled, the system automatically adjusts the dates to reflect the longer transport time. Assuming there's no delay and the item can be shipped on 1.11.2025, the result is:

| Field | Value |
|---|---|
| Requested ship date | 1.11.2025 |
| Confirmed ship date | 1.11.2025 |
| Requested receipt date | 10.11.2025 |
| Confirmed receipt date | 10.11.2025 |

Without this feature, the requested and confirmed receipt dates would shift to 19.11.2025 because the original ship date of 9.11.2025 plus 10 transport days would be used, even though the item is available earlier.
