---
title: Item arrival journal for return orders creates inconsistent inventory quantity
description: The item arrival journal for return orders may create an inconsistent inventory quantity if the referenced item uses different sales and inventory units.
author: SmithaNataraj
ms.date: 4/11/2021
ms.topic: troubleshooting
ms.search.form: ItemArrival
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: henrikan
ms.search.validFrom: 2021-04-11
ms.dyn365.ops.version: 10.0.19
---

# Item arrival journal for return orders creates inconsistent inventory quantity

<!-- To KFM from Henrikan: Remove this topic as it is currently being addressed in a deliverable. -->

KB Number: 4613883

## Issue description

The item arrival journal for return orders may create an inconsistent inventory quantity if the referenced item uses a sales unit of measure that is different from the inventory unit of measure. This problem can occur for return orders in situations where the actualized unit of measure conversion for reference lot between sales and inventory units of measure is different than set up. <!-- KFM: This sentence isn't clear. Please revise. -->

The following scenario illustrates a situation where this will occur:
<!-- KFM: It might help if we specified the unit names we are referring to here, such as box and case. -->
1. The conversion between the sales and inventory unit of measure is 1:10. However, for the reference lot, quantity 3 were invoiced (sales unit of measure), whereas only quantity 25 (inventory unit of measure) were shipped.<!-- KFM: This sentence isn't clear. Please revise. -->
1. The actualized unit conversion is different than 1:10. Instead, it is 1:8.333333.
1. When the return order line is created, it specifies the quantity only for what was invoiced, using the sales unit of measure, and no inventory transaction is created.<!-- KFM: This sentence isn't clear. Please revise. -->

This is different from what happens when you create a credit line for a sales order of type *sales order*, where both the sales order line of quantity 3, and the inventory transaction of quantity 25 are created immediately. However, for return orders, inventory transactions aren't created until registration, given that the disposition action is different from credit only. Upon registration, the expected quantity expressed in the inventory unit of measure is assessed against the reference issue lot.

In this scenario, a quantity of 3 was invoiced, so the expected result is 3x10 = 30. The validation therefore returns an error because the quantity being returned is greater than what can be covered by the return lot. In the case of a blind return, without any reference to an issue lot and hence no validation, the registration page would open with quantity 30, and allow the user to change this to, for example, 25. In cases where the decimal precision is other than 0 for the sales unit of measure, the invoiced quantity in the sales unit of measure would have been 2.5, and the resulting return order quantity in the sales unit of measure would be 2.5, with the registered quantity of 25 in the inventory unit of measure.

## Workaround

There are three ways to work around this feature limitation for a case such as this:

- Use a regular sales order (type *sales order*) and use the create credit note function.
- Create a bind return (returned order) without any reference to an issue lot. <!--KFM: is it a blind return or a blind return? We have used both terms. -->
- Set the decimal precision for the sales unit of measure to a value other than 0.
