---
# required metadata

title: Monitor consignment inventory using vendor collaboration
description: This procedure shows how to use vendor collaboration to see information about the stock level of product that you have placed in consignment with a customer.
author: mkirknel
manager: AnnBe
ms.date: 10/13/2016
ms.topic: business-process
ms.prod:  
ms.service: dynamics-ax-applications
ms.technology:  

# optional metadata

# ms.search.form:   
audience: Application User
# ms.devlang:  
ms.reviewer: YuyuScheller
ms.search.scope: Operations
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Distribution
ms.author: mkirknel
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: AX 7.0.0
---
# Monitor consignment inventory using vendor collaboration

[!include[task guide banner](../../includes/task-guide-banner.md)]

This procedure shows how to use vendor collaboration to see information about the stock level of product that you have placed in consignment with a customer. You can also monitor the consumption of the stock when the customer takes ownership of the inventory. You can use this procedure in the USMF demo data company. This procedure is for a feature that was added in Dynamics 365 for Operations, version 1611.


## View consumed inventory
1. Go to Vendor collaboration > Consignment inventory > Products received from consignment inventory.
    * The list shows the product receipt lines that were generated when ownership of the consignment inventory was changed from the vendor to the customer. You might have to scroll to the right to see quantities and other information. You can use the information in this list to generate invoices for your customer. You can also export the data to Microsoft Excel.   
2. Click View purchase order.
3. Expand the Line details section.
    * The line is marked as Consignment, and the header section shows that the purchase order has a status of Received.  
4. Close the page.

## View on-hand inventory
1. Go to Vendor collaboration > Consignment inventory > On-hand consignment inventory.
    * The On-hand consignment inventory page shows the stock that you own at the customer’s warehouse. You can show additional dimensions, such as the site and warehouse, by clicking the Display dimensions tab.   
