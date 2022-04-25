---
# required metadata

title: Inventory posting 
description: Details of the inventory posting tab of the inventory posting profile page.  
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

# Inventory posting

The **Inventory** tab in the **Inventory posting profiles** page is used to control how inventory transactions that are not created from sales orders, purchase orders, or production orders, for example, will post to the general ledger. In general, inventory transactions automatically post the physical update and financial update to the inventory simultaneously. One exception to this rule is transfer orders which go through separate physical and financial updates when you ship and receive the inventory. In many cases these transactions may be integrated with another system when Dynamics 365 Supply Chain Management is not used as the system of record for inventory.

Examples of inventory transactions include the following:

| Transaction type | Receipt or Issue | P/F/Both | Description |
|-------------------------|-------------------------|-------------------------|-------------------------|
| Movement | Both | Both | A movement journal is an inventory journal that allows you to add or remove inventory. This journal functions the same as the Inventory adjustment journal, with one key difference that you can specify the main account to offset an entry to.</br>This journal is typically used to do beginning balance loads and for one-off adjustments that need to be expensed. For example, removing inventory for a sales sample.</br>The physical and financial updates are made simultaneously when the journal is posted.</br>Positive quantities on the journal lines represent receipts and negative quantities represent issues. |
| Inventory adjustment | Both | Both | An inventory adjustment journal is used to add or remove inventory. This journal does not allow you to select an offset account, so the general ledger entry is updated using only the accounts specified in the **Inventory posting profile** page. |
| Transfer (journal) | Both | Both | A transfer journal is used to move inventory from one location to another (using storage dimensions) or to update the product information on an inventory transaction with new product or tracking dimensions.</br>A transfer journal creates one line for the movement of an item with from and to fields for the inventory dimensions. However, each line in a transfer journal correlates to two inventory transactions. One transaction is an issue that correlates to the "from" inventory dimensions with a negative quantity, and another transaction is created for the "to" inventory dimensions to represent the receipt with a positive quantity.</br>Transfer journals may not create a voucher if the movement of the inventory is considered a non-financial transfer. In other words, the inventory dimensions that are different on the from and to values are not marked with the **Financial inventory** option in the Storage or Tracking dimension group page. For example, if you do not mark the **Financial inventory** option on the **Location** dimension, and you move inventory from one location to another location with the same site and warehouse, no voucher is created.</br>Transfer journals are different from transfer orders in that there are no documents for the movement, and the update is performed in one transaction by posting the journal. While a transfer order can generate picking and shipping documents and requires two updates to process the transaction. |
| Transfer order shipment | Issue | Both | When you create a new transfer order, each line and inventory combination includes two inventory transactions, one for the Transfer order shipment and one for the Transfer order receipt. When you ship the transfer order, the system updates the two inventory transactions and creates two additional inventory transactions to handle the transit of goods, for a total of four inventory transactions.</br><ol type="1"></br><li>The first inventory transaction is used to remove the item from the transfer from warehouse and location. This transaction's issue status is sold to indicate the item is no longer available in the warehouse.</li></br><li>The second inventory transaction is used to add the item into the transit warehouse that is selected on the warehouse where the item is being transferred from. This transaction's receipt status is Purchased.</li></br><li>The third inventory transaction is for the transfer from the transit warehouse into the destination warehouse. The issue status on this transaction is Reserved physical. This ensures that item cannot be consumed by another process while it is still in transit.</li></br><li>The fourth inventory transaction is for the receipt of goods into the destination warehouse. The receipt status of this transaction is Ordered.</li></br></ol> |
| Transfer order receive | Receipt | Both | When a transfer order is received into the destination warehouse, the inventory status for the inventory transaction that is in the transit warehouse (number 3 in the example above) is updated to Sold, and the inventory transaction for the destination warehouse is updated to Purchased. |
| Bills of materials | Both | Both | You can use the BOM Journal to report a product as finished and consume the raw materials that were consumed in the process without the use of a production order. A BOM journal typically includes at least one positive line for the finished good and one or more negative lines for the raw materials being consumed. The finished good line is a receipt into inventory, while the negative lines are issues from inventory for the raw materials. When you create a BOM journal, the first line is the BOM header and subsequent lines that are added after are the BOM lines. |
| Inventory ownership change | Both | Both | An inventory ownership change journal is used for consigned inventory to change the ownership from the vendor to your organization. Inventory ownership change journals are like inventory transfer journals in that there are two inventory transactions related to each line and inventory dimension combination. One inventory transaction removes the inventory from the vendor in the Ownership dimension, and second transaction add the item to the legal entity in the Ownership dimension. |
| Item arrival | Receipt | Physical | The item arrival journal is used to update the receipt status of inventory to Registered. It is typically used for purchase order receipt of goods and sales order returns. |
| Production input | Receipt | Physical | The production input journal is like the item arrival journal. However, production input is used to receive finished goods from a production order into the warehouse. The status of the inventory transaction is updated to Registered when the journal is posted. |
| Counting | Both | Both | A counting journal is used to record the quantity of items counted for a specific inventory dimension combination. Inventory transactions are only created if the line of the journal has a counting difference. A line with a higher counted quantity results in a receipt into inventory. A line with a lower counted quantity results in an issue from inventory. Lines where the quantity counted match the expected quantity have no inventory transactions. |
| Tag counting | NA | NA | A tag counting journal is used to keep track of inventory tags that are assigned and used in a full inventory count. You can use the journal to assign a tag number to a specific item and inventory dimension combination and track the status of the tag during a full inventory. Tag counting journals do not create inventory transactions. |
| Quality orders | Issue | Physical | A quality order is used to record test results for a given lot in inventory. Each quality order is related to an existing inventory transaction or a portion of the inventory transaction.</br>A quality order will generate a new inventory transaction in two situations:</br><ol type="1"></br><li>If the quality order is marked as a **Destructive test** on the **General** tab.</li></br><li>If the quality order is marked as **Quarantine upon validation failure** is marked on the **General** tab and the test fails, the validation. In this example, multiple inventory transactions are created. One to remove the item from the original inventory dimension combination and location, and second to add the item to the quarantine warehouse.</li></br></ol> |
| Quarantine orders | Both | Both | A quarantine orders' inventory transactions are like a transfer order. A quarantine warehouse is used to track the inventory and there are two receipt and two issue transactions.</br>When you initially create the order, the two transactions are created. The receipt transaction has a status of ordered for the quarantine warehouse that is linked to the warehouse where the item is located. The issue transaction has a status of on order that is for the warehouse where the item is stored.</br>When you start the quarantine order, two additional transactions are created and the existing transactions are updated. The receipt transaction for the quarantine warehouse is updated to Received and the issue transaction for the storage warehouse is updated to Deducted.</br>The two new transactions created are used to indicate the eventual movement back to the storage warehouse. A receipt transaction is created with a status of Ordered in the storage warehouse, and an issue transaction is created for the quarantine warehouse with a status of Reserved physical.</br>When you Report as finished a quarantine order, this represents the physical update of the quarantine order. This updates the receipt status in the storage warehouse to Received.</br>When you End the quarantine order, this represents the financial update of the quarantine order. The status of the issue transactions is updated to Sold, and the status of the receipt transactions are updated to Purchased.</br>You can alternatively scrap the quarantine order which removes the item from inventory. When you scrap a quarantine order, only three transactions will remain. The receipt transaction for the storage warehouse is removed, and the remaining receipt transaction is updated to a status of Purchased while the two issue transactions are updated to a status of Sold. This is physical and financial update for the order. |

## Fixed receipt price posting

Fixed receipt price is an alternative way to use a standard cost for a product than selecting the Standard cost option on the **Inventory model** field in the **Item model group** page for an item. The main difference is that when using the **Fixed receipt price** the system will use the current cost price configured for the item when the receipt into inventory is posted. There is no cost revaluation process for **Fixed receipt price** and when a financial update is posted the current cost price is used at the time of posting. If there is a difference between the cost price used at receipt and invoice, the system will post the variance to the Fixed receipt price profit and loss accounts.

To optionally use a Fixed receipt price for a product, you must configure the following:

-   The **Post physical inventory** in ledger check box must be selected in the **Item model group** page for the item selected on the inventory transaction line.

-   The **Fixed receipt price** check box must be selected in the **Item model group** page.

-   The main accounts must be specified in the **Inventory posting profile** page for the following posting types:

    -   Fixed receipt price profit

    -   Fixed receipt price loss

For more information, refer to [Fixed receipt price](fixed-receipt-price.md).

## Catch weight posting

Catch weight products are often used in industries where products can vary slightly by weight or size, or both, such as the food industry. Catch weight products use two units of measure – an inventory unit and a catch weight unit. Because the weight of inventory when it comes into a warehouse can differ from the weight when the inventory is issued out of the warehouse, the catch weight product processing must adjust the inventory.

When there is a variance in the catch weight, the differences are posted to the Catch weight loss account and Catch weight profit account on the Inventory posting profile page. Typically, the main account specified in the two fields are the same.

The following table shows examples of the default posting types with sample main accounts and descriptions. The Debit/Credit column indicates if the transaction typically Debit or Credits or in some cases can post either. The Clearing account column indicates the posting type is a clearing account. This means the amount posted in this account is automatically reversed when a later transaction is posted. The P/F column indicates P for physical posting and F for financial posting. The Follow column indicates if the main account for a specific posting type is typically the same as another posting type. The value in the column indicated the posting type that is typically followed.

> [!NOTE]
> The suggested main accounts and main account names are only suggestions, we recommend that you work with your accountant to determine the best configuration for your business needs.


| Posting type                | Main account example | Main account name example | Account type | Debit/ Credit? | Clearing account | P/F  | Follow                      | Description                                                                                           |
|-----------------------------|----------------------|---------------------------|--------------|----------------|------------------|------|-----------------------------|-------------------------------------------------------------------------------------------------------|
| Catch weight loss account   | 510520               | Inventory Adjustment      | Expense      |                | No               | Both | Catch weight profit account | This account is used when posting an inventory transaction with a catch weight amount that is lower.  |
| Catch weight profit account | 510520               | Inventory Adjustment      | Expense      |                | No               | Both | Catch weight loss account   | This account is used when posting an inventory transaction with a catch weight amount that is higher. |

For more information about catch weight products and their processing, refer to [About catch weight items](/dynamicsax-2012/appuser-itpro/about-catch-weight-items.md) and [Catch weight product processing with warehouse management](/supply-chain/warehousing/catch-weight-processing.md).

## Inventory to fixed asset transfer posting

The **Inventory to fixed asset journal** is found in the **Fixed assets** module under the **Journals** area. This journal is used to move items out of inventory and convert them into a Fixed asset. For more information about Inventory to fixed asset journals, refer to [Fixed assets integration](/fixed-assets/fixed-asset-integration.md).

The following table shows examples of the default posting types with sample main accounts and descriptions. The Debit/Credit column indicates if the transaction typically Debit or Credits or in some cases can post either. The Clearing account column indicates the posting type is a clearing account. This means the amount posted in this account is automatically reversed when a later transaction is posted. The P/F column indicates P for physical posting and F for financial posting. The Follow column indicates if the main account for a specific posting type is typically the same as another posting type. The value in the column indicated the posting type that is typically followed.

> [!NOTE]
> The suggested main accounts and main account names are only suggestions, we recommend that you work with your accountant to determine the best configuration for your business needs.


| Posting type      | Main account example | Main account name example | Account type | Debit/ Credit? | Clearing account | P/F  | Follow | Description                                                                                                                             |
|-------------------|----------------------|---------------------------|--------------|----------------|------------------|------|--------|-----------------------------------------------------------------------------------------------------------------------------------------|
| Fixed asset issue | 180100               | Tangible Fixed Assets     | Asset        | Credit         | No               | Both | N/A    | This account is used when you post an inventory to fixed asset journal to remove an item from inventory and convert into a fixed asset. |

## Moving average posting

Moving average is a perpetual costing method based on the average principle, where the costs on inventory issues do not change when the purchase cost does. The difference is capitalized and is based on a proportional calculation. The amount that remains is expensed.

The following table shows examples of the default posting types with sample main accounts and descriptions. The Debit/Credit column indicates if the transaction typically Debit or Credits or in some cases can post either. The Clearing account column indicates the posting type is a clearing account. This means the amount posted in this account is automatically reversed when a later transaction is posted. The P/F column indicates P for physical posting and F for financial posting. The Follow column indicates if the main account for a specific posting type is typically the same as another posting type. The value in the column indicated the posting type that is typically followed.

> [!NOTE]
> The suggested main accounts and main account names are only suggestions, we recommend that you work with your accountant to determine the best configuration for your business needs.


| Posting type                        | Main account example | Main account name example       | Account type | Debit/ Credit? | Clearing account | P/F  | Follow | Description                                                                  |
|-------------------------------------|----------------------|---------------------------------|--------------|----------------|------------------|------|--------|------------------------------------------------------------------------------|
| Price difference for moving average | 510600               | Moving Average Price Difference | Expense      | Both           | No               | Both | N/A    | Used when there is a difference in the cost between the receipt and invoice. |
| Revaluation for moving average      | 510610               | Moving Average Revaluation      | Expense      | Both           | No               | Both | N/A    | Used when you adjust the moving average cost of a product                    |

## Sample posting profile configuration

The following table shows examples of the default posting types with sample main accounts and descriptions. The Debit/Credit column indicates if the transaction typically Debit or Credits or in some cases can post either. The Clearing account column indicates the posting type is a clearing account. This means the amount posted in this account is automatically reversed when a later transaction is posted. The P/F column indicates P for physical posting and F for financial posting. The Follow column indicates if the main account for a specific posting type is typically the same as another posting type. The value in the column indicates the posting type that is typically followed.

> [!NOTE]
> The suggested main accounts and main account names are only suggestions, we recommend that you work with your accountant to determine the best configuration for your business needs.


| Posting type                  | Main account example | Main account name example | Account type | Debit/ Credit? | Clearing account | P/F  | Follow                        | Description                                                                                                                                                                                                                                                                          |
|-------------------------------|----------------------|---------------------------|--------------|----------------|------------------|------|-------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Inventory issue               | 140100               | Materials Inventory       | Asset        | Credit         | N                | Both | Inventory receipt             | Used when you post an inventory transaction that is an issue (negative quantity) that is not related to sales, purchases, or production. The offset to this account is the Inventory expenditure, loss account. This account typically represents inventory in the balance sheet.    |
| Inventory expenditure, loss   | 510100               | Inventory Profit and Loss | Expense      | Debit          | N                | Both | Inventory expenditure, profit | Used when you post an inventory transaction that is an issue (negative quantity) that is not related to sales, purchases, or production. The offset to this account is the Inventory issue.                                                                                          |
| Inventory receipt             | 140100               | Materials Inventory       | Asset        | Debit          | N                | Both | Inventory issue               | Used when you post an inventory transaction that is a receipt (positive quantity) that is not related to sales, purchases, or production. The offset to this account is the Inventory expenditure, profit account. This account typically represents inventory in the balance sheet. |
| Inventory expenditure, profit | 510100               | Inventory Profit and Loss | Expense      | Credit         | N                | Both | Inventory expenditure, loss   | Used when you post an inventory transaction that is a receipt (positive quantity) that is not related to sales, purchases, or production. The offset to this account is the Inventory receipt.                                                                                       |
| Inter-unit payable            | 231500               | Interunit Payable         | Liability    | Debit          | N                | Both |                               | Used when you transfer inventory between inventory dimensions such as sites and there is a cost difference for an item between the sites.                                                                                                                                            |
| Inter-unit receivable         | 131500               | Interunit Receivable      | Asset        | Credit         | N                | Both |                               | Used when you transfer inventory between inventory dimensions such as sites and there is a cost difference for an item between the sites.                                                                                                                                            |
