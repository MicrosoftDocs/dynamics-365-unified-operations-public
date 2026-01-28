---
title: Hybrid customer orders
description: Learn about hybrid customer orders in Microsoft Dynamics 365 Commerce.
author: josaw1
ms.date: 01/22/2026
ms.topic: overview
ms.reviewer: v-griffinc
ms.assetid: 9d99a5b9-4662-499a-bece-3ea1d6092934
ms.search.region: global
ms.author: johnmichalak
ms.search.validFrom: 2016-11-30
ms.custom: 
  - bap-template
---

# Hybrid customer orders

[!INCLUDE [banner](includes/banner.md)]

This article explains hybrid customer orders in Microsoft Dynamics 365 Commerce.

A hybrid customer order is a single order that contains both products that a customer can take out of the store and products that the customer picks up or that the store ships later.

In Commerce, you can select either carry out all products or carry out selected products for a customer order. The product lines that you mark as carry out are automatically invoiced after you create the order. The same process applies to an order that the customer picks up after you create the order. To determine the amount due on hybrid orders, add the deposit percentage on pick and ship product lines with the full amount of the carry out lines. For hybrid orders, the system switches between customer order mode and cash and carry mode as follows:

- If all products in the cart are set to **Carry out delivery**, the system handles the order as a cash and carry transaction.
- If any or all lines in the cart are set to either **Pick** or **ship delivery**, the system handles the order as a customer order transaction.

If you select a cart line and select **Pick selected**, **Ship selected**, or **Carry out selected**, you set that delivery method for only the specific cart line. The downstream flow of the operation continues as usual. However, if you select **Pick selected**, **Ship selected**, or **Carry out selected** without selecting a cart line, a new page opens that lists all the cart lines. On that screen, you can select multiple lines at once for setting the delivery method. When you use that method for selecting lines, you override any previous delivery method that you assigned to the line.

## Additional resources

[Customer orders in point of sale (POS)](customer-orders-overview.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
