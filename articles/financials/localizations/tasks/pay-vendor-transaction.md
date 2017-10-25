--- 
# required metadata 
 
title: Pay a vendor transaction by endorsing a customer bill of exchange (Japan)
description: This task walks you through paying a vendor transaction by endorsing a customer bill of exchange. 
author: ShylaThompson
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
# Pay a vendor transaction by endorsing a customer bill of exchange (Japan)

[!include[task guide banner](../../includes/task-guide-banner.md)]

This task walks you through paying a vendor transaction by endorsing a customer bill of exchange.



Before you can complete this task, you must have at least one bill of exchange with a status of "Drawn".



This task was created using the demo data company JPMF.


## Endorse a customer bill of exchange to a vendor
1. Go to Accounts receivable > Payments > Bill of exchange > Endorse bills of exchange.
2. In the list, find and select the desired record.
    * Select a bill of exchange that has a status of "Drawn".  
3. Click Endorse to vendor to open the drop dialog.
4. In the Date of endorsement field, enter a date.
    * The date cannot be later than the due date of the bill of exchange.  
5. In the Vendor account field, click the drop-down button to open the lookup.
6. In the list, click the link in the selected row.
    * For example: select the record 'JPMF-000001'.  
7. In the Description field, type a value.
8. In the BusinessUnit field, click the drop-down button to open the lookup.
9. In the list, click the link in the selected row.
    * For example: select the record '003'.  
10. Click Endorse to vendor.
11. Click Inquiry.
12. Click Voucher.
    * Verify that an accounting voucher is generated for the endorsement.  

