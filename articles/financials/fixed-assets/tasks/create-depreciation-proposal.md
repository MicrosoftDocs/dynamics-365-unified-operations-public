--- 
# required metadata 
 
title: Create a depreciation proposal
description: This procedure describes how depreciation batch proposals work and explains how to propose depreciation for fixed assets. 
author: saraschi2
manager: AnnBe 
ms.date: 11/14/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: saraschi
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Create a depreciation proposal

[!include[task guide banner](../../includes/task-guide-banner.md)]

This procedure describes how depreciation batch proposals work and explains how to propose depreciation for fixed assets. This task uses the USMF demo company and the accountant role.


## Create depreciation proposal
1. Go to Fixed assets > Journal entries > Create depreciation proposal.
2. In the Name of journal field, click the drop-down button to open the lookup.
3. In the list, click the link in the selected row.
4. In the To date field, enter a date.
    * Select the Summarize depreciation option to summarize monthly depreciations into one journal line.  
    * For example, if the To date value is March 31, 2015, the following description is generated: “Depreciation since January 31, 2015.” The Date field on the proposed journal lines is then set to March 31, 2015.  
    * The depreciation proposal can be filtered by asset, asset group, or other criteria using the Filter option.  
    * When you use the Create acquisition or depreciation proposals for fixed assets form, you can propose depreciation in batches. This is recommended for larger proposals that will use more system resources. If you select the batch option, you can still complete other tasks during that time. When you propose depreciation in this way, depreciation is calculated for value models for fixed assets.  
5. Click Create journal.

## Review depreciation entries
1. Go to Fixed assets > Journal entries > Fixed assets journal.
2. In the list, find and select the desired record.
3. Click Lines.
4. Click Post.

