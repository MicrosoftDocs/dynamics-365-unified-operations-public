--- 
# required metadata 
 
title: Create and acquire assets from accounts payable
description: This task guide will walk through creation and acquisition of a fixed asset with the purchasing process. 
author: saraschi2
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
# Create and acquire assets from accounts payable

[!include[task guide banner](../../includes/task-guide-banner.md)]

This task guide will walk through creation and acquisition of a fixed asset with the purchasing process. It uses the Accountant and Accounts payable clerks and the demo company USMF.


## Set Fixed assets parameters
1. Go to Fixed assets > Setup > Fixed assets parameters.
2. Expand or collapse the Purchase orders section.
3. Check the Allow asset acquisition from Purchasing checkbox.
4. Check the Create asset during product receipt or invoice posting checkbox.

## Create a new vendor invoice
1. Go to Accounts payable > Workspaces > Vendor invoice entry.
2. Click New vendor invoice.
3. In the Invoice account field, click the drop-down button to open the lookup.
4. In the list, click the link in the selected row.
5. In the Number field, type a value.
6. In the Posting date field, enter a date.
7. Click Add line.
8. In the Item number field, click the drop-down button to open the lookup.
    * Either non-stocked items or procurement categories can be used for fixed asset acquisition.  
9. In the list, click the link in the selected row.
10. In the Quantity field, enter a number.
    * One invoice line will only create one fixed asset, regardless of quantity.  The invoice quantity field value will be transferred to the fixed asset quantity.  
11. In the Unit price field, enter a number.
12. Expand or collapse the Line details section.
13. Click the Fixed assets tab.
14. Check the Create a new fixed asset checkbox.
15. In the Fixed asset group field, click the drop-down button to open the lookup.
16. In the list, select the fixed asset group to be used when creating the new fixed asset.
17. In the list, click the link in the selected row.
18. Click Post.
    * The fixed asset will be created and acquired when the invoice is posted.  

