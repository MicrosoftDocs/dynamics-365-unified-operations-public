---
# required metadata

title: Return items across multiple customer orders and invoices
description: Learn about functionality that enables returns across multiple customer orders and invoices in Microsoft Dynamics 365 Commerce.
author: josaw1
ms.date: 01/23/2026
ms.topic: how-to 
ms.reviewer: v-griffinc
ms.assetid: ed0f77f7-3609-4330-bebd-ca3134575216
ms.search.region: global
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2019-01-15
ms.custom: 
  - bap-template
---
# Return items across multiple customer orders and invoices

[!include [banner](includes/banner.md)]

This article explains functionality that enables returns across multiple customer orders and invoices in Microsoft Dynamics 365 Commerce.

You can make returns across multiple orders and invoices. 

## Configure Commerce to support returns across multiple customer order and invoices

1. Go to **Commerce parameters \> Customer orders**.
1. Turn on the **Enable returns for multiple orders** parameter. 

## Process returns

After you turn on the parameter and synchronize the changes to the stores, the cashier in the store can select multiple sales orders for a customer for their return.

When the cashier selects the orders, a list of all the returnable products across all the invoices for the orders displays. The cashier can then select the products to return. The system creates a single return order for all the selected products.

[!INCLUDE[footer-include](../includes/footer-banner.md)]