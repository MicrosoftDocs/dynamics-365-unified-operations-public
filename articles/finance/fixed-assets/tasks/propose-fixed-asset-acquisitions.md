--- 
# required metadata 
 
title: Propose fixed asset acquisitions
description: This article describes how to acquire a fixed asset using the acquisition proposal in the Fixed assets journal. 
author: moaamer
ms.date: 03/28/2023
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: AssetTable, AssetBook, LedgerJournalTable, LedgerJournalTransAsset, SysQueryForm   
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: moaamer
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Propose fixed asset acquisitions

[!include [banner](../../includes/banner.md)]

This article describes how to acquire a fixed asset using the acquisition proposal in the **Fixed assets journal**. It uses the accountant role and demo data for the USMF legal entity. To acquire a fixed asset through a fixed asset proposal journal, you must first create the fixed asset record, and then define the acquisition price in the asset book.

## Create an asset acquisition proposal

Complete the following steps to create an asset acquisition proposal. 

1. Go to **Fixed assets > Journal entries > Fixed assets journal**.
2. Select **New**.
3. In the **Name** field, enter or select a value.
4. In the Action Pane, select **Lines**.
5. Select **Proposals**.
6. Select **Acquisition proposal**.
7. Select **Filter**. Select **Reset** to clear previous values.
8. Select the **Fixed asset number** row.
9. In the **Criteria** field, enter or select a value. Set the remaining criteria for the fixed assets that you want to acquire with this proposal.  
10. Select **OK** twice to exit out of the pane.
- Verify that the transaction lines are created.  
- Only fixed assets with the acquisition date and acquisition price set on the book will be included in the acquisition proposal.  
11. On the page, select the **Books** tab.
12. Select **Post**.

## Include default financial dimensions in an acquisition proposal

The acquisition transaction can be created using Excel add-ins, by going to **Fixed assets > Journal entries > Fixed asset journal**. Create a new journal and move to the **Lines** section on the page and select the Excel icon, and then select a Fixed asset journal line. The system will create and open an Excel template representing journal lines. You can add data for the journal lines you're adding into the template, and then publish that information back into the system. 

If default dimensions have been set up for the selected asset book and the corresponding fixed assets that were entered in the Excel template, the default financial dimensions will be called from the asset book master data when the journal is published from the Excel to the system. To include financial dimensions on an asset book automatically while publishing the fixed asset journal from the Excel add-in, the default dimensions must be set up in advance.  


[!INCLUDE [footer-include](../../../includes/footer-banner.md)]
