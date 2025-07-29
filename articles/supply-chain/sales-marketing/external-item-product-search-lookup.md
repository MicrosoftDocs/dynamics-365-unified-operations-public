---
title: Use external item identifiers to add products to orders (preview)
description: Learn how to define external item numbers and descriptions for each customer, and how to add products to sales orders based on these identifiers.
author: AditiPattanaik
ms.author: adpattanaik
ms.reviewer: kamaybac
ms.search.form: SalesTableDetails, SalesLine
ms.topic: how-to
ms.date: 07/28/2025
ms.custom: 
  - bap-template
---

# Use external item identifiers to add products to orders (preview)

[!include [banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until 10.0.45 GA -->

When you're adding an item to a sales order, you can search for it using its external item identifier or external description/name. You can define external item identifiers and descriptions for each customer, allowing you to use the customer's terminology when adding products to orders.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## Prerequisites

To use the features described in this article, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.45 or later.
- You must ensure that the feature named *Enable lookup based search for Sales External Item Identifier field* is turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Specify external item identifiers for a customer

External item identifiers are set up on the account for the customer that uses them. You can add external item identifiers to a customer account by following these steps:

1. Go to **Account Receivable** \> **All customers**.
1. Find and open the customer you want to set up with external item identifiers.
1. On the Action Pane, open the **Sell** tab and then select **Setup** \> **External item description**.
1. The **External item description** page opens, showing the existing external item identifiers for the customer. To add a new one, select **New** on the Action Pane and then enter values for the following fields:
    - **ABC code** – If the customer has assigned an ABC inventory classification to the item, you can note that here. ABC analysis is an inventory management technique that determines the value of inventory items based on their importance to the business.
    - **Item number** – Select your standard (internal) item number for the product.
    - **External item number** – Enter the external item identifier that this customer uses to identify the item you specified. Users will be able to search for this number when creating a sales order.
    - **Description** – Enter the name or other short description that the customer uses to identify the item. Users will be able to search for this description when creating a sales order.
    - **External item text** – Enter text that this customer uses to describe the item.
    - *Other dimensions* – If the external item number is associated with other specific dimension values (such as configuration, size, color, style, and so on), then enter these dimension values in the remaining columns as needed to finish identifying the item.

1. Continue to add external item identifiers as needed. When you're done, select **Save** on the Action Pane.

## Add a product to a sales order using its external item identifier

When a customer has external item identifiers defined, you can use them to quickly find and add products to sales orders. To do this, follow these steps:

1. Go to **Sales and marketing** \> **Sales orders** \> **All sales orders**.
1. Either [create a new sales order](tasks/create-sales-orders.md) or open an existing one that you want to add lines to. The sales order must be for a customer that has external item identifiers defined.
1. Make sure that the **External** column is visible in the grid on the **Sales order line** FastTab. If it isn't, you can add it by doing the following steps:
    1. Open the **Grid options** dropdown list, which is the button with three dots on it located at the right side of the heading row of the grid.
    1. Select **Insert columns** to open the **Insert columns** dialog.
    1. Find the row with **Field** name *External* and select the checkbox in that row.
    1. Select **Update** to apply the change and close the dialog.
1. On the **Sales order line** FastTab toolbar, select **Add line**.
1. In the **External** column for the new line, select the item that you want to use based on its external item number or description. You can either type it in the field or select it from the lookup list. The field supports *search as you type*, which filters the list based on the **External item number** and **Description** values from the external item description.
1. On selecting a value, the **Item number**, **Product name**, and other related fields are populated based on the item setup.
