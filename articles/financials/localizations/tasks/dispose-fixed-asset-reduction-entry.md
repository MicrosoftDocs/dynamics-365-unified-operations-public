--- 
# required metadata 
 
title: Dispose of a fixed asset with reduction entry (Japan)
description: Use this task to learn how to dispose of a fixed asset with reduction entry for Japan. 
author: ShylaThompson
manager: AnnBe 
ms.date: 09/22/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: shylaw
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Japan
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Dispose of a fixed asset with reduction entry (Japan)

[!include[task guide banner](../../includes/task-guide-banner.md)]

Use this task to learn how to dispose of a fixed asset with reduction entry for Japan.



In order to complete this task, the Fixed Asset configuration key must be selected.



This task was completed using the JPMF demo data company.

1. Go to Fixed assets > Journal entries > Fixed assets journal.
2. Click New.
3. In the Name field, type a value.
4. Click Lines.
5. Click Proposals.
6. Click Disposal - scrap.
7. Enter the date of disposal transaction
8. Click Filter.
9. In the Criteria field, type a value.
10. Click OK.
11. Click OK.
12. Enter the main accounts where the fixed asset disposal expenses will be posted to.
    * You can also choose to enter the disposal expenses later in a journal.     The fixed asset main account and accumulated depreciation main account and other fixed asset related accounts are automatically determined by the configuration in the fixed asset posting profile.  
    * The disposal of reduction entry document is separated from that of the fixed asset.  
    * The original subsidy amount and accumulated amortization amount are automatically determined by the configuration in the fixed asset posting profile.  
13. Click Post.

