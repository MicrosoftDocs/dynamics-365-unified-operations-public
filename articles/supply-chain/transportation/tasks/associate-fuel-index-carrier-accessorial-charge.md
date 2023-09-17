--- 
# required metadata 
 
title: Associate a fuel index with a carrier as an accessorial charge
description: This guide shows how to create an accessorial assignment, carrier accessorial charge, accessorial master for fuel surcharge, and associate a carrier fuel index with a carrier. 
author: Weijiesa
ms.date: 11/14/2016
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: TMSRatingProfile
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
# Associate a fuel index with a carrier as an accessorial charge

[!include [banner](../../includes/banner.md)]

This guide shows how to create an accessorial assignment, carrier accessorial charge, accessorial master for fuel surcharge, and associate a carrier fuel index with a carrier. You need to have set up a carrier fuel index before you run this guide. You can use the "Set up a carrier fuel index" guide to do this. These setup tasks are typically done by a Logistics manager. The demo data used to create this procedure is USMF.


## Create an accessorial master
1. Go to Transportation management > Setup > Rating > Accessorial masters.
2. Click New.
3. In the Accessorial master field, type a value.
4. In the Name field, type a value.
5. Click Save.

## Create a carrier accessorial charge
1. Go to Transportation management > Setup > Rating > Carrier accessorial charges.
2. Click New.
3. In the Carrier accessorial ID field, type a value.
4. In the Shipping carrier field, click the drop-down button to open the lookup.
5. In the list, find and select the desired record.
    * In this example, choose Truck Carrier.  
6. In the list, click the link in the selected row.
7. In the Carrier service field, click the drop-down button to open the lookup.
8. In the list, click the link in the selected row.
9. In the Accessorial master field, click the drop-down button to open the lookup.
10. In the list, find and select the desired record.
    * In this example, choose the newly created Accessorial master.  
11. Click Save.

## Create an accessorial assignment
1. Click Accessorial assignments.
2. Click New.
3. In the Name field, type a value.
4. Toggle the expansion of the Criteria section.
    * In the criteria, you can choose to always apply the fuel surcharge or for this example choose that it only applies within a certain region.  
5. In the ZIP/postal code from field, type a value.
6. In the ZIP/postal code to field, type a value.
7. Toggle the expansion of the Calculation section.
    * In the calculation section you can specify how to calculate the fuel surcharge. This calculation depends on the Accessorial unit that you chose as the base for your calculation.  
8. In the Accessorial fee type field, select 'Fuel surcharge'.
9. In the Accessorial unit field, select 'Mileage'.
10. In the Region field, click the drop-down button to open the lookup.
11. In the list, click the link in the selected row.
12. Click Save.

## Update the carrier rating profile
1. Go to Transportation management > Setup > Carriers > Shipping carriers.
2. In the list, find and select the desired record.
3. Toggle the expansion of the Rating profiles section.
4. Click Edit.
5. In the Carrier fuel index field, click the drop-down button to open the lookup.
6. In the list, click the link in the selected row.
7. Click Save.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]