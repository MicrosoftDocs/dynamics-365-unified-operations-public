---
title: Quarantine orders
description: Learn how to use quarantine orders to block inventory, including an outline and step-by-step process on quarantine on-hand inventory.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form: InventLocation, InventModelGroup, InventQuarantineOrder, InventQuarantineParmEnd, InventQuarantineParmReportFinished, InventQuarantineParmStartUp, InventTrans
ms.topic: how-to
ms.date: 05/27/2026
ms.update-cycle: 1095-days
ms.custom:
  - bap-template
  - evergreen
---

# Quarantine orders

[!include [banner](../includes/banner.md)]

This article describes how to use quarantine orders to block inventory.

Quarantine orders block inventory. For example, you might want to quarantine items for quality control reasons. When you quarantine inventory, it gets transferred to a quarantine warehouse.

> [!NOTE]
> If you're using warehouse management processes (WMS), quarantine order processing only applies to return sales orders.

## Quarantine on-hand inventory items

When you quarantine items, you can either manually create the quarantine orders or set up the system to automatically create them during inbound processing.

To set up the system to automatically generate quarantine orders, follow these steps:

1. Go to **Inventory management \> Setup \> Inventory \> Item model groups**.
1. Select a relevant model group in the list pane, or create a new model group.
1. On the **Inventory policies** FastTab, select the **Quarantine management** check box.
1. Close the page.
1. In the **Quarantine warehouse** field for the receiving warehouses, specify a default quarantine warehouse.

When an item that is registered as received at the warehouse belongs to a model group where the **Quarantine management** check box is selected, the system generates a quarantine order for it. The quarantine order instructs workers to move the item to the quarantine warehouse.

When you manually create quarantine orders on the **Quarantine orders** page, the item doesn't need to be set up for quarantine management in the associated item model group. For this process, you must specify the on-hand inventory that you want to quarantine and the quarantine warehouse that you want to use. You can use the quarantine order statuses to help plan the process.

## Quarantine order statuses

Quarantine orders can have the following statuses:

- Created
- Started
- Reported as finished
- Ended

### Created

When you manually create a quarantine order but don't yet place the item in the quarantine warehouse, the quarantine order has a status of *Created*. This status generates two inventory transactions. One transaction is an issue transaction that can have a status of *On order*, *Reserved physical*, or *Picked*. The other transaction is a receipt transaction that can have a status of *Ordered* or *Registered* at the quarantine warehouse. You can reserve, pick, and register updates to the inventory by using the usual processes.

### Started

When a quarantine order has a status of *Started*, the inventory is transferred from the regular warehouse to the quarantine warehouse, and two inventory transactions are generated. One transaction has a status of *Deducted*, and the other transaction has a status of *Received*. At the same time, two inventory transactions are created to handle the return transfer. These transactions aren't dated. One transaction has a status of *Reserved physical*, and the other transaction has a status of *Ordered*.

### Reported as finished

To report a started quarantine order as finished, open the order, and select **Report as finished** on the Action Pane. The item is released from quarantine, but it isn't yet moved back to the regular warehouse. You can process the movement back to the regular warehouse through an item arrival journal that you can initialize during the report as finished process.

### Ended

When you end a quarantine order, move the item from the quarantine warehouse back to the regular warehouse. The status of the item transaction is set to *Sold* at the quarantine warehouse and *Purchased* at the regular warehouse.

## Quarantine order scrap

As part of the quarantine order process, you can scrap inventory. When you process scrap, the status of the inventory is set to *Sold* by an issue transaction from the quarantine warehouse.

## Related information

- [Inventory blocking](inventory-blocking.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
