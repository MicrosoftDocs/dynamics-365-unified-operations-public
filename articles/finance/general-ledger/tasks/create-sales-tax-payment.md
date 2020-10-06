--- 
# required metadata 
 
title: Create a sales tax payment
description: The settle and post sales tax job settles sales tax balances on the sales tax accounts and offsets them to the sales tax settlement account for a given period. 
author: twheeloc
manager: AnnBe 
ms.date: 08/29/2018
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: Dialog   
audience: Application User 
# ms.devlang:  
ms.reviewer: roschlom
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: vstehman
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Create a sales tax payment

[!include [banner](../../includes/banner.md)]

The settle and post sales tax job settles sales tax balances on the sales tax accounts and offsets them to the sales tax settlement account for a given period.

1. Go to Tax > Declarations > Sales tax > Settle and post sales tax.
2. In the Settlement period field, click the drop-down button to open the lookup.
3. In the list, click the link in the selected row.
4. In the From date field, enter a date.
    * If the Include corrections option is not selected on the General ledger parameters page, the settlement can be processed for different versions. Original is the first settlement for a period interval and can only processed once for a period interval. Latest corrections will settle sales tax transactions which have been posted after the original version has been created.   
5. In the Transaction date field, enter a date.
6. Click OK.

