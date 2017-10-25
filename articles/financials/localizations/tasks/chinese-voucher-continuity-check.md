--- 
# required metadata 
 
title: Chinese voucher continuity check
description: Before you can close a fiscal period, the Chinese voucher numbers for each voucher type must start at 1 and be sequential. 
author: ShylaThompson
manager: AnnBe 
ms.date: 10/27/2016
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
ms.search.region: China (PRC)
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Chinese voucher continuity check

[!include[task guide banner](../../includes/task-guide-banner.md)]

Before you can close a fiscal period, the Chinese voucher numbers for each voucher type must start at 1 and be sequential.
This procedure shows how to check all posted vouchers in a fiscal period and renumber the Chinese voucher numbers to to be sequential. This process is part of the fiscal period closing process, so it can only be run for On hold fiscal periods. The first sub task walks you through stopping a fiscal period. 

This procedure was created using the demo data company CNMF. This procedure is for a feature that was added in Dynamics 365 for Operations version 1611.


## Stop a fiscal period
1. Go to General ledger > Calendars > Ledger calendars.
2. In the Fiscal year field, enter or select a value.
3. In the list, find and select the desired record.
4. In the list, mark the selected row.
5. Click Edit.
6. Click Stop period.
7. Click Validate.
8. Click OK.
9. Click OK.

## Check whether posted vouchers have continuity voucher numbers
1. Go to General ledger > Inquiries and reports > Voucher transactions.
2. In the Criteria field, enter or select a value.
3. In the Criteria field, enter or select a value.
4. Click OK.

## Run the Chinese voucher continuity check process
1. Go to General ledger > Periodic tasks > Chinese voucher continuity check.
2. Select Yes in the Print out the result of renumbering field.
3. In the Period start field, enter a date.
4. Click OK.
5. Go to General ledger > Inquiries and reports > Voucher continuity check log.

