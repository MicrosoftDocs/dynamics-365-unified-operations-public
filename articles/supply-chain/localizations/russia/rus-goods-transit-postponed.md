---
title: Register goods shipped to customers (Russia)
description: Learn how to register the shipment and transfer the ownership of goods that are transported to a customer, including an outline on settings. 
author: kfend
ms.author: kfend
ms.topic: article
ms.date: 04/24/2019
ms.custom: 
ms.reviewer: kamaybac
ms.search.region: Russia
ms.search.form: 
---

# Register goods shipped to customers (Russia)

[!include [banner](../../includes/banner.md)]

In accordance with Russian legislation, a company must register the shipment of goods when goods are transported to a customer. When goods are shipped, ownership of the goods is transferred from the seller to the buyer. This transfer of ownership is also referred to as the passing of property rights.

You can also ship goods when the passing of property is postponed to a later date. The customer is liable for the goods only when the passing of property rights occurs.
The following functionality is included:

- Registration of a shipment where there is postponed passing of property rights.  
- Registration of a transfer of ownership. This registration includes registration of the customer's debt and write-off of the goods that were sold.
- Cancellation of a shipment where there is postponed passing of property rights.
- Allocation of charges to a sales invoice.

> [!NOTE]
> Although the shipment doesn't change the customer's balance, the supplier must still pay value-added tax (VAT). The goods are moved to a special warehouse for shipped goods.

## Settings

### Set up a warehouse

1. Go to **Inventory management** \> **Setup** \> **Inventory breakdown** \> **Warehouses**.
1. Create a warehouse of the *Goods shipped* type.

For a warehouse of any other type, in the **Warehouse for items shipped** field, you can specify a **Goods shipped** warehouse that should be used for the shipment of goods when there is postponed passing of property rights.

For a warehouse of the **Goods shipped** type, you can set a location for items that are shipped, if the **Location** dimension is activated for the items.

### Set up a posting type and number sequences for passing of property rights

1. Go to **Accounts receivable** \> **Setup** \> **Accounts receivable parameters**.
1. On the **General** tab, on the **Sales default values** FastTab, in the **Posting type** field, select the type of posting:
    - *Standard* – Property rights are passed to the buyer when the sales invoice is posted.
    - *Postponed passing of property* – The passing of the property rights to the buyer is postponed when the sales invoice is posted.

1. On the **Number sequences** tab, in the **Number sequence code** field, select a number sequence for the **Journal of passing of property**, **Voucher of passing of property**, and **Charges voucher references**.

### Set up a ledger posting group to post shipped goods tax

1. Go to **Tax** \> **Setup** \> **Sales tax** \> **Ledger posting groups**.
1. Select the ledger posting group and on the **General** FastTab in the **Shipped item tax** field, select a ledger account for shipped goods tax.

### Set up a charge code that uses a transit account

Use the **Charges code** page to set up a charge code. You can allocate the charges by using a transit account.

1. Go to **Accounts receivable** \> **Setup** \> **Charges setup** \> **Charges code**.
1. On the **Posting** FastTab, in the **Debit** section, in the **Type** field, select *Customer/Vendor*.
1. In the **Credit** section, in the **Type** field, select *Ledger account*.
1. In the **Credit** section, in the **Posting** field, select the posting type for the credit account.
1. In the **Credit** section, in the **Account** field, select the account number that the charge should be credited to.
1. Set the **Use transit account** option to *Yes* to use the transit ledger account for charges when you post a sales invoice where there is postponed passing of property rights.

### Set up revenue, consumption, and transit accounts to post miscellaneous sales charges

1. Go to **Accounts receivable** \> **Charges setup** \> **Charges posting**.
1. In the **Misc. charges posting type** field group, select the posting type for miscellaneous charges:
    - *Revenue* – Set up ledger accounts to post revenue for sales miscellaneous charges to.
    - *Consumption* – Set up ledger accounts to post consumption for sales miscellaneous charges to.
    - *Transit account* – Set up ledger accounts to post sales miscellaneous charges for postponed passing of property rights to.

    > [!NOTE]
    > You must set up revenue, consumption, and transit accounts to post sales orders where there are miscellaneous charges and postponed passing of property rights.

1. In the **Account code** field, select an account relation:
    - *Table* – The account relation is for a specific customer.
    - *Group* – The account relation is for a list of customer groups.
    - *All* – The account relation is for all customers.
  
1. In the **Account relation** field, select the customer or customer group to set up an account relation.

    > [!NOTE]
    > This field is available only if you selected *Table* or *Group* in the **Account code** field.
  
1. In the **Misc. charges relation** field, select a miscellaneous charges code:
    - *Table* – Posting is set up for a specific miscellaneous charges code.
    - *All* – Posting is set up for all miscellaneous charges codes.
  
1. In the **Charges code** field, select the miscellaneous charges code.

    > [!NOTE]
    > This field is available only if you selected *Table* in the **Misc. charges relation** field.
  
1. In the **Main account** field, select the ledger account that the transactions are posted to.
1. In the **Posting type** field, select the posting type for posting miscellaneous charges.

### Set up ledger accounts and offset ledger accounts for shipped goods

1. Go to **Inventory management** \> **Setup** \> **Posting** \> **Posting**.
1. On the **Sales order** tab, in the left pane, select the type of ledger account to set up for shipped goods:
    - *Goods shipped* – Set up ledger accounts to post the ledger transactions for shipped goods to.
    - *Goods shipped offset* – Set up offset ledger accounts to post the ledger transactions for shipped goods to.
  
1. In the **Item code** field, select an item relation:
    - *Table* – The item code is for a specific item.
    - *Group* – The item code is for a specific item group.
    - *All* – The item code is for all items.
  
1. In the **Item relation** field, select an item or item group.

    > [!NOTE]
    > This field is available only if you selected *Table* or *Group* in the **Item code** field.
  
1. In the **Account code** field, select an account relation:
    - *Table* – The account relation is for a specific customer.
    - *Group* – The account relation is for a list of customer groups.
    - *All* – The account relation is for all customers.
  
1. In the **Account relation** field, select a customer or customer group to set up an account relation.

    > [!NOTE]
    > This field is available only if you selected *Table* or *Group* in the **Account code** field.
  
1. In the **Sales tax group** field, select a sales tax group.
1. In the **Main account** field, select the ledger account number.

### Set up a posting type for a customer and an agreement

1. Go to **Accounts receivable** \> **Customers** \> **All customers**.
1. Select a customer account.
1. On the **Sales order defaults** FastTab, in the **Posting type** field, select the posting type:
    - *Standard* – Property rights are passed to the customer when the sales invoice is posted.
    - *Postponed passing of property* – The passing of the property rights to the customer is postponed when the sales invoice is posted.
  
1. Go to **Sales and marketing** \> **Sales agreements** \> **Sales agreements**.
1. Select a sales agreement.
1. Switch to the **Header** view.
1. On the **Financial** FastTab, in the **Posting type** field, select the posting type:
    - *Standard* – Property rights are passed to the customer when the sales invoice is posted.
    - *Postponed passing of property* – The passing of the property rights to the customer is postponed when the sales invoice is posted.

## Working with sales invoices where there is postponed passing of property rights

Complete the procedures in this section to create a sales order where there is postponed passing of property rights, post the sales invoice, and register the passing of property rights.

### Create a sales order and post a sales invoice where there is postponed passing of property rights

1. Go to **Accounts receivable** \> **Orders** \> **All sales orders**.
1. Create a sales order.
1. Switch to the **Header** view.
1. On the **Setup** FastTab, in the **Posting type** field, select *Postponed passing of property*.
1. In the **Sales tax group** field, select the sales tax group for the sales order.
1. Switch back to **Lines** view.
1. Create sales order lines. In the **Item sales tax group** field, select the sales tax group.
1. Post the invoice.

    > [!NOTE]
    > To post an invoice of the *Postponed passing of property* type, make sure that the terms of payment that are assigned to the sales orders aren't for a cash payment, and that the **Kind of activity** field isn't set to *Bailee* or *Commission agent*.

For each inventory transaction that has an issue status of *Sold*, two additional inventory transactions are created for the **Goods shipped warehouse**: one transaction has a receipt status of *Purchased*, and the other transaction has an issue status of *Deducted*.

No customer balance and revenue transactions are generated at this point.

The following ledger transactions are generated:

- **Debit**: Sales order, Goods shipped offset; **Credit**: Cost of units, invoiced
- **Debit**: Sales order, Goods shipped; **Credit**: Sales order, Goods shipped offset
- **Debit**: Shipped items tax; **Credit**: Sales tax payable

### Allocate miscellaneous charges to a sales invoice

Use the **Allocate charges** dialog box to allocate charges to a posted sales invoice.

1. Go to **Accounts receivable** \> **Inquiries and reports** \> **Invoices** \> **Invoice journal**.
1. Select a sales invoice of the **Postponed passing of property** posting type, and then select **Adjustment** to open the **Allocate charges** dialog box.
1. In the **Posting date** field, enter the date when miscellaneous charges should be posted.
1. Set the **Credit correction** option to *Yes* to indicate that charges should be posted as credit corrections.
1. In the **Charges code** field, select the charge code. This field lists only charges where the **Type** field in both the **Debit** and **Credit** sections is set to *Ledger account*.
1. In the **Charges value** field, enter the value of the charge.
1. Select **OK** to post the charge to the sales invoice.

### Cancel a shipment for the passing of property rights

Use the **Cancel shipment** dialog box to cancel a shipment. You can cancel the shipment for goods if the passing of property rights isn't fully or partially registered. When you cancel a shipment, a credit note is created.

1. Go to **Accounts receivable** \> **Inquiries and reports** \> **Invoices** \> **Invoice journal**.
1. Select a sales invoice of the *Postponed passing of property* posting type.
1. Select **Passing of property** \> **Shipment cancellation** to open the **Cancel shipment** dialog box.
1. In the **Processing** section, in the **Date** field, select the date of cancellation.
1. Set the **Credit correction (physical)** option to *Yes* to indicate that physical inventory update should be posted as a credit correction.

    > [!NOTE]
    > This option is automatically set to *Yes* if the **Storno for physical posting** option is set to *Yes* on the **Inventory accounting** tab of the **Inventory and warehouse management parameters** page.
  
1. Set the **Credit note as correction** option to *Yes* to post the credit note transaction as a credit correction.

    > [!NOTE]
    > This option is automatically set to *Yes* if the **Credit note as correction** option is set to *Yes* on the **Updates** tab of the **Accounts receivable parameters** page.
  
1. Set the **Credit remaining quantity** option to *Yes* to restore the open quantity of the sales order.

    > [!NOTE]
    > When a sales invoice is canceled, the quantity that is specified in the sales order is open for another shipment.
  
1. Set the **Corrective document** option to *Yes* to provide a reference to the source sales invoice in the credit note.
1. Use the **Mark** field to select one or more invoice lines for cancellation.

    > [!NOTE]
    > To select all invoice lines, you can set the **Select all** option to *Yes*.
  
1. In the **For processing** field, enter the quantity that shipment should be canceled for.
1. Select **OK** to cancel the shipment.
1. Close the **Invoice journal** page.

### Register the passing of property rights for a posted sales invoice

Use the **Register a passing of property** dialog box to register the passing of property rights for a posted sales invoice. Each invoice line in the dialog box contains the quantity that the passing of property rights must be registered for. You can specify a date and the quantity on the invoice line to confirm the passing of property rights. The sales tax charges and miscellaneous charges are recalculated based on the quantity, date of shipment, and the date of the passing of property rights.

1. Go to **Accounts receivable** \> **Inquiries and reports** \> **Invoices** \> **Invoice journal**.
1. Select a sales invoice of the **Postponed passing of property** posting type.
1. Select **Passing of property** \> **Passing of property** to open the **Register a passing of property** dialog box.
1. In the **Processing** section, in the **Date** field, select the date of the passing of property rights.
1. Use the **Mark** field to select one or more invoice lines for the passing of property rights.

    > [!NOTE]
    > To select all invoice lines, you can set the **Select all** option to **Yes**.
  
1. In the **For processing** field, select the quantity to register the passing of property rights for.
1. Select **OK** to register the passing of property rights.

At this point, the customer balance and revenue transactions are created.

> [!NOTE]
> The charges are processed as a total amount, regardless of whether the registration of the passing of property rights is fully processed or partially processed.
  
The following ledger transactions are posted:

- **Debit**: Cost of goods sold, invoiced; **Credit**: Sales order, Goods shipped
- **Debit**: Payment offset account (Sales tax); **Credit**: Shipped items tax

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
