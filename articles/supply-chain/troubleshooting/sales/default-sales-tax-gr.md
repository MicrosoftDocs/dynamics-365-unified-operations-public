---
title: Default Sales tax group to Sales order either from Delivery address or Customer account
description: Default Sales tax group to Sales order either from Delivery address or Customer account
author: SmithaNataraj
ms.date: 4/11/2021
ms.topic: troubleshooting
ms.search.form: SalesTable
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: smnatara
ms.search.validFrom: 2021-04-11
ms.dyn365.ops.version: 10.0.19
---

# Default Sales tax group to Sales order either from Delivery address or Customer account

KB Number: 4612561

Default Sales tax group to Sales order either from Delivery address or Customer account

## Resolution
Microsoft has investigated the reported issue. It works like this: Two addresses palying the role of delivery address exists; one primary without a sales tax group, another with a sales tax group. For the term of delivery to be applied for this customer, it is explicitly set that the sales tax address must be based on "Delivery". That implies that the address on the sales order used as delivery address will dictate the sales tax group applied onto the sales order. If this is blank, then blank will be applied. It is on purpose that we do not interpret blank as requiring to fall back to the sales tax group on the customer masterand apply this one. Such would not be in compliance with the explicit term of delivery rule for sales tax address. This is not a bug, but by intent. 

When term of delivery to be applied is explicitly for sales tax address is set to "Delivery", then you need to ensure that the delivery address applied has the proper sales tax group. 


