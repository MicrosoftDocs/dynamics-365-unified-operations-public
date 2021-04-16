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
# Default sales tax group to sales order either from delivery address or customer account

KB Number: 4612561

## Issue description
<!-- KFM: The issue needs to be described more clearly. -->

Default sales tax group to sales order either from delivery address or customer account.

## Resolution

This is the expected behavior. The system applies sales tax as illustrated in the following example:

1. Suppose a customer has two delivery addresses: <!-- KFM: The rest of the example doesn't mention these two addresses. Later, we talk about a "blank" address. -->
    - A primary address without a sales tax group
    - A secondary address with a sales tax group
1. In the terms of delivery to be applied for this customer, it is explicitly stated that the sales tax address must be based on the delivery address. That implies that the address on the sales order used as delivery address will dictate the sales tax group applied to the sales order.
1. If the delivery address on the sales order is blank, no address is assumed when it comes to applying sales tax. The system does not fall back to the sales tax group defined on the customer master. This would not be in compliance with the explicit terms of delivery rule for the sales tax address.
1. When the terms of delivery explicitly specify that the sales tax address is the delivery address, then you must ensure that the delivery address applied has the proper sales tax group.
