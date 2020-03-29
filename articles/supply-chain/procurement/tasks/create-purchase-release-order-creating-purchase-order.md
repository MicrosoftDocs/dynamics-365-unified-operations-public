--- 
# required metadata 
 
title: Create a purchase release order when creating the purchase order
description: This procedure shows how to use a purchase agreement when you create a purchase order. 
author: mkirknel
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
ms.reviewer: josaw
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: mkirknel
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Create a purchase release order when creating the purchase order

[!include [banner](../../includes/banner.md)]

This procedure shows how to use a purchase agreement when you create a purchase order. The purchase agreement has to be applied when you create the purchase order because there are general terms that should be copied to the purchase order header. Typically this task would be carried out by a purchasing agent. As a prerequisite for this guide, you must have an effective purchase agreement with a product quantity commitment for a vendor and items. The same procedure can be used if you have a purchase agreement with other types of commitments. You can run this guide in demo data company USMF. If you're using USMF, you can run the "Create a purchase agreement" guide first to set up the necessary preconditions for this guide.


## Create a purchase order
1. Open the purchase order preparation workspace.
2. Click New purchase order.
3. In the Vendor account field, click the drop-down button to open the lookup.
4. In the list, find and select the desired record.
5. In the list, click the link in the selected row.
6. Toggle the expansion of the General section.
7. In the Purchase agreement field, click the drop-down button to open the lookup.
    * All available agreements for the vendor are listed here. Find the effective agreement that you want to use.  
8. In the list, click the link in the selected row.
9. Click Yes.
10. Click OK.

## Add a line
1. In the Item number field, type a value.
    * If there are specific inventory or location dimensions on the commitment you must enter the same values on the purchase order line to make use of the agreement.  
2. In the Site field, click the drop-down button to open the lookup.
    * The site may already be populated with the default value from the order, or from the vendor. If this is the case, skip this step.  
3. In the list, find and select the desired record.
4. In the list, click the link in the selected row.
5. In the Quantity field, enter a number.
    * Validate that the price is copied from the commitment.  

## Look up the commitment
1. Click Update line.
2. Click Attached.
    * Here you can get details for the purchase agreement. For example, you can see the price and whether the price and discount are fixed, which means that if you change price or discount on the purchase order to a different value than on the commitment, the system will remove the link so the purchase order line does not fulfill the commitment. You can also see if the Max is enforced option is selected, which means that the quantity on the commitment cannot be exceeded by summing all of the purchases that fulfill the commitment.  
3. Close the page.

## Look up the purchase agreement
1. On the Action Pane, click General.
2. Click Purchase agreement.
3. Close the page.
4. Close the page.

