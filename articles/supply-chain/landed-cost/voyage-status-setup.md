---
title: Voyage status setup
description: Learn how to establish the status values that users can assign to voyages, including a table that defines various fields.
author: Weijiesa
ms.author: weijiesa
ms.reviewer: kamaybac
ms.search.form: ITMStatusTable
ms.topic: how-to
ms.date: 07/30/2024
ms.custom: 
  - bap-template
---

# Voyage status setup

[!include [banner](../../includes/banner.md)]

On the **Voyage statuses** page, you establish the set of status values that users can assign to voyages. Users can assign voyage status values to all levels of a voyage: voyage, shipping container, folio, purchase order, and item (purchase lines and transfer order lines). They are used for two purposes:

- Inform the user about the status of the voyage, shipping container, folio, purchase order, or item (purchase lines and transfer order lines).
- Limit the use of the cost area by preventing modification or deletion.

To set up your voyage statuses, go to **Landed cost \> Setup \> Voyage statuses**. There, you can add, remove, and edit statuses by using the buttons on the Action Pane.

Each cost area has its own set and hierarchy of voyage statuses. Therefore, on the **Voyage statuses** page, in the **Cost area** field, you must first select the cost area that you want to view or create voyage statuses for. Then, for each voyage status, set the fields that are described in the following table, as required. Note that the status of a voyage can also be automatically changed by system events, such as rules that have been established by using the tracking control center.

| Field | Description |
|---|---|
| Voyage status | Enter the name of the voyage status. |
| Description | Enter a description of the voyage status. |
| Modify | Select this check box if users are allowed to modify voyages that have this status. |
| Delete | Select this check box if users are allowed to delete voyages that have this status. |
| Mandatory | Select this check box to make the voyage status mandatory, so that it can't be skipped. |
| Parent | Use this field to establish a hierarchy among the status values. Voyage statuses can be changed (either manually or automatically) only downward in the hierarchy, from a parent status to one of its child statuses. |

> [!NOTE]
> You have to set up only the specific voyage statuses that your organization uses. Typical voyage statuses include *Confirmed*, *Goods in transit*, *Received*, *Ready for costing*, and *Costed*. However, other statuses might be present.
