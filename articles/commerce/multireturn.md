---
# required metadata

title: Return items across multiple customer orders and invoices
description: This article describes the functionality enabling returns across multiple customer orders and invoices in Dynamics 365  Commerce.
author: josaw1
ms.date: 08/27/2020
ms.topic: conceptual
# optional metadata

# ms.search.form: 
# ROBOTS: NOINDEX, NOFOLLOW
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: ed0f77f7-3609-4330-bebd-ca3134575216
ms.search.region: global
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2019-01-15
ms.dyn365.ops.version: 10.0

---
# Return items across multiple customer orders and invoices

[!include [banner](includes/banner.md)]


Returns can be made across multiple orders and invoices. 

## Configure Commerce to support returns across multiple customer order and invoices

1. Go to **Commerce parameters \> Customer orders**.
1. Turn on the **Enable returns for multiple orders** parameter. 

## Process returns

After the parameter is turned on and the changes are synchronized to the stores, the cashier in the store can select multiple sales orders for a customer for their return.

When the orders are selected, a list of all the returnable products across all the invoices for the orders will display. The cashier can then select the products to return. A single return order will be created for all the selected products.
