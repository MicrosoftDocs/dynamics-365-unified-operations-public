--- 
# required metadata 
 
title: Initialize stock levels in the warehouse
description: This procedure shows you how to get the on-hand inventory updated manually using an Inventory movement journal. 
author: yufeihuang
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: InventJournalMovement, InventJournalCreate, InventItemIdLookupSimple, InventLocationIdLookup, WMSLocationIdLookup   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Distribution
ms.author: yufeihuang
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Initialize stock levels in the warehouse

[!include [banner](../../includes/banner.md)]

This procedure shows you how to get the on-hand inventory updated manually using an Inventory movement journal. (It's also possible to update on-hand inventory by importing transactions in data entities.) You can run this guide in demo data company USMF where all the prerequisites like journal name, item setup, posting profiles, and accounts are available. The guide suggests specific values for the item and dimensions that are used. If you choose a different item, you may need to enter values for different dimensions.

1. Go to Inventory management > Journal entries > Items > Movement.
2. Click New.
3. In the Name field, click the drop-down button to open the lookup.
4. Select IMov.
    * It's a good practice to use different journal name templates for the different business purposes.  
5. In the list, click the link in the selected row.
6. In the Offset account field, specify the values '140200'.
    * This is the offset account that will be the default account on the journal lines. It's possible to override the default to assign different offset accounts per line.  
7. Click OK.
8. Click New.
9. In the Item number field, click the drop-down button to open the lookup.
10. Select item A0001.
11. In the list, click the link in the selected row.
12. Click the Inventory dimensions tab.
13. In the Site field, click the drop-down button to open the lookup.
14. Select site 1.
15. In the Warehouse field, click the drop-down button to open the lookup.
16. Select warehouse 13.
17. In the list, click the link in the selected row.
18. In the Location field, click the drop-down button to open the lookup.
19. Select location 13.
20. In the Quantity field, enter a number.
21. Click Save.
22. Click Post.
23. Check or uncheck the Transfer all posting errors to a new journal check box.
    * If you enable this option, any lines that fail to post will be copied to a new journal. You can use the information in the log to correct the issues and then re-post the lines.  
24. Click OK.
25. Close the page.
26. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]