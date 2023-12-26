---
# required metadata

title: Inventory blocking
description: This article provides an overview of inventory blocking, which is part of the quality inspection process in Supply Chain Management. You can use inventory blocking to prevent items from being processed or consumed.
author: yufeihuang
ms.date: 08/09/2022
ms.topic: article
ms.prod:
ms.technology:

# optional metadata

ms.search.form: InventBlocking, InventQualityOrderTable
# ROBOTS:
audience: Application User
# ms.devlang:
ms.reviewer: kamaybac
# ms.tgt_pltfrm:
ms.custom: 2094
ms.assetid: 1968e32f-eff9-4c17-8f7f-a870f0c38fbc
ms.search.region: Global
ms.search.industry: Distribution
ms.author: yufeihuang
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Inventory blocking

[!include [banner](../includes/banner.md)]

This article provides an overview of inventory blocking, which is part of the quality inspection process in Supply Chain Management. You can use inventory blocking to prevent items from being processed or consumed.

You can block inventory items in the following ways:

- Manually
- By creating a quality order
- By using a process that generates a quality order
- By using inventory status blocking

## Blocking items manually

You can block a quantity of an item by creating a transaction on the **Inventory blocking** page. Only items that are available as on-hand inventory can be blocked manually. For manually blocked quantities, you must decide whether planning activities include expected receipts as an expected on-hand quantity. Expected receipts are blocked items that you expect to be available as on-hand inventory after inspection is completed. You can maintain the expected date. By default, the **Expected receipts** option is selected for items that are blocked through a quality order. You can cancel a manual block on a quantity by deleting the transaction on the **Inventory blocking** page.

## Blocking items by creating a quality order

You can specify items that must be inspected by creating a quality order on the **Quality orders** page. When you create a quality order, the quantity that you specify for an item is blocked. The sampling plan that is associated with a quality order controls only the quantity of items that must be inspected, not the quantity that is blocked. The quantity that is entered on the quality order is the quantity that is blocked, regardless of the quantity that the sampling plan specifies should be sent for inspection.

> [!NOTE]
> Using both the batch expiry date and blocking inventory status features is not supported by master planning. This could result in double exclusion of on-hand inventory, which can occur during master planning. We recommend that you rely on batch disposition codes, instead of inventory status, for blocking expired batches.

## Blocking items by using a process that generates a quality order

If a quality process specifies that an item must be inspected, a quantity of the item is blocked automatically. Therefore, when a quality order is generated automatically, the item sampling plan that is associated with the quality order controls both the quantity of items that is blocked and the quantity that must be inspected. If the **Full blocking** option on the **Item sampling** page is selected, the full quantity of, for example, a purchase order line is blocked during inspection, regardless of the item sampling quantity.

### Example

In the following example, a quality order is generated when a purchase order packing slip is posted. On the **Quality associations** page, you specified that posting of a purchase order packing slip is the process that activates a quality order.

|Setup |User action |Result |
|----|---|---|
| A quality association specifies that a quality order must be generated when a purchase order packing slip is posted. The item sampling setup of the quality order specifies that 10 percent of the quantity on the purchase order line must be inspected. Furthermore, because the **Full blocking** option selected in the item sampling setup, the full quantity of the purchase order line must be blocked during inspection, regardless of the quantity that is sent for inspection. | The packing slip is posted. | A quality order is generated. Ten percent of the purchase order quantity for the item is sent to inspection. The full quantity of the purchase order line is blocked. |

## Blocking items by using inventory status blocking

You can specify which inventory statuses are blocking statuses by using the **Inventory blocking** parameter on the **Inventory statuses** page. You can't use inventory statuses as blocking statuses for production orders, sales orders, transfer orders, outbound transactions, or project integrations. For outbound work, use items that have an available inventory status. If items have a status of **Broken**, and master planning is run on those items, the items are considered missing, and inventory is automatically replenished.

## Take care when blocking items that use both inventory status blocking and quality order blocking

You can create a quality order associated with inventory having an inventory status that has its **Inventory blocking** parameter enabled. In this case, the quality order will generate an extra inventory blocking record in addition to the one created by the inventory status. Because the quality order inventory blocking will have the parameter **Expected receipts** enabled, this generates an extra *Ordered inventory* transaction that is also blocked by its inventory status. This combination can lead to difficulties in understanding the meaning of generated inventory transactions, because it will appear as though the total blocked quantity is in excess of the total quantity on hand. Let us examine the transactions on an example of a receipt of 10 pieces of item A0001 with a quality order generated to sample 1 piece. The behavior will also depend on whether the option **Reserve ordered items** is enabled on the **Inventory and warehouse management parameters** page.

>[!NOTE]
>If you are using inventory status blocking and quality orders together, we strongly recommend having the **Reserve ordered items** option enabled.

### Example with "Reserve ordered items" enabled

When **Reserve ordered items** is enabled, all inventory blocking transactions will have a status of either *Reserved physical* or *Reserved ordered*.

| Inventory transaction reference | Receipt | Issue | Quantity | Site | Warehouse | Inventory status | Location | License plate | Comment |
|---|---|---|---|---|---|---|---|---|---|
| Purchase order | Purchased | | 10 Pcs | 2 | 24 | Blocking | RECV | receiptLp1 | | 
| Inventory blocking | | Reserved physical | -9 Pcs | 2 | 24 | Blocking | | | Transaction generated by the inventory status blocking |
| Inventory blocking | | Reserved physical | -1 Pcs | 2 | 24 | Blocking | RECV | receiptLp1 | Transaction generated by the quality order sampling blocking |
| Inventory blocking | Ordered | | 1 Pcs | 2 | 24 | Blocking | RECV | receiptLp1 | Expected receipts from the quality order sampling blocking |
| Inventory blocking | | Reserved ordered | 1 Pcs | 2 | 24 | Blocking | | | Transaction generated by the inventory status blocking

### Example with "Reserve ordered items" disabled

When **Reserve ordered items** is disabled, the expected receipts can't be reserved because they are in status *Ordered*, so some blocking will be left in status *On order*.

| Inventory transaction reference | Receipt | Issue | Quantity | Site | Warehouse | Inventory Status | Location | License Plate | Comment |
|---|---|---|---|---|---|---|---|---|---|
| Purchase order | Purchased | | 10 Pcs | 2 | 24 | Blocking | RECV | receiptLp1 | |
| Inventory blocking | | Reserved physical | -9 Pcs | 2 | 24 | Blocking | | | Transaction generated by the inventory status blocking |
| Inventory blocking | | Reserved physical | -1 Pcs | 2 | 24 | Blocking | RECV | receiptLp1 | Transaction generated by the quality order sampling blocking |
| Inventory blocking | Ordered | | 1 Pcs | 2 | 24 | Blocking | RECV | receiptLp1 | Expected receipts from the quality order sampling blocking |
| Inventory blocking | | On order | 1 Pcs | 2 | 24 | Blocking | RECV | receiptLp1 | Transaction generated by the inventory status blocking

Note the difference in transaction status and dimensions between the two cases. For this reason, we recommend enabling the **Reserve ordered items** option.

## Disable expected receipts from quality orders that sample blocked inventory

To simplify the inventory transactions in the case of quality orders that sample inventory blocked as a consequence of inventory status, the system provides a feature that disables expected receipts from such quality orders. Because the expected receipt is immediately blocked by inventory status blocking, there is no reduction of on-hand inventory because of this change.

To use this feature, it must be turned on for your system. As of Supply Chain Management version 10.0.29, it's turned on by default. As of Supply Chain Management version 10.0.32, this feature is mandatory and can't be turned off. If you're running a version older than 10.0.32, then admins can turn this functionality on or off by searching for the *Disable expected receipts from quality orders that sample blocked inventory* feature in the [**Feature management** workspace](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Additional resources

[Create and maintain an inventory blocking](tasks/create-maintain-inventory-blocking.md)

[Quality management processes](quality-management-processes.md)

[Inspect the quality of goods](tasks/inspect-quality-goods.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]