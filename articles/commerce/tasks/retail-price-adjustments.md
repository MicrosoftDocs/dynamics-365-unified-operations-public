--- 
# required metadata 
 
title: Retail price adjustments
description: This procedure will walk through creating a commerce price adjustment. 
author: josaw1
ms.date: 08/29/2018
ms.topic: business-process 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: DefaultDashboard, RetailDiscountPricingWorkspace, RetailPeriodicDiscount, RetailDiscountPriceGroup   
audience: Application User 
# ms.devlang:  
ms.reviewer: josaw
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Retail price adjustments

[!include [banner](../includes/banner.md)]

This procedure will walk through creating a commerce price adjustment. A price adjustment can set an item's sale price directly, or modify its base sale price or trade agreement sale price. This procedure uses the USRT demo data company.

1. Click Pricing and discount management.
2. Click the Price adjustments tab.
3. Click New.
    * From here you can create all of the most commonly used price and discount rules, including discounts, price adjustments, trade agreement journals, and category pricing rules.  
4. Click Price adjustment.
5. In the Name field, type a value.
6. Expand the Lines section.
7. Click Add.
    * For this example, enter '81126' in the Product field. Then, enter '10.0' in the Discount percentage field.  
    * A discount percentage type price adjustment will reduce a base sales price or trade agreement sales price.  
8. Click Add.
    * For this example, enter '81125' in the Product field. Then, select 'Cash discount amount' in the Discount method field.    Finally, enter '5.0' in the Cash discount amount field.  
    * A Cash discount amount discount type is an amount taken off from a base price or a trade agreement price.  
9. Click Price groups.
    * Select 'RP-Houston' in the Price group field.  
    * This will associate the Price adjustment to the Houston store.  
10. Click Save.
11. Close the page.
12. In the Status field, select 'Enabled'.
13. Click Save.
14. Close the page.
15. Refresh the page.



[!INCLUDE[footer-include](../../includes/footer-banner.md)]