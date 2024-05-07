---
title: Inventory posting 
description: Learn about the Inventory posting tab on the Inventory posting profile page, including an outline on inventory to fixed asset transfer posting.
author: rachelprofitt
ms.author: raprofit
ms.topic: overview
ms.date: 04/25/2022
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.form: InventPosting, InventItemGroup
---

# Inventory posting

The **Inventory** tab on the **Inventory posting profiles** page is used to control how inventory transactions are posted to the general ledger. Inventory transactions are transactions that aren't created from sales orders, purchase orders, or production orders. They automatically post the physical and financial updates to the inventory simultaneously. One exception is transfer orders that separate physical and financial updates when you ship and receive the inventory.

The following table shows some examples of inventory transactions.

| Transaction type | Receipt or issue | Physical posting, financial posting, or both | Description |
|---|---|---|---|
| Movement | Both | Both | <p>A movement journal is an inventory journal that you can use to add or remove inventory. It works like an inventory adjustment journal. However, one key difference is that the main account that offsets the entry is specified.</p><p>The movement journal enters beginning balances and one-off adjustments that must be expensed. For example, it's used when inventory is removed for a sales sample.</p><p>When the journal is posted, the physical and financial updates occur simultaneously.</p><p>Positive quantities on the journal lines represent receipts, and negative quantities represent issues.</p> |
| Inventory adjustment | Both | Both | An inventory adjustment journal is used to add or remove inventory. It doesn't let you select an offset account. Only the accounts that are specified on the **Inventory posting profile** page are used to update the general ledger entry. |
| Transfer (journal) | Both | Both | <p>A transfer journal is used to move inventory from one location to another (by using storage dimensions). It updates the product information on an inventory transaction with new product or tracking dimensions.</p><p>A transfer journal creates one line for the movement of an item. This line has "from" and "to" fields for the inventory dimensions. Each line in a transfer journal creates two inventory transactions. One transaction is created for the "from" inventory dimensions. It represents the issue and has a negative quantity. The other transaction is created for the "to" inventory dimensions. It represents the receipt and has a positive quantity.</p><p>Transfer journals might not create a voucher if the movement of the inventory is considered a non-financial transfer. Inventory dimensions that differ for the "from" and "to" values aren't marked with the **Financial inventory** option on the **Storage dimension group** or **Tracking dimension group** page. For example, if the **Financial inventory** option isn't marked on the **Location** dimension, and you move inventory from one location to another location in the same site and warehouse, no voucher is created.</p><p>Transfer journals differ from transfer orders in that there are no documents for the movement. The update is done in one transaction by posting the journal. By contrast, a transfer order can generate picking and shipping documents, and requires two updates to process the transaction.</p> |
| Transfer order shipment | Issue | Both | <p>When you create a new transfer order, each combination of a line and an inventory dimension has two inventory transactions: one for the transfer order shipment and one for the transfer order receipt. When you ship the transfer order, two inventory transactions are updated, and two additional inventory transactions are created for the transit of goods, for a total of four inventory transactions.</p><ol><li>The first inventory transaction is used to remove the item from the source warehouse and location. This transaction's issue status is **Sold** to indicate that the item is no longer available in the warehouse.</li><li>The second inventory transaction is used to add the item to the transit warehouse that is selected for the warehouse that the item is being transferred from. This transaction's receipt status is **Purchased**.</li><li>The third inventory transaction is for the transfer from the transit warehouse to the destination warehouse. This transaction's issue status is **Reserved physical**. This status ensures that the item can't be consumed by another process while it's still in transit.</li><li>The fourth inventory transaction is for the receipt of goods in the destination warehouse. This transaction's receipt status is **Ordered**.</li></ol> |
| Transfer order receive | Receipt | Both | When a transfer order is received in the destination warehouse, the inventory status of the inventory transaction that is in the transit warehouse (number 3 in the preceding example) is updated to **Sold**, and the inventory status of the inventory transaction for the destination warehouse is updated to **Purchased**. |
| Bills of materials | Both | Both | You can use a bill of materials (BOM) journal to report a product as finished and consume the raw materials that were consumed during the process without using a production order. A BOM journal typically includes at least one positive line for the finished good, and one or more negative lines for the raw materials that are being consumed. The finished good line is a receipt into inventory, whereas the negative lines are issues from inventory for the raw materials. When you create a BOM journal, the first line is the BOM header, and subsequent lines that are added are the BOM lines. |
| Inventory ownership change | Both | Both | An inventory ownership change journal is used to change the ownership of consigned inventory from the vendor to your organization. Inventory ownership change journals resemble inventory transfer journals in that two inventory transactions are related to each combination of a line and an inventory dimension. One inventory transaction removes the inventory from the vendor in the **Ownership** dimension, and the other adds the item to the legal entity in the **Ownership** dimension. |
| Item arrival | Receipt | Physical | An item arrival journal is used to update the receipt status of inventory to **Registered**. It's typically used for purchase order receipt of goods and sales order returns. |
| Production input | Receipt | Physical | A production input journal resembles an item arrival journal. Production input is used to receive finished goods from a production order in the warehouse. When the journal is posted, the status of the inventory transaction is updated to **Registered**. |
| Counting | Both | Both | A counting journal is used to record the quantity of items that were counted for a specific combination of inventory dimensions. Inventory transactions are created when the line of the journal has a counting difference. A line that has a higher counted quantity causes a receipt into inventory. A line that has a lower counted quantity causes an issue from inventory. Lines where the counted quantity matches the expected quantity have no inventory transactions. |
| Tag counting | Not applicable | Not applicable | A tag counting journal is used to track inventory tags that are assigned and used in a full inventory count. You can use the journal to assign a tag number to a specific combination of an item and an inventory dimension, and to track the status of that tag during a full inventory. Tag counting journals don't create inventory transactions. |
| Quality orders | Issue | Physical | <p>A quality order is used to record test results for a given lot in inventory. Each quality order is related to an existing inventory transaction or a portion of an inventory transaction.</p><p>A quality order will generate a new inventory transaction in two situations:</p><ul><li>The quality order is marked as **Destructive test** on the **General** tab.</li><li>The quality order is marked as **Quarantine upon validation failure** on the **General** tab, and the test fails the validation. In this case, two inventory transactions are created. One inventory transaction removes the item from the original inventory dimension combination and location, and the other adds the item to the quarantine warehouse.</li></ul> |
| Quarantine orders | Both | Both | <p>A quarantine orders' inventory transactions are like a transfer order. A quarantine warehouse is used to track the inventory. There are two receipt transactions and two issue transactions.</p><p>When you initially create the order, two transactions are created. The receipt transaction has a status of **Ordered** for the quarantine warehouse that is linked to the warehouse where the item is located. The issue transaction has a status of **On order** for the warehouse where the item is stored.</p><p>When you start the quarantine order, two additional transactions are created, and the existing transactions are updated. The status of the receipt transaction for the quarantine warehouse is updated to **Received**, and the status of the issue transaction for the storage warehouse is updated to **Deducted**.</p><p>The two new transactions are used to indicate the eventual movement back to the storage warehouse. The receipt transaction has a status of **Ordered** for the storage warehouse, and that issue transaction has a status of **Reserved physical** for the quarantine warehouse.</p><p>When you report a quarantine order as finished, this operation represents the physical update of the quarantine order. The receipt status in the storage warehouse is updated to **Received**.</p><p>When you end the quarantine order, this operation represents the financial update of the quarantine order. The status of the issue transactions is updated to **Sold**, and the status of the receipt transactions is updated to **Purchased**.</p><p>Alternatively, you can scrap the quarantine order. This operation removes the item from inventory. When you scrap a quarantine order, only three transactions remain. The receipt transaction for the storage warehouse is removed, and the status of the remaining receipt transaction is updated to **Purchased**. The status of the two issue transactions is updated to **Sold**. This operation is a physical and financial update for the order.</p> |

## Fixed receipt price posting

Fixed receipt price lets you use a standard cost for a product. It's an alternative to selecting the **Standard cost** option on the **Item model group** page for an item. The main difference when you use a fixed receipt price is that the cost price that is currently configured will be used for the item when the receipt into inventory is posted. There is no cost revaluation process for a fixed receipt price. When a financial update is posted, the current cost price is used at the time of posting. If the cost price that is used at receipt and the invoice differ, the variance will be posted to the fixed receipt price profit and loss accounts.

To optionally use a fixed receipt price for a product, you must complete the following configuration:

- Select the **Post physical inventory** checkbox on the **Item model group** page for the item that is selected on the inventory transaction line.
- Select the **Fixed receipt price** checkbox on the **Item model group** page.
- Specify the main accounts for the following posting types on the **Inventory posting profile** page:

    - Fixed receipt price profit
    - Fixed receipt price loss

For more information, see [Fixed receipt price](../../supply-chain/cost-management/fixed-receipt-price.md).

## Catch weight posting

Catch weight products are often used in industries such as the food industry, where products can vary slightly by weight, size, or both. Catch weight products use two units of measure: an inventory unit and a catch weight unit. The weight of inventory when it comes into a warehouse can differ from the weight when the inventory is issued out of the warehouse. Catch weight product processing adjusts the inventory.

If there is a variance in the catch weight, the differences are posted to the accounts that are specified in the **Catch weight loss** and **Catch weight profit** fields on the **Inventory posting profile** page. Typically, the same main account is specified in both fields.

The following table shows examples of the default posting types, and includes sample main accounts and descriptions.

- The "Debit/Credit?" column indicates whether the transaction typically debit or credits. In some case, the transaction can post either debits or credits.
- The "Clearing account" column indicates that the posting type is a clearing account. In other words, the amount that is posted in this account is automatically reversed when a later transaction is posted.
- The "P/F" column indicates the type of posting. "P" represents physical posting, and "F" represents financial posting.
- The "Follow" column indicates whether the main account for the posting type is typically the same as the main account for another posting type. Specifically, it indicates the posting type that is typically used for the posting.

> [!NOTE]
> The main accounts and main account names in the table are suggestions. We recommend that you work with your accountant to determine the best configuration for your business needs.

| Posting type | Main account example | Main account name example | Account type | Debit/Credit? | Clearing account | P/F | Follow | Description |
|---|---|---|---|---|---|---|---|---|
| Catch weight loss account | 510520 | Inventory adjustment | Expense | | No | Both | Catch weight profit account | This account is used when you post an inventory transaction where the catch weight amount is lower. |
| Catch weight profit account | 510520 | Inventory adjustment | Expense | | No | Both | Catch weight loss account | This account is used when you post an inventory transaction where the catch weight amount is higher. |

For more information about catch weight products, see <!-- Outdated link [About catch weight items](/dynamicsax-2012/appuser-itpro/about-catch-weight-items.md) and -->[Catch weight product processing with warehouse management](../../supply-chain/warehousing/catch-weight-processing.md).

## Inventory to fixed asset transfer posting

The inventory to fixed asset journal (**Fixed assets** \> **Journals** \> **Inventory to fixed asset journal**) is used to move items out of inventory and convert them to fixed assets. For more information, see [Fixed assets integration](../fixed-assets/fixed-asset-integration.md).

The following table shows examples of the default posting types, and includes sample main accounts and descriptions.

- The "Debit/Credit?" column indicates whether the transaction typically debit or credits. In some case, the transaction can post either debits or credits.
- The "Clearing account" column indicates that the posting type is a clearing account. In other words, the amount that is posted in this account is automatically reversed when a later transaction is posted.
- The "P/F" column indicates the type of posting. "P" represents physical posting, and "F" represents financial posting.
- The "Follow" column indicates whether the main account for the posting type is typically the same as the main account for another posting type. Specifically, it indicates the posting type that is typically used for the posting.

> [!NOTE]
> The main accounts and main account names in the table are suggestions. We recommend that you work with your accountant to determine the best configuration for your business needs.

| Posting type | Main account example | Main account name example | Account type | Debit/Credit? | Clearing account | P/F | Follow | Description |
|---|---|---|---|---|---|---|---|---|
| Fixed asset issue | 180100 | Tangible fixed assets | Asset | Credit | No | Both | Not applicable | This account is used when you post an inventory to fixed asset journal to remove an item from inventory and convert it to a fixed asset. |

## Moving average posting

Moving average is a perpetual costing method that is based on the average principle. The costs on inventory issues don't change when the purchase cost does. The difference is capitalized and is based on a proportional calculation. The amount that remains is expensed.

The following table shows examples of the default posting types with sample main accounts and descriptions.

- The "Debit/Credit?" column indicates whether the transaction typically debit or credits. In some case, the transaction can post either debits or credits.
- The "Clearing account" column indicates that the posting type is a clearing account. In other words, the amount that is posted in this account is automatically reversed when a later transaction is posted.
- The "P/F" column indicates the type of posting. "P" represents physical posting, and "F" represents financial posting.
- The "Follow" column indicates whether the main account for the posting type is typically the same as the main account for another posting type. Specifically, it indicates the posting type that is typically used for the posting.

> [!NOTE]
> The main accounts and main account names in the table are suggestions. We recommend that you work with your accountant to determine the best configuration for your business needs.

| Posting type | Main account example | Main account name example | Account type | Debit/Credit? | Clearing account | P/F | Follow | Description |
|---|---|---|---|---|---|---|---|---|
| Price difference for moving average | 510600 | Moving average price difference | Expense | Both | No | Both | Not applicable | This account is used when there is a difference in the cost between the receipt and the invoice. |
| Revaluation for moving average | 510610 | Moving average revaluation | Expense | Both | No | Both | Not applicable | This account is used when you adjust the moving average cost of a product |

## Sample posting profile configuration

The following table shows examples of the default posting types with sample main accounts and descriptions.

| Posting type | Main account example | Main account name example | Account type | Debit/Credit? | Clearing account | P/F | Follow | Description |
|---|---|---|---|---|---|---|---|---|
| Inventory issue | 140100 | Materials inventory | Asset | Credit | No | Both | Inventory receipt | This account is used when an inventory transaction that is posted is an issue (negative quantity) and isn't related to sales, purchases, or production. The offset to this account is the Inventory expenditure, loss account. This account typically represents inventory in the balance sheet. |
| Inventory expenditure, loss | 510100 | Inventory profit and loss | Expense | Debit | No | Both | Inventory expenditure, profit | This account is used when an inventory transaction that is posted is an issue (negative quantity) and isn't related to sales, purchases, or production. The offset to this account is the Inventory issue account. |
| Inventory receipt | 140100 | Materials inventory | Asset | Debit | No | Both | Inventory issue | This account is used when an inventory transaction that is posted is a receipt (positive quantity) and isn't related to sales, purchases, or production. The offset to this account is the Inventory expenditure, profit account. This account typically represents inventory in the balance sheet. |
| Inventory expenditure, profit | 510100 | Inventory profit and loss | Expense | Credit | No | Both | Inventory expenditure, loss | This account is used when an inventory transaction that is posted is a receipt (positive quantity) and isn't related to sales, purchases, or production. The offset to this account is the Inventory receipt account. |
| Inter-unit payable | 231500 | Interunit payable | Liability | Debit | No | Both | | This account is used when inventory is transferred between inventory dimensions such as sites, and the cost of an item differs between the sites. |
| Inter-unit receivable | 131500 | Interunit receivable | Asset | Credit | No | Both | | This account is used when inventory is transferred between inventory dimensions such as sites, and the cost of an item differs between the sites. |
