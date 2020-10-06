--- 
# required metadata 
 
title: Configure intercompany project invoicing
description: This topic shows how to set up project invoicing between two companies in your organization. 
author: KimANelson
manager: AnnBe 
ms.date: 07/29/2019
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: VendTable, InterCompanyTradingRelationSetupVendor, SysDataAreaSelectLookup, ProjParameters, ProjPosting, ProjTransferPrice   
audience: Application User 
# ms.devlang:  
ms.reviewer: josaw
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Service industries
ms.author: knelson
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Configure intercompany project invoicing

[!include [banner](../../includes/banner.md)]

This topic shows how to set up project invoicing between two companies in your organization. This task uses the USSI data set.

1. In the navigation pane, go to **Modules > Accounts payable > Vendors > All vendors**.
2. In the **All vendors** list, find and select the desired record.
3. On the Action Pane, select **General**.
4. Select **Intercompany**.
5. Set **Active** to **Yes** to enable intercompany trading.
6. In the **Customer company** field, enter or select a value.
7. In the **My account** field, enter or select a value.
8. Select **Save**.
9. Close the pages to return to the home page.
10. In the navigation pane, go to **Modules > Project management and accounting > Setup > Project management and accounting parameters**.
11. Select the **Intercompany** tab.
12. Move the slider to **Yes** to enable intercompany resource scheduling and timesheets.
13. In the list, mark the selected row.
14. Select **New**.
15. In the **Borrowing legal entity** field, enter or select a value.
16. Select the **Accrue revenue** check box.
17. In the **Default timesheet category** field, enter or select a value.
18. In the **Default expense category** field, enter or select a value.
19. Select **Save**.
20. Close the page.
21. In the navigation pane, go to **Modules > Project management and accounting > Setup > Posting > Ledger posting setup**.
22. In the **Ledger account types** field, select an option.
23. Select **New**.
24. In the **Main account** field of the new row, specify the desired values.
25. Select **Save**.
26. Close the page.
27. In the navigation pane, go to **Modules > Project management and accounting > Setup > Prices > Transfer price**.
28. Select **New**.
29. In the **Effective date** field, enter a date.
30. In the **Borrowing legal entity** field, enter or select a value.
31. In the **Transfer price model** field, select an option.
32. In the **Pricing** field, enter a number.
33. Select **Save**.

