---
title: Inventory transaction details
description: Learn about the Transactions details page that shows details of a selected inventory transaction, including a table defining various FastTabs. 
author: rachel-profitt
ms.author: raprofit
ms.reviewer: kamaybac
ms.search.form: InventTrans, InventTransDetails
ms.topic: how-to
ms.date: 06/07/2024
ms.custom: 
  - bap-template
  - evergreen
---

# Inventory transaction details

Use the **Transactions details** page to view details of any selected inventory transaction.

## Open the Transaction details page

To open the **Transactions details** page, follow these steps.

1. Go to **Inventory management \> Inquiries and reports \> Transactions**.
1. Select the transaction that you want to inspect.
1. On the Action Pane, select **Transaction details**.

## FastTabs overview

The **Transactions details** page is split into several FastTabs. The following table describes the purpose of each FastTab.

| FastTab | Description |
|---|---|
| General | This FastTab shows basic information about the selected inventory transaction. In addition to the fields that appear on the **Inventory transactions** page, it includes the additional fields that are described later in this article. |
| Updates | This FastTab shows information that is related to the physical, financial, and settlement aspects of the selected inventory transaction. Depending on the current status of the transaction, some fields might be blank. However, those fields will automatically be set when transactions are posted. In addition to the fields that appear on the **Inventory transactions** page, this FastTab includes the additional fields that are described later in this article. |
| Ledger postings | This FastTab shows the posting type and ledger account that are used for the physical update, financial update, physical revenue, physical charges, financial revenue, and financial charges that are related to the selected inventory transaction. |
| References | This FastTab shows additional information about the source transaction that created the selected inventory transaction. For example, this information might include details from the purchase order or sales order. |
| Related information | This FastTab shows additional information about the selected inventory transaction. These fields might not be set if you aren't using some features, such as procurement categories or projects. |
| Financial dimensions – physical | This FastTab shows the financial dimension values that were used when the physical update was posted. If the physical update hasn't been posted, the fields will be blank. |
| Financial dimensions – financial | This FastTab shows the financial dimension values that were used when the financial update was posted. If the financial update hasn't been posted, the fields will be blank. |
| Inventory dimensions | This FastTab shows the inventory dimension values that are assigned to the selected inventory transaction. These values include the site, warehouse, size, color, configuration, location, batch number, serial number, inventory status, license plate, and owner. |

## Fields on the General FastTab

The following table describes the fields on the **General** FastTab that don't also appear on the **Inventory transactions** page.

| Field | Description |
|---|---|
| Party | The name of the relevant party for the selected inventory transaction. For example, a purchase order transaction shows the name of the vendor on the purchase order, and a sales order transaction shows the name of the customer. This field isn't available for all types of inventory transactions. |
| Inventory reference | If another inventory transaction is related to the selected inventory transaction, the type of that other transaction. For example, if a purchase order is marked against a sales order, the **Inventory reference** field of the purchase order transaction will be set to *Sales order*. Marking automatically occurs for direct delivery orders and intercompany orders. When you use marking with costing methods other than *standard cost* and *moving average*, the system will create settlements and adjustments to the exact transactions that are marked. In this way, you can achieve "actual" costing that overrides the logic for first in, first out (FIFO); last in, first out (LIFO); or weighted average. |
| Inventory number | The specific transaction that is related to the selected inventory transaction. For example, if a purchase order is marked against a sales order, the **Inventory number** field of the purchase order transaction will be set to the sales order number. |
| Project ID | If the selected inventory transaction is related to a project, this field is set to the project number. |
| Lot ID | The unique lot ID that the system has assigned to the selected inventory transaction. |
| Reference lot | If another inventory transaction is related to the selected inventory transaction, the lot ID of that other transaction. For example, if a purchase order is marked against a sales order, the **Reference lot** field of the purchase order transaction will be the **Lot ID** value of the sales order line's inventory transaction. |
| Dimension number | A unique ID that represents the combination of all the inventory dimension values that are assigned to the selected inventory transaction. |
| Value open | A value that indicates whether the selected inventory transaction has been settled by the inventory closing process. If this field is set to *Yes*, the transaction hasn't been settled. |
| Expected date | For receipt transactions, the date when the inventory receipt is expected to occur. For example, this field might show the expected receipt date on an inventory blocking order or the delivery date on a purchase order line. |
| Inventory date | This field is set when a registration transaction was done on the receipt order before a physical receipt was posted. |
| Non-financial transfer | A value that indicates whether the selected inventory transaction is a non-financial transfer. A non-financial transfer occurs when a change in inventory dimensions isn't financially tracked on the **Item model group** page. |
| Transfer lot ID | If the selected inventory transaction is a non-financial transfer, this field is set to the **Lot ID** value of the other inventory transaction that the selected transaction is settled against. |

## Fields on the Updates FastTab

The following table describes the fields on the **Updates** FastTab that don't also appear on the **Inventory transactions** page.

| Field | Description |
|---|---|
| Physical voucher | The voucher number from the general ledger where the physical posting for the selected inventory transaction was generated. |
| Route | The route that is related to the selected inventory transaction. This field is set only for production picking list transactions where the bill of materials (BOM) or formula line is related to a specific item. |
| Packing slip | The packing slip number that was entered for a purchase order product receipt transaction. |
| Physical cost amount | The amount that was posted to the general ledger for the physical update. For a standard cost product, this amount represents the standard cost. For other costing methods, it represents the weighted average for the product at the time of posting. |
| Physical revenue | The amount of deferred revenue that was posted to the general ledger for the physical update. |
| Load ID | If the current transaction is related to a load in Transportation management, this field shows the unique number of the load that included the item. |
| Physically posted | A value that indicates whether the selected inventory transaction has been physically posted. If the current transaction is posted to the general ledger, there will also be a physical voucher. |
| Financially posted | A value that indicates whether the selected inventory transaction has been financially posted. If the current transaction is posted to the general ledger, there will also be a financial voucher. |
| Physical charge posted | A value that indicates whether the physical charges that are related to the selected inventory transaction have been posted. |
| Financial charge posted | A value that indicates whether the financial charges that are related to the selected inventory transaction have been posted. |
| Financial voucher | The voucher number in the general ledger where the financial posting was generated. |
| Invoice | The invoice number that was generated, for example, for a purchase order or sales order. |
| Adjustment | The amount that was adjusted on the selected inventory transaction from the inventory close and adjustment process. |
| Profit and loss, posted amount | The amount of the selected inventory transaction that was posted to the profit and loss statement. |
| Unposted invoice | The invoice number of a related purchase order that appears on the **Pending vendor invoice** page. |
| Financially closed | The date when the transaction was fully settled. |
| Covered CW quantity | The catch weight quantity that is covered by the settlement. |
| Settled quantity | The quantity that has been settled for the selected inventory transaction. |
| Amount settled | The value that has been settled for the selected inventory transaction. |
