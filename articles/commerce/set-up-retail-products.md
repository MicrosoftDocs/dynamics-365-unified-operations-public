---
title: Set up retail products
description: Learn how to set up retail products in Microsoft Dynamics 365 Commerce.
author: josaw1
ms.date: 09/03/2025
ms.topic: how-to
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2016-02-28
ms.assetid: b1b57734-1406-4ed6-8e28-21c705ee17e2
ms.search.form: RetailProductAndCategoryWorkspace, EcoResProductDetails
---

# Set up retail products

[!include [banner](includes/banner.md)]

This article explains how to set up retail products in Microsoft Dynamics 365 Commerce.

Before you can offer products for resale in your commerce channels, you must create and configure the products. Commerce creates organization-wide products in the product master. You can create the products, define the product properties and attributes, and assign the products to commerce category hierarchies. To make the products available to your channels and add them to an active assortment, you must release the products to the legal entities where they're available. To set up the products that you sell by using channels, complete the following tasks.

1. **Define a product hierarchy** - By using the category hierarchy features in Commerce, you can define category hierarchies to group and categorize the products that you distribute to your channels. User-defined and system attributes can be defined at the category level. Then, all products that are assigned to the category inherit those attributes. Multiple category hierarchies can be defined, and each product can be assigned to multiple hierarchies. However, in a single hierarchy, each product can be assigned to only one category.
1. **Add products and product variants to the product master** - Products that are added to the product master represent a global list of products. You can add products manually, one at a time, or you can import product data from your vendors. Ensure that all product masters have at least one variant configured before they're made available for sale to avoid errors at a later stage.
1. **Release the products to legal entities** - Only products that are released to legal entities can be made available to your channels. When you first define a product, you define it on an organization-wide level. You can then select one or more legal entities to release the product to. The product then becomes available to multiple channels across your organization. You can use this functionality to create a product, add and update product attributes and properties, and then distribute the product to the channels where it's available across your organization.
1. **Add products to assortments** - An assortment represents a collection of products that you offer in your channels. You can define one or more assortments, and each product can be assigned to one or more assortments. To assign products to channels, you assign the assortments to those channels. When you create an assortment, you can add products that aren't yet been released to a legal entity. However, you must release the products to a legal entity before those products can be made available to the channels.
1. **Add products to navigation hierarchies** - Before products can be browsed online or in point of sale (POS), they must be categorized in a Commerce navigation hierarchy.
1. **Add products to catalogs** - Although this step is optional for POS, online stores require that products be included in at least one catalog.

> [!NOTE]
> Some configuration is required to make products discoverable in a channel. To confirm that products are set up correctly, refer to the [Product discovery checklist](product-discovery-checklist.md). You can also use the [Channel merchandising configuration validator](dev-itpro/channel-merch-config-validator.md) to validate configurations of all assorted products for a channel.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
