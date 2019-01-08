---
# required metadata

title: Return across multiple customer order & invoices
description: This topic describes the return across multiple customer order & invoices functionality in Microsoft Dynamics 365 for Retail.
author: josaw1
manager: AnnBe
ms.date: 1/08/2019
ms.topic: index-page
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: ed0f77f7-3609-4330-bebd-ca3134575216
ms.search.region: global
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2018-11-15
ms.dyn365.ops.version: 

---
# Return across multiple customer order & invoices


In the previous versions of the product, a cashier was able to process a
return order only for a single invoice at a time. If a customer wanted
to return products in the store that was fulfilled across multiple
invoices for an order, or if the products were purchased across multiple
customer orders, the only way the returns could be processed by the
cashier would be perform multiple return transactions and have it
processed invoice by invoice. This is a cumbersome experience for the
cashier and is not a true omni-channel experience for the end customer
as well.

**Configure retail to support returns across multiple customer order &
invoices**

Follow these steps to configure the system to support returns across
multiple customer order & invoices:

1.  A new parameter has been introduced under the path Retail
    parameters &gt; Customer orders called as "Enable returns for
    multiple orders" which needs to be turned on to enable this feature

**Process returns**

1.  Once the parameter is turned on and the changes are synchronized to
    the stores, the cashier in the store would be able to select
    multiple sales orders for a given customer for which returns have to
    be processed for

2.  Selecting the orders will return a list of all the returnable
    products across all the invoices for the orders. The cashier can
    then select the products to return and process a single return order
    for all the products.
