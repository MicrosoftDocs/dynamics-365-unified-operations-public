--- 
# required metadata 
 
title: Apply a purchase agreement when creating a purchase order
description: This procedure shows how to use a purchase agreement when you create a purchase order. 
author: GalynaFedorova
ms.date: 08/09/2019
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: gfedorova
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Apply a purchase agreement when creating a purchase order

[!include [banner](../../includes/banner.md)]

This procedure shows how to use a purchase agreement when you create a purchase order. The purchase agreement must be applied when you create the purchase order because there are general terms that should be copied to the purchase order header. Typically this task would be carried out by a purchasing agent. As a prerequisite for this guide, you must have an effective purchase agreement with a product quantity commitment for a vendor and items. The same procedure can be used if you have a purchase agreement with other types of commitments.

## Create a purchase order

1. Go to **Production and sourcing \> Workspaces \> Purchase order preparation**.
1. On the Action Pane, select **New purchase order**.
1. The **Create purchase order** dialog opens. Select a **Vendor account**. Inspect and adjust the other address fields as needed.
1. Expand the **General** FastTab.
1. In the **Purchase agreement** field, find and select the effective agreement that you want to use. All available agreements for the vendor are listed here.  
1. Select **Yes**.
1. Select **OK**.

## Add a line

1. In the **Item number** field, type a value. If there are specific inventory or location dimensions on the commitment you must enter the same values on the purchase order line to make use of the agreement.
1. In the **Site** field, select the drop-down button to open the lookup. The site may already be populated with the default value from the order, or from the vendor. If this is the case, skip this step.  
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. In the **Quantity** field, enter a number. Validate that the price is copied from the commitment.  

## Look up the commitment

1. Select **Update line**.
1. Select **Attached**. Here you can get details for the purchase agreement. For example, you can see the price and whether the price and discount are fixed, which means that if you change price or discount on the purchase order to a different value than on the commitment, the system will remove the link so the purchase order line does not fulfill the commitment. You can also see if the Max is enforced option is selected, which means that the quantity on the commitment cannot be exceeded by summing all of the purchases that fulfill the commitment.  
1. Close the page.

## Look up the purchase agreement

1. On the **Action Pane**, select **General**.
1. Select **Purchase agreement**.
1. Close the page.
1. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]