---
title: Display charges for a manufactured item
description: The constant costs of a manufactured item reflect the operation setup times and the components that have a constant quantity or a constant scrap amount.
author: prasungoel
ms.author: prasungoel
ms.topic: article
ms.date: 04/20/2017
ms.reviewer: kamaybac
ms.search.form: CostingVersion, InventItemPrice
ms.assetid: 6f5b851b-c5a7-43ef-b380-0d316667c1ef
---

# Display charges for a manufactured item

[!include [banner](../includes/banner.md)]

The constant costs of a manufactured item reflect the operation setup times and the components that have a constant quantity or a constant scrap amount.

The calculated amount of an item's charges can be displayed with the item's unit costs. However, the charges are sometimes displayed as separate fields, and they are not included in the item's unit costs. When the charges appear as separate fields, one field displays the total amount of charges, and another field displays the costing lot size that is used to amortize the amount. The Item price page, for example, displays the charges as two separate fields. However, the Complete page displays the item's total cost per unit, and the amortized costs are included in the unit costs.

The charges for a manufactured item are always included in the item's unit cost for standard cost purposes. They can optionally be included for planned cost purposes. A policy in the costing version enforces the inclusion of charges in the cost of a manufactured item. When you activate an item's cost record, you update the charges for the item's base cost information, which is displayed in the Item price page. The charges are displayed as two separate fields, and they are not included in the item's unit cost. Each activation updates the item's base cost information, even if the activation reflects different sites. Therefore, you should view the base cost information as reference information.







[!INCLUDE[footer-include](../../includes/footer-banner.md)]