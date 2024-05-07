---
title: Sales order posting
description: Learn about the Sales order tab of the inventory posting profile page, including a sample posting profile configuration.
author: rachelprofitt
ms.author: raprofit
ms.topic: overview
ms.date: 04/25/2022
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.form: InventPosting, InventItemGroup
---

# Sales order posting

The **Sales order** tab on the **Inventory posting profiles** page is used to control how sales orders will be posted to the general ledger. Two main activities are posted to the general ledger for a sales order: 

- Packing slip
- Invoice

For a physical transaction (packing slip) to post to the general ledger for a sales order, the following conditions must be met:

- On the **Inventory and warehouse management parameters** page, the **Post packing slip in ledger** checkbox must be selected .
- On the **Item model group** page for the item selected on the sales order line, the **Post physical inventory in ledger** checkbox must be selected.
- On the **Inventory posting profile** page, the main accounts must be specified  for the following posting types:
  - Cost of units, delivered
  - Cost of goods sold, delivered

For a financial transaction (invoice) to post to the general ledger for a sales order, the following conditions must be met:

- On the **Item model group** page for the item selected on the sales order line, the **Post financial inventory in ledger** checkbox must be selected.
- The main accounts must be specified on the **Inventory posting profile** page for the following posting types:
  - Cost of units, invoiced
  - Cost of goods sold, invoiced
  - Revenue
  - Discount\*

> [!NOTE]
> The Discount account is optional. Many accounting regulations, such as GAAP and IFRS, require that discounts reduce the sales revenue, and therefore these accounts aren't used in many scenarios. If local regulations allow, use a separate main account to post the portion of sales price that's discounted.

To post the deferred (estimated) revenue value to the general ledger when you generate a packing slip for a sales order, the following conditions must be met:

- On the **Item model group** page for the item selected on the sales order line, the **Post physical inventory in ledger** checkbox must be selected.
- On the **Item model group** page, the **Post to Deferred Revenue Account on Sales Delivery** checkbox must be selected.
- On the **Inventory and warehouse management parameters** page., the **Post packing slip in ledger** checkbox must be selected.
- On the **Inventory and warehouse management parameters** page, the **Post physical sales tax** checkbox must be selected.
- On the **Accounts receivable parameters** page, the **Post packing slip in ledger** checkbox must be selected.
- On the **Inventory posting profile** page, the main accounts must be specified for the following posting types:
  - Deferred revenue on delivery
  - Deferred revenue offset on delivery
  - Deferred sales tax on delivery

> [!NOTE]
> We generally recommend that you enable the options **Post physical inventory** and **Post packing slip in ledger**. Enabling these options can help to accelerate month-end closing procedures, because no deferrals will need to be manually calculated and posted. Additionally, financial statements will reflect the deferred amounts automatically without manual intervention.

> [!IMPORTANT]
> The **Post to Deferred Revenue Account on Sales Delivery** option isn't used with revenue recognition. For more information about Revenue recognition, go to [Revenue recognition overview](../accounts-receivable/revenue-recognition-overview.md).

## Sample posting profile configuration 

The following table shows examples of the default posting types with sample main accounts and descriptions:
 
- The **Clearing account** column indicates that the posting type is a clearing account. The amount posted in this account is automatically reversed when a later transaction is posted. 
- The **P/F** column indicates **P** for physical posting and **F** for financial posting. 
- The **Follow** column indicates whether the main account for a specific posting type is typically the same as another posting type. The value in the column indicates the type of posting that's typically used.

> [!NOTE]
> These main accounts and main account names are only suggestions. We recommend that you work with your accountant to determine the best configuration for your business needs.


| Posting type | Main account example | Main account name example | Account type | Debit/ Credit? | Clearing account | P/F | Follow | Description |
|------------|------------------------|-------------------------|--------------|---------|-------------------|------------|------|-------------------------|
| Cost of units, delivered | 140100</br>140101 | Materials inventory</br>Materials shipped not invoiced | Asset | Credit | Yes | P | Cost of units, invoiced | Used when a sales order packing slip is posted. The offset to the account is the Cost of goods sold, delivered. The amount in this account is reversed when a sales order invoice is posted. You might want to use a Materials shipped not invoiced account to represent the physical inventory, and reserve the Materials inventory account for the financial update. |
| Cost of goods sold, delivered | 500150 | Deferred COGS | Expense | Debit | Yes | P  | Used when a sales order packing slip is posted. The offset to the account is the Cost of units, delivered. The amount in this account is reversed when a sales order invoice is posted. |
| Cost of units, invoiced | 140100 | Materials inventory | Asset | Credit | No | F | Cost of units, delivered | Used when a sales order invoice is posted. The offset to this account is the Cost of goods sold, invoiced. This account represents the inventory on your balance sheet. |
| Cost of goods sold, invoiced | 500100 | COGS Materials | Expense | Debit | No | F  | Used when a sales order invoice is posted. The offset to this account is the Cost of units, invoiced. This account represents the COGS on your P&amp;L statement. |
| Revenue (Sales order revenue*) | 400100 | Revenue materials | Revenue | Credit | No | F   | Used when a sales order invoice is posted. The offset to this account is the Summary account (Customer balance*) on the **Accounts receivable posting profile**. |
| Commission (Sales, commission*) | 602150 | Commission expense | Expense | Debit | No | F  | Used when commission is enabled and calculated for a sales and posted during the sales order invoice process. The offset to this account is the Commission payable. |
| Commission offset (Sales, commission offset*) | 201110 | Commissions payable | Liability | Credit | Yes | F | Used when commission is enabled and calculated for a sales and posted during the sales order invoice process. The offset to this account is the Commission expense. |
| Deferred revenue on delivery (Sales – packing slip revenue*) | 401400 | Accrued sales | Revenue | Credit | Yes | P  | Used when Deferred revenue for delivery is enabled and is posted when you process a sales order packing slip. The offset to this account is the Deferred revenue offset. The amounts in this account are automatically reversed when you post the sales order invoice. |
| Deferred revenue offset on delivery (Sales – packing slip revenue offset)* | 130400 | Accounts receivable – not invoiced | Asset | Debit | Yes | P  | Used when Deferred revenue for delivery is enabled and posts when you process a sales order packing slip. The offset to this account is the Deferred revenue on delivery. The amounts in this account are automatically reversed when you post the sales order invoice. |
| Deferred sales tax on delivery (Sales, packing slip tax*) | 250500 | Deferred sales tax | Liability | Credit | Yes | P  | Used when Deferred revenue for delivery is enabled and the Post physical sales tax is enabled. The tax amount is posted when you process a sales order packing slip. |

\*Values shown in parentheses in this table represent the value that's used in the**Posting type** field on the **Voucher transactions** page. You can view the **Posting type** in the **Voucher transactions** page on the **General** tab.

## Sales category posting

As an alternative to setting up the inventory posting for all items, a group of items, or a single item, you can set up categories and control the ledger posting by sales categories. For more information about setting up a category hierarchy and assigning categories to products, go to [Create a hierarchy of product classification](../../supply-chain/pim/tasks/create-hierarchy-product-classification.md) and [Classify a product using category hierarchies](../../supply-chain/pim/tasks/classify-product-category-hierarchies.md).

After you create a category hierarchy, you must assign the hierarchy to one or more types. To use a category hierarchy on sales orders, you must assign the category to the Sales category hierarchy type. <!-- outdated link - For more information, go to [About category hierarchies](/dynamicsax-2012/appuser-itpro/about-category-hierarchies.md). -->

## Create revenue posting by sales category

To assign ledger postings for a sales order based on a sales category, follow these steps:

1. Go to **Inventory management** > **Setup** > **Posting** > **Posting**.
2. Select the **Sales** tab.
3. Select the radio button for the posting type you want to configure (for example, **Revenue**).
4. Select **New**.
5. In the **Item code** field, select **Category**.
6. Use the **Category relation** field to select the category for the posting profile.
7. In the **Account code** field, select an option for **Table**, **Group**, or **All**. For example, to apply the posting profile to all customers, select **All**.
   - If you selected **Table** in step 6, select the specific **Vendor number** for the posting profile in the **Account relation** field.
   - If you selected **Group** in step 6, select the **Vendor group** for the posting profile in the **Account relation** field.
   - If you selected **All** in step 6, the **Account relation** field will be left blank.

8. To associate a particular tax group that has the selected posting type, select a **Sales tax group**. If you leave this field blank, the posting type applies to all existing tax groups. Posting that's specified for tax groups applies only to transactions that are made for sales and purchases.

9. In the **Main account** field, specify the account number to post the account type to. Select one of the existing account numbers in the chart of accounts.
