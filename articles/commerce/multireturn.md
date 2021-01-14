---
# required metadata

title: Return items across multiple customer orders and invoices
description: This topic describes the functionality enabling returns across multiple customer orders and invoices in Dynamics 365  Commerce.
author: josaw1
manager: AnnBe
ms.date: 08/27/2020
ms.topic: index-page
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: NOINDEX, NOFOLLOW
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
#ms.search.scope: Core, Operations, Retail
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


This article describes two features that optimize customer order returns over multiple invoices. 

## Enable refunds over multiple captures

This feature enables multiple linked refunds against the same customer order. 

1. Go to the **Feature management** workspace and search for **Enable refunds over multiple captures**.
2. Select **Enable refunds over multiple orders** and then click **Enable**. 

## Enable proper tax calculation for returns with partial quantity

This feature ensures that when an order is returned using multiple invoices, the taxes will ultimately be equal to the tax amount originally charged. 

1. Go to the **Feature management** workspace and search for **Enable proper tax calculation for returns with partial quantity**.
2. Select **Enable proper tax calculation for returns with partial quantity** and then click **Enable**. 


## Process returns

After these features are turned on and the changes are synchronized to the stores, the cashier in the store can select multiple sales orders for a customer for their return.

When the orders are selected, a list of all the returnable products across all the invoices for the orders will display. The cashier can then select the products to return. A single return order will be created for all the selected products.

If the order is fully returned, the amount of taxes returned to the customer will be equal to the amount of tax originally charged.

