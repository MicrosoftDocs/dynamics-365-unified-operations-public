---
title: Inventory transaction details
description: Learn about the Transactions details page that shows details of a selected inventory transaction, including a table defining various FastTabs. 
author: AndersEvenGirke
ms.author: aevengir
ms.reviewer: kamaybac
ms.search.form: InventTrans, InventTransDetails
ms.topic: how-to
ms.date: 11/18/2026
ai-usage: ai-assisted
ms.update-cycle: 1095-days
ms.custom: 
  - bap-template
  - evergreen
---

# Inventory transaction details

[!INCLUDE [banner](../includes/banner.md)]

Use the **Transaction details** page to view details of any selected inventory transaction.

> [!TIP]
> Many transactions and updates are categorized as being either *physical* or *financial*. To learn more about these categories, see [Physical and financial updates](../cost-management/physical-financial-updates.md).

## Inventory transactions page performance improvement

Supply Chain Management version 10.0.39 introduced the *Inventory transaction details page's performance improvement* feature, which improves the performance of the **Inventory transactions** page. As of version 10.0.43, this feature is turned on by default. As of Supply Chain Management version 10.0.45, it's mandatory and can't be turned off.

To allow the **Inventory transactions** list page to load more quickly, it now provides a **Filters** pane that you can use to limit the sets of transactions listed. The next time you open the page, it remembers your last-used filter settings. The page doesn't list any transactions until you select **Apply** on the **Filters** pane. In addition, the page now shows only inventory-related fields.

> [!IMPORTANT]
> The *Inventory transaction details page's performance improvement* feature changes the form used to create the **Inventory transactions** page from `InventTrans` to `InventTransNew`. The feature also changes the navigation so that the new form opens when you go to **Inventory management** > **Inquiries and reports** > **Transactions** (which now opens a URL that resembles `https://contoso.operations.dynamics.com/?cmp=usmf&mi=InventTransNew`). This same form also creates the **Transaction details** page. After upgrading to a version of Supply Chain Management that has this feature turned on, you must reproduce any customizations that you made to the old form on the new form.

## Improve performance by using noncontinuous lot IDs

Each inventory transaction has a unique **Lot ID** (`InventTransId`), which the system uses to track inventory across transactions. The system assigns the lot ID based on a defined number sequence. The lot ID doesn't require a continuous number sequence, so you can reduce overhead and improve performance by configuring it as a noncontinuous sequence.

Noncontinuous number sequences can skip numbers, for example when a transaction is canceled. Use continuous number sequences only for references that require continuous numbering for regulatory or legal compliance.

To learn how to set up a noncontinuous number sequence that you can use for the lot ID, see [Number sequences overview](../../fin-ops-core/fin-ops/organization-administration/number-sequence-overview.md#continuous-and-noncontinuous-number-sequences) and [Set up number sequences on an individual basis](../../fin-ops-core/fin-ops/organization-administration/tasks/set-up-number-sequences-individual-basis.md).

To assign the number sequence for the lot ID, go to **Inventory management** > **Setup** > **Inventory and warehouse management parameters**. Find the sequence with a **Reference** of *Lot ID* and set its **Number sequence code** to the number sequence you want to use.

You can see the lot ID used by each inventory transaction on the **General** FastTab of **Transaction details** page, as described later in this article.

## Open the Transaction details page

To open the **Transaction details** page, follow these steps:

1. Go to **Inventory management** > **Inquiries and reports** > **Transactions**.
1. The **Inventory transactions** page opens.
1. On the **Filters** pane, set filters to narrow down the list of inventory transactions and then select **Apply**.
1. Find and select the transaction that you want to inspect.
1. On the Action Pane, select **Transaction details**.

## FastTabs overview

The **Transaction details** page is split into several FastTabs. The following table describes the purpose of each FastTab.

| FastTab | Description |
|---|---|
| General | This FastTab shows basic information about the selected inventory transaction. In addition to the fields that appear on the **Inventory transactions** page, it includes the additional fields that are described later in this article. |
| Updates | This FastTab shows information that is related to the physical, financial, and settlement aspects of the selected inventory transaction. Depending on the current status of the transaction, some fields might be blank. However, those fields are automatically set when you post transactions. In addition to the fields that appear on the **Inventory transactions** page, this FastTab includes the additional fields that are described later in this article. |
| Ledger postings | This FastTab shows the posting type and ledger account that are used for the physical update, financial update, physical revenue, physical charges, financial revenue, and financial charges that are related to the selected inventory transaction. |
| References | This FastTab shows additional information about the source transaction that created the selected inventory transaction. For example, this information might include details from the purchase order or sales order. |
| Related information | This FastTab shows additional information about the selected inventory transaction. These fields might not be set if you aren't using some features, such as procurement categories or projects. |
| Financial dimensions – physical | This FastTab shows the financial dimension values that were used when the physical update was posted. If the physical update isn't posted, the fields are blank. |
| Financial dimensions – financial | This FastTab shows the financial dimension values that were used when the financial update was posted. If the financial update isn't posted, the fields are blank. |
| Inventory dimensions | This FastTab shows the inventory dimension values that are assigned to the selected inventory transaction. These values include the site, warehouse, size, color, configuration, location, batch number, serial number, inventory status, license plate, and owner. |

## Fields on the General FastTab

The following table describes the fields on the **General** FastTab that don't also appear on the **Inventory transactions** page.

| Field | Description |
|---|---|
| Party | The name of the relevant party for the selected inventory transaction. For example, a purchase order transaction shows the name of the vendor on the purchase order, and a sales order transaction shows the name of the customer. This field isn't available for all types of inventory transactions. |
| Inventory reference | If another inventory transaction is related to the selected inventory transaction, the type of that other transaction. For example, if a purchase order is marked against a sales order, the **Inventory reference** field of the purchase order transaction is set to *Sales order*. Marking automatically occurs for direct delivery orders and intercompany orders. When you use marking with costing methods other than *standard cost* and *moving average*, the system creates settlements and adjustments to the exact transactions that are marked. In this way, you can achieve "actual" costing that overrides the logic for first in, first out (FIFO); last in, first out (LIFO); or weighted average. |
| Inventory number | The specific transaction that is related to the selected inventory transaction. For example, if a purchase order is marked against a sales order, the **Inventory number** field of the purchase order transaction is set to the sales order number. |
| Project ID | If the selected inventory transaction is related to a project, this field is set to the project number. |
| Lot ID | The unique lot ID that the system assigned to the selected inventory transaction. |
| Reference lot | If another inventory transaction is related to the selected inventory transaction, the lot ID of that other transaction. For example, if a purchase order is marked against a sales order, the **Reference lot** field of the purchase order transaction is the **Lot ID** value of the sales order line's inventory transaction. |
| Dimension number | A unique ID that represents the combination of all the inventory dimension values that are assigned to the selected inventory transaction. |
| Value open | A value that indicates whether the selected inventory transaction is settled by the inventory closing process. If this field is set to *Yes*, the transaction isn't settled. |
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
| Packing slip | The packing slip number entered for a purchase order product receipt transaction. |
| Physical cost amount | The amount that was posted to the general ledger for the physical update. For a standard cost product, this amount represents the standard cost. For other costing methods, it represents the weighted average for the product at the time of posting. |
| Physical revenue | The amount of deferred revenue that was posted to the general ledger for the physical update. |
| Load ID | If the current transaction is related to a load in Transportation management, this field shows the unique number of the load that included the item. |
| Physically posted | A value that indicates whether the selected inventory transaction is physically posted. If the current transaction is posted to the general ledger, there is also a physical voucher. |
| Financially posted | A value that indicates whether the selected inventory transaction is financially posted. If the current transaction is posted to the general ledger, there is also a financial voucher. |
| Physical charge posted | A value that indicates whether the physical charges that are related to the selected inventory transaction are posted. |
| Financial charge posted | A value that indicates whether the financial charges that are related to the selected inventory transaction are posted. |
| Financial voucher | The voucher number in the general ledger where the financial posting was generated. |
| Invoice | The invoice number that was generated, for example, for a purchase order or sales order. |
| Adjustment | The amount that was adjusted on the selected inventory transaction from the inventory close and adjustment process. |
| Profit and loss, posted amount | The amount of the selected inventory transaction that was posted to the profit and loss statement. |
| Unposted invoice | The invoice number of a related purchase order that appears on the **Pending vendor invoice** page. |
| Financially closed | The date when the transaction was fully settled. |
| Covered CW quantity | The catch weight quantity that is covered by the settlement. |
| Settled quantity | The quantity that is settled for the selected inventory transaction. |
| Amount settled | The value that is settled for the selected inventory transaction. |
