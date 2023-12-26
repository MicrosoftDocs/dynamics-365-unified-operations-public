--- 
# required metadata 
 
title: Set up rate masters
description: This procedure shows you how to set up a rate master. 
author: Weijiesa
ms.date: 10/16/2020
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
ms.search.form: TMSBreakMaster,TMSRateMaster,TMSRateMasterBase,TMSRateBaseType, TMSRouteWorkbench
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Distribution
ms.author: weijiesa
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Set up rate masters

[!include [banner](../../includes/banner.md)]

This procedure shows you how to set up a rate master. The logistic manager usually sets up rate masters, depending on the contracts signed with the carriers. In this scenario you will set up a rate master for an air carrier. The demo data company used to create this procedure is USMF.

## Set up break master

1. Go to **Transportation management > Setup > Rating > Break master**. Break masters are used to define the pricing structure and its breakpoints. The pricing structure uses tiered pricing that is based on physical dimensions.  
1. Select **New**.
1. In the **Break master** field, enter a value.
1. In the **Name** field, enter a value.
1. In the **Data type** field, select the data type.
1. In the **Comparison** field, enter the kind of comparison requested (using operators).
1. In the **Break unit** field, enter the break unit.
1. In the **Details** section, create as many breaks as needed for the pricing structure.
1. Select **Save**.

## Set up rate master

1. Go to **Transportation management > Setup > Rating > Rate master**.
1. Select **New**.
1. In the **Rate master** field, type a value.
1. In the **Name** field, type a value.
1. In the **Rating metadata ID** field, select the drop-down button to open the lookup. The rating metadata ID will determine the data needed for the rate master, as it defines the metadata expected by the transportation management engine using this rate master.  
1. For this example, select the P2P option. This is already defined in the demo data.
1. In the list, select the link in the selected row.
1. Select **Save**.

## Set up rate base

1. Select **Rate base**.
    * The rate base determines the rate of the carrier, and can be used to set up a tariff structure as it structures the rates in the breakpoints defined in the break master.  
2. Select **New**.
3. In the **Rate base** field, type a value.
4. In the **Name** field, type a value.
5. In the **Break master** field, select the drop-down button to open the lookup.
    * Break masters are used to define the pricing structure and its breakpoints. The pricing structure uses tiered pricing that is based on physical dimensions.  
6. For this example, use weight. This is already defined in the demo data.
7. In the list, select the link in the highlighted row.
8. Expand the **Details** section.
9. Select **New**.
10. In the **Drop-off Postal Code From** field, type "30301".
11. In the **Drop-off Postal Code To** field, type "30318".
12. In the **Drop-off Country Region** field, type "USA".
13. In the **<1.00 Lbs** field, type "100".
    * Insert the rate per pounds if the total weight of the load is less than 1 pound.  
14. In the **<5.00 Lbs** field, type "300".
    * Insert the rate per pounds if the total weight of the load is less than 5 pounds.  
15. In the **<20.00 Lbs** field, type "500".
    * Insert the rate per pounds if the total weight of the load is less than 20 pounds.  
16. In the **<100.00 Lbs** field, type "1000".
    * Insert the rate per pounds if the total weight of the load is less than 100 pounds.  
17. In the **<1,000.00 Lbs** field, type "3000".
    * Insert the rate per pounds if the total weight of the load is less than 1000 pounds.  
18. Select **Save**.
19. Close the page.

## Assign rate base

1. Expand the **Rate base assignments** section.
2. Select **New**.
    * You can have several rate base assignments for each rate master. This makes it possible to create several different price points for each carrier depending on destinations, services, or different rate bases. In this procedure you will only create one rate base assignment.  
3. In the **Name** field, type a value.
4. In the **Rate base** field, select the drop-down button to open the lookup.
5. In the list, select the link in the highlighted row.
6. In the **Service** field, select the drop-down button to open the lookup.
7. In the list, find and select the desired record.
8. In the list, select the link in the highlighted row.
9. In the **Pick-up Postal Code** field, type "98052".
    * Specify which postal code this rate base assignment should be valid from.
10. In the **Pick-up Country Region** field, type "USA".
11. Select **Save**.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]