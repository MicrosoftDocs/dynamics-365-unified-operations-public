---
title: Inventory journals
description: Learn how you can use inventory journals to post various types of physical inventory transactions with an outline on types of inventory journals.
author: banluo-ms
ms.author: banluo
ms.reviewer: kamaybac
ms.search.form: InventJournalBOM, InventJournalCount, InventJournalCountTag, InventJournalLossProfit, InventJournalMovement, InventJournalTransfer, WMSJournalTable
ms.topic: overview
ms.date: 08/29/2025
ms.custom:
  - bap-template
---

# Inventory journals

[!include [banner](../includes/banner.md)]

This article describes how you can use inventory journals to post various types of physical inventory transactions.

In Supply Chain Management, use inventory journals to post physical inventory transactions of various types, such as the posting of issues and receipts, inventory movements, the creation of bills of materials (BOMs), and the reconciliation of physical inventory. All these inventory journals work in a similar way, but they're divided into different types.

## Types of inventory journals

The following types of inventory journals are available:

- Movement
- Inventory adjustment
- Transfer
- BOM
- Item arrival
- Production input
- Counting
- Tag counting

### Movement

When you use an inventory movement journal, you can add cost to an item when you add inventory, but you must manually allocate the extra cost to a particular general ledger account by specifying a general ledger offset account when you create the journal. This inventory journal type is useful if you want to overwrite the default posting accounts.

### Inventory adjustment

When you use an inventory adjustment journal, you can add cost to an item when you add inventory. The extra cost is automatically posted to a specific general ledger account, based on the setup of the item group posting profile. Use this inventory journal type to update gains and losses to inventory quantities when the item should keep its default general ledger offset account. When you post an inventory adjustment journal, you post an inventory receipt or issue, change the inventory values, and create ledger transactions.

### Transfer

Use transfer journals to transfer items between stocking locations, batches, or product variants without associating any cost implications. For example, you can transfer items from one warehouse to another warehouse within the same company. When you use a transfer journal, you must specify both the "from" and "to" inventory dimensions (for example, for Site and Warehouse). The on-hand inventory for the defined inventory dimensions changes accordingly. Inventory transfers reflect the immediate movement of material. In-transit inventory isn't tracked. If you need to track in-transit inventory, use a transfer order instead. When you post a transfer journal, two inventory transactions are created for each journal line:

- An inventory issue at the "from" location.
- An inventory receipt at the "to" location.

### BOM

When you report a BOM as finished, you can create a BOM journal. By using a BOM journal, you can post the BOM directly. This posting generates an inventory receipt of the product, together with an associated BOM and an inventory issue of the products that are included in the BOM. This inventory journal type is useful in simple or high-volume production scenarios where routes aren't required.

### Item arrival

Use the item arrival journal to register the receipt of items (for example, from purchase orders). You can create an item arrival journal as part of arrival management from the **Arrival overview** page, or you can manually create a journal entry from the **Item arrival** page. If you enable the item arrival journal name to check for picking locations, Supply Chain Management looks for a location for received items and, if there's room, generates location destinations for the incoming items.

### Production input

Production input journals work like the item arrival journals but are used for production orders.

### Counting

Counting journals let you correct the current on-hand inventory that is registered for items or groups of items, and then post the actual physical count, so that you can make the adjustments that are required to reconcile the differences. You can associate counting policies with counting groups to help group items that have various characteristics, so that those items can be included in a counting journal. For example, you can set up counting groups to count items that have a specific frequency, or to count items when stock falls to a particular level. For information about how to define counting groups, see [Define inventory counting processes](tasks/define-inventory-counting-processes.md).

### Tag counting

Use tag counting journals to assign a numbered tag to a count lot. The tag contains a tag number, item number, and item quantity. To ensure that a tag is used only one time, and that all tags are used, every item number has a unique set of tags with its own number sequence. You can set three status values for each tag:

- **Used** – The item number is counted for this tag.
- **Voided** – The item number is voided for this tag.
- **Missing** – The item number is missing for this tag.

When you post a tag counting journal, you create a new counting journal based on the tag counting journal lines. For more information about tag counting, see [Inventory tag counting](inventory-tag-counting.md).

## Working with journals

Only one user at a time can access a journal. If several users need to access journals at the same time to create journal lines, they must select journals that aren't currently being used. This approach prevents information from being overwritten. In situations where multiple departments use the same journal type, it's helpful to create multiple journal names (for example, one per department). It can also be helpful to divide journals so that each posting routine is entered in its own unique inventory journal. For posting routines that are associated with inventory transactions, create one journal for periodic inventory adjustments and another for inventory counting.

## Posting journal lines

You can post the journal lines that you create at any time until you lock an item from additional transactions. The data that you enter in a journal remains in that journal, even if you close the journal without posting the lines.

## Data entity support for inventory journals

Data entities support the following types of integration scenarios:

- Synchronous service (OData)
- Asynchronous integration

Learn more in [Data entities](../../fin-ops-core/dev-itpro/data-entities/data-entities.md).

> [!NOTE]
> Not all inventory journals are OData-enabled, so you can't use the Excel data connector to get data published, updated, and imported back to Supply Chain Management.

Another difference between the journal data entities is the ability to use composite entities that include both the header and line data. Currently, you can use the composite entities for:

- Inventory adjustment journal
- Inventory movement journal

These two inventory journals only support the *Initialize stock* scenario as part of a data management import project:

- When you don't specify a journal header number but specify a number sequence for the journal type, the import job automatically creates journal headers per 1,000 lines. For example, importing 2,020 lines results in the following three journal headers:
    - Header 1: contains 1,000 lines
    - Header 2: contains 1,000 lines
    - Header 3: contains 20 lines
- The import process assumes that unique line information exists per inventory dimension, which can be a product, storage, and tracking dimension. Therefore, you can't import journal lines where only the date field differs on the lines within the same import project.

## Related information

- [Data entities](../../fin-ops-core/dev-itpro/data-entities/data-entities.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
