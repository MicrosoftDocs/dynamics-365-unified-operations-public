--- 
# required metadata 
 
title: Create a new trade agreement
description: This procedure shows you how to create a trade agreement where you register a new product sales price that you've agreed with a specific customer. 
author: omulvad
manager: AnnBe 
ms.date: 11/11/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: omulvad
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Create a new trade agreement

[!include[task guide banner](../../includes/task-guide-banner.md)]

This procedure shows you how to create a trade agreement where you register a new product sales price that you've agreed with a specific customer. You can run this procedure in demo data company USMF or on your own data. If you’re using your own data, before you start this guide you need to make sure that a Trade agreement journal name exists where the Default relation is set to “Price (sales)”.


## Create and post a new trade agreement journal
1. Go to Sales and marketing > Prices and discounts > Trade agreement journals.
2. Click New.
3. In the Name field, click the drop-down button to open the lookup.
4. In the list, find and select the desired record.
5. In the list, click the link in the selected row.
6. Click Lines.
7. In the Account code field, select 'Table'.
    * In this example, you're updating the price for a specific customer, which means you need to choose Table. If you were updating the product's list price, you would select All, so that the new price is valid for all customers. If you were differentiating prices among different customer segments, then you would select Group. To select Group, you must have set up Customer price groups.  
8. In the Account selection field, click the drop-down button to open the lookup.
9. In the list, find and select the desired record.
10. In the Item code field, select 'Table'.
    * When you are entering a trade agreement of type 'Price (sales)', you must only select 'Table' in the Item code field. This is because a price is an absolute value and cannot be same for all products or a group of products.  
11. In the Item relation field, click the drop-down button to open the lookup.
12. In the list, select the product you want to include in the agreement.
    * Make a note of which product you've selected.  
13. In the list, click the link in the selected row.
14. In the From field, enter a minimum quantity.
    * If the customer has to order a minimum quantity  before they can qualify for the new price, then you need to specify that quantity here.  
    * Enter a value in the To field to specify the maximum quantity above which the agreement's price will not be valid. If you offer prices and discounts based on multiple quantity breaks, then specify each quantity bracket as a pair of minimum and maximum quantity in the 'From' and 'To' fields respectively.  
15. In the Amount in currency field, enter a price.
16. In the From date field, enter a date from which this agreement will be valid.
17. Click Save.
18. Click Validate.
19. Click Validate selected lines.
20. Click OK.
21. Click Post.
22. Click OK.

## View trade agreements for a product
1. Go to Product information management > Products > Released products.
2. In the list, find and select the product whose price you have just updated.
3. On the Action Pane, click Sell.
4. Click View trade agreements.
    * Review the details of the price trade agreement you have just created.    
5. Close the page.

