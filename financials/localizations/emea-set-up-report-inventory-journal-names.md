---
# required metadata

title: Inventory journal reports
description: When you use configurable inventory reports based on electronic reporting, you need to set up a relationship between a specific report and a journal type.
author: ShylaThompson
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: InventJournalName
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 81
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 265144
ms.assetid: 0f07f62f-1053-46e9-b235-a7b38cbda409
ms.search.region: Estonia, Hungary, Latvia, Lithuania, Poland
# ms.search.industry: 
ms.author: v-lenest
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Inventory journal reports

When you use configurable inventory reports based on electronic reporting, you need to set up a relationship between a specific report and a journal type.

To set up a relationship between a specific report and a journal type, on the **Inventory journal names** page (**Inventory management** &gt; **Setup** &gt; **Journal names** &gt; **Inventory**), enter a name for the report. **Note:** To set up supported configurations, download the required electronic reporting configurations. For more information, see [Download Electronic reporting configurations from Lifecycle Services](/dynamics365/operations/dev-itpro/analytics/download-electronic-reporting-configuration-lcs). Examples of inventory reports with supported configurations in Europe are listed in the following table.
|                    |                                     |                  |                                         |
|--------------------|-------------------------------------|------------------|-----------------------------------------|
| **Country**        | **Report description**              | **Journal type** | **Format mapping name**                 |
| Lithuania, Hungary | Inventory statement report          | Counting         | Inventory statement (HU, LT)            |
| Latvia, Poland     | Inventory reclassification document | Transfer         | InventoryReclassificationDocument\_PLLV |
| Estonia            | Inventory reclassification document | Transfer         | InventoryReclassificationDocument\_EE   |
| Poland             | Internal PW/RW                      | Movement         | InventJournalLinesDocPL                 |
| Latvia             | Inventory movement document         | Movement         | Movement\_LV                            |
| Latvia             | Inventory write-down document       | Adjustment       | InventJournalLines\_LV                  |
| Latvia             | Transfer delivery note              | Transfer         | InternalTransferDeliveryNote\_LV        |
| Latvia             | Counting document report            | Counting         | CountedDocument\_LV                     |
| Latvia             | Counting list report                | Counting         | Counting list                           |



