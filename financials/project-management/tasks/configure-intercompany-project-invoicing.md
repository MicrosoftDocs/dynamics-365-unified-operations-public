--- 
# required metadata 
 
title: Configure intercompany project invoicing
description: This procedure shows how to set up project invoicing between two companies in your organization. 
author: KimANelson
manager: AnnBe 
ms.date: 02/13/2017
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
ms.search.industry: Service industries
ms.author: knelson
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Configure intercompany project invoicing

[!include[task guide banner](../../includes/task-guide-banner.md)]

This procedure shows how to set up project invoicing between two companies in your organization. This task uses the USSI data set.

1. Go to Accounts payable > Vendors > All vendors.
2. In the list, find and select the desired record.
3. On the Action Pane, click General.
4. Click Intercompany.
5. Set Active to Yes to enable intercompany trading.
6. In the Customer company field, enter or select a value.
7. In the My account field, enter or select a value.
8. Click Save.
9. Close the page.
10. Close the page.
11. Go to Project management and accounting > Setup > Project management and accounting parameters.
12. Click the Intercompany tab.
13. Move the slider to Yes to enable intercompany resource scheduling and timesheets.
14. In the list, mark the selected row.
15. Click New.
16. In the list, mark the selected row.
17. In the Borrowing legal entity field, enter or select a value.
18. Select the Accrue revenue check box.
19. In the Default timesheet category field, enter or select a value.
20. In the Default expense category field, enter or select a value.
21. Click Save.
22. Close the page.
23. Go to Project management and accounting > Setup > Posting > Ledger posting setup.
24. In the Ledger account types field, select an option.
25. Click New.
26. In the list, mark the selected row.
27. In the list, mark the selected row.
28. In the Main account field, specify the desired values.
29. Click Save.
30. Close the page.
31. Go to Project management and accounting > Setup > Prices > Transfer price.
32. Click New.
33. In the Effective date field, enter a date.
34. In the Borrowing legal entity field, enter or select a value.
35. In the Transfer price model field, select an option.
36. In the Pricing field, enter a number.
37. Click Save.

