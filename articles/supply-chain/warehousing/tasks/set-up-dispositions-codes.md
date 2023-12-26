--- 
# required metadata 
 
title: Set up dispositions codes
description: This procedure focuses on the setup of a disposition code that can be used on a mobile device for the return order receiving process. 
author: Mirzaab
ms.date: 11/11/2016
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: WHSDispositionTable
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Distribution
ms.author: mirzaab
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Set up dispositions codes

[!include [banner](../../includes/banner.md)]

This procedure focuses on the setup of a disposition code that can be used on a mobile device for the return order receiving process. Disposition codes are a collection of rules that can be used when items are received. For example, when a work user uses a mobile device to receive items that were damaged, the user must scan a disposition code for damaged items. The inventory status of the goods received, the work template, and the location directive can be determined from the scanned disposition code. For the purchase order receiving process and the production order report as finished process, the use of a disposition code is optional. For the sales order return receiving process, if the items are registered using a mobile device, the use of disposition code is mandatory.  This guide was created using the demo data company USMF. This procedure is intended for the warehouse manager. 

1. Go to Warehouse management > Setup > Mobile device > Disposition codes.
2. Click New.
    * Create a new disposition code to use for customer returns.  
3. In the Disposition code field, type a value.
4. In the Inventory status field, select an inventory status where there is inventory blocking.
    * If you're using USMF, select 'Blocking'. You can add an inventory status to the disposition code to override the default status that's on the order lines.  
5. In the Work template field, type a value.
    * Optional: Select a work template code that is associated with a return order. If no value is provided, the work template will be resolved using the standard rules configured in your system. Selecting a work template will limit the processes this disposition code can be used with. For example, if a disposition code has a work template with a work order of type purchase order, it can't be used to register items that are returned by customers.  
6. In the Return disposition code field, type a value.
    * The return disposition code determines the remainder of the return order process for the items registered. In this example, the customer should receive a credit note. Add a returns disposition code that contains an action Credit.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]