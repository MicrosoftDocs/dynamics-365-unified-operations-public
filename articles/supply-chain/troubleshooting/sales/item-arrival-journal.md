---
title: Item arrival journal for return order may create inconsistent inventory quantity if referenced item has different sales/inventory units
description: Item arrival journal for return order may create inconsistent inventory quantity if referenced item has different sales/inventory units
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

# Item arrival journal for return order may create inconsistent inventory quantity if referenced item has different sales/inventory units

KB Number: 4613883

Item arrival journal for return order may create inconsistent inventory quantity if referenced item has different sales/inventory units


## Resolution
Microsoft has investigated the reported issue and concluded that it is due to a feature/design limitation in the original feature introduced in Dynamics Ax2009. The feature limitation related to  sales order type returned order, when the actualized unit of measure conversion for reference lot between sales and inventory units of measure is different than setup. In the reported scenario the conversion between sales and inventory unit of measure is 1:10. However, for the reference lot, quantity 3 were invoiced (sales unit of measure), whereas only quantity 25 (inventory unit of measure) were shipped.  The actualized unit conversion is different than 1:10. It is 1:8.333333. When the return order line is created, it is created with the quantity in sales unit of measure only for what was invoiced, and no inventory transaction is created. This is different compared to creating a credit line for a sales order of type sales order, where both the sales order line of quantity 3, and the inventory transaction of quantity 25 is created immediately. The reason for this difference in behavior is the design of the return order, where creation of the inventory transaction is deferred until registration, given that the disposition action is different from credit only. Upon registration, the expected quantity expressed in inventory unit of measure is assessed against the reference issue lot. As quantity 3 was invoiced, the expectation is 3x10 = 30, the validation returns a failure: The quantity being returned is greater than what can be covered by the return lot. In case of a blind return, without any reference to an issue lot and hence no validation, then the registration form would open with quantity 30, and allow the user to change this to, as example, 25. In case of decimal precision being different from 0 for the sales unit of measure, the invoiced quantity in sales unit of measure would have been 2.5, and the resulting return order quantity in sales unit of measure 2.5 with the registered quantity of 25 in inventory unit of measure.

There are three ways to work around the feature limitation. Either use the regular sales order type sales order, and create credit note function, for a case such as this, or to create a bind return (returned order) without any reference to an issue lot. Alternatively set the decimal prevision different from 0 on the sales unit of measure.

This feature/design limitation cannot be resolved as a hot fix. As Microsoft however understands the customer scenario, we will assess in future planning of return orders, if  the  feature/design limitation can be changed. 



