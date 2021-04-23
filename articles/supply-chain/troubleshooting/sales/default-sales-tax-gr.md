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
<!-- KFM: the title and issue description are not clear. -->
# Sales tax group on a sales order must be defaulted either from customer account or delivery address 

KB Number: 4612561

## Symptoms
Customer has sales tax group assigned. The same customer record has two addresses one address set with primary address that does not have sales tax group set and a secondary address with the sales tax group set. When a sales order is created for this customer, with the primary address set, the sales tax group was not set. 

If the address on sales order is modified to the secondary address which has the sales tax group set, then the sales tax group defined is defaulted to the sales order.

The expectation here is to  default sales tax group defined on the customer account or the delivery address.

## Resolution

The system is behaving as designed. The "Terms of Delivery" controls how the sales tax group is defaulted. The system applies sales tax as illustrated in the following example:

1. Suppose a customer has two delivery addresses: 
    - A primary address without a sales tax group
    - A secondary address with a sales tax group
1. If the terms of delivery to be applied for this customer, is explicitly set so that the sales tax address must be based on the delivery address, i.e. "Delivery", then this implies that the address on the sales order used as delivery address will dictate the sales tax group applied to the sales order. So in this case, if the primary address is set as the delivery address, the sales tax group is defaulted from this. Hence if that was not set, the sales order will not have a sales tax group set.
1. If the delivery address on the sales order is blank, no address is assumed when it comes to applying sales tax. The system does not fall back to the sales tax group defined on the customer account. This would not be in compliance with the explicit terms of delivery rule for the sales tax address.
1. When the "terms of delivery" explicitly specifies that the sales tax address is the delivery address, then you must ensure that the delivery address applied has the proper sales tax group.
