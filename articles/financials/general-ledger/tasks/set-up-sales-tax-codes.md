--- 
# required metadata 
 
title: Set up sales tax codes
description: Sales tax codes are created for every indirect tax or duty that the legal entity is obligated to calculate, collect, and pay to sales tax authorities. 
author: twheeloc
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
ms.author: vstehman
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Set up sales tax codes

[!include[task guide banner](../../includes/task-guide-banner.md)]

Sales tax codes are created for every indirect tax or duty that the legal entity is obligated to calculate, collect, and pay to sales tax authorities.

This task uses the USMF demo company.



1. Go to Tax > Indirect taxes > Sales tax > Sales tax codes.
2. Click New.
3. In the Sales tax code field, type a value.
4. In the Name field, type a value.
5. Select a Settlement period to specify which Sales tax authority and in which intervals this sales tax needs to be reported and paid.
6. In the list, click the link in the selected row.
7. Select a Ledger posting group to specify the main accounts to post sales tax to the general ledger.
8. In the list, find and select the desired record.
9. In the list, click the link in the selected row.
10. Expand the Calculation FastTab.
    * The Calculation FastTab has multiple fields that control how sales tax amounts will be calculated.  
11. On the Action Pane, click Sales tax code.
12. Click Values.
13. In the list, mark the selected row.
14. Enter the value for this tax code.
    * On the Calculation FastTab, in the Origin field, if Amount per unit is selected, the value will be multiplied by the quantity on the transaction to calculate the sales tax amount.  If the tax code is not a unit based tax, the value is a percentage that is applied on the Origin for this tax code to calculate the sales tax amount.     
15. Click Save.
16. Close the page.
17. Click Save.

