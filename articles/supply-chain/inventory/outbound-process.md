---
title: Outbound process overview
description: Access an overview of the outbound process in Inventory management, including outlines about picking route status for sales and transfer orders and output orders.
author: banluo-ms
ms.author: banluo
ms.reviewer: kamaybac
ms.search.form: WMSOrder, WMSShipment, MCRPickingWorkbench, WMSPickingRegistration, CustomFilterGroup
ms.topic: how-to
ms.date: 04/30/2026
ms.custom: 
  - bap-template
---

# Outbound process overview

[!include [banner](../includes/banner.md)]

This article provides an overview of the outbound process in Inventory management.

## Output orders

Use output orders to link sales order lines and transfer order lines with the outbound picking processes that use picking lists.

When picking lists are generated from either sales orders or transfer orders, output orders and shipments are automatically created. A picking list has a one-to-one relationship with a shipment. The transfer order shipment or the sales order packing slip can be processed from the shipment.

The following diagram shows an overview of the process for outbound orders.

:::image type="content" source="media/outbound-order.png" alt-text="Overview of the outbound order process." lightbox="media/outbound-order.png":::

Set up outbound rules to define how the program should handle the outbound process. Use these rules to control the shipment process. In particular, use the rules to control which stage in the process a shipment can be sent during. The following settings define how the outbound processes are handled.

## Picking route status for sales and transfer orders

Go to **Account receivable** > **Setup** > **Account receivable parameters**, and then, on the **Updates** tab, select a value in the **Picking route status** field.

If the **Picking route status** field is set to **Completed**, the picking process occurs automatically as part of the process of generating picking lists. If the field is set to *Activated*, the picking list lines must be manually updated.

The same setup applies to transfer orders. Go to **Inventory management** > **Setup** > **Inventory and warehouse management parameters**, and then, on the **Transport** tab, select a value in the **Picking route status** field.

## End output inventory orders

Go to **Inventory management** > **Setup** > **Inventory and warehouse management parameters**. On the **General** tab, set the **End output inventory order** option.

When the warehouse worker reduces the picking list quantities, the corresponding inventory order quantities are removed from the shipment. When the picking list is updated at a point in time, the remaining quantities are reported back to the order if the **End output inventory order** option is set to *Yes*. If the **End output inventory order** option is set to *No*, the remaining quantities stay as an open output order quantity. They must be added to a new picking list as part of the **Open output orders** functionality.

## Reduce quantity

Use the **Reduce quantity** parameter as part of the process of generating picking lists. The setting of this parameter works together with the **Reservation** setting that triggers a reservation process as part of the release to the warehouse.

## Example of an outbound process for a sales order

For this example, there's a sales order for two items. During picking list generation, you select the **Reduce quantity** parameter. Therefore, you release and create picking lines only for available on-hand inventory. You must report the picking via a registration process for picking lists (**Picking route status** = *Activated*).

The inventory, which isn't already reserved, is reserved during picking list generation. The unavailable inventory can be either removed from the sales order or released to the warehouse for outbound processing later, when inventory is available for picking.

As soon as you pick all the picking lines on the **Picking list registration** page, the associated shipment is completed. The process for sales order packing slips can then be initialized based on the picked inventory.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
