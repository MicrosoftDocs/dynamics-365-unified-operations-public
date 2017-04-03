---
# required metadata

title: Quarantine orders
description: This article describes how quarantine orders are used to block inventory. 
author: YuyuScheller
manager: AnnBe
ms.date: 2017-04-04
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: InventLocation, InventModelGroup, InventQuarantineOrder, InventQuarantineParmEnd, InventQuarantineParmReportFinished, InventQuarantineParmStartUp, InventTrans
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 2084
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 30021
ms.assetid: d5047727-653c-49da-b489-6fd3fe50445e
ms.search.region: Global
# ms.search.industry: 
ms.author: perlynne
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Quarantine orders

This article describes how quarantine orders are used to block inventory. 

Quarantine orders can be used to block inventory. For example, you might want to quarantine items for quality control reasons. Inventory that has been quarantined is transferred to a quarantine warehouse. **Note:** If you're using advanced warehouse management processes (in Warehouse management), quarantine order processing is used only for return sales orders.

## Quarantine onhand inventory items
When you quarantine items, you can either create the quarantine orders manually or set up the system to create the quarantine orders automatically during inbound processing. To create quarantine orders automatically, select the **Quarantine management** option on the **Inventory policies** tab on the **Item model groups** page. You must also specify a default quarantine warehouse in the **Quarantine warehouse** field for the receiving warehouses. When the physically on-hand inventory is recorded in a purchase order or production order, quarantined items are automatically moved to a quarantine warehouse in Microsoft Dynamics 365 for Operations. This movement occurs because the status of the quarantine order is changed to **Started**. When you create quarantine orders manually, the item doesn't have to be set up for quarantine management in the associated item model group. For this process, you must specify the on-hand inventory that should be quarantined and the quarantine warehouse that should be used. You can use the quarantine order statuses to help plan the process.

## Quarantine order statuses
Quarantine orders can have the following statuses:

-   Created
-   Started
-   Reported as finished
-   Ended

### Created

When a quarantine order has been created manually, but the item isn't yet in the quarantine warehouse, the quarantine order has a status of **Created**. Two inventory transactions are generated. One transaction is an issue transaction that can have a status of **On order**, **Reserved physical**, or **Picked**. The other transaction is a receipt transaction that can have a status of **Ordered** or **Registered** at the quarantine warehouse. You can reserve, pick, and register updates to the inventory by using the usual processes.

### Started

When a quarantine order has a status of **Started**, the inventory is transferred from the regular warehouse to the quarantine warehouse, and two inventory transactions are generated. One transaction has a status of **Deducted**, and the other transaction has a status of **Received**. At the same time, two inventory transactions are created to handle the return transfer. These transactions aren't dated. One transaction has a status of **Reserved physical**, and the other transaction has a status of **Ordered**.

### Reported as finished

By clicking **Report as finished**, you can report a started quarantine order as finished. The item is released from quarantine but isn't yet moved back to the regular warehouse. The movement back to the regular warehouse can be procesed via an Item arrival journal that can be initialized during the Report as finished process.

### Ended

When a quarantine order is ended, the item is moved from the quarantine warehouse back to the regular warehouse. The status of the item transaction is set to **Sold** at the quarantine warehouse and **Purchased** at the regular warehouse.

## Quarantine order scrap
As part of the quarantine order process, you can scrap inventory. When you process scrap, the status of the inventory will be set to **Sold** by an issue transaction from the quarantine warehouse.

See also
--------

[Inventory blocking](inventory-blocking.md)

