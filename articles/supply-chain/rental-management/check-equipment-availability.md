---
title: Check fleet item availability and select fleet items (preview)
description: Learn how to check fleet item availability and select fleet items for rental contracts using the fleet item availability screen.
author: jodahlMSFT
ms.author: jodahl
ms.reviewer: kamaybac
ms.search.form: FLMFleetItemAvailability, FLMFleetItemAvailabilitySum
ms.topic: how-to
ms.date: 10/23/2026
ai-usage: ai-assisted
ms.custom:
  - bap-template
---

# Check fleet item availability and select fleet items (preview)

[!INCLUDE [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

The **Fleet item availability** screen lists fleet items with their agreement, physical, and service status, location, and any attachments. It reflects each fleet item's *current* state. To hold fleet items for future demand, use reservations instead. Learn more in [Reserve fleet items](reserve-rental-equipment.md).

## Understand how worker settings affect availability

Personalize the fleet item availability screen through **Rental user setups**, which store per-user defaults. These settings control what you see by default when you open the screen:

- **Show all on fleet item availability** – When enabled, **Show all** is selected when you open the screen from the menu. The list then includes fleet items in every status except *Not available*, including fleet items on active contracts and sales orders. When disabled, the list leaves out fleet items that are reserved, on a sales order, on a rental contract, or on order.
- **Fleet item types in availability view** – Sets the **Fleet item type** filter to *Fleet item*, *Bulk fleet item*, *Attachment*, or *All* when you open the screen from the menu.
- **Utilization on availability** – Controls whether the screen displays utilization figures.

An administrator configures these defaults per user on the **Rental user setups** tab of the rental parameters, at **Rental management (Preview)** > **Setup** > **Rental parameters**. Learn more in [The Rental user setups tab](configure-rental-parameters.md#rental-workers).

## Understand fleet item statuses

Each fleet item has three status indicators. Understanding them helps you quickly assess what you can and can't do with a fleet item.

> [!NOTE]
> The system enforces hard blocks on specific status values. **Physical status** *Not available* and *On hold* prevent adding the fleet item to a contract. **Service status** *Hard down* prevents renting, selling, and adding the fleet item to a fleet item movement, and it also prevents you from selecting the fleet item as the replacement in a swap. Most other status values place no direct block on a transaction, but every value affects visibility. The system folds the three statuses into one summarized **Availability status** through the **Availability status combinations** setup. Learn more in [How the availability status is calculated and configured](#how-the-availability-status-is-calculated-and-configured).

### Agreement status

The agreement status shows the fleet item's current contractual commitment. The system sets this status automatically when you assign the fleet item to a contract or sales order, or release it from one.

| Status | Description |
|---|---|
| *None* | No agreement status is assigned. |
| *Available* | The fleet item is free to be assigned to a new rental quotation or contract. |
| *Rental* | The fleet item is on an active rental contract. |
| *Lease* | The fleet item is on an active lease contract. |
| *No-charge* | The fleet item is on a no-charge contract. |
| *Sale* | The fleet item is included in a sales transaction. |
| *Returned* | The fleet item is returned from a contract. |
| *Sold* | The fleet item is sold and no longer part of the rental fleet. |
| *Not available* | The fleet item is excluded from rental operations. The system skips fleet items that have this status when you create fleet item movements from the availability view. |

### Physical status

The physical status tracks the fleet item's location and handling state throughout its lifecycle. The system sets most values automatically as the fleet item moves through purchase receipts, fleet item movements, and sales transactions. You configure fleet item movement changes under **Fleet item movement status setup**.

| Status | Description |
|---|---|
| *None* | No physical status is assigned. |
| *Ordered* | The fleet item is on an open purchase order, and you didn't receive it yet. |
| *In transit* | The fleet item is in transit between locations. |
| *Under receiving* | You're receiving the fleet item against a purchase order. |
| *In stock* | The fleet item is in stock at a warehouse, available for use. |
| *Under preparation* | The fleet item is being prepared (for example, first service or detailing) before you can rent it. |
| *Inspection* | The fleet item is undergoing a pre- or post-rental inspection. |
| *Ready* | The fleet item is ready to ship on a rental contract. |
| *In shop* | The fleet item is in the service shop. |
| *Prepared* | The fleet item completed preparation and is ready. |
| *On job site* | The fleet item is currently on a customer job site on an active contract. |
| *Sold* | The fleet item is delivered against a sales order. |
| *Closed* | The fleet item is closed and inactive. |
| *On hold* | The fleet item is on hold. **Blocks adding to a contract and swapping.** |
| *To be shipped* | The fleet item is scheduled for outbound shipment. |
| *To be picked* | The fleet item is scheduled for customer pickup. |
| *Returned* | The fleet item is returned from a job site. |
| *Received* | The fleet item is received back at the branch. |
| *Delivered* | The fleet item is delivered to the customer. |
| *Not available* | The fleet item isn't available for rental operations. **Blocks adding to a contract and swapping.** |
| *No update* | No physical status update is applied in the current transaction. |
| *In territory* | The fleet item is within its assigned territory. |
| *Out of territory* | The fleet item is outside its assigned territory. |
| *Inactive in territory* | The fleet item is inactive within its territory. |
| *Installed* | The fleet item is installed at a customer site. |

### Service status

The service status communicates the fleet item's operational readiness to the rental team. You can update this status manually on the fleet item master record, optionally with a reason code. A manual change takes effect immediately. Most values don't directly block a transaction. The exception is *Hard down*, which the system enforces as a hard block. <!-- You can also update the service status from the Dynamics 365 Supply Chain Management mobile app. Learn more in [Use the Dynamics 365 Supply Chain Management mobile app](use-rental-mobile-app.md). -->

| Status | Description | System enforced? |
|---|---|---|
| *Ready* | The fleet item is operationally ready to rent. | - |
| *In shop* | The fleet item is in the service shop for maintenance. | - |
| *Under preparation* | The fleet item is being prepared for its next rental (for example, first service, detailing, or decal work). | - |
| *Inspection* | The fleet item is under inspection before or after a rental. | - |
| *Closed* | The fleet item's service record is closed. | - |
| *Installed* | The fleet item is installed at a customer site. | - |
| *Hard down* | The fleet item has a major failure and is unavailable for an extended period (for example, an engine replacement). | **Yes** |
| *Under repair* | The fleet item is being repaired and should be available soon. | - |
| *Preparation needed* | The fleet item needs a return-to-ready inspection before it can go back out. | - |
| *None* | No service status is set. | - |

Learn more about updating service status in [Manage fleet item master data](manage-equipment-master-data.md).

## How the availability status is calculated and configured

The three statuses described earlier are the source values. The **Fleet item availability** page also shows a fourth column, **Availability status**, which summarizes whether you can commit a fleet item to a customer. You can't enter this value manually. The system derives it from the agreement, physical, and service status of each fleet item, by using a mapping that you maintain.

### How the summarized status is resolved

Each fleet item has the three source statuses plus the derived **Availability status**. A fleet item gets the availability status of the combination that matches its agreement status, physical status, and service status exactly. When no combination matches, the fleet item gets the status that's marked **Default fallback**.

The system recalculates the value when you create a fleet item, and whenever one of the three source statuses changes, so day-to-day operations keep it current automatically. Bulk data loads and integrations that write statuses directly are the exception, and the update job later in this section covers them.

### Configure availability status combinations

You need to set up this configuration. The default configuration doesn't work for most operations. The installation provides two availability statuses, *Available* and *Not available*, with *Not available* as the default fallback, and exactly one combination: agreement status *Available* with physical status *In stock* and service status *Ready* resolves to *Available*. Every other combination resolves to the fallback status. For example, a fleet item that's *Available*, *In stock*, and *Under preparation* can be rented, but the grid shows it as *Not available* until you map that combination.

To define the statuses and the mapping, follow these steps:

1. Go to **Rental management (Preview)** > **Setup** > **Availability status combinations**.
1. In the **Fleet item availability statuses** pane, create one row for each word you want to see on the availability grid, such as *Available*, *On rent*, *In shop*, and *Not available*. Enter an **Availability status** and a **Description**.
1. Set **Default fallback** on the status that applies when no combination matches. Only one status can carry the flag, and you can't clear it or delete that status, only move the flag to another status. Choose a conservative value, so that you never promise an unmapped combination to a customer by accident.
1. In the list, select the availability status that the combination resolves to. On the **Availability status combinations** FastTab, select **New**, and then select the **Agreement status**, **Physical status**, and **Service status** that make up the combination.
1. Repeat for every combination that occurs in your operation. Map the status combinations that your organization uses, rather than every possible combination.
1. When you're prompted to update the availability status on all existing fleet items, select **Yes**. The prompt appears whenever you add, change, or delete a combination.

### Recalculate availability for all fleet items

**Update fleet item availability statuses** recomputes the availability status of every fleet item by reapplying the configured status combinations. Fleet items that match a combination get the mapped status, and everything else gets the default fallback.

To run the job, go to **Rental management (Preview)** > **Setup** > **Availability status combinations**, select the **Update status fields** tab, and then select **Update fleet item availability statuses**. You can run it interactively or schedule it as a batch job.

Run it in the following situations:

- After you add or change combinations following go-live, so that the system reclassifies existing fleet items and you don't have to open each record.
- After a data import or an integration writes agreement, physical, or service statuses directly.
- On a nightly schedule, so that the grid can't drift out of step with the configuration.

### Why a fleet item doesn't appear in the list

A fleet item that never appears on the grid is a different problem from one that appears with a not-available summary. The availability list excludes fleet items that are marked **Inactive** and any fleet item whose status reason code has **Show on availability** cleared. Check the reason code on the fleet item, and then check its setup at **Rental management (Preview)** > **Setup** > **Fleet items** > **Fleet item status reason codes**. The list also shows only the fleet types that apply where you open it. From the menu, it shows every fleet type except those whose **Value tracking method** is *Customer* or *Canceled*. From a rental quotation or contract, it shows the fleet types allowed on its rental template. From a sales order or sales quotation, it shows only fleet types whose **Value tracking method** is *Inventory*.

## Check availability for a specific fleet item type

To check which fleet items are available for a specific fleet item type, follow these steps:

1. Go to **Rental management (Preview)** > **Common** > **Fleet items** > **Fleet item availability**.
1. On the **Filters** FastTab, narrow the list by **Fleet item type**, **Rental category**, **Default rental class** (the rental class groups interchangeable fleet items, such as *Medium skid steer*), **Bar code**, or **Not for sale**. The **Default rental class** lookup lists only the rental classes that match the selected **Fleet item type**, or every rental class when it's set to *All*. Unless **Show all** is selected, the list leaves out fleet items that are reserved, on a sales order, on a rental contract, or on order. Select **Show all** to include them, or select **Reserved**, **On sales order**, **On rental contract**, or **On order** to list only those fleet items.
1. Review the list to identify available fleet items. The status columns show the agreement, physical, and service status for each fleet item.
1. Expand the **Attachments** FastTab to see the attachments that are attached to the selected fleet item.

## View fleet item details and attachments

Each fleet item in the availability list includes details such as the serial number, model, manufacturer, and current location. For prime fleet items (the main rentable fleet item, as opposed to an attachment), you can also see:

- **Last SMU** – The most recent service meter reading, which is important for scheduling maintenance and for usage billing.
- **Attachments** – The **Attachments** FastTab lists the attachments, such as buckets, forks, or augers, that are attached to the selected prime fleet item. For an attachment, the **Attached to** column shows the prime fleet item that it's attached to. You can pre-attach attachments for convenience, or add them separately to the contract as individual line items.

## Check availability at the rental class level

The **Rental availability summary** shows availability grouped by rental class rather than by individual fleet item.

To access the **Rental availability summary** page, go to **Rental management (Preview)** > **Common** > **Fleet items** > **Fleet item availability summary**.

From this view, you can:

- Read the count columns for each rental class: **Available for rent (including re-rent)**, **Total available**, **On rent**, **Not available**, **Reserved**, **Available for sale**, and **On RPO contract**. **Available for sale** and **On RPO contract** are the columns you need when you sell fleet items from the rental fleet. **Available for sale** excludes fleet items that are on a rental purchase option contract and those that are flagged **Not for sale**.
- Drill into individual fleet items within a class.
- Check adjacent classes if the requested class is sold out - for example, if no medium skid steers are available, check the small or large class for alternatives.
- Select **Display details** to group the class rows by fleet type or by fleet location, and to choose the utilization period.

> [!IMPORTANT]
> The summary counts don't use the availability status combinations that drive the **Availability status** column for each fleet item. They combine the agreement status with the **Physical statuses for rental availability summary** setup, at **Rental management (Preview)** > **Setup** > **Physical statuses for rental availability summary**. Fleet items whose physical status isn't listed there are left out of the summary. A listed physical status that has **Available in summary** cleared counts as *Not available*. List every physical status that your fleet uses, and configure both setups.

## Select fleet items for a contract

When you're ready to add a fleet item to a quotation or contract, you can do so in two ways:

- **Select directly from the fleet item availability screen** – This approach is useful when you know the specific serial number the customer needs. Select the **Marked** check box for each fleet item, and then select **Rental contract** or **Rental quotation** to create a document for them. To add fleet items to an existing quotation or contract, select **Add fleet item** on the **General** tab of the document's Action Pane, mark the fleet items, and then select **Add to contract** or **Add to quotation**. To fill a line that's already on the document, select the line, and then select **Assign fleet item**. The screen opens filtered to the line's rental class, with **Fleet item type** set to the kind of fleet items that the class holds, or *All* when it holds more than one kind.
- **Use the rental cart** – The rental cart dialog walks you through a step-by-step process. Learn more in [Create rental quotations and contracts by using the rental cart](create-rental-quotations-contracts.md).

## Related information

- [Rental management overview](rental-management-overview.md)
- [Create rental quotations and contracts by using the rental cart](create-rental-quotations-contracts.md)
- [Reserve fleet items](reserve-rental-equipment.md)
