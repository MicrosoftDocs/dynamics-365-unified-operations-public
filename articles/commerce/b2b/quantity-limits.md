---
# required metadata

title: Set product quantity limits for B2B e-commerce sites
description: This topic describes how to set product quantity limits for B2B e-commerce sites.
author: josaw1
manager: AnnBe
ms.date: 01/15/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 
# optional metadata
ms.search.form:  RetailOperations
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: v-chgri
#ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
ms.search.industry: retail
ms.author: josaw
ms.search.validFrom: 2021-01-31
ms.dyn365.ops.version: 10.0.14

---

# Set product quantity limits for B2B e-commerce sites

[!include [banner](../../includes/banner.md)]

This topic describes how to set product quantity limits for B2B e-commerce sites.

Most products have a unit of measure that defines their grouping, which affects how they can be sold. Some products may have an additional grouping for quantities, which determines if they can be sold as individual units or multiples and if there is a minimum/maximum order quantity limit that needs to be followed.

The quantity limiting feature ensures that the configured minimum, maximum, multiple, and standard quantities specified in Commerce (of the default order settings or Commerce site builder site settings) are applied to customer orders placed on an e-commerce site. Product quantity restriction for point of sale (POS) and call centers is currently not supported.

Many retailers provide the option of customer orders (also known as special orders) to meet various product and fulfillment requirements. Some typical scenarios are:

- A customer wants products of certain variants to be sold in multiples of a few.
- A customer wants to pick up products from a store or location that differs from the store or location where the customer purchased those products, but the packing standards for the stores differ from those for online sales distribution.
- A customer wants to buy a limited-edition product that may have a maximum quantity limit for items that can be purchased.

## Enable default order settings feature in Commerce headquarters

A prerequisite to settings product quantity limits is to enable the default order settings feature in Commerce headquarters.

To enable the default order settings feature, follow these steps.

1. Go to **System administration \> Workspaces \> Feature management**.
1. Find and select the **Support the Site and Default order settings in the customer order** feature.
1. At the bottom of the right pane, select **Enable now**. 

## Define quantity settings 

One can define the quantity settings on the Default order settings page. To open this page, 

1. Go to Product **Retail and Commerce \> Products and categories \> Released products by category**
1. Select a released product.
1. On the Action Pane, select **Manage inventory \> Order settings \> Default order settings**. 
1. On the **Sales order** fast tab of the **Default order settings** page, set the product sales quantities under **SALES QUANTITY**.
    - **Multiple** - Product can be bought in multiples of this quantity.
    - **Minimum Order Quantity** - Minimum number of products that needs to be purchased.
    - **Maximum Order Quantity** - Maximum limit for products that needs to be purchased.
    - **Standard Order Quantity** - The default quantities that are set when the product is selected.

## Enable B2B order quantity limits feature in Commerce site builder

To enable B2B order quantity limits feature in Commerce site builder, follow these steps.

1. Go to **Site settings \> Extensions**
1. Under **Enable Order Quantity Limits**, select **Enabled for B2B customers** from the drop-down menu. 

> [!NOTE] 
> Updated site builder settings will only take effect after the app.settings.json file has been updated. For more information, see [SDK and Module library updates](../e-commerce-extensibility/sdk-updates.md#update-the-appsettingsjson-file).

