---
title: Add fleet items to the rental fleet (preview)
description: Learn how to add fleet items through purchase orders, re-rentals, and movement journals, and how to transfer fleet items between fleet types.
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

# Add fleet items to the rental fleet (preview)

[!INCLUDE [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

Fleet items enter your rental fleet in several ways. You can purchase them, create them from a movement journal or from stock that you already have on hand, add bulk fleet items, and re-rent fleet items that you source from another rental business. Each route ends with the fleet transfer process, which moves the fleet item into the active rental fleet so that it can be rented.

## Purchase new fleet items

When you order new fleet items from a manufacturer or distributor, use a standard purchase order with rental-specific steps for serial number tracking and fleet item record creation. Fleet item numbers come from the fleet item number sequence on the **Number sequences** tab of **Rental management (Preview)** > **Setup** > **Rental parameters**, so set up that number sequence first.

To purchase new fleet items, follow these steps:

1. Go to **Procurement and sourcing** > **Purchase orders** > **All purchase orders** and create a new purchase order.
1. Select the vendor (manufacturer or distributor).
1. Add a line for the fleet item (for example, a medium compact track loader). Unless the product is a bulk fleet item, the line quantity is always 1 (or -1 on a return line), so add one line for each fleet item.
1. Select the **Configuration** if applicable. Use configurations to distinguish between variants such as enclosed cab versus open ROPS.
1. If **Fleet item ID creation** on the **Rental parameters** page is *With serial number*, enter the **Serial number** for the fleet item on the line details. If it's *Without serial number*, you can leave the serial number empty and enter it when the fleet item arrives, as described in [Enter serial numbers when fleet items arrive](#enter-serial-numbers-when-fleet-items-arrive). You choose the fleet type when you create the fleet item in the next step.
1. On the purchase order line, select **Fleet item** > **Create fleet item**. In the dialog, confirm the **Model**, which defaults from the released product, select a **Fleet type** whose **Value tracking method** is *Inventory*, such as *New*, optionally select a **Default rental class**, and then select **OK**.
1. Repeat for additional fleet items.
1. Confirm the purchase order. Every open line for a fleet item product needs a fleet item before you confirm the order and before you post the vendor invoice later.
1. Optionally, create an *inbound fleet item movement* (on the Action Pane, on the **Fleet item order** tab, in the **Inquiries** group, select **Fleet item movements**) to give the operations staff a receiving document with inspection checklists. <!-- After the movement is scheduled, it also appears in the Dynamics 365 Supply Chain Management mobile app, so the receiving worker can complete it on a device. Learn more in [Use the Dynamics 365 Supply Chain Management mobile app](use-rental-mobile-app.md). -->
1. Complete the **Product receipt** to bring the fleet items into inventory. Each line needs its serial number before you post the receipt.

After receiving, the fleet item is in inventory at the designated warehouse, in the fleet type that you selected when you created it. A fleet item can be rented only from a fleet type that the rental template allows, so you transfer it to a fleet type such as *Rental* first. That transfer assigns the fixed asset, so leave the fixed asset field on the purchase order line empty.

Open the order at **Rental management (Preview)** > **Common** > **Trade** > **All purchase orders** to work with it in the rental context. The lines then show two extra columns: **Fleet item line**, which tells you whether the product is set up as a fleet item, and **Fleet item**, which holds the fleet item number. On a line that has the status *Open order*, you can select **Fleet item** > **Attach to fleet item** to link the line to an existing fleet item instead of creating one. The fleet item must use the same product, and the same configuration when the product uses configurations. For a purchase, you can select only fleet items in a fleet type whose **Value tracking method** is *Canceled*. That's how you bring back a fleet item whose earlier purchase was canceled. To reach the rest of the order's rental values for the header, open the **Fleet item order** tab on the Action Pane and, from the **Manage** group, select **Rental information**. For a line, select **Fleet item** > **Rental information**.

### Enter serial numbers when fleet items arrive

Often you don't know the serial number of a fleet item until it arrives. You can order the fleet item and create it without a serial number, and enter the serial number on the purchase order line when the fleet item arrives, before you post the product receipt.

First, set these rental parameters at **Rental management (Preview)** > **Setup** > **Rental parameters**, on the **Fleet items** tab:

- **Fleet item ID creation** – *Without serial number*, so that you can create the fleet item for a purchase order line that doesn't have a serial number yet.
- **Serial number update** – Turned on, so that **Serial number update** is available on purchase order lines that have a fleet item.

To enter the serial number when a fleet item arrives, follow these steps:

1. Create the purchase order line without a serial number, select **Fleet item** > **Create fleet item**, and confirm the purchase order, as described earlier in this article.
1. When the fleet item arrives, select its purchase order line, and then select **Serial number update** on the lines toolbar.
1. Enter the **Serial number**, and then select **OK**. The system sets the serial number on the purchase order line and on its fleet item. Another active fleet item of the same product can't already use it.
1. Post the product receipt.

**Serial number update** is available on a purchase order line that has a fleet item and the status *Open order*.

> [!IMPORTANT]
> Always enter the serial number with **Serial number update** before you post the product receipt. Don't register serial numbers during receiving instead—for example, by using **Registration** on the purchase order line or an item arrival journal. A fleet item gets its serial number only through **Serial number update**.

## Create fleet items from existing inventory

A fleet item doesn't have to come from a purchase order. You can create one from an inventory movement journal line, or from stock that you already have on hand, which is how you bring an existing fleet into rental management.

To create a fleet item from a movement journal line, follow these steps:

1. On the journal line for a product that you set up as a fleet item, select **Create fleet item**. If **Fleet item ID creation** on the **Rental parameters** page is *With serial number*, enter the serial number on the line first.
1. In the **Create fleet item** dialog, confirm the **Model**, select a **Fleet type** whose **Value tracking method** is *Inventory*, complete the remaining details, and then select **OK**. The system creates the fleet item with the physical status *Ordered*.
1. Post the journal. When you post a receipt line, the system sets the fleet item's received date to the journal date. When you post an issue line, the system moves the fleet item to the fleet type whose **Value tracking method** is *Canceled* and sets its agreement status to *Not available*.

To create fleet items from stock that you already have on hand, follow these steps:

1. Go to **Rental management (Preview)** > **Common** > **Fleet items** > **Create fleet item from inventory**.
1. On the **Serialized fleet items** tab, select an on-hand row that has no fleet item yet. The **Bulk fleet items** tab covers bulk fleet items, as described in [Add bulk fleet items to the rental fleet](#add-bulk-fleet-items-to-the-rental-fleet).
1. Select **Create fleet item**.
1. In the dialog, select the **Model**, which fills in the manufacturer, and set **Fleet item name**, **Not for sale**, **Eligible for service**, **Attached to fleet item**, **Default rental class**, and **Manufacture year** as needed. If you leave the default rental class blank, the fleet item takes the default from the **Rental class definition** rows on the released product.
1. Select a **Fleet type** whose **Value tracking method** is *Inventory*, and then select **OK**. The system creates the fleet item with the physical status *In stock*.

In both cases, transfer the fleet item to a fleet type whose **Value tracking method** is *Fixed asset* before you rent it.

## Add bulk fleet items to the rental fleet

A bulk fleet item is one fleet item record for a product and its product dimensions that holds quantities per fleet type and location, instead of one record for each serialized fleet item. To use it, set **Fleet item type** to *Bulk fleet item* on the released product.

To assign on-hand quantity to a bulk fleet item, follow these steps:

1. Go to **Rental management (Preview)** > **Common** > **Fleet items** > **Create fleet item from inventory**, and select the **Bulk fleet items** tab. Each row shows an on-hand quantity and the **Assigned quantity** that already belongs to a bulk fleet item.
1. On a row that has no bulk fleet item yet, select **Create fleet item**. Enter the **Fleet item number**, **Fleet item name**, and **Quantity**, select a **Fleet type** whose **Value tracking method** is *Inventory* and a **Default rental class**, and then select **OK**. **Model** and **Manufacture year** aren't used for a bulk fleet item. If a bulk fleet item already exists for the product, its details are locked and the quantity is added to it.
1. To change the quantity later, select the row and then select **Adjust quantity**. Enter the **New assigned quantity**, which can be anything from zero up to the available physical quantity.

The assigned quantity is held by an inventory blocking record for the product and its inventory dimensions, so other processes can't consume it. The system releases it when the quantity is transferred into a fleet type whose **Value tracking method** is *Fixed asset*. **Create fleet item** on a purchase order line or a movement journal line for a bulk product adds the received quantity to the bulk fleet item in the same way.

You move a quantity of a bulk fleet item between fleet types with the same transfer request as other fleet items, as described in [Transfer fleet items between fleet types](#transfer-fleet-items-between-fleet-types).

The change actions on the fleet item master, and the commands that create sales orders and sales quotations from fleet item availability, aren't available for bulk fleet items.

## Add re-rent fleet items

When you don't own a fleet item that a customer needs, you can source it from another rental business and rent it out as a **re-rent** fleet item. Re-rent fleet items use a fleet type whose **Value tracking method** is *Manual*, such as *Re-rent*. Because you don't own them, they aren't backed by inventory or a fixed asset, so you don't create them through the purchase and receipt flow.

To add a re-rent fleet item, follow these steps:

1. Go to **Rental management (Preview)** > **Common** > **Fleet items** > **Fleet items**.
1. Select **New**. In the **Create fleet item** dialog, set **Fleet type** to a fleet type whose **Value tracking method** is *Manual*, such as *Re-rent*.
1. Select the **Model**. The model is required. The manufacturer ID and manufacturer name are read-only and are filled in from the model, so you can't enter a manufacturer yourself. Selecting the model also proposes the **Fleet item name**, which is required.
1. Select the **Fleet location**. The fleet location is required, and you can select only a hub or a hub location. The fleet item's address is set to that fleet location, and its fleet item movements start from there.
1. Select the **Item number** of the released product that the fleet item is rented as, and enter the **Serial number**. You can't add or change the item number later. Only a fleet item that has an item number appears in fleet item availability, so enter it for any re-rent fleet item that you intend to rent out. No other active fleet item with the same item number can have the same serial number.
1. Complete the remaining details on the dialog as needed: **Default rental class**, **Manufacture year**, **Not for sale**, **Eligible for service**, **Attachment**, and **Attached to fleet item**. If you leave the default rental class blank, the fleet item takes the default rental class of the released product. **Eligible for service** drives creation of the matching record in Dataverse for Field Service.

> [!NOTE]
> Creating a fleet item directly with **New** on the Fleet items form is supported only for fleet types whose **Value tracking method** is *Manual*, such as *Re-rent*. Owned fleet items are brought into the fleet through the purchase and receipt flow.
>
> **New** on the Fleet items page accepts only fleet types whose **Value tracking method** is *Manual*, such as *Re-rent*. **Create fleet item** on a purchase order line or an inventory movement journal line accepts only fleet types whose **Value tracking method** is *Inventory*.

You rent out re-rent fleet items to your customers on rental contracts the same way as owned fleet items—they appear in availability, and you can add them to contract lines and activate them. The rental template of the quotation or contract must allow the *Re-rent* fleet type under **Fleet type** before re-rent fleet items appear in availability for the document and you can add them to it. Learn more in [Configure fleet type eligibility](set-up-rental-templates.md#configure-fleet-type-eligibility).

## Transfer fleet items between fleet types

A fleet item starts in the fleet type that you selected when you created it. A fleet item that comes from a purchase order, a movement journal, or stock on hand starts in a fleet type whose **Value tracking method** is *Inventory*. Before you rent it, transfer it to a fleet type that the rental template allows, typically *Rental*.

Fleet types are setup data that you create and maintain at **Rental management (Preview)** > **Setup** > **Fleet items** > **Fleet types**, typically *New*, *Rental*, *Lease*, *Used*, *Re-rent*, *Customer*, and *Canceled*. Each fleet type has a **Value tracking method**, which decides how the system tracks the value of the fleet items in it and which fleet transfers it can take part in. Learn more in [Fleet types](rental-management-overview.md#fleet-types) and [Configure inventory and location settings for rental management](configure-inventory-location-settings.md#configure-fleet-types).

Not every pair of fleet types can be transferred. Before you can save a transfer request, **Rental management (Preview)** > **Setup** > **Transfers** > **Transfer rules** must hold a row for the exact **Fleet from** and **Fleet to** fleet types. The system then processes the transfer when the value tracking methods of the two fleet types are one of these combinations:

- *Inventory* to *Fixed asset*
- *Fixed asset* to *Inventory*
- *Fixed asset* to *Fixed asset*

With the fleet types in the preceding example, that means *New* or *Used* to *Rental* or *Lease*, *Rental* or *Lease* to *New* or *Used*, and *Rental* to *Lease* or back. Any other combination, including *Inventory* to *Inventory* and anything that involves a *Manual*, *Customer*, or *Canceled* fleet type, is outside the supported set. **Fleet from** and **Fleet to** can't be the same, and each fleet item that you assign must be *Available* and have an item number and a serial number. Learn more in [Supported fleet transfers](configure-inventory-location-settings.md#supported-fleet-transfers).

To transfer fleet items between fleet types, follow these steps:

1. Go to **Rental management (Preview)** > **Common** > **Fleet items** > **Transfer requests** and create a new transfer request.
1. Set **Fleet from** (for example, *New*) and **Fleet to** (for example, *Rental*). Set **Move to fleet location** when you transfer from a fleet type whose **Value tracking method** is *Inventory* to one that is *Fixed asset*. Set **Move to warehouse** when you transfer the other way. You can also set **Move to location** to place the fleet item in a warehouse location. The fleet location that you select becomes the fleet item's fleet location and address.
1. Select **Assign fleet item**, and then mark the fleet items that you want to move. When **Transfer attachments** is turned on on the **Rental parameters** page, the attachments connected to a fleet item are marked with it. For a bulk fleet item, mark the row and enter the **Quantity to add**; the request line then shows that amount as the **Transfer quantity**, which is always 1 for other fleet items. **Approve request** becomes available after you assign at least one fleet item.
1. Select **Approve request**.
1. **Send** the transfer for processing.
1. Select **Approve transfer**. This command becomes enabled only after the request is sent, and a different user might handle this step, depending on your workflow.
1. **Transfer** the fleet item to complete the request. The transfer status changes to *Transferred*.

When the fleet item is transferred to a fleet type whose **Value tracking method** is *Fixed asset* (for example, *Rental*), the system automatically:

- Creates a *fixed asset* for the fleet item, or reuses the fleet item's existing fixed asset. The fixed asset takes the fixed asset group and book specified on the **Posting configuration for fleet types** page for the target fleet type and the fleet item's item group. Unless **Autonumber fixed assets** is selected for the fixed asset group or in the fixed assets parameters, the fixed asset ID matches the fleet item ID.
- Issues the fleet item from inventory and posts the fixed asset acquisition at the fleet item's posted inventory cost value.
- Opens the appropriate **depreciation books** (for example, rental depreciation books with revenue-based depreciation).
- Updates the fleet item's fleet type on the fleet item master.

A bulk fleet item gets one fixed asset for each fleet type whose **Value tracking method** is *Fixed asset*, and a later transfer of more quantity into the same fleet type adds to that fixed asset. Review them at **Rental management (Preview)** > **Common** > **Fleet items** > **Bulk fleet item—fixed asset**, which lists the fleet item, the fleet type, and the fixed asset.

When you later move a fleet item out of the rental fleet, the result depends on the target fleet type. A transfer to a fleet type whose **Value tracking method** is *Inventory* (for example, *Used*) disposes of the fixed asset and receives the fleet item back into inventory at its net book value. A transfer to another fleet type whose **Value tracking method** is *Fixed asset* (for example, *Lease*) moves the fixed asset into the target fleet type's book when the books differ. The fleet item can then use a different depreciation profile. Fleet transfer rules record which of the supported fleet-to-fleet combinations your organization allows.

Learn more about the financial transactions and GL postings that occur during fleet transfers in [Understand rental management financial integration](understand-rental-financial-integration.md).

### Automatic fleet transfers

You start most fleet transfers manually, as described earlier in this article. In a few circumstances, the system moves a fleet item to a different fleet type automatically:

- **On purchase cancellation** – If the originating purchase is canceled or reversed, the system moves the fleet item to the *Canceled* fleet and sets its physical and agreement status to *Not available*.
- **On a rental purchase option (RPO) buyout** – When a contract uses the rental purchase option transfer process, initiating the buyout automatically creates a transfer request that targets the fleet configured for the option. Only the creation is automatic. The system creates the request with the status *Created*. Before the fleet item changes fleet, process it through **Approve request**, **Send**, **Approve transfer**, and **Transfer** on the **Rental purchase option transfer requests** page at **Rental management (Preview)** > **Common** > **Rental contracts**. On the **Transfer requests** page, these commands aren't available for a request that comes from a rental contract.
- **On sale** – When you post the customer sales invoice, the fleet item automatically moves to the *Customer* fleet, which is customer-owned but still tracked and potentially serviced by the rental business. The system sets its agreement status to *Sold* and records the sell date and buying customer. Fleet item availability adds only fleet items in a fleet type whose **Value tracking method** is *Inventory* to a sales order or a sales quotation. Transfer a fleet item that's tracked as a fixed asset to such a fleet type before you sell it. If you credit the sales invoice, the sale is reversed: the fleet item returns to the fleet type it had before the sale, its agreement status becomes *Available*, and the customer and sell date are cleared.

## Related information

- [Rental management overview](rental-management-overview.md)
- [Understand rental management financial integration](understand-rental-financial-integration.md)
- [Manage fleet item master data](manage-equipment-master-data.md)
- [Check fleet item availability and select fleet items](check-equipment-availability.md)
- [Ship and receive fleet items using fleet item movements](ship-receive-rental-equipment.md)
- [Track rental fleet utilization](track-rental-fleet-utilization.md)
