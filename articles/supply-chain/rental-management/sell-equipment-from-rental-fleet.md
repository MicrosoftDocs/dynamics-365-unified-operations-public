---
title: Sell fleet items from the rental fleet (preview)
description: Learn how to sell fleet items to customers with sales orders, sales quotations, and sales outbound fleet item movements.
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

# Sell fleet items from the rental fleet (preview)

[!INCLUDE [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

You can sell a fleet item in several common scenarios:

- A fleet item reaches the end of its useful rental life, and you retire it through a sale.
- A customer who is renting a fleet item decides to purchase it. When the contract is a rental purchase option contract, start the buyout with **Rental purchase option transfer** on the contract. Learn more in [The Rental purchase option parameters FastTab](set-up-rental-templates.md#the-rental-purchase-option-parameters-fasttab).
- A customer wants to buy a used fleet item outright, without renting it first.

In each case, you sell the fleet item by using a sales order with a sales outbound fleet item movement for delivery and inspection.

> [!NOTE]
> You can only sell fleet items out of inventory fleets. To sell a fleet item that's in the rental fleet, first do a fleet transfer into an inventory fleet, which eliminates the associated fixed asset.

> [!TIP]
> Sometimes a customer wants a *specific* fleet item that's on an active rental contract—for example, because it has the right range of service meter units (SMU) or the exact features or configuration they need. In that case, swap the on-rent fleet item for another comparable one so the desired fleet item becomes free to sell. Learn more in [Manage fleet item swaps, substitutions, and transfers](manage-equipment-swaps-substitutions-transfers.md).

## Create a sales order for a fleet item

The sales process for fleet items follows the standard Dynamics 365 Finance and Supply Chain Management sales order workflow with extra steps for fleet item tracking.

To create a sales order for a fleet item, follow these steps:

1. If the fleet item is in a fleet type whose **Value tracking method** is *Fixed asset*, first do a fleet transfer into a fleet type whose **Value tracking method** is *Inventory*. This transfer removes the associated fixed asset. Set **Move to warehouse** on the transfer request to the warehouse that the fleet item is received into and sold from. Learn more in [Transfer fleet items between fleet types](add-equipment-to-rental-fleet.md#transfer-fleet-items-between-fleet-types).
1. Go to **Rental management (Preview)** > **Common** > **Fleet items** > **Fleet item availability**.
1. The list hides fleet items that are on a rental contract, on order, reserved, or on an open sales order. To include them, select **Show all**.
1. Select the **Marked** check box for the fleet item. On the **Fleet items** tab, in the **Sales** group, select **Sales order**.
1. In the **Set up fields to create sales order** dialog, enter the **Customer account** and **Invoice customer**. Add a **Currency** and a **Customer requisition** if needed, and then select **OK**. The system creates the sales order for the marked fleet items and opens it. Each fleet item gets a sales order line whose text adds the fleet item number, model, manufacturer, serial number, fleet type, and usage to the product name.
1. Adjust the price as needed.
1. Confirm the sales order and process it by using the standard sales processes. When you post the sales invoice, the fleet item moves to the fleet type whose **Value tracking method** is *Customer*, and its agreement status becomes *Sold*. The sell date, the buying customer, and the fixed asset book that the fleet item was disposed from are recorded on the fleet item. Learn more in [Add fleet items to the rental fleet](add-equipment-to-rental-fleet.md#automatic-fleet-transfers).

You handle delivery and inspection of the sold fleet item on a sales outbound fleet item movement, in the same way as a rental shipment. Learn more in [Ship and receive fleet items using fleet item movements](ship-receive-rental-equipment.md).

> [!NOTE]
> A fleet transfer alone doesn't make a fleet item sellable. A fleet item that has **Not for sale** set to *Yes* can't be added to a sales quotation line or a sales order line. You also can't create an order or a quotation for it from the fleet item availability list. This rule applies regardless of the agreement status and the fleet type. Clear **Not for sale** on the fleet item before you sell it.

### Work with fleet items on a sales order

Open the order at **Rental management (Preview)** > **Common** > **Trade** > **All sales orders** to work with it in the rental context. The lines then show two extra columns: **Fleet item line**, which tells you whether the product is set up as a fleet item, and **Fleet item**, which holds the fleet item number. On a fleet item line, select the fleet item in **Fleet item**. The lookup lists the fleet items of the line's product, with their serial number and statuses, and the line takes its inventory dimensions from the one you select. Orders that you create from a rental contract, from fleet item availability, from an invoice schedule, or from the combined order inquiry open in this context as well.

The order's other rental values are on the **Rental information** pages:

- On the Action Pane, open the **Fleet item order** tab and, from the **Manage** group, select **Rental information** to open **Rental sales order information**. The **Rental sales header** tab holds the rental contract, **Ship to**, job site, pickup fleet location, invoice schedule, and notice to owner. The **Rental lines** tab lists each line with its fleet item and the fleet item's agreement, physical, and service status, together with **Ship to**, job site, pickup fleet location, **Attached to a line**, and **Over allowance**.
- On a fleet item line, select **Fleet item line** > **Rental information** to open the same rental fields for that one line.

### Create a sales order from a rental contract

When the customer who is renting the fleet item decides to buy it, start from the contract instead of from the availability list. Open the rental contract and, on the Action Pane, on the **Rental** tab, in the **New** group, select **Sales order**. The sales order takes the customer account, invoice account, ship-to setting, pickup fleet location, job site, and delivery address from the contract, and the system links the order back to the contract. If the fleet item is still on the contract when you add it to a sales order line, the **Sales order validation** rental parameter decides what happens: *None* allows it, *Prompt* asks you to confirm, and *Error* blocks it.

## Create a sales quotation for a fleet item

Start with a sales quotation when the customer wants a formal quote before committing. On **Fleet item availability**, mark the fleet item and, in the **Sales** group, select **Sales quotation**, and then complete the **Create sales quotation** dialog. The quotation path differs from the sales order path in the following ways:

- The sales order path requires a customer account.
- The sales quotation path accepts either a customer account or a prospect. If the prospect is already linked to a customer account, the quotation uses that account.
- The sales quotation path also creates an opportunity for the quotation, so you can track the deal before a customer account exists.

Sales quotations for fleet items open at **Rental management (Preview)** > **Common** > **Trade** > **All quotations**, and they carry the same rental fields as sales orders. On the Action Pane, open the **Fleet item order** tab and, from the **Manage** group, select **Rental information** to open **Rental sales quotation information**, which has the same **Rental sales header** and **Rental lines** tabs. On a line, select **Fleet item line** > **Rental information** for that line alone, or **Fleet item line** > **Fleet item availability** to select a fleet item. Learn more in [Work with fleet items on a sales order](#work-with-fleet-items-on-a-sales-order).

## Related information

- [Rental management overview](rental-management-overview.md)
- [Manage fleet item master data](manage-equipment-master-data.md)
- [Ship and receive fleet items using fleet item movements](ship-receive-rental-equipment.md)
- [Add fleet items to the rental fleet](add-equipment-to-rental-fleet.md)
