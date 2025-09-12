---
title: Improved handling of batch-tracked items
description: Learn about the improved handling of batch-tracked items during the statement posting process in Microsoft Dynamics 365 Commerce.
author: josaw1
ms.date: 07/09/2025
ms.topic: how-to
ms.reviewer: johnmichalak
ms.custom: 
  - bap-template
ms.search.region: Global
ms.search.industry: Retail
ms.author: shajain
---
# Improved handling of batch-tracked items

[!include [banner](includes/banner.md)]

This article describes the improved handling of batch-tracked items during the statement posting process in Microsoft Dynamics 365 Commerce.

In Dynamics 365 Commerce point of sale (POS), batch numbers can't be captured for batch-tracked items at the time of sale. However, for specific configurations when sales are posted in Commerce headquarters through customer orders or statement posting, Commerce expects that valid batch numbers for batch-tracked items are used during the invoicing process.

If valid batch numbers are available for products, both the customer order invoicing process and the sales order invoicing process from statement posting use them. If valid batch numbers aren't available for products, the customer order invoicing process can't post, and the POS user receives an error message. Statement posting then goes into an error state, even if negative inventory is turned on for the products.

Improvements to Commerce help ensure that when negative inventory is turned on for batch-tracked items, customer order and sales order invoicing through statement posting isn't blocked for those items if the inventory is 0 (zero) or a batch number isn't available. The improved functionality uses a default batch ID for the sales lines when batch numbers aren't available.

## Define the default batch ID that is used for customer orders

The following procedure defines a default a batch ID to order lines created from POS if the inventory reservation is set to **Automatic**.

To define the default batch ID that is used for customer orders, follow these steps.

1. In Commerce headquarters, go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce parameters**.
1. On the **Customer orders** tab, on the **Order** FastTab, enable the **Use default batch ID when batch numbers are not found** option, and then enter a value in the **Default batch ID** field.
1. Go to **Account receivable parameters** \> **General** \> **Sales default values** and set the **Reservation** field to **Automatic**.

> [!NOTE]
> Customer orders created from POS don't support adding a batch ID value for batch-controlled items. If POS is used to create orders that include batch-controlled items, then you should add the batch number in headquarters before fulfillment. 
  
## Define the default batch ID that is used for sales order invoicing through statement posting

To define the default batch ID that is used for sales order invoicing through statement posting, follow these steps.

1. In Commerce headquarters, go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce parameters**.
1. On the **Posting** tab, on the **Inventory update** FastTab, enter a value in the **Default batch id** field, and then enable the **Use default batch id when batch numbers are not found** option.

> [!NOTE]
> Physical negative inventory must be turned on for the batch-tracked item's item model group.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
