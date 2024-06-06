---
# required metadata

title: Improved handling of batch-tracked items
description: This article describes the improved handling of batch-tracked items during the statement posting process in Microsoft Dynamics 365 Commerce.
author: josaw1
ms.date: 09/09/2021
ms.topic: conceptual
# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
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

This article describes the improved handling of batch-tracked items during the statement posting process in Microsoft Dynamics 365 Commerce.

In Dynamics 365 Commerce point of sale (POS), batch numbers can't be captured for batch-tracked items at the time of sale. However, for specific configurations when sales are posted in Commerce headquarters through customer orders or statement posting, Commerce expects that valid batch numbers for batch-tracked items exist and will be used during the invoicing process.

If valid batch numbers are available for products, both the customer order invoicing process and the sales order invoicing process from statement posting use them. If valid batch numbers aren't available for products, the customer order invoicing process can't post, and the POS user receives an error message. Statement posting then goes into an error state, even if negative inventory has been turned on for the products.

Improvements to Commerce help ensure that when negative inventory is turned on for batch-tracked items, customer order invoicing and sales order invoicing through statement posting aren't blocked for those items if the inventory is 0 (zero) or a batch number isn't available. The improved functionality uses a default batch ID for the sales lines when batch numbers aren't available.

## Define the default batch ID that is used for customer orders

To define the default batch ID that is used for customer orders, follow these steps.

1. In Commerce headquarters, go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce parameters**.
1. On the **Customer orders** tab, on the **Order** FastTab, enter a value in the **Default batch id** field.

## Define the default batch ID that is used for sales order invoicing through statement posting

To define the default batch ID that is used for sales order invoicing through statement posting, follow these steps.

1. In Commerce headquarters, go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce parameters**.
1. On the **Posting** tab, on the **Inventory update** FastTab, enter a value in the **Default batch id** field.

> [!NOTE]
> - Default batch ID functionality is available only when advanced warehousing is enabled for the specific store warehouse and items. In a future release, default batch ID functionality will also be supported for scenarios where advanced warehouse management isn't enabled.
> - Support for the improved handling of batch-tracked items during statement posting for non-advanced warehouse management scenarios was introduced in the Commerce version 10.0.5 release.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
