--- 
# required metadata 
 
title: Define loyalty programs
description: This procedure shows how to set up a loyalty program with two loyalty tiers. 
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
# Define loyalty programs

[!include [banner](../includes/banner.md)]

This procedure shows how to set up a loyalty program with two loyalty tiers. This procedure uses the USRT demo data company.

1. Go to Retail and Commerce > .. > Loyalty programs.
2. Click New.
3. In the Name field, type a value.
4. In the Description field, type a value.
5. Click Add line.
6. In the Level field, enter a number.
7. In the Tier field, enter a name for the loyalty tier.
8. In the Description field, type a value.
9. In the Date interval field, click the drop-down button to open the lookup.
    * This date interval should extend into the future. For example, if the date interval that is selected for gold tier is a one-year period, any customer who qualifies for the gold tier can receive the rewards that are assigned to the gold tier for one year. If the customer re-qualifies for the gold tier while they are in the tier, the date that the tier expires is extended by another year from the date when they re-qualify.  
10. In the list, click the link in the selected row.
11. Click Add line.
12. In the Level field, enter a number.
13. In the Tier field, enter a name for the loyalty tier.
14. In the Description field, type a value.
15. In the Date interval field, click the drop-down button to open the lookup.
16. In the list, click the link in the selected row.
17. Click Save.
18. In the list, find and select the desired record.
    * Tier rules define the minimum number of a reward point needed to be earned during a time period to qualify for the tier.  
19. Toggle the expansion of the Tier rules section.
20. Click New.
    * You can have more than one tier rule per tier. For example, you could have three different criteria to earn a tier; by spending $500 in one month, by spending $1000 over one year, and by having 20 transactions in one year. To do this, you would need to create three tier rules.  
21. In the Reward point field, click the drop-down button to open the lookup.
    * This should be a non-redeemable loyalty reward point.  
22. In the list, click the link in the selected row.
23. In the Minimum issued points field, enter a number.
    * For the lowest level tier, if all customers qualify simply by participating in the program, enter '0'.  
24. In the Evaluation date interval field, click the drop-down button to open the lookup.
    * This date interval should extend into the past. Only points earned during this date interval will be counted towards reaching the minimum issued points value.  
25. In the list, click the link in the selected row.
26. Click Save.
27. In the list, find and select the desired record.
28. Click New.
29. In the Reward point field, click the drop-down button to open the lookup.
30. In the list, click the link in the selected row.
31. In the Minimum issued points field, enter a number.
32. In the Evaluation date interval field, click the drop-down button to open the lookup.
    * This date interval should extend into the past.  
33. In the list, click the link in the selected row.
34. Click Save.
35. Click Price groups.
    * If you want to give loyalty customers discounts. you'll need to assign one or more price groups to the loyalty program and assign the price groups to discounts. It is a best practice to not mix price groups across different types of discounting entities.  For example, don't use the same price group for a loyalty discount and a channel discount.  
36. In the Price group field, click the drop-down button to open the lookup.
    * The Price groups link at the top of the page is for the loyalty program. The Price groups link in the Program tiers FastTab is for a specific loyalty tier only.  
37. In the list, click the link in the selected row.
38. Click Save.
39. Close the page.
40. Click Save.



[!INCLUDE[footer-include](../../includes/footer-banner.md)]