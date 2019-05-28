---
# required metadata

title: Improved handling of batch tracked items during retail statement posting & customer order process
description: This topic describes the improvements made to handling of batches for batch tracked items during Retail statement posting process.
author: josaw1
manager: AnnBe
ms.date: 05/28/2019
ms.topic: index-page
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: ed0f77f7-3609-4330-bebd-ca3134575216
ms.search.region: global
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2019-05-28
ms.dyn365.ops.version: 10.0

---
# Improved handling of batch tracked items during retail statement posting & customer order process

For batch tracked items, Retail POS does not support the capture of batch numbers at the time of sale.  However, based on specific configurations, during the posting of sales in the HQ through customer orders or statement posting, system would expect the existence of valid batch number for such products that can be used during the invoicing process.

If there are valid batch numbers available for products, the customer order invoicing process and the sales order invoicing process from statement posting will use the same. In its absence, the customer order invoicing process would fail posting and present the relevant message to the POS user. In the case of statement posting, the invoicing process fail’s and the statements gets into an error state. This is true even when negative inventory has been turned on for the products. 

This feature ensures that both customer order invoicing and sales order invoicing through statement posting is not blocked for batch tracked items where the inventory is zero / batch number is not available as long as negative inventory is turned on for these items. This is achieved by using a default batch id for the sales lines when batch numbers are not available. 

The default batch id to be used for customer orders can be defined under the following path: **Retail parameters > Customer orders tab > Order fast tab > Default batch id**

The default batch id to be used for sales order invoicing through statement posting can be defined under the following path: **Retail parameters > Posting tab > Inventory update fast tab > Default batch id**

> [!NOTE]
> This functionality is only available when Advanced warehousing is turned on for the concerend store warehouse and items. In a subsequent release, this feature will be supported for non advanced warehouse management scenarios as well. 



