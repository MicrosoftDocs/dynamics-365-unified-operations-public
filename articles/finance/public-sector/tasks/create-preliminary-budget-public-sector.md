--- 
# required metadata 
 
title: Create a preliminary budget for Public sector
description: You can create preliminary budget register entries for a specific budget model and dimension values. 
author: twheeloc
ms.date: 02/14/2022
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: BudgetTransaction, BudgetAccountStructureLookup, BudgetTransactionMultiPost   
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Service industries
ms.author: twheeloc
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Create a preliminary budget for Public sector

[!include [banner](../../includes/banner.md)]

You can create preliminary budget register entries for a specific budget model and dimension values. After the actual budget is approved, you can create original budget register entries. This procedure was created using the PSUS demo company data in the public sector partition.

1. Go to **Budgeting > Budget register entries**.
2. Click **New**.
3. In the **Budget model** field, click the drop-down button to open the lookup.
4. In the list, find and select the desired record.
5. In the **Budget code** field, click the drop-down button to open the lookup.
6. In the list, find and select the desired record.
7. In the **Reason code** field, click the drop-down button to open the lookup.
8. In the list, click the desired record.
9. Click **Save**.
10. Click **Add line**.
    * Optional: If you want to change the date from the one in the header, enter a new date. This date determines the fiscal period that the budget will be recorded to. When viewing the task guide, to fill out other fields, click **Unlock** at the top of the page.  
11. In the **Account structure** field, click the drop-down button to open the lookup.
12. In the list, find and select the desired record.
13. In the **Dimension values** field, specify the desired values.
14. In the **Amount** field, enter a number.
    * You can also enter an amount type.  
15. In the **Currency** field, click the drop-down button to open the lookup.
16. In the list, find and select the desired record.
17. Click **Save**.
18. Click **Update budget balances**.
19. Click **Update**.
    * To see the results of the update, click **Message details** on the blue bar.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
