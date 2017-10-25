---
# required metadata

title: Inventory journals
description: This article describes how you can use inventory journals to post various types of physical inventory transactions.
author: MarkusFogelberg
manager: AnnBe
ms.date: 06/20/2017
ms.topic: article
ms.prod:
ms.service: dynamics-ax-applications
ms.technology:

# optional metadata

ms.search.form: InventJournalBOM, InventJournalCount, InventJournalCountTag, InventJournalLossProfit, InventJournalMovement, InventJournalTransfer, WMSJournalTable
# ROBOTS:
audience: Application User
# ms.devlang:
ms.reviewer: YuyuScheller

ms.search.scope: Core, AX 7.0.0, Operations, UnifiedOperations, Retail

# ms.tgt_pltfrm:
ms.custom: 51631
ms.assetid: 3fedeaaf-502f-483c-93d2-ab266828189e
ms.search.region: Global
# ms.search.industry:
ms.author: mafoge
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Inventory journals

[!include[banner](../includes/banner.md)]

[!include[retail name](../includes/retail-name.md)]


This article describes how you can use inventory journals to post various types of physical inventory transactions.

The inventory journals in Microsoft Dynamics 365 for Finance and Operations are used to post physical inventory transactions of various types, such as the posting of issues and receipts, inventory movements, the creation of bills of materials (BOMs), and the reconciliation of physical inventory. All these inventory journals are used in a similar way, but they are divided into different types.

## Types of inventory journals
The following types of inventory journals are available:

-   Movement
-   Inventory adjustment
-   Transfer
-   BOM
-   Item arrival
-   Production input
-   Counting
-   Tag counting

### Movement

When you use an inventory movement journal, you can add cost to an item when you add inventory, but you must manually allocate the additional cost to a particular general ledger account by specifying a general ledger offset account when you create the journal. This inventory journal type is useful if you want to expense an item against a different department, or if you want to remove items from inventory for expense purposes.

### Inventory adjustment

When you use an inventory adjustment journal, you can add cost to an item when you add inventory. The additional cost is automatically posted to a specific general ledger account, based on the setup of the item group posting profile. Use this inventory journal type to update gains and losses to inventory quantities when the item should keep its default general ledger offset account. When you post an inventory adjustment journal, an inventory receipt or issue is posted, the inventory values are changed, and ledger transactions are created.

### Transfer

You can use transfer journals to transfer items between stocking locations, batches, or product variants without associating any cost implications. For example, you can transfer items from one warehouse to another warehouse within the same company. When you use a transfer journal, you must specify both the "from" and "to" inventory dimensions (for example, for Site and Warehouse). The on-hand inventory for the defined inventory dimensions is changed accordingly. Inventory transfers reflect the immediate movement of material. In-transit inventory isn't tracked. If in-transit inventory must be tracked, you should use a transfer order instead. When you post a transfer journal, two inventory transactions are created for each journal line:

-   An inventory issue at the "from" location
-   An inventory receipt at the "to" location

### BOM

When you report a BOM as finished, you can create a BOM journal. By using a BOM journal, you can post the BOM directly. This posting generates an inventory receipt of the product, together with an associated BOM and an inventory issue of the products that are included in the BOM. This inventory journal type is useful in simple or high-volume production scenarios where routes aren't required.

### Item arrival

You can use the item arrival journal to register the receipt of items (for example, from purchase orders). An item arrival journal can be created as part of arrival management from the **Arrival overview** page, or you can manually create a journal entry from the **Item arrival** page. If you enable the item arrival journal name to check for picking locations, Finance and Operations looks for a location for received items and, if there is room, generates location destinations for the incoming items.

### Production input

Production input journals work like the item arrival journals but are used for production orders.

### Counting

Counting journals let you correct the current on-hand inventory that is registered for items or groups of items, and then post the actual physical count, so that you can make the adjustments that are required in order to reconcile the differences. You can associate counting policies with counting groups to help group items that have various characteristics, so that those items can be included in a counting journal. For example, you can set up counting groups to count items that have a specific frequency, or to count items when stock falls to a particular level. For information about how to define counting groups, see [Define inventory counting processes (Task guide)](tasks/define-inventory-counting-processes.md).

### Tag counting

Tag counting journals are used to assign a numbered tag to a count lot. The tag should contain a tag number, item number, and item quantity. To help guarantee that a tag is used only one time, and that all tags are used, every item number should have a unique set of tags that has its own number sequence. Three status values can be set for each tag:

-   **Used** – The item number is counted for this tag.
-   **Voided** – The item number is voided for this tag.
-   **Missing** – The item number is missing for this tag.

When you post a tag counting journal, a new counting journal is created, based on the tag counting journal lines. For more information about tag counting, see [Inventory tag counting](inventory-tag-counting.md).

## Working with journals
A journal can be accessed by only one user at a time. If several users must access journals at the same time to create journal lines, those users must select journals that aren't currently being used, to prevent information from being overwritten. In situations where multiple departments use the same journal type, it's helpful to create multiple journal names (for example, one per department). It can also be helpful to divide journals so that each posting routine is entered in its own unique inventory journal. For posting routines that are associated with inventory transactions, create one journal for periodic inventory adjustments and another for inventory counting.

## Posting journal lines
You can post the journal lines that you create at any time until you've locked an item from additional transactions. The data that you enter in a journal remains in that journal, even if you close the journal without posting the lines.
