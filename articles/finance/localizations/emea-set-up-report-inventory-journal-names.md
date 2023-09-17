---
title: Inventory journal reports
description: When you use configurable inventory reports based on electronic reporting, you need to set up a relationship between a specific report and a journal type.
author: AdamTrukawka
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Estonia, Hungary, Latvia, Lithuania, Poland
ms.author: atrukawk
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611
ms.custom: 265144
ms.search.form: InventJournalName
---

# Inventory journal reports

[!include [banner](../includes/banner.md)]

When you use configurable inventory reports based on electronic reporting, you need to set up a relationship between a specific report and a journal type.

To set up a relationship between a specific report and a journal type, on the **Inventory journal names** page (**Inventory management** &gt; **Setup** &gt; **Journal names** &gt; **Inventory**), enter a name for the report. **Note:** To set up supported configurations, download the required electronic reporting configurations. For more information, see [Download Electronic reporting configurations from Lifecycle Services](../../fin-ops-core/dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md). Examples of inventory reports with supported configurations in Europe are listed in the following table.

| Country/region            |    Report description               | Journal type     |    Format mapping name                  |
|--------------------|-------------------------------------|------------------|-----------------------------------------|
| Lithuania, Hungary | Inventory statement report          | Counting         | Inventory statement (HU, LT)            |
| Latvia, Poland     | Inventory reclassification document | Transfer         | InventoryReclassificationDocument\_PLLV |
| Estonia            | Inventory reclassification document | Transfer         | InventoryReclassificationDocument\_EE   |
| Poland             | Internal PW/RW                      | Movement         | InventJournalLinesDocPL                 |
| Latvia             | Inventory movement document         | Movement         | Movement\_LV                            |
| Latvia             | Inventory write-down document       | Adjustment       | InventJournalLines\_LV                  |
| Latvia             | Transfer delivery note              | Transfer         | InternalTransferDeliveryNote\_LV        |
| Latvia             | Counting document report            | Counting         | CountedDocument\_LV                     |
| Latvia             | Counting list report                | Counting         | Counting list                           |







[!INCLUDE[footer-include](../../includes/footer-banner.md)]
