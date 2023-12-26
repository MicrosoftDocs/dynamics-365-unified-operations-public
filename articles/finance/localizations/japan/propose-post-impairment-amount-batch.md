---
title: Propose and post the impairment amount by batch
description: This task walks you through proposing and posting the impairment amount by batch.
author: kfend
ms.date: 08/29/2018
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Japan
ms.author: kfend
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: LedgerJournalTable, LedgerJournalTransAsset
---

# Propose and post the impairment amount by batch

[!include [banner](../../includes/banner.md)]

This task walks you through proposing and posting the impairment amount by batch. Before you can complete this task, you must have an impairment test confirmed and saved. This task uses the JPMF demo company data.

1. Go to Fixed assets > Periodic tasks > Impairment proposal.
2. In the Name of journal field, click the drop-down button to open the lookup.
3. In the list, find and select the desired record.
4. In the list, click the link in the selected row.
5. In the Impairment test ID field, click the drop-down button to open the lookup.
6. In the list, click the link in the selected row.
7. Expand the Run in the background section.
8. Select Yes in the Batch processing field.
9. Click Create journal.
10. Go to Fixed assets > Journal entries > Fixed assets journal.
    * The batch is processed asynchronously. The journal may not be created yet.  
11. Refresh the page.
    * You can refresh the page to see the latest information. You may need to refresh multiple times depending on when the batch is processed.  
12. In the list, find and select the desired record.
    * You may need to refresh the page multiple times depending on when the batch is been processed.  
13. Click Lines.
    * Confirm that the correct fixed assets were created and that they have the correct impairment amount.  
14. Click Post.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
