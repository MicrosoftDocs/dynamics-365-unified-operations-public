---
title: Purchase order posting
description: Learn about the purchase order tab of the inventory posting profiles page, including an overview on fixed receipt price posting.
author: rachelprofitt
ms.author: raprofit
ms.topic: overview
ms.date: 04/01/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.form: InventPosting, InventTrans
---

# Purchase order posting

The **Purchase order** tab on the **Inventory posting profiles** page controls how purchase orders post to the general ledger. Two main activities post to the general ledger for a purchase order:

- Product receipt
- Invoice

For a physical transaction (product receipt) to post to the general ledger on a purchase order, select the following checkboxes:

- On the **Inventory and warehouse management parameters** page, select the **Post product receipt in ledger** checkbox.
- On the **Item model groups** page, select the **Post physical inventory** and **Accrue liability on product receipt** checkboxes.

Specify the main accounts in the **Inventory posting profile** page for the following posting types:

- Cost of purchased materials received
- Purchase expenditure, uninvoiced
- Purchase, accrual

For a financial transaction (invoice) to post to the general ledger on a purchase order, meet the following conditions:

- Select the **Post financial inventory** checkbox in the **Item model groups** page for the item selected on the purchase order line.
- Specify the main accounts in the **Inventory posting profile** page for the following posting types:
  - Cost of purchased materials invoiced
  - Purchase expenditure for product
  - Purchase expenditure for expense
  - Discount (optional)

## Fixed receipt price posting

Use fixed receipt price as the standard cost for a product instead of selecting the **Standard cost** option in the **Inventory model** field on the **Item model groups** page for an item. The main difference is that when you use **Fixed receipt price**, the current cost price is used for the item when you post the inventory receipt. There's no cost revaluation process for **Fixed receipt price**. When you post a financial update, the current cost price is used at the time of posting. If there's a difference between the cost price used at receipt and invoice, the variance posts to the fixed receipt price profit and loss accounts.

To use a fixed receipt price for a product, configure the following settings:

- On the **Item model groups** page, select the **Post physical inventory** and the **Fixed receipt price** checkboxes.
- On the **Inventory and warehouse management parameters** page, select the **Post packing slip in ledger** checkbox.
- On the **Inventory posting profile** page, specify the main accounts for the following posting types:
  - Fixed receipt price profit
  - Fixed receipt price loss
  - Fixed receipt price offset

For more information, see [Fixed receipt price](../../supply-chain/cost-management/fixed-receipt-price.md).

## Purchase charges and stock variation posting

If you plan to account for purchase charges and stock variations, complete the following steps:

- On the **Accounts payable parameters** page, on the **Invoice** tab, select the **Post to charge account in ledger** checkbox.
- On the **Item model groups** page, for the item selected on the purchase order line, select the **Post physical inventory**, **Post financial inventory**, and **Accrue liability on product receipt** checkboxes.
- On the **Procurement and sourcing parameters** page, select the **Generate charges on product receipt** checkbox.
- On the **Inventory and warehouse management parameters** page, select the **Post packing slip in ledger** checkbox.

On the **Inventory posting profile** page, specify the main accounts for the following posting types:

- Purchase expenditure, uninvoiced
- Purchase expenditure for product
- Stock variation

> [!NOTE]
> The **Charge** posting type isn't used when you select the **Post to charge account in ledger** parameter.

For more information, see [Post to charge account accounting principle](../../supply-chain/cost-management/post-to-charge-account-accounting-principle.md).

## Sample posting profile configuration

The following table shows examples of the default posting types with sample main accounts and descriptions:

- The **Clearing account** column indicates that the posting type is a clearing account. The amount posted in this account is automatically reversed when a later transaction is posted.
- The **P/F** column indicates **P** for physical posting and **F** for financial posting.
- The **Follow** column indicates if the main account for a specific posting type is typically the same as another posting type. The value in the column indicates the posting type that's typically used.

> [!NOTE]
> The main accounts and main account names are only suggestions. Work with your accountant to determine the best configuration for your business needs.

| Posting type | Main account example | Main account name example | Account type | Debit/ Credit? | Clearing account | P/F | Follow | Description |
|--------------|---------------------|-------------------------|----------------|----------------|--------------------|----|----------|-----------|
| Cost of purchased materials received | 140100</br>140101 | Materials inventory</br>Materials shipped not invoiced | Asset | Debit | Yes | P | Cost of purchased materials invoiced | Used when a purchase order product receipt is posted, the offset to the account is Purchase expenditure, uninvoiced. The amount in this account is reversed when a purchase order invoice is posted. |
| Purchase expenditure, uninvoiced | 600180 | Material receipts | Expense | Debit | Yes | P | |Used when a purchase order product receipt is posted. Two vouchers are created for the receipt to track purchase price variances when standard cost is used. The offset to the account on the first voucher is Purchase accrual. The offset on the second voucher is the sum of the Cost of purchased materials received and Purchase price variance accounts. The amounts posted in this account are reversed when a purchase order invoice is posted. |
| Cost of purchased materials invoiced | 140100 | Materials inventory | Asset | Debit | No | F  |Cost of purchased materials received | Used when a purchase order invoice is posted. The offset to this account is the Purchase expenditure for product. This account represents the inventory on your balance sheet. The account used is typically the same account used for Cost of units delivered and Cost of units invoiced for sales order. |
| Purchase expenditure for product | 600180 | Materials receipt | Expense | Credit | Yes | F  | |Used when a purchase order invoice is posted. Two vouchers are created for the invoice to track purchase price variances when standard cost is used. The offset to this account is the Purchase expenditure, uninvoiced account which is used on the receipt posting and reversed during the invoice posting. Represents costs for the inventory purchased at invoicing that's not reflected in inventory account on the balance sheet. This is a profit and loss posting for purchase price variance most commonly seen in standard cost item purchases.|
| Fixed receipt price profit (Purchase, fixed receipt price profit*) | 510310 | Purchase price variance | Expense | Credit | No | F | Fixed receipt price loss | Used when a purchase order invoice is posted and there's a difference between the invoiced price and the default cost for the item. This account is used when the difference is higher. The offset to this account is the Fixed receipt price offset. |
| Fixed receipt price loss (Purchase, fixed receipt price loss*) | 510310 | Purchase price variance | Expense | Debit | No | F | Fixed receipt price profit | Used when a purchase order invoice is posted and there's a difference between the invoiced price and the default cost for the item. This account is used when the difference is lower. The offset to this account is the Fixed receipt price offset. |
| Fixed receipt price offset (Purchase, fixed receipt price offset*) | 140900 | Stock variation | Asset | Both | No | F  | |Used when a purchase order invoice is posted and there's a difference between the invoiced price and the default cost for the item. This account is the offset to the Fixed receipt price profit and loss accounts. |
| Charge | NA | NA | NA | NA | NA | NA | NA | This account is no longer used. Use Stock variation instead. |
| Stock variation | 600170 | Stock variation | Expense | Credit | No | Both | | This account is used when: <ul><li>There's a difference in the unit price between product receipt and invoice.</li><li>Charges are posted to the item.</li><li>Indirect costs have been added to the purchased items. </li><li>The offset to this account is the Purchase expenditure, uninvoiced account.</li></ul> |
| Purchase, accrual | 200140 | Accrued Purchases | Liability | Credit | Y | P | |Used when a purchase order product receipt is posted and the option to accrue purchase amounts is enabled. |
| Accrued sales tax on receipt | 250500 | Accrued Sales Tax | Liability | Credit | Y | Both  | |This account is used when you select the **Post physical tax** option on the **Inventory and warehouse management parameters** and you have a purchase order with tax. The amount is posted when you update the purchase order physically (product receipt), and reversed when you post the purchase order financially (invoice). |
| Fixed asset receipt (Fixed asset debit*) | 180100 | Tangible fixed assets | Asset | Debit | N | Both | Both | This account is used when you select the option on the purchase order line for Fixed assets. The purchase order integration has been configured to acquire the fixed asset upon product receipt or invoice. For more information about Fixed asset purchase order integration, see [Acquire assets through procurement](../fixed-assets/acquire-assets-procurement.md). |
| Purchase expenditure for expense | 618900 | Miscellaneous expense | Expense | Debit | N | Both | |Used when posting a product receipt or invoice for a purchase order where the items aren't stocked, or a procurement category is used. |
| Prepayment | 132190 | Prepaid expense | Asset | Debit | N | Both | | Used when processing a prepayment invoice on a purchase order. |

\*Values shown in parentheses represent the value that is used in the **Posting type** field on the **Voucher transactions** page. You can view the **Posting type** on the **Voucher transactions** page on the **General** tab.

## Fixed asset posting with purchase orders

If you use the **Fixed assets** module and plan to purchase fixed assets through purchase orders, configure the **Fixed asset receipt** posting type on the **Purchase order** tab of the **Inventory posting profile** page. For more information, see [Fixed assets integration](../fixed-assets/fixed-asset-integration.md) and [Create and acquire assets from Accounts payable](../fixed-assets/tasks/create-acquire-assets-accounts-payable.md).

## Prepayment purchase order invoice posting

If you plan to use the **Prepayment invoice** feature for purchase orders, select the **Prepayment** posting type on the **Purchase order** tab on the **Inventory posting profile** page. For more information, see [Prepayment invoices vs. prepayments](../accounts-payable/prepayments-invoices-vs-prepayments.md).

## Purchase requisition and purchase order confirmation posting

You can configure purchase requisitions and purchase order confirmations to post pre-encumbrances and encumbrances to the general ledger. A posting definition controls these postings. For more information, see [About purchase order encumbrances](/dynamicsax-2012/appuser-itpro/about-purchase-order-encumbrances).

## Procurement category posting

Instead of setting up the inventory posting for all items, a group of items, or a single item, set up categories and control the ledger posting by procurement categories. For more information about setting up categories and assigning them to products, see [Sample posting profile configuration](#sample-posting-profile-configuration) earlier in this article.

When you use categories with purchase orders or vendor invoices, assign the category hierarchy to the **Procurement category hierarchy** type on the **Category hierarchy role assignments** page.

### Vendor invoices with procurement categories

If your organization uses purchases orders for some purchases and not for others, you can process non–purchase order related invoices in a variety of ways. This variety of ways includes using journals in **Accounts payable** or by the **Pending vendor invoices** page that's used to generate invoices for purchase orders. When you create invoices for non–purchase order related invoices, create procurement categories for each type of expense. Map the category to the correct expense account on the **Inventory posting profiles** page.

The exact number of categories varies based on the number of expense accounts that you use to post your invoices. You need at least one procurement category for each main account that you expense non–purchase order invoices to. Many categories can be used for a single main account. This arrangement can be useful for usability, searchability, and reporting the types of expenses you use.

### Benefits of using procurement categories for vendor invoices

Some benefits of using procurement categories for vendor invoices include:

- Consistent user experience: When you configure procurement categories for all non–purchase order related expenses, users can be trained on one process for invoicing by using the **Pending vendor invoices** page.
- Improved reporting experience: When you configure procurement categories for all items and all non–purchase order related expenses, the procurement spend report analyzes the spend by vendor, category, and more.
- Consistent workflow: When you use **Pending vendor invoices** to process all invoices, you can create a consistent workflow and approval process by using a single workflow.

## Consignment inventory posting

Consignment inventory uses the same ledger posting as other purchased items. The key difference is that when you receive the inventory, you don't record any ledger transactions. To transfer ownership to the organization when you post an **Inventory ownership change** journal, you generate a voucher to record the cost of the item. For more information, see [Set up consignment](../../supply-chain/inventory/consignment.md).
