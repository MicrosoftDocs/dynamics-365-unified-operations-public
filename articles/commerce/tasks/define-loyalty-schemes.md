--- 
# required metadata 
 
title: Define loyalty schemes
description: This procedure walks through how to define a loyalty scheme. 
author: jashanno
ms.date: 11/14/2017
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: josaw
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Retail
ms.author: jashanno
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---

# Define loyalty schemes

[!include [banner](../includes/banner.md)]

This procedure walks through how to define a loyalty scheme. Loyalty schemes are reward earning and redeeming rules for a loyalty program. This procedure uses the USRT demo data company.

1. Go to Retail and Commerce > Customers > Loyalty > Loyalty schemes.
2. Click New.
3. In the Scheme ID field, type a value.
4. In the Description field, type a value.
5. In the Name field, click the drop-down button to open the lookup.
    * You can have multiple loyalty schemes for a loyalty program. Loyalty schemes can be for all channels or only a sub-set of channels.  
6. In the list, find and select the desired record.
7. In the list, click the link in the selected row.
8. Click Save.
9. Click Add line.
10. In the Activity type field, select an option.
    * Select Purchase products by amount if you want customers to earn rewards based on how much they spend. Select Purchase products by quantity if you want customers to earn rewards based on how many products they buy.  Select Sales transaction count if you want customers to earn rewards for each sales transaction, regardless of what or how much is purchased.  
    * Select a category. The category will limit which products this earning rule applies to.  
    * If you want the earning rule to apply to all products, leave this field blank.  
11. In the Activity amount/quantity field, enter a number.
    *  For activity type Sales transaction count, you should always use a value of '1.0'. For activity types of Purchase by amount or Purchase by quantity, any transaction that is less than the value entered will not trigger the earning rule. For example, if the activity type is Purchase by amount, and you enter '10.00', then a sales transaction for '9.00' will not earn rewards for this earning rule.  
12. In the Activity currency field, type a value.
13. In the Reward point ID field, click the drop-down button to open the lookup.
14. In the list, click the link in the selected row.
15. In the Reward points field, enter a number.
    * Amount type reward points will record earned amounts with decimals. For example, if the earning rule states 1 reward point earned for every 1 Canadian Dollar spent, and the customer spends 1.25 Canadian Dollars, then the customer will earn 1.25 reward points. Quantity type reward points will record earned amounts in integers. Using the example where the earning rule states 1 reward point earned for every 1 Canadian Dollar spent, and the customer spends 1.25 Canadian Dollars, then the customer will earn 1.0 reward points.  
16. Click Save.
17. Click Add line.
    * Redemption rules are used when the loyalty payment method is used.  
18. In the Reward point ID field, click the drop-down button to open the lookup.
    * Only redeemable reward points are shown.  
19. In the list, click the link in the selected row.
20. In the Reward points field, enter a number.
21. In the Redemption type field, select an option.
    * Selecting Payment by amount causes the Amount or quantity field to be treated as a currency value. In this case, the amount of reward points used per currency unit of payment is a fixed ratio. Selecting Payment by quantity causes the Amount or quantity field to be treated as a quantity value. In this case, the amount of reward points used per item quantity is a fixed ratio, however, the amount in currency can vary if the price of items paid for with loyalty reward points varies for the same quantity. Redemption type of Loyalty points discount is only valid when the 'Russia' Country/Regional specific features configuration key is enabled, and the POS functionality profiles has an ISO code of 'RU'.  
    * Select a category. The category will limit which products this redemption rule applies to.  
    * If you want the redemption rule to apply to all products, leave this field blank.  
22. In the Amount or quantity field, enter a number.
23. In the Currency field, type a value.
24. Click Save.
25. Click Add line.
    * Select one or more nodes from the Available organization nodes list and move them to the Selected organization nodes list by clicking the arrow between the two lists.  
26. Click OK.
27. Click Save.
    * Anytime you change the channels for a loyalty scheme, you must run Process loyalty schemes. That way, the channels will get updated loyalty schemes.  



[!INCLUDE[footer-include](../../includes/footer-banner.md)]