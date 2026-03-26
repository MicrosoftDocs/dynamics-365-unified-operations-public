--- 
title: Set up number sequences using a wizard
description: Learn about how to set up all required number sequences at the same time by using a wizard, including a step-by-step process. 
author: SunilGarg
ms.author: sunilg
ms.topic: how-to
ms.date: 03/10/2026
ms.custom:
ms.reviewer: johnmichalak
audience: Application User   
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: NumberSequenceTableListPage, NumberSequenceWizard 
ms.dyn365.ops.version: Version 7.0.0 
---

# Set up number sequences by using a wizard

[!INCLUDE [banner](../../includes/banner.md)]

Number sequences generate readable, unique identifiers for master data records and transaction records that need them. A master data or transaction record that needs an identifier is called a reference. Before you can create new records for a reference, you need to set up a number sequence and associate it with the reference. This article explains how to set up all required number sequences at the same time by using a wizard. The demo data company used to create this procedure is USMF.

1. Go to **Navigation > Modules > Organization administration > Number sequences > Number sequences**.
1. Select **Generate**.
1. Select **Next**.

   - On this page, you can modify the identification code, the lowest value, and the highest value. You can also specify whether the number sequence must be continuous.
   - Don't select the **Continuous** option if you need to preallocate numbers for the number sequence. To add a scope segment to the format of a number sequence, select the format in the list, and then select **Include scope in format**. To remove a scope segment from the format of a number sequence, select the format in the list, and then select **Remove scope from format**. To exclude a number sequence from automatic generation, select the number sequence in the list, and then select **Delete**.  

1. Select **Next**.
1. Select **Finish**.

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
