---
# required metadata

title: System grouping on an open work list
description: This topic describes how to filter the open work list on a mobile device.
author: Mirzaab
manager: AnnBe
ms.date: 05/26/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  WHSRFMenuItem
audience: Application User
# ms.devlang: 
ms.reviewer: bis
ms.search.scope: Core, AX 7.0.0, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 269384
ms.search.region: Global
# ms.search.industry: 
ms.author: mirzaab
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# System grouping on an open work list

[!include[banner](../includes/banner.md)]

By using a system grouping field, you can filter an open work list without having to edit the mobile device menu item.
Where it applies, system grouping works for filtering a work list on a single work header field. You cannot use system grouping to filter on line level fields.

## Set up system grouping on an open work list
Use these steps to set up system grouping on an open work list.

-	From a mobile device menu item, select **Mode: Indirect** and **Activity Code: Display open work list**. The following options become available. These options are required for system grouping on an open work list. 

| Option        | Description   | 
| ------------- | ------------- |
| Allow system grouping   | Enables system groping for a selected work list menu item.| 
| System grouping field   | Available only if **Allow system work** is set to **Yes**. Select the field that determines how picking work will be grouped for workers. For example, if you select the **ShipmentId** field, the worker will scan the shipment ID to group the picking work. All work for the shipment is then assigned to the worker. This field requires that you create a menu item to use existing work that is grouped by the system. Use the **System grouping label** field to inform the worker what to scan. |
| System grouping label   | Available only if **Allow system work** is set to **Yes**. Enter information for the worker about what to scan when picking work is grouped. For example, if you use the **ShipmentId** field to group picking work by shipment, you might enter Shipment ID in the field. This field requires that you create a menu item to use existing work that is grouped by the system. You must also select the field to group by in the **System grouping** field.|
