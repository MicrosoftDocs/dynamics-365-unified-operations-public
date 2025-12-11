---
title: Propose and post the impairment amount by batch
description: Learn how to propose and post the impairment amount by batch for Japan in Microsoft Dynamics 365 Finance.
author: kfend
ms.author: johnmichalak
ms.topic: how-to
ms.date: 12/08/2025
ms.reviewer: johnmichalak
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: LedgerJournalTable, LedgerJournalTransAsset
ms.custom: 
  - bap-template
---

# Propose and post the impairment amount by batch

[!include [banner](../../includes/banner.md)]

This article explains how to propose and post the impairment amount by batch for Japan in Microsoft Dynamics 365 Finance.

Before you can complete the following procedure, you must have an impairment test confirmed and saved. The procedure uses the JPMF demo company data.

To propose and post the impairment amount by batch, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets \> Periodic tasks \> Impairment proposal**.
1. In the **Name of journal** field, select the drop-down button to open the lookup.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. In the **Impairment test ID** field, select the drop-down button to open the lookup.
1. In the list, select the link in the selected row.
1. Expand the **Run in the background** section.
1. In the **Batch processing** field, select **Yes**.
1. Select **Create journal**.
1. Go to **Fixed assets \> Journal entries \> Fixed assets journal**. The batch processes asynchronously, so the journal might not be created yet.  
1. Refresh the page to see the latest information. You might need to refresh multiple times depending on when the batch is processed.  
1. In the list, find and select the desired record. You might need to refresh the page multiple times depending on when the batch is processed.  
1. Select **Lines**.
1. Confirm that the correct fixed assets are created and that they have the correct impairment amount.  
1. Select **Post**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
