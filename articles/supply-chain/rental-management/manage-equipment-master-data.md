---
title: Manage fleet item master data (preview)
description: Learn how to use the fleet item master to track fleet item details, financial summaries, damage history, and service status.
author: jodahlMSFT
ms.author: jodahl
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 10/23/2026
ai-usage: ai-assisted
ms.custom:
  - bap-template
---

# Manage fleet item master data (preview)

[!INCLUDE [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

The fleet item record is the central record for each fleet item in your rental fleet.

## View fleet item details

To open the fleet item master, go to **Rental management (Preview)** > **Common** > **Fleet items** > **Fleet items** and select a fleet item record.

The fleet item includes the following key information:

- **Fleet item number** – The unique identifier assigned when the fleet item record is created.
- **Serial number** – The manufacturer's serial number for the fleet item.
- **Model and manufacturer** – The fleet item's model and manufacturer.
- **Default rental class** – The rental class that a fleet item is rented under unless a contract line says otherwise. When you create a fleet item, the default comes from the **Default rental class** that you enter in the create dialog. If you leave that field blank, the default comes from the default row in **Rental class definition** on the released product, which is keyed by item number and configuration. Bulk fleet items get their default rental class the same way. A fleet item can belong to more than one rental class, as described in [Assign a fleet item to more than one rental class](#assign-a-fleet-item-to-more-than-one-rental-class). Learn more in [Configure inventory and location settings for rental management](configure-inventory-location-settings.md).
- **Address** – Address details for the fleet item, including its job site or location and the displayed postal address. The address follows the fleet item as you post fleet item movements. The **Update location** action is different: it moves a fleet item to another location in its current warehouse and doesn't change the fleet item's address.
- **Last SMU** – The most recent service meter unit (SMU) reading, shown with **Lifetime SMU** on the **Usage information** FastTab. The reading is critical for scheduling maintenance and calculating overtime charges (fees applied when a fleet item exceeds its contracted usage hours).
- **Bar code** – Maintain bar codes with **Bar codes** in the **Setup changes** group on the **Setup** tab. On **Fleet item availability**, the **Bar code** filter finds fleet items by bar code. Operations staff can scan a fleet item instead of entering its number or serial number manually during fleet item movement processing.
- **Attached to** – For an attachment (such as a bucket or forks), the prime fleet item it's connected to.

### Descriptive details

The fleet item master also captures descriptive details that the service department and rental coordinators use for reference. These details include the manufacture date and year, an optional **Fleet item feature**, a **Search name**, and a free-text **Note**. You change the note with **Change note**.

Some attributes are shared by every fleet item of the same model, such as the **Fuel type** (*Fuel* or *Diesel*), **Manufacturer**, and **Group code**. You define them once on the fleet item model rather than on each fleet item, and the fleet item reads them through its model, as described in the next section.

## Fleet item master data

Fleet items build on a small set of shared master data that you maintain under **Rental management (Preview)** > **Setup** > **Fleet items**. Keeping this master data consistent keeps every fleet item that points to a model consistent with it.

- **Fleet item models** – A model represents a specific make and model of fleet item, such as a particular skid steer. The model carries the attributes that are common to every fleet item of that model, including the **Fuel type** (*Fuel* or *Diesel*), **Manufacturer**, and **Group code**. When you create a fleet item and select its model, the dialog proposes **Not for sale**, **Eligible for service**, and **Attachment** from the model, and you can change them before you confirm. **Eligible for service** makes Dataverse create a serviceable asset for the fleet item, so that the service team can maintain it in Field Service. Learn more in [Rental management overview](rental-management-overview.md#maintenance-with-field-service). Fuel type, manufacturer, and group code stay on the model, so a correction there applies to every fleet item of that model. The model's **Miscellaneous** tab holds its remaining settings, including **Attached to**, **Vendor family**, and **Notice to owner exempt**. From the Action Pane you also maintain the model's **Attachment validity rules** and its **Checklist items**.
- **Manufacturers** – The list of manufacturers that fleet item models reference. A fleet item shows the manufacturer of its model.
- **Fleet item group codes** – A grouping that you apply to fleet item models to organize and report on them.
- **Fleet item features** – Capability codes that you assign to individual fleet items, one per fleet item in its **Fleet item feature** field. A feature records what a specific fleet item can do—for example, *auto grading*, *GPS guidance*, or a *cold-weather package*. Because two fleet items of the same model can be equipped differently, you set features on the fleet item rather than on the model.

Features are especially useful for matching a fleet item to a customer's requirement. The *fleet item availability* view displays the feature and lets you filter on it. A coordinator can quickly find an available fleet item that has the capability the customer needs—for example, an available skid steer with *auto grading*. Learn more in [Check fleet item availability and select fleet items](check-equipment-availability.md).

> [!NOTE]
> The price fields on the **Insurance** tab of the fleet item model don't set rental rates. Rental prices come from the rental rates that you set up per rental class. Learn more in [Set up rental rates and discounts](set-up-rental-rates-discounts.md).

## Assign a fleet item to more than one rental class

A fleet item isn't limited to a single rental class. The **Rental classes** page lists every class that you can rent a fleet item under, and flags one of them as the default.

To review or change the list, open a fleet item and, on the **Setup** tab of the Action Pane, in the **Rental class** group, select **Rental classes** to open the **Rental class definition** page. Each row names a **Rental class** that isn't a package, and exactly one row must be marked **Default**. If you delete every row, the **Default rental class** field on the fleet item is cleared as well, and you can no longer add the fleet item to a contract.

### Why a fleet item belongs to more than one class

A rental contract line carries a rental class, and it's that class—not the fleet item's own class—that determines the rate the customer pays.

Extra memberships are therefore what let a single fleet item serve demand in several classes:

- **Trade-downs** – A higher-specification fleet item that is also listed in a lower class can fill an order for that class, at that class's rate, without raising a class mismatch.
- **Overlapping classes** – A fleet item can sit in a size-based class and a capability-based class at the same time, so a coordinator finds it from either starting point.
- **Negotiated classes** – Add a fleet item to a secondary, lower-priced class that you use for long-term customers, and leave its everyday class as the default.
- **Class migration** – Add the new class before you retire the old one, so contracts written on either class keep working. To move a whole group of fleet items at once, use the **Rental class change** batch job instead. Learn more in [Run rental management periodic jobs](run-rental-periodic-jobs.md#update-rental-class-definitions).

A fleet item that you place on a line for a class it doesn't belong to is a rental class mismatch. The **Check on active**, **Check on assign**, and **Check on swap** parameters control what happens next. The mismatch can be ignored, logged as a rental class exception, refused outright, or let through and logged as an exception that also puts the document on hold. Review logged exceptions at **Rental management (Preview)** > **Inquiries and reports** > **History** > **Rental class exceptions**. Learn more in [The Fleet item validation FastTab](configure-rental-parameters.md#fleet-item-validation).

### What the default class still controls

The default class remains the fleet item's home class, and it's what the rest of the system reads:

- The **Default rental class** field on the fleet item, and the availability filter of the same name, which shows only fleet items whose *default* class is the one you select.
- Package matching, which compares a fleet item's default class against the component classes of a package.
- The revenue split across the fleet items on a package line.

Because rates are defined per rental class, a fleet item that belongs to several classes is quoted from a different rate table in each one. Learn more in [Set up rental rates and discounts](set-up-rental-rates-discounts.md).

## Understand fleet item status indicators

Each fleet item has three status indicators that work together to communicate the fleet item's current state. A fleet item is typically available for rent when the agreement status is *Available*, the physical status is *In stock*, and the service status is *Ready*. The system also folds the three statuses into one summarized **Availability status** that the availability grid shows, through a mapping that you configure. Learn more in [How the availability status is calculated and configured](check-equipment-availability.md#how-the-availability-status-is-calculated-and-configured).

### Agreement status

The agreement status indicates the fleet item's contractual state. Common values include:

| Status | Description |
|---|---|
| *Available* | Not assigned to any contract. Ready for rent or sale. |
| *Rental* | Assigned to an active rental contract. |
| *Lease* | Assigned to an active lease contract. |
| *Sale* | Assigned to a sales order but not yet shipped or invoiced. Still in stock. |
| *Sold* | Shipped and invoiced on a sales order. No longer in the rental business's inventory. |

> [!IMPORTANT]
> Agreement status alone doesn't decide whether you can sell a fleet item. A fleet item on a *Rental*, *Lease*, or *No-charge* agreement is checked against **Sales order validation** on the **Rental parameters** page, which allows it, asks you to confirm, or blocks it. The **Not for sale** flag on the fleet item blocks the fleet item from sales quotation lines and sales order lines. It also blocks quotation or order creation from the fleet item availability list, whatever the agreement status and fleet type are. Clear that flag on the fleet item before you add it to a sales document. A new fleet item takes the flag from its model.

### Physical status

The physical status tracks the fleet item's physical state and location across its full lifecycle, from procurement through deployment and return. Common values include:

| Status | Description |
|---|---|
| *Ordered* | A purchase order is placed and the fleet item is awaiting delivery. |
| *In transit* | The fleet item is in transit from a supplier or between locations. |
| *In stock* | The fleet item is at the rental business's facility. |
| *Ready* | The fleet item is ready to ship or rent. |
| *In shop* | The fleet item is in the service shop. |
| *Prepared* | Preparation is complete. |
| *On job site* | The fleet item is deployed at a customer's job site. |
| *To be shipped* | The fleet item is scheduled for outbound shipment. |
| *To be picked* | The fleet item is scheduled for customer pickup. |
| *Received* | The fleet item is received back at the facility. |
| *Delivered* | The fleet item is delivered to its destination. |
| *On hold* | The fleet item is on hold. |
| *Sold* | The fleet item is sold and no longer in the rental business's fleet inventory. |

Learn more in [Check fleet item availability and select fleet items](check-equipment-availability.md#physical-status).

## Track service status

The service status communicates operational readiness to the rental team. Most service statuses don't block transactions. The exception is *Hard down*, which the system enforces as a hard block. A fleet item in *Hard down* status can't be rented, sold, or added to a fleet item movement. You also can't select it as the replacement fleet item in a swap.

Learn more about all service status values and their operational impact in [Understand fleet item statuses](check-equipment-availability.md#understand-fleet-item-statuses).

Common service statuses include:

| Status | Description | System enforced? |
|---|---|---|
| *Ready* | Fleet item is available for rent. | - |
| *Hard down* | Fleet item has a major issue and is unavailable for an extended period (for example, an engine replacement, or a component removed to repair another fleet item while awaiting a back-ordered replacement). | **Yes** |
| *Under repair* | Fleet item is being repaired and should be available soon. | - |
| *Under preparation* | Fleet item is being prepared for the next rental (first service, detailing, or decal work). | - |
| *In shop* | Fleet item is in the service shop for a routine service call. | - |
| *Inspection* | Fleet item is undergoing an inspection before or after a rental. | - |
| *Preparation needed* | Fleet item needs a return-to-ready inspection. This is typically a quick-turn status. | - |

To update a fleet item's service status, follow these steps:

1. Open the fleet item master record.
1. In the **Service status** field, select the new status.
1. Optionally, select a **Reason code** to document why the status changed.
1. Select **Save**.

<!--
You can also change the service status in the Dynamics 365 Supply Chain Management mobile app: open a fleet item on a fleet item movement, select **Service status**, select the new status, and then select **Update status**. Learn more in [Use the Dynamics 365 Supply Chain Management mobile app](use-rental-mobile-app.md).
-->

> [!NOTE]
> A service status change is recorded in the service status history, including changes that come from a posted fleet item movement<!-- and from the Dynamics 365 Supply Chain Management mobile app-->.

## Review fleet item inquiries

The fleet item master provides several inquiry views that give you quick access to a fleet item's history. To access these inquiries, open a fleet item record and select the relevant option from the **Transactions**, **Rental**, **Fleet item**, or **Finance** groups on the **Inquiries** tab of the Action Pane.

- **Fleet item movement** – All fleet item movements associated with this fleet item, showing every shipment and return.
- **Swap history** – Records of every swap where this fleet item was exchanged for another.
- **Damage history** – All damage records, including the damage code, responsible customer, invoice reference, and repair status.
- **Attachment history** – A log of every attachment that was connected to this fleet item.
- **Usage history** – Service meter readings over time, showing how the fleet item's hours accumulate across rentals. To exclude a reading that you entered in error from usage, billing, and depreciation, select it and then select **Void reading**. A voided reading can't be restored.
- **Physical transactions** – A log in the **Transactions** group that records the fleet item's physical movements and status changes. For the fleet item's inventory transactions, use **Inventory transactions** in the same group.
- **Fleet type history** – A log in the **Finance** group that tracks changes to the fleet item's fleet type, with the from and to fleet types and the transaction date.
- **Rental contract history** – All rental contracts that have included this fleet item.
- **Rental quotation history** – All quotations that have included this fleet item.
- **Fleet item utilization** – Utilization figures for this specific fleet item.

## Related information

- [Rental management overview](rental-management-overview.md)
- [Understand rental management financial integration](understand-rental-financial-integration.md)
- [Set up rental rates and discounts](set-up-rental-rates-discounts.md)
- [Check fleet item availability and select fleet items](check-equipment-availability.md)
- [Ship and receive fleet items using fleet item movements](ship-receive-rental-equipment.md)
- [Add fleet items to the rental fleet](add-equipment-to-rental-fleet.md)
