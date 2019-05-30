---
# required metadata

title: Improved handling of batch tracked items
description: This topic describes improvements made to handling of batches for batch tracked items during the Retail statement posting process.
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
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2019-05-28
ms.dyn365.ops.version: 10.0

---
# Improved handling of batch tracked items

Dynamics 365 for Retail point of sale (POS) does not support the capture of batch numbers for batch tracked items at the time of sale. For specific configurations, though, during the posting of sales in the headquarters (HQ) through customer orders or statement posting, the Dynamics system expects the existence of valid batch numbers for batch tracked products to be used during the invoicing process.

If there are valid batch numbers available for products, the customer order invoicing process and the sales order invoicing process from statement posting will use them. In its absence, the customer order invoicing process fails posting and presents an error message to the POS user. Statement posting will then get into an error state. The error state will occur even when negative inventory has been turned on for the products. 

In Dynamics for Retail version 10.0.4 and higher, improvements were made that will ensure that both customer order invoicing and sales order invoicing through statement posting is not blocked for batch tracked items where the inventory is zero or a batch number is not available, when negative inventory is turned on for these items. The new functionality uses a default batch id for the sales lines when batch numbers are not available. 

To define the default batch id to be used for customer orders, go to **Retail parameters > Customer orders tab > Order fast tab > Default batch id**.

To define the default batch id to be used for sales order invoicing through statement posting, got to **Retail parameters > Posting tab > Inventory update fast tab > Default batch id**.

> [!NOTE]
> This functionality is only available when advanced warehousing is turned on for the specific store warehouse and items. In a later release, this functionality will be supported for non-advanced warehouse management scenarios as well. 



