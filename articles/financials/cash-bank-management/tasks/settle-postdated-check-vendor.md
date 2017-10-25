--- 
# required metadata 
 
title: Settle a postdated check for a vendor
description: Settle a postdated check issued to a vendor when the bank has cleared the check transaction after the check has been overdue and cleared by the bank. 
author: kweekley
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
ms.author: kweekley
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Settle a postdated check for a vendor

[!include[task guide banner](../../includes/task-guide-banner.md)]

Settle a postdated check issued to a vendor when the bank has cleared the check transaction after the check has been overdue and cleared by the bank. 

Complete the following procedures before you start this one.

1) Set up postdated checks

2) Register and post a postdated check for a vendor



The role of this procedure is Treasurer. This procedure uses the USMF demo company.

1. Go to Accounts payable > Payments > Vendor postdated checks.
2. Click Settle.
3. Click Settle clearing entries.
    * Settle the vendor account for the check transaction.  
4. Close the page.
5. Go to General ledger > Journal entries > General journals.
6. In the Show field, select 'All'.
7. Select or clear the Show user-created only check box.
8. In the list, mark the selected row.
9. Click Lines.
10. Click Voucher.
11. Close the page.

