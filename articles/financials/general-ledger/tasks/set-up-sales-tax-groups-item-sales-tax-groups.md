--- 
# required metadata 
 
title: Set up sales tax groups and item sales tax groups
description: This task recording walks you through the setup of Sales tax and Item sales tax groups. 
author: twheeloc
manager: AnnBe 
ms.date: 11/10/2015
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
ms.author: vstehman
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Set up sales tax groups and item sales tax groups

[!include[task guide banner](../../includes/task-guide-banner.md)]

This task recording walks you through the setup of Sales tax and Item sales tax groups. Sales tax groups are groups of sales tax codes that are attached to customers and vendors. They are also attached to ledger accounts for transactions that are not posted to a particular vendor or customer.  Item sales tax groups are groups of sales tax codes that are attached to resources like products.  The sales taxes that apply to a particular transaction are determined by the sales tax codes that are included both in the sales tax group and in the item sales tax group of the transaction.  Sales tax can be calculated only if a sales tax group and an item sales tax group are selected for each transaction for which sales tax must be calculated or recorded.  

1. Go to Tax > Indirect taxes > Sales tax > Sales tax groups.
2. Click New.
3. In the Sales tax group field, type a value.
4. In the Description field, type a value.
5. Toggle the expansion of the Setup section.
6. Click Add.
7. In the list, mark the selected row.
8. In the Sales tax code field, click the drop-down button to open the lookup.
9. In the list, click the link in the selected row.
10. Click Save.
11. Close the page.
12. Go to Tax > Indirect taxes > Sales tax > Item sales tax groups.
13. Click New.
14. In the Item sales tax group field, type a value.
15. In the Description field, type a value.
16. Click Add.
17. In the list, mark the selected row.
18. In the Sales tax code field, click the drop-down button to open the lookup.
19. In the list, click the link in the selected row.
20. Click Save.

