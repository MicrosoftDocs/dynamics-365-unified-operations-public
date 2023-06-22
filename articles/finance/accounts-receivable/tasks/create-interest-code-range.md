--- 
# required metadata 
 
title: Create an interest code with a range
description: Interest codes can be set up to calculate different interest amounts based on a range of values. 
author: ShivamPandey-msft
ms.date: 03/28/2023
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: Interest, CustInterestRange   
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Create an interest code with a range

[!include [banner](../../includes/banner.md)]
Interest codes can be set up to calculate different interest amounts based on a range of values. This procedure will show you how to add an interest code and add a range to it.

1. Go to **Credit and collections > Interest > Set up interest codes**.
2. Click **New**.
3. In the **Interest code** field, enter the name of the interest code.
4. In the **Description** field, enter a description for the interest code.
5. Select **Month**.
6. Expand the **Earnings** section.
7. Expand the **Earnings by currency** section.
8. In the **Ledger posting account** field, specify the desired values.
9. In the **Interest by range** field, select **Months**.
10. Click **Add**.
11. In the **Description** field, enter a description for this currency and range.
12. Click **Save**.
13. Click **Ranges**.
14. Click **New**.
15. Enter the **From value** as 0 and then enter the interest percent per month that will be used to calculate the interest. For our example, it is 1.5.
16. Click **New**.
17. Enter the next **From value** as 4, which is the first month that you will be calculating a new interest amount.
18. Enter the **Interest percent per month** that will be used to calculate the interest starting in month 4. For this example, it is 2.0.
19. Click **New**.
20. Enter the next **From value** as 7, which is the next month that you will be calculating a new interest amount.
21. Enter the **Interest percent per month** that will be used to calculate the interest starting in month 7. For this example, it is 2.5.
22. Click **Close**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
