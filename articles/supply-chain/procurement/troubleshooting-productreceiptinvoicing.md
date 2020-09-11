---
# required metadata

title: Troubleshoot Product Receipts and Invoicing
description: This topic describes how to fix issues that you might encounter while working with Product Receipts and Invoicing.
author: SmithaNataraj
manager: tfehr
ms.date: 05/07/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: PurchTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: smnatara
ms.search.validFrom: 2020-5-7
ms.dyn365.ops.version: AX 10.0.14

---
# Troubleshoot Product Receipt and Invoicing 

This topic describes how to fix common issues that you might encounter while working with Product Receipt and Invoicing.

## Unable to post more than one invoice for a purchase order line with category based items

Quantity is mandatory for posting invoices. So, if the full quantity on the line has been invoiced but only a partial amount and the expectation is to invoice the rest of the amount in another invoice, then that is not possible.

## "Object reference not set" error seen during purchase order confirmation, or "Exception has been thrown by the target of an invocation", exception thrown during vendor invoice posting.

**Fix**
This is an issue that could occur due to inconsistency in purchase order distributions. 

It is possible to unblock the above issues and reset the purchase order to a draft state using Procurement and Sourcing > Periodic Task > Clean up > Purchase Order Distribution Reset. See more [Resolve PO distribution errors in Dynamics 365 Supply Chain Management](https://cloudblogs.microsoft.com/dynamics365/it/2020/08/12/resolve-po-distribution-errors-in-dynamics-365-supply-chain-management/).

## Cannot consolidate multiple Product Receipts (PR) into a single Purchase order
Cannot consolidate multiple PR into a single PO when the different PR lines have different accounting dates.

**Resolution**
This was possibility in an earlier version that allowed for consolidating PR lines with different accounting dates. However, this is error prone. The accounting date on the created PO lines - which is the same as the accounting date on the header of the PO - should not be different from the accounting date on the PR line from which the PO line was created. Hence, the consolidation of multiple product receipts into a single purchase orders will is not allowed. 

The accounting date is used e.g. for budget reservations and encumbrance, this should be kept when transitioning from PR to PO. 

## Cancelling Product Receipts allows to post transactions to the suspended ledger account.
System is allowing the posting of transactions to suspended ledger accounts on cancelling of the Product Receipt even though the main accounts are “suspended”.

**Repro Steps**
1. Ensure the “Post product receipt in ledger “enabled in parameter.
2. Create a purchase order and create a line with a product, with 1000 quantity and confirm the purchase order.
3. Post the Product receipt and check the vouchers.
4. Suspend the relevant main accounts 200140 and 140200.
5. Cancel the posted product receipt.

Result: This allows posting transactions to the suspended leger accounts.

**Resolution**
This is allowed in order to to be able to correct postings.

## Product receipt Voucher number is consumed even if no financial voucher is generated, during Product Receipt
When the "Accrue liability on product receipt" is OFF on the item model group, then no postings to GL will happen. However, there is a physical event that is recorded for the purpose of accounting in subledger and that needs a voucher number. This is what is referenced in the Inventory transactions.

In the following blogpost, we recommend the "Accrue liability on product receipts" to be YES: [Post Misc. charges at time of Product receipt](https://cloudblogs.microsoft.com/dynamics365/no-audience/2014/11/11/post-misc-charges-at-time-of-product-receipt/)

## Setting - 'Post to charge account in ledger' is not active

**Scenario**

This issue occurs upon invoicing a purchase order, when the “Post to charge account in ledger“ is turned ON in Accounts payable > Setup > Accounts payable parameters.

**Steps**
1. Go to Accounts payable> Setup>Accounts payable parameters; Activate “Post to charge account in ledger “
2. Go to Inventory Management > Setup > Posting > Posting > Purchase Order 
3. Make sure you have deleted all of the lines in purchase expenditure for product
4. Go to Accounts payable > Purchase orders > All Purchase order and create a new PO. Select for Vendor Account – 1001 Acme Office Supplies
5.For Item number select D0011 Laser Projector; Site 1 ; Warehouse 11; Quantity 4
6. Confirm the PO by clicking on PURCHASE > Action > Confirm
7. Click on RECEIVE > Product receipt. And add a product receipt number (random number)
8. After that Invoice > Invoice
9. Add an Invoice Number (random number); Update match status and Post

**Result**
Error “Account number for transaction type Purchase expenditure for product does not exist” when we generate Invoice form a PO.

**Fix**
This is dependent on the parameter settings for invoices and invoice groups. Please find full details in this blog: [Accounting for Purchase charge and Stock variation](https://cloudblogs.microsoft.com/dynamics365/no-audience/2014/12/15/accounting-for-purchase-charge-and-stock-variation/).



## Additional resources

[Product receipts against purchase orders](product-receipt-against-purchase-orders.md)
[Vendor Invoicing](vendor-invoices-overview.md)
