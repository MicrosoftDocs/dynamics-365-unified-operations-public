---
# required metadata

title: Customer management in asynchronous mode
description: This topic explains how retailers can enable customer management capabilities in asynchronous mode at the point of sale (POS) or e-Commerce channel in Microsoft Dynamics 365 Commerce.
author: [gvrmohanreddy]
manager: jeffbl
ms.date: 11/24/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 
# optional metadata
# ms.search.form:  
#ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: gmohanv
ms.search.validFrom: 2021-12-17
ms.dyn365.ops.version: 10.0.24
---


# Convert Async customers to Sync customers

[!include [banner](includes/banner.md)]

This topic explains necessary business process and schedule jobs to synchronize customers those are created in asynchronous mode, in Microsoft Dynamics 365 Commerce.


To convert Async customers to Sync customers, you must first run the **P-job** to send the Async customers to Commerce headquarters. Then run the **Synchronize customers and business partners from async mode** job (formerly named the **Synchronize customers and business partners from async mode** job) to create customer account IDs. Finally, run the **1010** job to sync the new customer account IDs to the channels.


Additionally, If an order is referenced to an async customer( or address), who is not synchronized to headquarters yet, customer will be synchronized as part of the "Synchronize orders" batch job. If a cash and carry transaction references an async customer (or address), the customer or address is synchronized before EOD posting.



## Additional resources


[Customer management in stores](/customer-mgmt-stores.md)

[Synchronous and asynchronous customer](/synchronous-and-asynchronous-customers.md)


[Customer attributes](dev-itpro/customer-attributes.md)

[Offline data exclusion](dev-itpro/implementation-considerations-cdx.md#offline-data-exclusion)
