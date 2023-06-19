--- 
# required metadata 
 
title: Set up a carrier fuel index
description: This guide shows how to create a fuel index region, a fuel index and a carrier fuel index. 
author: Weijiesa
ms.date: 11/14/2016
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
ms.search.form: TMSFuelIndexRegion,TMSCarrierFuelIndexTable,TMSFuelIndex
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
# Set up a carrier fuel index

[!include [banner](../../includes/banner.md)]

This guide shows how to create a fuel index region, a fuel index and a carrier fuel index. The fuel index region specifies which region the fuel index should apply to, and the fuel index specifies a fuel price for a particular period of time. To reflect the change in fuel prices over time, you can associate multiple fuel indexes with a carrier.  These tasks are normally done by a transportation coordinator. You can use this procedure in demo data company USMF or using your own data.


## Create a fuel index region
1. Go to Transportation management > Setup > Fuel indexes > Fuel index regions.
    * First you have to create the different regions, where you operate and calculate different fuel surcharges.  
2. Click New.
3. In the Region field, type a value.
4. In the Name field, type a value.
5. Click Save.

## Create a fuel index
1. Go to Transportation management > Setup > Fuel indexes > Fuel indexes.
    * For the regions you have set up you need to enter the current prices for the fuel.  
2. Click New.
3. In the Region field, click the drop-down button to open the lookup.
4. In the list, click the link in the selected row.
5. In the Price per gallon field, enter a number.
6. In the Effective start date and time field, enter a date and time.
7. Click Save.

## Create a Carrier fuel index
1. Go to Transportation management > Setup > Fuel indexes > Carrier fuel indexes.
2. Click New.
3. In the Carrier fuel index field, type a value.
4. In the Description field, type a value.
5. Click New.
6. In the Effective start date and time field, enter a date and time.
7. In the PPG From field, enter a number.
    * In this example, you can set PPG From field to 1.95.  
8. In the PPG To field, enter a number.
    * In this example you can set the PPG To field to 2.  
9. In the Percentage field, enter a number.
    * In this example you can set the percentage to 3.  
10. In the Currency field, click the drop-down button to open the lookup.
11. In the list, find and select the desired record.
12. In the list, click the link in the selected row.
13. Click Save.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]