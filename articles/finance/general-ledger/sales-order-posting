---
# required metadata

title: Sales order posting
description: Detailed information about the Sales order tab of the inventory posting profile page.   
author: raprofit
ms.date: 04/25/2022
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: InventPosting, InventItemGroup
# ROBOTS: 
audience: Application User
ms.search.region: Global
# ms.search.industry: 
ms.author: raprofit

---

# Sales order posting

The **Sales order** tab in the **Inventory posting profiles** page is used to control how sales orders will post to the general ledger. There are two main activities that post to the general ledger for a sales order, the packing slip, and the invoice.

For a physical transaction (packing slip) to post to the general ledger for a sales order, the following conditions must be met:

-   The **Post packing slip in ledger** check box must be selected in the **Inventory and warehouse management parameters** page.

-   The **Post physical inventory** in ledger check box must be selected in the **Item model group** page for the item selected on the sales order line.

-   The main accounts must be specified in the **Inventory posting profile** page for the following posting types:

    -   Cost of units, delivered

    -   Cost of goods sold, delivered

For a financial transaction (invoice) to post to the general ledger for a sales order, the following conditions must be met:

-   The **Post financial inventory** in ledger check box must be selected in the **Item model group** page for the item selected on the sales order line.

-   The main accounts must be specified in the **Inventory posting profile** page for the following posting types:

    -   Cost of units, invoiced

    -   Cost of goods sold, invoiced

    -   Revenue

    -   Discount\*

> [!NOTE]
> The Discount account is optional, and many organizations do not use a separate discount posting account. Many accounting regulations such as GAAP and IFRS require that discounts reduce the sales revenue, and therefore these accounts are not used in many scenarios. If local regulations allow, you can use a separate main account to post the portion of sales price that is discounted.

To optionally post the deferred (estimated) revenue value to the general ledger when you generate a packing slip for a sales order, the following conditions must be met:

-   The **Post physical inventory** in ledger check box must be selected in the **Item model group** page for the item selected on the sales order line.
-   The **Post to Deferred Revenue Account on Sales Delivery** check box must be selected in the **Item model group** page.
-   The **Post packing slip in ledger** check box must be selected in the **Inventory and warehouse management parameters** page.
-   The **Post physical sales tax** check box must be selected in the **Inventory and warehouse management parameters** page.
-   The **Post packing slip in ledger** check box must be selected in the **Accounts receivable parameters** page.
-   The main accounts must be specified in the **Inventory posting profile** page for the following posting types:
    -   Deferred revenue on delivery
    -   Deferred revenue offset on delivery
    -   Deferred sales tax on delivery

> [!NOTE]
> It is generally recommended to enable the options to **Post** **physical inventory** and **Post packing slip in ledger**. Enabling these options can help to accelerate month-end closing procedures as no deferrals need to be manually calculated and posted. Additionally, financial statements will reflect the deferred amounts automatically without manual intervention.

> [!IMPORTANT]
> The **Post to Deferred Revenue Account on Sales Delivery** option is not used with revenue recognition. For more information about Revenue recognition, refer to Revenue recognition overview (contains video) - Finance \| Dynamics 365 \| Microsoft Docs.

## Sample posting profile configuration 

The following table shows examples of the default posting types with sample main accounts and descriptions. The Debit/Credit column indicates if the transaction typically Debit or Credits or in some cases can post either. The Clearing account column indicates the posting type is a clearing account. This means the amount posted in this account is automatically reversed when a later transaction is posted. The P/F column indicates P for physical posting and F for financial posting. The Follow column indicates if the main account for a specific posting type is typically the same as another posting type. The value in the column indicates the type of posting that is typically followed.

> [!NOTE]
> The suggested main accounts and main account names are only suggestions, we recommend that you work with your accountant to determine the best configuration for your business needs.


| Posting type | Main account example | Main account name example | Account type | Debit/ Credit? | Clearing account | P/F | Follow | Description |
|-------------------------|-------------------------|-------------------------|-------------------------|-------------------------|-------------------------|-------------------------|-------------------------|-------------------------|
| Cost of units, delivered | 140100</br>140101 | Materials Inventory</br>Materials Shipped Not Invoiced | Asset | Credit | Yes | P | Cost of units, invoiced | Used when a sales order packing slip is posted. The offset to the account is the Cost of goods sold, delivered. The amount in this account is reversed when a sales order invoice is posted. You may want to use a Materials Shipped Not Invoiced account to represent the physical inventory, and reserve the Materials Inventory account for the financial update. |
| Cost of goods sold, delivered | 500150 | Deferred COGS | Expense | Debit | Yes | P |  | Used when a sales order packing slip is posted. The offset to the account is the Cost of units, delivered. The amount in this account is reversed when a sales order invoice is posted. |
| Cost of units, invoiced | 140100 | Materials Inventory | Asset | Credit | No | F | Cost of units, delivered | Used when a sales order invoice is posted. The offset to this account is the Cost of goods sold, invoiced. This account represents the inventory on your balance sheet. |
| Cost of goods sold, invoiced | 500100 | COGS Materials | Expense | Debit | No | F |  | Used when a sales order invoice is posted. The offset to this account is the Cost of units, invoiced. This account represents the COGS on your P&amp;L statement. |
| Revenue (Sales order revenue*) | 400100 | Revenue Materials | Revenue | Credit | No | F |  | Used when a sales order invoice is posted. The offset to this account is the Summary account (Customer balance*) on the Accounts receivable posting profile. |
| Commission (Sales, commission*) | 602150 | Commission Expense | Expense | Debit | No | F |  | Used when commission is enabled and calculated for a sales and posted during the sales order invoice process. The offset to this account is the Commission payable. |
| Commission offset (Sales, commission offset*) | 201110 | Commissions Payable | Liability | Credit | Yes | F |  | Used when commission is enabled and calculated for a sales and posted during the sales order invoice process. The offset to this account is the Commission expense. |
| Deferred revenue on delivery (Sales – packing slip revenue*) | 401400 | Accrued Sales | Revenue | Credit | Yes | P |  | Used when Deferred revenue for delivery is enabled and posts when you process a sales order packing slip. The offset to this account is the Deferred revenue offset. The amounts in this account are automatically reversed when you post the sales order invoice. |
| Deferred revenue offset on delivery (Sales – packing slip revenue offset)* | 130400 | Accounts Receivable – Not Invoiced | Asset | Debit | Yes | P |  | Used when Deferred revenue for delivery is enabled and posts when you process a sales order packing slip. The offset to this account is the Deferred revenue on delivery. The amounts in this account are automatically reversed when you post the sales order invoice. |
| Deferred sales tax on delivery (Sales, packing slip tax*) | 250500 | Deferred Sales Tax | Liability | Credit | Yes | P |  | Used when Deferred revenue for delivery is enabled and the Post physical sales tax is enabled. The tax amount posts when you process a sales order packing slip. |

\*Values shown in parenthesis in this table represent the value that is used in the**Posting type** field on the **Voucher transactions** page. You can view the **Posting type** in the **Voucher transactions** page on the **General** tab.

## Sales category posting

As an alternative to setting up the inventory posting for all items, a group of items, or a single item, you can optionally setup categories and control the ledger posting by sales categories. For more information about setting up a category hierarchy and assigning categories to products, refer to [Create a hierarchy of product classification](/supply-chain/pim/tasks/create-hierarchy-product-classification.md) and [Classify a product using category hierarchies](/supply-chain/pim/tasks/classify-product-category-hierarchies.md).

After you create a category hierarchy, you must assign the hierarchy to one or more types. To use a category hierarchy on sales orders, you must assign the category to the Sales category hierarchy type. For more information, refer to [About category hierarchies](/dynamicsax-2012/appuser-itpro/about-category-hierarchies.md).

## Create revenue posting by sales category

To assign ledger postings for a sales order based on a sales category, follow these steps:

1.  Open **Inventory management >; Setup > Posting > Posting**.

2.  Select the **Sales** tab.

3.  Select the radio button for the posting type you want to configure, for example, select **Revenue**.

4.  Click **New**.

5.  In the **Item code** field select Category.

6.  Use the **Category relation** field to select the category for the posting profile.

7.  In the **Account code** field select an option for Table, Group, or All. For example, to apply the posting profile to all customers, select All.

    1.  If you selected Table in step 5, select the specific Vendor number for the posting profile in the **Account relation** field.

    2.  If you selected Group in step 5, select the Vendor group for the posting profile in the **Account relation** field.

    3.  If you selected All in step 5, the **Account relation** field will be left blank.

8.  To associate a particular tax group that has the selected posting type, select a **Sales tax group**. If you leave this field blank, the posting type applies to all existing tax groups. Posting that is specified for tax groups applies only to transactions that are made for sales and purchases.

9.  Specify the account number to post the account type to in the **Main account** field. Select one of the existing account numbers in the chart of accounts. If you have not already created an account number for use as the accounting type, you can create a new account. You create a new account in the **Main account details** page in General ledger.
