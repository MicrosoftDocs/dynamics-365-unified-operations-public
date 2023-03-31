--- 
# required metadata 
 
title: Set up an item arrival overview profile
description: This article focuses on the setup of an arrival overview profile. 
author: yufeihuang
ms.date: 07/30/2019
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: WMSArrivalOverviewProfile   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
ms.custom: "intro-internal"
ms.search.region: Global
ms.search.industry: Distribution
ms.author: yufeihuang
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Set up an item arrival overview profile

[!include [banner](../../includes/banner.md)]

This article focuses on the setup of an arrival overview profile. The arrival overview profile is a collection of rules that will be applied when the Arrival overview page is opened by a user. You can use this procedure in demo data company USMF. This procedure would typically be carried out by a receiving clerk.

1. Go to **Inventory management > Setup > Distribution > Arrival overview profiles**.
2. Select **New**. Because you will almost always work in the same warehouse offloading full truck loads, you should create an arrival overview profile to simplify the process of registering received items.  
3. In the **Arrival overview profile name** field, type a value.
4. In the **Show lines** field, select an option. Select which lines to show for the receipts:  

    - **All** – Show all lines, regardless of status.   
    - **In progress** – Show lines for receipts in which the progress is Complete or Partly. This means that for each line, either the full quantity or part of the quantity has been registered in an arrival journal.   
    - **Not complete** – Show lines for receipts in which the progress is None or Partly. This means that for each line, nothing or only part of the quantity has been registered in an arrival journal.  

5. Expand or collapse the **Arrival options** section.
6. In the **Days forward** field, type a value. This sets a filter to show the receipt lines expected to be received within the next few days (depending on the number you set).  
7. In the **Days back** field, type a value. This sets a filter to show the receipt lines expected to be received a number of days before today.  
8. In the **Warehouses** field, type a value. Filter on one or more warehouses.  
9. In the **Mode of delivery** field, select a value. This sets a filter to show only the receipt lines with this Mode of delivery.  
10. In the **Name** field, select WHS.
11. In the **Warehouse** field, select warehouse 24. This is the default warehouse that will be used for registered receipt lines that use this profile.  
12. In the **Location** field, select **Baydoor**. This is the default location that will be used for registered receipt lines that use this profile.  
13. Expand or collapse the **Arrival query details** section.
14. In the **Restrict to site** field, select site 2. This sets a filter to show only the receipt lines with this site.  
15. Set the **Purchase orders** option to **Yes**. Select receipt lines from purchase orders.  
16. Set the **Transfer** orders option to **Yes**. Select receipt lines from transfer orders.  
17. Select **Save**.
18. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
