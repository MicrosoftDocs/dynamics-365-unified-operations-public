---
title: Post to charge account accounting principle
description: Learn about the post to charge account accounting principle, including overviews on European special accounting rules and prerequisites.
author: rachel-profitt
ms.author: raprofit
ms.reviewer: kamaybac
ms.search.form: InventPosting, InventItemGroup
ms.topic: how-to
ms.date: 06/07/2024
ms.custom: 
  - bap-template
  - evergreen
---

# Post to charge account accounting principle

The *post to charge account* accounting principle lets you account for and more easily reconcile any differences that occur in the unit price between a physical posting and financial posting, indirect costs on purchased items, or charges on a purchase order.

Two configurations for Accounts payable charges codes on the **Charges code** page (**Accounts payable \> Charges setup \> Charges code**) can cause a purchase order to affect the valuation of inventory assets:

- For charges codes where the **Debit type** field is set to *Item* and the **Credit type** field is set to *Ledger account*, the ledger account that is selected as the absorption account acts as a stock variation account.
- For charges codes where the **Debit type** field is set to *Item* and the **Credit type** field is set to *Customer/Vendor*, the charge will be accounted as material cost, and the stock variation account of the item will be used.

## European special accounting rule

In Europe, the *post to charge account* accounting principle is often used to incorporate a special accounting rule. For example, one of the following methods is typically used to account for inventory changes:

- **Cost of sales method** – The standard inventory posting profile configuration supports this method. The *post to charge account* accounting principle isn't required.
- **Nature of expense method** – Smaller organizations often use this method. It typically involves the following steps:

    1. Goods or services are fully expensed at the time of receipt.
    2. At the end of the period, a cycle count is performed.
    3. A manual adjustment for the quantity and value is posted into inventory. (The offset account is a stock variation account that offsets the expense that was posted in step 1. Therefore, you see the variation in the stock value only on this account.)

The *post to charge account* principle lets you fully automate the two postings. In this way, you can eliminate a manual period-end closing adjustment posting.

## Enable the post to charge account accounting principle

To enable the *post to charge account* accounting principle, follow these steps.

1. Go to **Accounts payable \> Setup \> Accounts payable parameters**.
2. On the **Invoice** tab, on the **Invoice** FastTab, set the **Post to charge account in ledger** option to *Yes*.
3. Close the page.

## Prerequisites and recommended parameters for the post to charge account accounting principle

If you plan to account for purchase charges and stock variations, the following prerequisites must be in place:

- On the **Invoice** tab of the **Accounts payable parameters** page (**Accounts payable \> Setup \> Accounts payable parameters**), the **Post to charge account in ledger** option must be set to *Yes*.
- On the **Item model groups** page (**Cost management \> Inventory accounting policies setup \> Item model groups**), all the following options must be set to *Yes* for every relevant model group that contains items that are included on a purchase order:

    - Post physical inventory
    - Post financial inventory
    - Accrue liability on product receipt

- On the **Delivery** tab of the **Procurement and sourcing parameters** page (**Procurement and sourcing \> Setup \> Procurement and sourcing parameters**), the **Generate charges on product receipt** option must be set to *Yes*.
- On the **Inventory accounting** tab of the **Inventory and warehouse management parameters** page (**Inventory management \> Setup \> Inventory and warehouse management parameters**), the **Post packing slip in ledger** option must be set to *Yes*.
- On the **Purchase order** tab of the **Posting** page (**Inventory management \> Setup \> Posting \> Posting**), main accounts that apply to every relevant item must be specified for each of the following posting types:

    - Purchase expenditure, un-invoiced
    - Purchase expenditure for product
    - Stock variation

## Example scenario 1: Change in unit cost price

This example scenario has the following prerequisites:

- First in, first out (FIFO) costing model

The following procedure provides an example that shows what happens when you change the unit cost price on a purchase order.

1. Create a purchase order for a quantity of 1 of an item that has a unit price of 100.00.
2. Confirm the purchase order.
3. Post the product receipt for the purchase order.
4. Validate the voucher on the product receipt. The following table shows a sample voucher.

    | Posting type | Main account | Main account name | Account type | Debit/Credit? | Clearing account | Physical/Financial? | Amount |
    |---|---|---|---|---|---|---|---|
    | Purchase, stock variation | 600170 | Stock variation materials | Expense | Credit | No | Physical | -100.00 |
    | Cost of purchased materials received | 140100 | Materials Inventory | Asset | Debit | Yes | Physical | 100.00 |
    | Purchase expenditure, un-invoiced | 600180 | Material Receipts | Expense | Debit | Yes | Physical | 100.00 |
    | Purchase, accrual | 200140 | Accrued Purchases | Liability | Credit | Yes | Physical | -100.00 |

5. Post the invoice for the purchase order that has an updated unit price of 110.00.
6. Validate the voucher on the invoice. The following table shows a sample voucher.

    | Posting type | Main account | Main account name | Account type | Debit/Credit? | Clearing account | Physical/Financial? | Amount |
    |---|---|---|---|---|---|---|---|
    | Purchase, stock variation | 600170 | Stock variation materials | Expense | Credit | No | Financial | -10.00 |
    | Cost of purchased materials received | 140100 | Materials Inventory | Asset | Debit | Yes | Financial | -100.00 |
    | Purchase expenditure, un-invoiced | 600180 | Material Receipts | Expense | Debit | Yes | Financial | -100.00 |
    | Purchase, accrual | 200140 | Accrued Purchases | Liability | Credit | Yes | Financial | 100.00 |
    | Cost of purchased materials invoiced | 140100 | Materials Inventory | Asset | Debit | No | Financial | 110.00 |
    | Purchase expenditure for product | 600180 | Materials Receipt | Expense | Credit | No | Financial | 110.00 |
    | Vendor balance | 211000 | Accounts Payable Trade | Liability | Credit | No | Financial | -110.00 |

## Example 2: Charges and indirect costs on the purchase order

This example scenario has the following prerequisites:

- FIFO costing model
- **Charges code 1:** Debit item and credit ledger account for 10%
- **Charges code 2:** Debit item and credit customer/vendor for 10.00 proportional
- **Indirect cost:** 2.00% added to the purchase price

The following procedure provides an example that shows what happens when you include charges and indirect costs on a purchase order.

1. Create a purchase order for a quantity of 1 of an item that has a unit price of 100.00.
2. Add one charges code for 10 percent that debits the item and credits the ledger.
3. Add one charges code for 10.00 that debits the item and credits the customer/vendor.
4. Allocate the charges to the purchase order lines.
5. Confirm the purchase order.
6. Post the product receipt for the purchase order.
7. Validate the voucher on the product receipt. The following table shows a sample voucher.

    | Posting type | Main account | Main account name | Account type | Debit/ Credit? | Clearing account | Physical or Financial | Amount |
    |---|---|---|---|---|---|---|---|
    | Purchase, stock variation | 600170 | Stock variation materials | Expense | Credit | No | Physical | -110.00 |
    | Estimated indirect cost absorbed | 600520 | Absorbed Indirect Costs | Expense | Credit | Yes | Physical | -2.40 |
    | Purchase freight | 600120 | Freight/ Transportation Costs | Expense | Credit | No | Physical | -10.00 |
    | Cost of purchased materials received | 140100 | Materials Inventory | Asset | Debit | Yes | Physical | 122.40 |
    | Purchase expenditure, un-invoiced | 600180 | Material Receipts | Expense | Debit | Yes | Physical | 110.00 |
    | Purchase, accrual | 200140 | Accrued Purchases | Liability | Credit | Yes | Physical | -110.00 |

8. Post the invoice for the purchase order.
9. Validate the voucher on the invoice. The following table shows a sample voucher.

    | Posting type | Main account | Main account name | Account type | Debit/Credit? | Clearing account | Physical/Financial? | Amount |
    |---|---|---|---|---|---|---|---|
    | Purchase, stock variation | 600170 | Stock variation materials | Expense | Credit | No | Financial | 0.00 |
    | Estimated indirect cost absorbed | 600520 | Absorbed Indirect Costs | Expense | Debit | Yes | Financial | 2.40 |
    | Indirect cost absorbed | 600520 | Absorbed Indirect Costs | Expense | Debit | No | Financial | -2.40 |
    | Cost of purchased materials received | 140100 | Materials Inventory | Asset | Credit | Yes | Financial | -110.00 |
    | Purchase expenditure, un-invoiced | 600180 | Material Receipts | Expense | Credit | Yes | Financial | -110.00 |
    | Purchase, accrual | 200140 | Accrued Purchases | Liability | Debit | Yes | Financial | 110.00 |
    | Cost of purchased materials invoiced | 140100 | Materials Inventory | Asset | Debit | No | Financial | 110.00 |
    | Purchase expenditure for product | 600180 | Materials Receipt | Expense | Credit | No | Financial | 110.00 |
    | Vendor balance | 211000 | Accounts Payable Trade | Liability | Credit | No | Financial | -110.00 |
