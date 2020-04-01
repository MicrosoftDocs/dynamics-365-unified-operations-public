--- 
# required metadata 
 
title: Set up shipping carriers
description: This topic shows how to set up a shipping carrier and define details such as service, shipment mode, transportation tender, transportation constraints, and shipping rate. 
author: ShylaThompson
manager: AnnBe 
ms.date: 07/19/2019
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: josaw
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Distribution
ms.author: shylaw
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Set up shipping carriers

[!include [banner](../../includes/banner.md)]

This topic shows how to set up a shipping carrier and define details such as service, shipment mode, transportation tender, transportation constraints, and shipping rate. A transportation coordinator can then assign a shipping carrier to an inbound or outbound load.


## Create a new shipping carrier
1. Go to **Navigation pane > Modules > Transportation management > Setup > Carriers > Shipping carriers**.
2. Select **New** in the Action pane.
3. In the **Shipping carrier** field, type a value.
4. In the **Name** field, type a value.
5. In the **Mode** field, select an option from the drop-down menu.

## Fill in the general information for the shipping carrier
1. Toggle the expansion of the **Overview** section.
2. Check or uncheck the **Activate shipping carrier** checkbox.
3. In the **Vendor account** field, select an option from the drop-down menu. Select the vendor account to assign the shipping carrier to.  
4. In the **Transportation tender type** field, select an option. Select **Manual** to use the Transportation Tender page, or select **EDI** to update the tender by using Electronic Data Interchange (EDI).  
5. Check or uncheck the **Activate carrier rating** checkbox.

## Create the necessary services for the shipping carrier
1. Toggle the expansion of the **Services** section.
2. Select **New**.
3. In the **Carrier service** field, type a value.
4. In the **Name** field, type a value.
5. In the **Transportation method** field, select an option from the drop-down menu.

## Set up the address for the carrier (optional)
1. Toggle the expansion of the **Addresses** section.
2. Select **New**.
3. In the **Name or description** field, type a value.
4. In the **Country/region** field, select an option from the drop-down menu.
5. In the **ZIP/postal code** field, select an option from the drop-down menu.
6. In the **Street** field, type a value.
7. Select **OK**.

## Set up the rating profile for the shipping carrier
1. Toggle the expansion of the **Rating profiles** section.
2. Select **New**.
3. In the **Rating profile** field, type a value.
4. In the **Name** field, type a value.
5. In the **Site** field, select an option from the drop-down menu.
6. In the **Warehouse** field, select an option from the drop-down menu.
7. In the **Rate engine** field, select an option from the drop-down menu. Select the Rate engine that is in accordance with the contract that you have with the carrier.  
8. In the **Rate master** field, select an option from the drop-down menu.
9. In the **Transit time engine** field, select an option from the drop-down menu.
10. Select **Save**.

