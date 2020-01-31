---
# required metadata

title: Improved handling of batch-tracked items
description: This topic describes the improvements that have been made to the handling of batches for batch-tracked items during the statement posting process.
author: josaw1
manager: AnnBe
ms.date: 11/04/2019
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
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2019-05-28
ms.dyn365.ops.version: 10.0

---
# Improved handling of batch-tracked items


[!include [banner](includes/banner.md)]


In Point of Sale (POS), batch numbers can't be captured for batch-tracked items at the time of sale. However, for specific configurations, when sales are posted in the headquarters through customer orders or statement posting, the Microsoft Dynamics system expects that valid batch numbers for batch-tracked items exist, and that they will be used during the invoicing process.

If valid batch numbers are available for products, the customer order invoicing process and the sales order invoicing process from statement posting use them. Otherwise, the customer order invoicing process can't post, and the POS user receives an error message. Statement posting then goes into an error state. This error state occurs even when negative inventory has been turned on for the products.

Improvements that have been made in Retail version 10.0.4 and later help guarantee that, when negative inventory is turned on for batch-tracked items, customer order invoicing and sales order invoicing through statement posting aren't blocked for those items if the inventory is 0 (zero) or a batch number isn't available. The new functionality uses a default batch ID for the sales lines when batch numbers aren't available.

To define the default batch ID that is used for customer orders, on the **Commerce parameters** page, on the **Customer orders** tab, on the **Order** FastTab, set the **Default batch id** field.

To define the default batch ID that is used for sales order invoicing through statement posting, on the **Commerce parameters** page, on the **Posting** tab, on the **Inventory update** FastTab, set the **Default batch id** field.

> [!NOTE]
> This functionality is available only when advanced warehousing is turned on for the specific store warehouse and items. In a later release, the functionality will also be supported for scenarios where advanced warehouse management isn't used.

> [!NOTE]
> Support for improved handling of batch-tracked items during statement posting for non-advanced warehouse management scenarios was introduced in Retail version 10.0.5.
