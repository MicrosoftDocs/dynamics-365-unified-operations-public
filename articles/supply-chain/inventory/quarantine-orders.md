---
# required metadata

title: Quarantine orders
description: This article describes how to use quarantine orders to block inventory.
author: yufeihuang
ms.date: 03/23/2021
ms.topic: article
ms.prod:
ms.technology:

# optional metadata

ms.search.form: InventLocation, InventModelGroup, InventQuarantineOrder, InventQuarantineParmEnd, InventQuarantineParmReportFinished, InventQuarantineParmStartUp, InventTrans
# ROBOTS:
audience: Application User
# ms.devlang:
ms.reviewer: kamaybac
# ms.tgt_pltfrm:
ms.assetid: d5047727-653c-49da-b489-6fd3fe50445e
ms.search.region: Global
# ms.search.industry:
ms.author: yufeihuang
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Quarantine orders

[!include [banner](../includes/banner.md)]

This article describes how to use quarantine orders to block inventory.

Quarantine orders let you block inventory. For example, you might want to quarantine items for quality control reasons. Inventory that has been quarantined is transferred to a quarantine warehouse.

> [!NOTE]
> If you're using warehouse management processes (in the Warehouse management module), quarantine order processing is used only for return sales orders.

## Quarantine on-hand inventory items

When you quarantine items, you can either manually create the quarantine orders or set up the system to automatically create them during inbound processing.

To set up the system to automatically generate quarantine orders, follow these steps.

1. Go to **Inventory management \> Setup \> Inventory \> Item model groups**.
1. Select a relevant model group in the list pane, or create a new model group.
1. On the **Inventory policies** FastTab, select the **Quarantine management** check box.
1. Close the page.
1. In the **Quarantine warehouse** field for the receiving warehouses, specify a default quarantine warehouse.

When an item that is registered as received at the warehouse belongs to a model group where the **Quarantine management** check box is selected, the system generates a quarantine order for it. The quarantine order instructs workers to move the item to the quarantine warehouse.

When you manually create quarantine orders on the **Quarantine orders** page, the item doesn't have to be set up for quarantine management in the associated item model group. For this process, you must specify the on-hand inventory that should be quarantined and the quarantine warehouse that should be used. You can use the quarantine order statuses to help plan the process.

## Quarantine order statuses

Quarantine orders can have the following statuses:

- Created
- Started
- Reported as finished
- Ended

### Created

When a quarantine order has been created manually, but the item isn't yet in the quarantine warehouse, the quarantine order has a status of **Created**. Two inventory transactions are generated. One transaction is an issue transaction that can have a status of **On order**, **Reserved physical**, or **Picked**. The other transaction is a receipt transaction that can have a status of **Ordered** or **Registered** at the quarantine warehouse. You can reserve, pick, and register updates to the inventory by using the usual processes.

### Started

When a quarantine order has a status of **Started**, the inventory is transferred from the regular warehouse to the quarantine warehouse, and two inventory transactions are generated. One transaction has a status of **Deducted**, and the other transaction has a status of **Received**. At the same time, two inventory transactions are created to handle the return transfer. These transactions aren't dated. One transaction has a status of **Reserved physical**, and the other transaction has a status of **Ordered**.

### Reported as finished

To report a started quarantine order as finished, open the order, and select **Report as finished** on the Action Pane. The item is released from quarantine, but it isn't yet moved back to the regular warehouse. The movement back to the regular warehouse can be processed via an item arrival journal that can be initialized during the report as finished process.

### Ended

When a quarantine order is ended, the item is moved from the quarantine warehouse back to the regular warehouse. The status of the item transaction is set to *Sold* at the quarantine warehouse and *Purchased* at the regular warehouse.

## Quarantine order scrap

As part of the quarantine order process, you can scrap inventory. When you process scrap, the status of the inventory is set to *Sold* by an issue transaction from the quarantine warehouse.

## Additional resources

- [Inventory blocking](inventory-blocking.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
