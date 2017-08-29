--- 
# required metadata 
 
title: Set up number sequences by using a wizard
description: Number sequences are used to generate readable, unique identifiers for master data records and transaction records that require them. 
author: sericks007
manager: AnnBe 
ms.date: 11/10/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: sericks
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: sericks
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Set up number sequences by using a wizard

[!include[task guide banner](../../includes/task-guide-banner.md)]

Number sequences are used to generate readable, unique identifiers for master data records and transaction records that require them. A master data or transaction record that requires an identifier is referred to as a reference. Before you can create new records for a reference, you must set up a number sequence and associate it with the reference. This procedure explains how to set up all required number sequences at the same time by using a wizard. The demo data company used to create this procedure is USMF.

1. Go to Organization administration > Number sequences > Number sequences.
2. Click Generate.
3. Click Next.
    * On this page, you can modify the identification code, the lowest value, and the highest value. In addition, you can indicate whether the number sequence must be continuous.   
    * Do not select the Continuous option if you must preallocate numbers for the number sequence.     To add a scope segment to the format of a number sequence, select the format in the list, and then click Include scope in format.     To remove a scope segment from the format of a number sequence, select the format in the list, and then click Remove scope from format.     To exclude a number sequence from automatic generation, select the number sequence in the list, and then click Delete.  
4. Click Next.
5. Click Finish.

