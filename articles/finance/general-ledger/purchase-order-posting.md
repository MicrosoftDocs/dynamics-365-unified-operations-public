---
# required metadata

title: Purchase order posting
description: This topic describes the Purchase order tab of the Inventory posting profiles page.
author: rachelprofitt
ms.date: 04/25/2022
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: InventPosting, InventTrans
# ROBOTS: 
audience: Application User
ms.search.region: Global
# ms.search.industry: 
ms.author: raprofit

---

# Purchase order posting

The **Purchase order** tab on the **Inventory posting profiles** page is used to control how purchase orders will post to the general ledger. There are two main activities that post to the general ledger for a purchase order: 
 - the product receipt
 - the invoice

For a physical transaction (product receipt) to post to the general ledger on a purchase order, the following check boxes must be selected:
-   The **Post product receipt in ledger** check box on the **Inventory and warehouse management parameters** page.
-   The **Post physical inventory** and **Accrue liability on product receipt** check boxes on the **Item model groups** page

The main accounts must be specified in the **Inventory posting profile** page for the following posting types:
    -   Cost of purchases materials received
    -   Purchase expenditure, uninvoiced
    -   Purchase, accrual

For a financial transaction (invoice) to post to the general ledger on a purchase order, the following conditions must be met:
-   The **Post financial inventory** check box must be selected in the **Item model groups** page for the item selected on the purchase order line.
-   The main accounts must be specified in the **Inventory posting profile** page for the following posting types:
    -   Cost of purchased materials invoiced
    -   Purchase expenditure for product
    -   Purchase expenditure for expense
    -   Discount (optional)

## Fixed receipt price posting

Fixed receipt price is an alternative way to use a standard cost for a product then selecting the **Standard cost** option in the **Inventory model** field on the **Item model groups** page for an item. The main difference is when using the **Fixed receipt price**, the current cost price will be used for the item when the inventory receipt is posted. There is no cost revaluation process for **Fixed receipt price** and when a financial update is posted the current cost price is used at the time of posting. If there is a difference between the cost price used at receipt and invoice, the variance will post to the fixed receipt price profit and loss accounts.

To use a Fixed receipt price for a product, you must configure the following:
-   The **Post physical inventory** and the **Fixed receipt price** check boxes must be selected on the **Item model groups** page.
-   The **Post packing slip in ledger** check box must be selected on the **Inventory and warehouse management parameters** page.
-   The main accounts must be specified on the **Inventory posting profile** page for the following posting types:
    -   Fixed receipt price profit
    -   Fixed receipt price loss
    -   Fixed receipt price offset

For more information, see [Fixed receipt price](fixed-receipt-price.md).

## Purchase charges and stock variation posting

If you plan to account for purchase charges and stock variations, the following check boxes must be selected: :
-   The **Post to charge account in ledger** on the **Accounts payable parameters** page on the **Invoice** tab.
-   The **Post physical inventory**, **Post financial inventory**, and the **Accrue liability on product receipt** on the **Item model groups** page for the item selected on the purchase order line.
-   The **Generate charges on product receipt** on the **Procurement and sourcing parameters** page.
-   The **Post packing slip in ledger** on the **Inventory and warehouse management parameters** page.

The main accounts must be specified in the **Inventory posting profile** page for the following posting types:
    -   Purchase expenditure, uninvoiced
    -   Purchase expenditure for product
    -   Stock variation

> [!NOTE]
> The **Charge** posting type is not used when the **Post to charge account in ledger** parameter is selected.

For more information, see [Post to charge account accounting principle](post-to-charge-account-accounting-principle.md).

## Sample posting profile configuration

The following table shows examples of the default posting types with sample main accounts and descriptions:
 - The **Clearing account** column indicates the posting type is a clearing account. The amount posted in this account is automatically reversed when a later transaction is posted. 
 - The **P/F** column indicates **P** for physical posting and **F** for financial posting. 
 - The **Follow** column indicates if the main account for a specific posting type is typically the same as another posting type. The value in the column indicates the posting type that is typically used.

> [!NOTE]
> The main accounts and main account names are only suggestions. It is recommended that you work with your accountant to determine the best configuration for your business needs.


| Posting type | Main account example | Main account name example | Account type | Debit/ Credit? | Clearing account | P/F | Follow | Description |
|--------------|---------------------|-------------------------|----------------|----------------|--------------------|----|----------|-----------|
| Cost of purchased materials received | 140100</br>140101 | Materials inventory</br>Materials shipped not invoiced | Asset | Debit | Yes | P | Cost of purchased materials invoiced | Used when a purchase order product receipt is posted. The offset to the account is the Purchase expenditure, uninvoiced. The amount in this account is reversed when a purchase order invoice is posted. |
| Purchase expenditure, uninvoiced | 600180 | Material receipts | Expense | Debit | Yes | P  |Used when a purchase order product receipt is posted. Two vouchers are created for the receipt to track purchase price variances when using standard cost. The offset to the account on the first voucher is the Purchase accrual. The offset on the second voucher is the sum of the Cost of purchased materials received and Purchase price variance accounts. The amounts posted in this account are reversed when a purchase order invoice is posted. |
| Cost of purchased materials invoiced | 140100 | Materials inventory | Asset | Debit | No | F  |Cost of purchased materials received | Used when a purchase order invoice is posted. The offset to this account is the Purchase expenditure for product. This account represents the inventory on your balance sheet. The account used is typically the same account used for Cost of units delivered and Cost of units invoiced for sales order. |
| Purchase expenditure for product | 600180 | Materials receipt | Expense | Credit | No | F   |Used when a purchase order invoice is posted. The offset to this account is the Cost of purchased materials purchased. This account represents the inventory on your balance sheet. |
| Fixed receipt price profit (Purchase, fixed receipt price profit*) | 510310 | Purchase price variance | Expense | Credit | No | F | Fixed receipt price loss | Used when a purchase order invoice is posted and there is a difference between the invoiced price and the default cost for the item. This account is used when the difference is higher. The offset to this account is the Fixed receipt price offset. |
| Fixed receipt price loss (Purchase, fixed receipt price loss*) | 510310 | Purchase price variance | Expense | Debit | No | F | Fixed receipt price profit | Used when a purchase order invoice is posted and there is a difference between the invoiced price and the default cost for the item. This account is used when the difference is lower. The offset to this account is the Fixed receipt price offset. |
| Fixed receipt price offset (Purchase, fixed receipt price offset*) | 140900 | Stock variation | Asset | Both | No | F  | |Used when a purchase order invoice is posted and there is a difference between the invoiced price and the default cost for the item. This account is the offset to the Fixed receipt price profit and loss accounts. |
| Charge | NA | NA | NA | NA | NA | NA | NA | This account is no longer used. Use the Stock variation instead. |
| Stock variation | 600170 | Stock variation | Expense | Credit | No | Both | This account is used when: </br>there is a difference in the unit price between product receipt and invoice</br>when there are charges that are posted to the item</br>when there are indirect costs added to the purchased items. </br>The offset to this account is the Purchase expenditure, uninvoiced account.</br> |
| Purchase, accrual | 200140 | Accrued Purchases | Liability | Credit | Y | P  |Used when a purchase order product receipt is posted and the option to accrue purchase amounts is enabled. |
| Accrued sales tax on receipt | 250500 | Accrued Sales Tax | Liability | Credit | Y | Both  | |This account is used when you select the **Post physical tax** option on the **Inventory and warehouse management parameters** and you have a purchase order with tax. The amount is posted when you update the purchase order physically (product receipt), and reversed when you post the purchase order financially (invoice). |
| Fixed asset receipt (Fixed asset debit*) | 180100 | Tangible fixed assets | Asset | Debit | N | Both | Both | This account is used when you select the option on purchase order line for Fixed assets. The purchase order integration has been configured to acquire the fixed asset upon product receipt or invoice. For more information about Fixed asset purchase order integration, see [Acquire assets through procurement](/fixed-assets/acquire-assets-procurement). |
| Purchase expenditure for expense | 618900 | Miscellaneous expense | Expense | Debit | N | Both  | Used when posting a product receipt or invoice for a purchase order where the items are not stocked, or a procurement category is used. |
| Prepayment | 132190 | Prepaid expense | Asset | Debit | N | Both  | Used when processing a prepayment invoice on a purchase order. |


\*Values shown in parenthesis represent the value that is used in the**Posting type** field on the **Voucher transactions** page. You can view the **Posting type** on the **Voucher transactions** page on the **General** tab.

## Fixed asset posting with purchase orders

If you use the **Fixed assets** module and plan to purchase fixed assets through purchase orders, you must configure the **Fixed asset receipt** posting type on the **Purchase order** tab of the **Inventory posting profile** page. For more information, see [Fixed assets integration](/fixed-assets/fixed-asset-integration.md) and [Create and acquire assets from Accounts payable](/fixed-assets/tasks/create-acquire-assets-accounts-payable.md).

## Prepayment purchase order invoice posting

If you plan to use the **Prepayment invoice** feature for purchase orders, the **Prepayment** posting type must be selected on the **Purchase order** tab on the **Inventory posting profile** page. For more information, see [Prepayment invoices vs. prepayments](/accounts-payable/prepayments-invoices-vs-prepayments.md).

## Purchase requisition and purchase order confirmation posting

Purchase requisitions and Purchase order confirmations can also be configured to post pre-encumbrances and encumbrances to the general ledger. These postings are controlled by a posting definition. For more information, see [About purchase order encumbrances](/dynamicsax-2012/appuser-itpro/about-purchase-order-encumbrances).

## Procurement category posting

As an alternative to setting up the inventory posting for all items, a group of items, or a single item, you can set up categories and control the ledger posting by procurement categories. For more information about setting up categories and assigning them to products, see the Sales order category posting section above.

When using categories with purchase orders or vendor invoices, the category hierarchy needs to be assigned to the **Procurement category** **hierarchy** type in the **Category hierarchy role assignments** page.

### Vendor invoices with procurement categories

If your organization uses purchases order for some purchases and not for others, there are a variety of ways that you can process the non-purchase order related invoices. This includes using journals in **Accounts payable** or by the **Pending vendor invoices** page that is used to generate invoices for purchase orders. When creating invoices for non-purchase order related invoices, you will need to create procurement categories for each type of expense. You will need to map the category to the correct expense account on the **Inventory posting profiles** page.

The exact number of categories will vary based on the number of expense accounts that you use to post your invoices. You will need at least one procurement category for each main account that you expense non-purchase order invoices to. Many categories can be used for a single main account. This can be useful for usability, searchability, and reporting of the types of expenses you use.

### Benefits of using procurement categories for vendor invoices

Some benefits of using procurement categories for vendor invoices include:
-   Consistent user experience: When you configure procurement categories for all non-purchase order related expenses, users can be trained on one process for invoicing using the **Pending vendor invoices** page.
-   Improved reporting experience: When you configure procurement categories for all items and all non-purchase order related expenses, the procurement spend report will analyze the spend by vendor, category and more.
-   Consistent workflow: When you use **Pending vendor invoices** to process all invoices, you can create a consistent workflow and approval process using a single workflow.

## Consignment inventory posting

Consignment inventory uses the same ledger posting as other purchased items. The key difference is when the inventory is received, no ledger transactions are recorded. When an **Inventory ownership change** journal is posted, to transfer the ownership to the organization, a voucher is generated to record the cost of the item. For more information, see [Set up consignment](/supply-chain/inventory/consignment.md).
