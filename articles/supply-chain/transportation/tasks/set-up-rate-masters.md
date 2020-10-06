--- 
# required metadata 
 
title: Set up rate masters
description: This procedure shows you how to set up a rate master. 
author: ShylaThompson
manager: tfehr 
ms.date: 11/11/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Distribution
ms.author: shylaw
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Set up rate masters

[!include [banner](../../includes/banner.md)]

This procedure shows you how to set up a rate master. The logistic manager usually sets up rate masters, depending on the contracts signed with the carriers. In this scenario you will set up a rate master for an air carrier. The demo data company used to create this procedure is USMF.


## Set up rate master
1. Go to Transportation management > Setup > Rating > Rate master.
2. Click New.
3. In the Rate master field, type a value.
4. In the Name field, type a value.
5. In the Rating metadata ID field, click the drop-down button to open the lookup.
    * The rating metadata ID will determine the data needed for the rate master, as it defines the metadata expected by the TMS engine using this rate master.  
6. For this example, select the P2P option
7. In the list, click the link in the selected row.
8. Click Save.

## Set up rate base
1. Click Rate base.
    * The rate base determines the rate of the carrier, and can be used to set up a tariff structure as it structures the rates in the breakpoints defined in the break master.  
2. Click New.
3. In the Rate base field, type a value.
4. In the Name field, type a value.
5. In the Break master field, click the drop-down button to open the lookup.
    * Break masters are used to define the pricing structure and its breakpoints. The pricing structure uses tiered pricing that is based on physical dimensions.  
6. For this example, use weight
7. In the list, click the link in the selected row.
8. Toggle the expansion of the Details section.
9. Click New.
10. In the Drop-off Postal Code From field, type '30301'.
11. In the Drop-off Postal Code To field, type '30318'.
12. In the Drop-off Country Region field, type 'USA'.
13. In the <1.00 Lbs field, type '100'.
    * Insert the rate per lbs if the total weight of the load is less than 1 pound.  
14. In the <5.00 Lbs field, type '300'.
    * Insert the rate per lbs if the total weight of the load is less than 5 pounds.  
15. In the <20.00 Lbs field, type '500'.
    * Insert the rate per lbs if the total weight of the load is less than 20 pounds.  
16. In the <100.00 Lbs field, type '1000'.
    * Insert the rate per lbs if the total weight of the load is less than 100 pounds.  
17. In the <1,000.00 Lbs field, type '3000'.
    * Insert the rate per lbs if the total weight of the load is less than 1000 pounds.  
18. Click Save.
19. Close the page.

## Assign rate base
1. Toggle the expansion of the Rate base assignments section.
2. Click New.
    * You can have several rate base assignments for each rate master. This makes it possible to create several different price points for each carrier depending on destinations, services, or different rate bases. In this procedure you will only create one rate base assignment.  
3. In the Name field, type a value.
4. In the Rate base field, click the drop-down button to open the lookup.
5. In the list, click the link in the selected row.
6. In the Service field, click the drop-down button to open the lookup.
7. In the list, find and select the desired record.
8. In the list, click the link in the selected row.
9. In the Pick-up Postal Code field, type '98052'.
    * Specify which postal code this rate base assignment should be valid from.    
10. In the Pick-up Country Region field, type 'USA'.
11. Click Save.

