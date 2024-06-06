--- 
title: Calculate fixed asset depreciation across legal entities
description: Learn about how to calculate fixed asset depreciation, which can be run across legal entities in a single step, including step-by-step processes.
author: moaamer
ms.author: moaamer
ms.topic: how-to
ms.date: 03/28/2023
ms.custom:
ms.reviewer: twheeloc
audience: Application User 
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: AssetParameters, AssetProposalDepreciation, DefaultDashboard, LedgerJournalTable
ms.dyn365.ops.version: Version 7.0.0 
---

# Calculate fixed asset depreciation across legal entities

[!include [banner](../../includes/banner.md)]

Fixed asset depreciation can be run across legal entities in a single step. This procedure shows you to how set up and run the process for multiple legal entities. It uses the accountant role and demo data for the USMF legal entity.


## Set up cross company depreciation run journals
1. Go to **Fixed assets > Setup > Fixed assets parameters**.
2. Expand the **Fixed asset proposals** section.
3. Click **Add**.
4. In the **Posting layer** field, enter or select a value.
5. In the **Journal name** field, enter or select a value.
    * Repeat the journal setup on the Fixed asset parameters page in each legal entity.  

## Depreciation run
1. Go to **Fixed assets > Journal entries > Create depreciation proposal**.
2. In the **Posting layer** field, enter or select a value.
    * The journal name will default from the **Fixed asset parameters**. It can be changed here for the current legal entity.  
3. In the **To date** field, enter a date.
    * Select the legal entities to be included in the depreciation run.  
    * Only legal entities with journals set up for **Fixed asset proposal**s on the **Fixed asset parameters** page will be shown in the list.  
4. Select **Yes** in the **Post journals** field.
    * Filtering fields include all fixed assets, groups, and books for the legal entities selected for this depreciation run.  
    * The **Batch processing** option is enabled by default. When this option is enabled, the depreciation journal creation and posting will run in the background.  
5. Click **Create journal**.
6. Go to **Fixed assets > Journal entries > Fixed assets journal**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
