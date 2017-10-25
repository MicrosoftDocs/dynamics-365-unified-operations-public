--- 
# required metadata 
 
title: Set up shipping carriers
description: This procedure shows how to set up a shipping carrier and define details such as service, shipment mode, transportation tender, transportation constraints, and shipping rate. 
author: BibiSp
manager: AnnBe 
ms.date: 11/14/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: bis
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Distribution
ms.author: bis
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Set up shipping carriers

[!include[task guide banner](../../includes/task-guide-banner.md)]

This procedure shows how to set up a shipping carrier and define details such as service, shipment mode, transportation tender, transportation constraints, and shipping rate. A transportation coordinator can then assign a shipping carrier to an inbound or outbound load.


## Create a new shipping carrier
1. Go to Transportation management > Setup > Carriers > Shipping carriers.
2. Click New.
3. In the Shipping carrier field, type a value.
4. In the Name field, type a value.
5. In the Mode field, click the drop-down button to open the lookup.
6. In the list, find and select the desired record.
7. In the list, click the link in the selected row.

## Fill in the general information for the shipping carrier
1. Toggle the expansion of the Overview section.
2. Check or uncheck the Activate shipping carrier checkbox.
3. In the Vendor field, click the drop-down button to open the lookup.
    * Select the vendor account to assign the shipping carrier to.  
4. In the list, find and select the desired record.
5. In the list, click the link in the selected row.
6. In the Transportation tender type field, select an option.
    * Select Manual to use the Transportation Tender page, or select EDI to update the tender by using Electronic Data Interchange (EDI).  
7. Check or uncheck the Activate carrier rating checkbox.

## Create the necessary services for the shipping carrier
1. Toggle the expansion of the Services section.
2. Click New.
3. In the list, mark the selected row.
4. In the Carrier service field, type a value.
5. In the Name field, type a value.
6. In the Transportation method field, click the drop-down button to open the lookup.
7. In the list, find and select the desired record.
8. In the list, click the link in the selected row.

## Set up the address for the carrier (optional)
1. Toggle the expansion of the Addresses section.
2. Click New.
3. In the Name or description field, type a value.
4. In the Country/region field, click the drop-down button to open the lookup.
5. In the list, click the link in the selected row.
6. In the ZIP/postal code field, click the drop-down button to open the lookup.
7. In the list, find and select the desired record.
8. In the list, click the link in the selected row.
9. In the Street field, type a value.
10. Click OK.

## Set up the rating profile for the shipping carrier
1. Toggle the expansion of the Rating profiles section.
2. Click New.
3. In the list, mark the selected row.
4. In the Rating profile field, type a value.
5. In the Name field, type a value.
6. In the Site field, click the drop-down button to open the lookup.
7. In the list, find and select the desired record.
8. In the list, click the link in the selected row.
9. In the Warehouse field, click the drop-down button to open the lookup.
10. In the list, find and select the desired record.
11. In the list, click the link in the selected row.
12. In the Rate engine field, click the drop-down button to open the lookup.
    * Select the Rate engine that is in accordance with the contract that you have with the carrier.  
13. In the list, find and select the desired record.
14. In the list, click the link in the selected row.
15. In the Rate master field, click the drop-down button to open the lookup.
16. In the list, find and select the desired record.
17. In the list, click the link in the selected row.
18. In the Transit time engine field, click the drop-down button to open the lookup.
19. In the list, click the link in the selected row.
20. Click Save.

