---
title: Create a depreciation proposal
description: Learn how depreciation batch proposals work and explains how to propose depreciation for fixed assets, including a step-by-step process. 
author: abruer
ms.author: abruer
ms.topic: how-to
ms.date: 03/28/2023
ms.custom:
ms.reviewer: twheeloc
audience: Application User   
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: LedgerJournalTable, LedgerJournalTransAsset
ms.dyn365.ops.version: Version 7.0.0
---

# Create a depreciation proposal

[!include [banner](../../includes/banner.md)]

This article describes how depreciation batch proposals work and explains how to propose depreciation for fixed assets. This task uses the USMF demo company and the accountant role.


## Create a depreciation proposal
1. Go to **Fixed assets > Journal entries > Create depreciation proposal**.
2. In the **Name of journal** field, select an option from the drop-down menu.
3. In the **To date** field, enter a date.

    - Select the **Summarize depreciation** option to summarize monthly depreciations into one journal line.  
    - For example, if the **To date** value is March 31, 2022, the following description is generated: **Depreciation since January 31, 2022.** The **Date** field on the proposed journal lines is then set to March 31, 2022.  
    - The depreciation proposal can be filtered by asset, asset group, or other criteria using the **Filter** option.  
    - When you use the **Create acquisition or depreciation proposals for fixed assets** page, you can propose depreciation in batches. This is recommended for larger proposals that will use more system resources. If you select the batch option, you can still complete other tasks during that time. When you propose depreciation in this way, depreciation is calculated for value models for fixed assets.  

4. Select **Create journal**.

## Review depreciation entries
1. Go to **Fixed assets > Journal entries > Fixed assets journal**.
2. In the list, find and select the desired record.
3. Select **Lines**.
4. Select **Post**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
