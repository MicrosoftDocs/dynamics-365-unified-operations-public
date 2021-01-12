---
# required metadata

title: Set order quantity for products
description: This topic describes how to set product quantity limits for B2B e-commerce sites.
author: josaw1
manager: AnnBe
ms.date: 01/12/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 
# optional metadata
ms.search.form:  RetailOperations
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: josaw
#ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
ms.search.industry: retail
ms.author: josaw
ms.search.validFrom: 2021-01-31
ms.dyn365.ops.version: 10.0.14

---

# Set order quantity for products

[!include [banner](../../includes/banner.md)]

Most products have a Unit of Measure that defines their grouping on how
they can be sold. Some products may have an additional grouping for the
quantities – which would determine if they can be sold as individual
units or multiple and if there is a minimum/maximum order quantity that
needs to be followed.

The scope of this feature is to enable the customer sales orders to
validate against the 'Default order settings' for Sales Quantity per
product. To ensure that the minimum, maximum, multiple, and standard
quantities of the default order settings or Site settings will be
respected to create any Customer order at AX-Call Center, POS &
e-Commerce. (Initial release the enforcements are available at the
eCommerce and Point-of-Sale only)

In an omni-channel commerce world, many retailers provide the option of
customer orders, or special orders, to meet various product and
fulfillment requirements. Here are some typical scenarios:

-   A customer wants products of certain variants to be sold in
    multiples of a few quantity.

-   A customer wants to pick up products from a store or location that
    differs from the store or location where the customer purchased
    those products, but the packing standards for the stores differ from
    online sales distribution.

-   A customer wants to buy a limited-edition product which may have a
    quantity limit for maximum purchase.

## Prerequisites

Turn on the 'Quantity' feature in Feature Management: "Support the Site
and Default order settings in the customer order"

## Setup - Released Products by variants

One can define the quantity settings on the Default order settings page.
To open this page, go to Product 'Released products by category &gt;
Select a released product &gt; on the Manage inventory Action Pane &gt;
Order settings &gt; Default order settings. 

The quantity limits for products sold are set based on the 'Default
Order Settings' in the 'Sales order' tab.

To learn more about the Product dimensions and default order settings
please review: [*Default order settings for dimensions and product
variants*](https://docs.microsoft.com/en-us/dynamics365/supply-chain/pim/product-dimensions)

## Turn on the Minimum / Maximum / Multiple / Standard Order Quantity

For e-Commerce: Select the "Enable Order Quantity Limits" feature in the
'eCommerce Site Builder', under the 'Site settings' 

-   Use the HQ settings to enable the quantity limits based on the
    'Default Quantity Settings'

-   Minimum Order Quantity: Minimum number of products that needs to be
    purchased

-   Maximum Order Quantity: Maximum limit for products that needs to be
    purchased

-   Multiple Order Quantity: Product can be bought in multiples of this
    quantity.

-   Default Order Settings: The default quantities that should be set
    when the product is selected.

NOTE: The new 'site settings' will only be available after the
App.Settings.Jason file has been updated. Please follow this below
link: [*SDK and Module library
updates*](https://docs.microsoft.com/en-us/dynamics365/commerce/e-commerce-extensibility/sdk-updates)

# Supported flows

-   Product quantity restriction for e-commerce sites

# Unsupported flows

-   Point of Sale is currently not supported.

-   Call center is currently not supported.

# Use case examples

1. **Default Setting Minimum/Maximum quantity limits per product**

-   For the Default '0' Rank, set the limits for the Maximum / Minimum /
    Default / Standard Order Quantity 

1. **Setting quantity limits per product variant** or \**Overriding
    "Default Site Settings"*

-   If you would like to set quantity limits based on specific variants
    or site 

    -   create a new rank-based setting and click override setting based
        on the variant selected.

    -   settings with higher rank are respected on the quantity limits


