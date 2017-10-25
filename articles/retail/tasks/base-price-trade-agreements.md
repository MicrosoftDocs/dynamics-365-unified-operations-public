--- 
# required metadata 
 
title: Base price and trade agreements
description: This procedure walks through creating channel-specific sales price trade agreements. 
author: josaw1
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
ms.reviewer: josaw
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Base price and trade agreements

[!include[task guide banner](../includes/task-guide-banner.md)]

This procedure walks through creating channel-specific sales price trade agreements. This procedure uses the USRT demo data company.

1. Go to Retail and commerce > Pricing and discounts > Price groups > All price groups.
    * Price groups are how trade agreements are assigned to specific channels. Using price groups to assign trade agreements to a channel enables channel-specific pricing.  
2. Click New.
3. In the Price groups field, type a value.
4. In the Name field, type a value.
5. Click Save.
6. Close the page.
7. Go to Retail and commerce > Channels > Retail stores > All retail stores.
8. In the list, select 'New York'
9. On the Action Pane, click Store.
10. Click Price groups.
11. Click New.
12. In the Price groups field, click the drop-down button to open the lookup.
13. In the list, find and select the desired record.
14. Click Save.
15. Close the page.
16. Close the page.
17. Go to Retail and commerce > Products and categories > Released products by category.
18. In the list, click the link in the selected row.
19. Click Edit.
20. Toggle the expansion of the Sell section.
21. In the Price field, enter a number.
    * This price is used if no applicable trade agreements are found.  
22. Click Save.
23. On the Action Pane, click Sell.
24. Click Create trade agreements.
25. Click New.
26. In the Name field, click the drop-down button to open the lookup.
27. In the list, select 'Retail'.
    * In the demo data, the 'Retail' journal name has the default relation of 'Price (sales)'. That means all new lines created will default to sales price trade agreements.  
28. Click Lines.
29. In the Account code field, select 'Group'.
30. In the Account selection field, click the drop-down button to open the lookup.
31. In the list, find and select the desired record.
    * This will complete the link from Channel to Price group to Trade agreement.  
32. In the Item relation field, type a value.
33. In the Amount in currency field, enter a number.
34. Check or uncheck the Find next checkbox.
    * When Find next is set to 'Yes', the pricing engine will continue to search for applicable trade agreements with a lower sale price. When Find next is set to 'No', the price engine stops searching and uses the trade agreement.  
35. Click Post.
36. Click OK.
37. Close the page.
38. On the Action Pane, click Sell.
39. Click Sales price.

