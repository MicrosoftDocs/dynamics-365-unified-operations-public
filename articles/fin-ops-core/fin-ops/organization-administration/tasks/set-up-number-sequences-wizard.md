--- 
# required metadata 
 
title: Set up number sequences using a wizard
description: This article explains how to set up all required number sequences at the same time by using a wizard. 
author: SunilGarg
ms.date: 07/18/2019
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: NumberSequenceTableListPage, NumberSequenceWizard   
audience: Application User 
# ms.devlang:  
ms.reviewer: sericks
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: sunilg
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Set up number sequences using a wizard

[!include [banner](../../includes/banner.md)]

Number sequences are used to generate readable, unique identifiers for master data records and transaction records that require them. A master data or transaction record that requires an identifier is referred to as a reference. Before you can create new records for a reference, you must set up a number sequence and associate it with the reference. This article explains how to set up all required number sequences at the same time by using a wizard. The demo data company used to create this procedure is USMF.

1. Go to **Navigation > Modules > Organization administration > Number sequences > Number sequences**.
2. Select **Generate**.
3. Select **Next**.

   - On this page, you can modify the identification code, the lowest value, and the highest value. In addition, you can indicate whether the number sequence must be continuous.   
   - Do not select the **Continuous** option if you must preallocate numbers for the number sequence. To add a scope segment to the format of a number sequence, select the format in the list, and then select **Include scope in format**. To remove a scope segment from the format of a number sequence, select the format in the list, and then select **Remove scope from format**. To exclude a number sequence from automatic generation, select the number sequence in the list, and then select **Delete**.  

4. Select **Next**.
5. Select **Finish**.



[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
