---
title: Inventory-aware product listing
description: Learn how organizations can configure inventory-aware product listing pages on their Microsoft Dynamics 365 Commerce e-commerce sites.
author: boycez
ms.date: 01/23/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: chuzheng
ms.search.validFrom: 2022-08-23
ms.custom: 
  - bap-template
---

# Inventory-aware product listing

[!include [banner](../includes/banner.md)]

This article describes how organizations can configure inventory-aware product listing pages on their Microsoft Dynamics 365 Commerce e-commerce sites. Product listing pages include category landing pages and search results pages.

Shoppers generally expect product discovery throughout an e-commerce website to be inventory aware, so that they can decide what to do if a product is out of stock. The [Commerce module library](starter-kit-overview.md) category and search results modules can be configured to incorporate inventory data. By using these modules, you can provide the following experiences:

- Display inventory level labels alongside products.
- Hide out-of-stock products from the product list.
- Move out-of-stock products to the bottom of product list pages.
- Support inventory-based product filtering.

To enable these experiences, first enable the **Enhanced e-commerce product discovery to be inventory-aware** feature in Commerce headquarters.

> [!NOTE]
> - In Commerce version 10.0.29 and later, the **Enhanced e-commerce product discovery to be inventory-aware** feature is enabled by default.
> - Inventory-aware product listing is calculated in headquarters and doesn't use channel-side inventory calculation. Discrepancies can occur between these two features.

## Set up product attribute for inventory availability

Inventory-aware product listing uses the product attributes framework. As a prerequisite, create a dedicated product attribute to capture inventory availability data.

To set up product attribute for inventory availability in Commerce headquarters, follow these steps:

1. Go to **Retail and Commerce > Retail and Commerce IT > Products and inventory > Populate product attributes with inventory level**.
1. In the **Populate product attributes with inventory level** dialog box, in the **Product attribute and type name** field, enter a custom name for the dedicated product attribute that captures inventory data.
1. In the **Inventory availability based on** field, select the quantity type that the inventory level calculation should be based on: **Available physical** or **Total available**.
1. Set the **Batch processing** option to **Yes**.
1. Select **OK**.

> [!NOTE]
> For consistent inventory level calculation across the pages of your e-commerce website, ensure that you select the same quantity type in both the **Inventory availability based on** field for the **Populate product attributes with inventory level** job and the **Inventory level based on** setting in Commerce site builder.

After you create the dedicated product attribute, configure the attribute for the online channel.

To configure the attribute for the online channel in Commerce headquarters, follow these steps:

1. Go to **Retail and Commerce > Channel setup > Channel categories and product attributes**.
1. Select the online channel to enable the inventory-aware product listing experience.
1. Select and open an associated attribute group, and then add the new product attribute to it.
1. Go to **Retail and Commerce > Retail and Commerce IT > Distribution schedule**, and run the **1150** (**Catalog**) job. Schedule this job as a batch process that runs at the same frequency as the **Populate product attributes with inventory level** job.

> [!NOTE]
> In Commerce version 10.0.26 and earlier, after you add the inventory availability product attribute to an attribute group, you must also select **Set attribute metadata**, and then turn on the **Show attribute on channel**, **Retrievable**, **Can be refined**, and **Can be queried** options for the new product attribute.

## Configure the display behavior for out-of-stock products on product listing pages

After you complete all the preceding configuration steps, the refiners on category and search results pages include an inventory-based filter option. An inventory level label appears for each product tile on the page.

The category and search results page displays products at the product master level, not the product variant level. The inventory level that appears alongside each product is an aggregated inventory level that comes from the inventory level of all a product's variants. The inventory level of a variant comes from the on-hand inventory of that variant in the default warehouse of the online channel in Commerce headquarters. The inventory level of a product master has two possible values that represent in-stock and out-of-stock states. A product master is out of stock when all its variants are out of stock. Otherwise, the product is in stock. The label for the value comes from the [inventory level](inventory-buffers-levels.md) definition. If no inventory level is defined, the default labels (in English) are **Available** and **Out of stock**.

You can configure the **Inventory settings for product list pages** setting in Commerce site builder to control how the category and search results page displays out-of-stock products. For more information, see [Apply inventory settings](inventory-settings.md).

### Choosing the right out-of-stock display behavior for your channel

The decision to hide out-of-stock products versus moving them to the bottom of a 
product listing page depends on how your customers behave and how your catalog is 
structured.

For retailers selling products with strong brand or model loyalty, hiding 
out-of-stock items entirely is often the more effective approach. When a 
best-selling model goes out of stock, customers who are attached to that specific 
product tend to wait for it to return rather than switching to an alternative. 
Keeping it visible on the listing page reinforces that attachment and draws 
attention away from models that are actually available. Removing it from the list 
redirects that browsing traffic toward in-stock alternatives, which keeps sales 
moving and prevents the listing page from becoming a source of frustration.

Displaying out-of-stock products also risks a negative customer experience. 
Shoppers who click through to a product detail page only to find it unavailable 
often leave the site without purchasing anything. In contrast, a listing page that 
shows only available products gives customers a cleaner path to purchase.

A practical approach for this scenario is to hide out-of-stock products by 
setting them to draft status when stock is depleted, then reactivating them once 
inventory is replenished. This keeps the listing page focused on what customers 
can actually buy, while ensuring that high-demand products return to full 
visibility as soon as stock is available again.

For products where customers are more flexible about which variant or model they 
choose, moving out-of-stock items to the bottom of the list may be sufficient, 
as it preserves catalog visibility without disrupting the shopping experience.
   
[!INCLUDE[footer-include](../includes/footer-banner.md)]
