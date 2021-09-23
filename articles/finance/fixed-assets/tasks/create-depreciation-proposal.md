---
# required metadata 
title: Create a depreciation proposal
description: This topic describes how depreciation batch proposals work and explains how to propose depreciation for fixed assets. 
author: abruer
ms.date: 08/01/2019
ms.topic: business-process 
ms.prod:  
ms.technology:  

# optional metadata 
ms.search.form: LedgerJournalTable, LedgerJournalTransAsset   
audience: Application User 
# ms.devlang:
ms.reviewer: roschlom
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: abruer
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0

---

# Create a depreciation proposal

[!include [banner](../../includes/banner.md)]

This topic describes how depreciation batch proposals work and explains how to propose depreciation for fixed assets. This task uses the USMF demo company and the accountant role.


## Create a depreciation proposal
1. In the navigation pane, go to **Modules > Fixed assets > Journal entries > Create depreciation proposal**.
2. In the **Name of journal** field, select an option from the drop-down menu.
3. In the **To date** field, enter a date.

    - Select the **Summarize depreciation** option to summarize monthly depreciations into one journal line.  
    - For example, if the To date value is March 31, 2015, the following description is generated: "Depreciation since January 31, 2015." The **Date** field on the proposed journal lines is then set to March 31, 2015.  
    - The depreciation proposal can be filtered by asset, asset group, or other criteria using the **Filter** option.  
    - When you use the **Create acquisition or depreciation proposals for fixed assets** form, you can propose depreciation in batches. This is recommended for larger proposals that will use more system resources. If you select the batch option, you can still complete other tasks during that time. When you propose depreciation in this way, depreciation is calculated for value models for fixed assets.  

4. Select **Create journal**.

## Review depreciation entries
1. In the navigation pane, go to **Modules > Fixed assets > Journal entries > Fixed assets journal**.
2. In the list, find and select the desired record.
3. Select **Lines**.
4. Select **Post**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]