---
# required metadata

title: Voyage status setup
description: This topic describes how to establish the status values that users can assign to voyages.
author: RichardLuan
manager: tfehr
ms.date: 01/13/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: ITMStatusTable
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: riluan
ms.search.validFrom: 2021-01-13
ms.dyn365.ops.version: Release 10.0.17
---

# Voyage status setup

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

The **Voyage statuses** settings establish the set of status values that users can assign to voyages. Users can assign voyage status values for all levels of a voyage (voyage, shipping container, folio, purchase order, and item (purchase lines, transfer order line)). They are used for two purposes:

- They inform the user of the status of the voyage, shipping container, folio, purchase order, or item (purchase lines, transfer order line)
- They can restrict the use of the cost area by preventing modification or deletion.

To set up your voyage statuses, go to **Landed cost \> Setup \> Voyage Statuses**. From here, you can add, remove, and edit statuses in the grid by using commands in the Action Pane.

Each cost area has it's own set and hierarchy of statuses. Start by making a selection from the **Cost area** drop-down list to choose which cost area you would like to view or create voyage statuses for. Then make the settings described in the following table, as needed, for each voyage status.

The status of any voyage might be changed automatically by other events in the system, such as rules established using the tracking control center.

| Field | Description |
|---|---|
| Voyage status | Specify the name of the voyage status. |
| Description | Enter a description of the voyage status. |
| Modify | Select this check box to allow voyages that have this status to be modified by users. |
| Delete | Select this check box to allow voyages that have this status to be deleted by users.  |
| Mandatory | Select this check box to make this voyage status mandatory, which means it can't be skipped. |
| Parent | Use this setting to establish a hierarchy among the status values. The system will only allow voyage status to be changed (manually or automatically) in the direction that goes down in the hierarchy from a parent status to one of its child statuses.

> [!NOTE]
> You only need to set up the specific voyage statuses that your organization uses.  Common voyage statuses include confirmed, goods in transit, received, ready for costing, and costed, but additional statuses may be present.
