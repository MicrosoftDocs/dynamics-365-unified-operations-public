---
# required metadata

title: Inventory posting profiles
description: This topic provides an overview of inventory posting profiles.  
author: rachelprofitt
ms.date: 04/25/2022
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: InventPosting, InventTrans
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.custom: 24651
ms.assetid: cb82245e-8c02-429c-b36e-8db0e3e6f7e5
ms.search.region: Global
# ms.search.industry: 
ms.author: raprofit
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Inventory posting profiles

[!include [banner](../includes/banner.md)]

Inventory posting profiles control the posting of inventory subledger transactions to the general ledger. Inventory subledger transactions may be generated from many 
modules including **Sales and marketing**, **Procurement and sourcing**, **Production control**, and more. Inventory subledger transactions may be posted
any time an item is used in a sales order or purchase order. For example, additional inventory subledger transactions may be posted each time a document is 
updated, when a sales order packing slip or invoice is posted, or when a purchase order product receipt or invoice is generated.

For more information, see to Inventory subledger transactions.

## Inventory transaction overview

Each inventory subledger transaction contains the quantity, price, and specific inventory details such as the site, warehouse, location, and so on. Inventory subledger
transactions have two connections to the general ledger through the physical posting and the financial posting. For more information, see to 
[Physical and financial updates](/supply-chain/cost-management/physical-financial-updates.md).

Consider the following example of a purchase order with three lines. For this example, assume that the entire order is for a single site and warehouse.
Each purchase order line has a single related InventTrans record also known as an inventory transaction and each line is for a quantity of 10. The 
following diagram shows the relationship of one purchase order header, to three purchase order lines, each with one InventTrans record.

[![Relationship diagram for a purchase order with three lines each with one InventTrans record.](./media/InventTransRelationship.PNG)](./media/InventTransRelationship.PNG)

A quantity of 5 is received on the first purchase order line, the full quantity for the second line and nothing on the third line of the 
purchase order. There is now a second inventory transaction related to the first purchase order line. The transaction for the second purchase order line will be
updated to received, and the third transaction will remain the same. The following diagram shows the relationship with the additional InventTrans record for purchase
order line 1.

[![Relationship diagram for a purchase order with three lines. One line is partially received and shows two InventTrans records.](./media/InventTransRelationshipPartialReceipt.PNG)](./media/InventTransRelationshipPartialReceipt.PNG)

In this example, a voucher will be posted to the general ledger that is the physical voucher. In this example, the item model group is configured to post physical 
inventory, and all items use the same item model group. The inventory posting profile is using a single set of main accounts, a single voucher will be created and the
InventTrans record will link both InventTrans 1 and InventTrans 2 to the same voucher.

Next, an invoice is received for the quantity that is received on lines 1 and 2. Another voucher is created in the general ledger that is the financial voucher. 
The item model group is configured to post financial inventory. The new second voucher is related to InventTrans 1 and InventTrans 2.

Depending on the costing model, a third general ledger posting may exist for your inventory subledger transactions related to the closing and settlement
of the inventory. For more information, see [Inventory close](/supply-chain/cost-management/inventory-close.md). You can view the details of all inventory 
transactions by going to **Inventory management > Inquiries and reports > Transactions**.

>[!Important]
> The inventory transactions will be split for each unique combination of inventory dimensions and for each partial update. This was shown in the example above for 
partial updates.

### Split inventory based on inventory dimension example

The purchase order line 3 in the example is a serialized item. 10 serial numbers are registered for the purchase order during the receiving process. The inventory 
transaction will be split into 10 inventory transactions. 
The following diagram shows the relationship and additional inventory transaction each with their own serial number related to purchase order
line 3.

[![Relationship diagram for a purchase order with three lines. One line is serialized and shows addditional InventTrans records](./media/InventTransRelationshipSerialNumber.PNG)]

In the example above, if each serial number is received on a single product receipt, there would be one additional voucher created. The physical voucher field will
be linked to each serial number. The same is true for the financial update when you invoice the purchase order.

## Inventory transactions
You can view inventory transcations on the **Inventory transcations** page from the main menu under **Inventory and warehouse management** or
**Cost management** modules. You can also view inventory transactions related to a specific source document line such as a purchase order line or sales order line by 
clicking **Inventory** and selecting **Transactions**. 
The **Inventory transactions** page contains the following fields:

| Field            | Description                                                                                                                                                                                                                                                                        |
|------------------|------------------------------------------------------------------------------------------------------------------------------------------------|
| Item number      | The item number related to the transaction.                                                                                                                                                                                                                                        |
| Physical date    | The date the inventory arrives at the warehouse, leaves the warehouse, is consumed in production, or is produced. For example, the posting date on
the packing slip posting for a sales order, or of the product receipt posting for a purchase order.                             |
| Financial date   | The date the inventory transaction is closed and the cost is recorded in the general ledger. For example, the posting date on the invoice 
generation for a sales or purchase order. Updates to the reference document are not allowed after the financial date is populated. |
| Reference        | Indicates the source of the transaction and the type of document that is displayed in the **Number** field. For example, sales order, purchase 
order, transfer order receipt, and so on.                                                 |
| Number           | Indicates the reference ID for a transaction. For example, if the **Reference** field indicates sales order, the **Number** field indicates the
sales order number.                                                       |
| Receipt (status) | For inventory transactions that are receipts, this field indicates the status of the receipt. For example, a purchase order is a receipt, and the 
statuses may be **Ordered** or **Purchased**.                                                            |
| Issue (status)   | For inventory transactions that are issues, this field indicates the status of the issue. For example, a sales order is an issue, and the statuses
may be **On order** or **Sold**.                         |
| Quantity         | The quantity of the inventory transaction. Positive numbers are used for receipts to inventory while negative numbers are used for issues from 
inventory.                                                                                                                          |
| Unit             | The unit of measure that the quantity is expressed in.                                                                                   |
| CW quantity      | The catch weight quantity for the transaction. For more information, see [About catch weight items](/dynamicsax-2012/appuser-itpro/about-catch-weight-items.).                                                                                                             |
| CW unit          | The catch weight unit of measure the catch weight quantity is expressed in.                                                         |
| Cost amount      | The final cost of the inventory transaction. This field is populated when a transaction is financially updated. Depending on the costing 
methodology, the Inventory close and adjustment process may update this field.                            |

## Inventory statuses

Each inventory transaction has a status that is displayed in either the **Receipt** or the **Issue** field. The field that is used depends on the type of
inventory transactions. Receipts are transactions that increases the inventory. For example, a purchase order with a positive quantity, or a sales order return 
with a negative quantity. Issues are inventory transactions that decreased the inventory. For example, a sales order with a positive quantity, or a purchase order 
return with a negative quantity.

### Receipt statuses

The following table describes **Receipt** statuses:

| **Receipt status** | **Description**       |
|--------------------|------------------------------------------------------------------------------------------------------------------------------------------|

| Ordered            | The initial status of any inventory transaction that represents a receipt. This includes but is not limited to, Purchase orders with a 
positive quantity, Production orders (finished good), Sales order returns with a negative quantity.                                                   |
| Registered         | This status is used when a two-step receiving process is in place or when Item arrival is used to indicate product has arrived. It is used when 
batch or serial numbers are "allocated" or registered to the order. For more information about item arrival, refer to
[Arrival overview](/supply-chain/inventory/arrival-overview.md) |
| Received           | This status is used when the transaction is physically updated. For a purchase order this would be the product receipt is posted, or for a 
sales order return this would be the packing slip is posted.                                                                            |
| Purchased          | This is the status used when the transaction is financially updated. For a purchase order or sales order return this is when the invoice is 
generated.                                                                                             |

### Issue statuses

The following table describes **Issue** statuses:

| **Issue status**  | **Description**            |
|-------------------|-------------------------------------------------------------------------------------------------------------------------------------------|

| On order          | The initial status of any inventory transaction that represents an issue. This includes but is not limited to Sales orders with a
positive quantity, Production orders BOM or Formula lines, Purchase order returns with a negative quantity.                                             |
| Reserved ordered  | This inventory status indicates that inventory is reserved against an order that is created, but not yet physically received in 
inventory. When the inventory is received, the status will automatically update to **Reserved physical**. For more information about reservations, see
[Reserve inventory quantities](/supply-chain/inventory/reserve-inventory-quantities.md). |
| Reserved physical | This status indicates that the inventory has been allocated or reserved against a specific order. When inventory is reserved, it is
not physically available for other orders.                                 |
| Picked            | This indicates that the inventory has been picked from the warehouse. The inventory is still physically in warehouse, hasn't been removed 
physically but isn't available for other orders.  |
| Deducted          | This status is used when the transaction is physically updated. For a sales order, this would be the packing slip is posted, or for a purchase
order return this would be the product receipt is posted.                                                                      |
| Sold              | This is the status used when the transaction is financially updated. For a purchase order or sales order, this is when the invoice is generated.|

For more information about the inventory transactions, see [Inventory transactions detail](supply-chain/inventory/inventory-transactions.md).

## Configure an inventory posting profile

To configure an inventory posting profile, follow these steps:
1.  Open **Inventory management > Setup > Posting > Posting**.
2.  Select the tab for the type of transaction, for example, select **Purchase order**.
3.  Select the radio button for the posting type, for example, select **Purchase expenditure for expense**.
4.  Click **New**.
5.  In the **Item code** field select an option for **Table**, **Group**, **All**, or **Category**. For example, to configure a posting profile for a specific item 
    group, select **Group**.
     - If you selected **Table** in step 5, select the specific Item number for the posting profile in the **Item relation** field.
     - If you selected **Group** in step 5, select the **Item group** for the posting profile in the **Item relation** field.
     - If you selected **All** in step 5, the **Item relation** field will be blank.
     - If you selected **Category** in step 5, the **Item relation** field will be blank. Use the **Category relation** field to select the category the posting 
        profile applies to.

6.  In the **Account code** field select an option for **Table**, **Group**, or **All**. For example, to apply the posting profile to all vendors, select All.
     - If you selected **Table** in step 5, select the specific Vendor number for the posting profile in the **Account relation** field.
     - If you selected **Group** in step 5, select the Vendor group for the posting profile in the **Account relation** field.
     - If you selected **All** in step 5, the **Account relation** field will be blank.

7.  To associate a particular tax group that has the selected posting type, select a **Sales tax group**. If this field is blank, the posting type applies to
all existing tax groups. Posting that is specified for tax groups only applies to sales and purchases transactions.
8.  Specify the account number to post the account type to the **Main account** field. Select one of the existing account numbers in the chart of accounts. 
If an account number hasn't been created for use as the accounting type, you can create a new account. You create a new account in the **Main account details** page 
in General ledger.

## Additional resources

Each tab on the **Inventory posting profile** page relates to a subledger in Dynamics 365 Supply Chain Management. 
See the following pages for more details:
-   [Sales order posting](general-ledger/sales-order-posting.md)
-   [Purchase order posting](general-ledger/purchase-order-posting.md)
-   [Inventory posting](general-ledger/inventory-posting.md)
-   [Production control posting](general-ledger/production-control-posting.md)
-   [Standard cost variance posting](general-ledger/standard-cost-variance-posting.md)
