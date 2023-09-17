--- 
# required metadata 
 
title: Create an original budget and then reverse preliminary budget entries in the public sector
description: This article provides information about how to create and reverse an original budget entry using budget model and dimension values that have preliminary budget amounts. 
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
# Create an original budget and then reverse preliminary budget entries in the public sector

[!include [banner](../../includes/banner.md)]

When you create an original budget entry and use the budget model and dimension values that contain preliminary budget amounts, the preliminary budget amounts can be reversed. This procedure was created using the PSUS demo company data in the public sector partition.

1. Go to **Budgeting > Budget register entries**.
2. Click **New**.
3. In the **Budget model** field, click the drop-down button to open the lookup.
4. In the list, find and select the desired record.
5. In the **Budget code** field, click the drop-down button to open the lookup.
6. In the list, click **Original budget**.
7. Click **Save**.
8. Click **Add line**.
9. Optional: If you want to change the date from the one in the header, enter a new date. This date determines the fiscal period that the budget will be recorded to.
10. In the **Account structure** field, click the drop-down button to open the lookup.
11. In the list, find and select the desired record.
12. In the **Dimension values** field, specify the desired values.
13. In the **Amount** field, enter a number.
14. In the **Currency** field, click the drop-down button to open the lookup.
15. In the list, click the link in the selected row.
16. Click **Save**.
17. Click **Update budget balances**.
    * Optional: You can select the **Reverse preliminary budget** option. Note that you can reverse all preliminary budget entries, or only the preliminary budget entries that have the budget code that you specify.  
    * To make optional selections, click the **Unlock** icon at the top of the page.  
18. Click **Update**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
