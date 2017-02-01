---
# required metadata

title: Inventory journal reports | Microsoft Docs
description: When you use configurable inventory reports based on electronic reporting, you need to set up a relationship between a specific report and a journal type.
author: ShylaThompson
manager: AnnBe
ms.date: 2016-12-22 15:24:32
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

keywords: InventJournalName
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: 81
ms.suite: Released- Dynamics 365 for Operations version 1611
# ms.tgt_pltfrm: 
ms.custom: 265144
ms.assetid: 7f67c4f1-5172-4057-9e2d-9c6e83a1e58d
ms.region: Estonia, Hungary, Latvia, Lithuania, Poland
# ms.industry: 
ms.author: v-lenest

---

# Inventory journal reports

When you use configurable inventory reports based on electronic reporting, you need to set up a relationship between a specific report and a journal type.

To set up a relationship between a specific report and a journal type, on the **Inventory journal names** page (**Inventory management** &gt; **Setup** &gt; **Journal names** &gt; **Inventory**), enter a name for the report. **Note:** To set up supported configurations, download the required electronic reporting configurations. For more information, see [Download Electronic reporting configurations from Lifecycle Services](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/analytics-bi-reporting/download-electronic-reporting-er-configuration-from-lifecycle-services). Examples of inventory reports with supported configurations in Europe are listed in the following table.
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



