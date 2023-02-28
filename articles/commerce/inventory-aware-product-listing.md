---
# required metadata

title: Inventory-aware product listing
description: This article describes how organizations can configure product listing pages on their Microsoft Dynamics 365 Commerce e-commerce websites so that they are inventory aware.
author: boycez
ms.date: 01/30/2023
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: boycez
ms.search.validFrom: 2022-08-23

---

# Inventory-aware product listing

[!include [banner](../includes/banner.md)]

This article describes how organizations can configure product listing pages on their Microsoft Dynamics 365 Commerce e-commerce websites so that they are inventory aware. Product listing pages include category landing pages and search results pages.

Shoppers generally expect product discovery throughout an e-commerce website to be inventory aware, so that they can decide what to do if a product is out of stock. The [Commerce module library](starter-kit-overview.md) category and search results modules can be configured to incorporate inventory data. In this way, they can provide the following experiences:

- Display inventory level labels alongside products.
- Hide out-of-stock products from the product list.
- Move out-of-stock products to the bottom of product list pages.
- Support inventory-based product filtering.

To enable these experiences, you must first enable the **Enhanced e-Commerce product discovery to be inventory-aware** feature in Commerce headquarters.

> [!NOTE]
> - In Commerce version 10.0.29 and later, the **Enhanced e-Commerce product discovery to be inventory-aware** feature is enabled by default.
> - Inventory-aware product listing is calculated in headquarters and doesn't use channel-side inventory calculation. Discrepancies can occur between these two features.

## Set up product attribute for inventory availability

Inventory-aware product listing uses the product attributes framework. As a prerequisite, a dedicated product attribute must be created to capture inventory availability data.

To set up product attribute for inventory availability in Commerce headquarters, follow these steps.

1. Go to **Retail and Commerce \> Retail and Commerce IT \> Products and inventory \> Populate product attributes with inventory level**.
1. In the **Populate product attributes with inventory level** dialog box, in the **Product attribute and type name** field, enter a custom name for the dedicated product attribute that will be created to capture inventory data.
1. In the **Inventory availability based on** field, select the quantity type that the inventory level calculation should be based on: **Available physical** or **Total available**.
1. Set the **Batch processing** option to **Yes**.
1. Select **OK**.

> [!NOTE]
> For consistent inventory level calculation across the pages of your e-commerce website, ensure that you select the same quantity type in both the **Inventory availability based on** field for the **Populate product attributes with inventory level** job and the **Inventory level based on** setting in Commerce site builder.

After the dedicated product attribute is created, the next step is to configure the attribute for the online channel.

To configure the attribute for the online channel in Commerce headquarters, follow these steps.

1. Go to **Retail and Commerce \> Channel setup \> Channel categories and product attributes**.
1. Select the online channel to enable the inventory-aware product listing experience for.
1. Select and open an associated attribute group, and then add the new product attribute to it.
1. Go to **Retail and Commerce \> Retail and Commerce IT \> Distribution schedule**, and run the **1150** (**Catalog**) job. We recommend that you schedule this job as a batch process that runs at the same frequency as the **Populate product attributes with inventory level** job.

> [!NOTE]
> In Commerce version 10.0.26 and earlier, after you add the inventory availability product attribute to an attribute group, you must also select **Set attribute metadata**, and then turn on the **Show attribute on channel**, **Retrievable**, **Can be refined**, and **Can be queried** options for the new product attribute.

## Configure the display behavior for out-of-stock products on product listing pages

After all the preceding configuration steps are completed, the refiners on category and search results pages will have an inventory-based filter option. An inventory level label will be displayed for each product tile that appears on the page.

The category and search results page displays products at the master level, not the product variant level. The inventory level that is displayed alongside each product is an aggregated inventory level that is determined by the inventory level of all a product's variants. The inventory level of a variant is calculated based on the on-hand inventory of that variant in the default warehouse of the online channel in Commerce headquarters. The inventory level of a master product has two possible values that represent in-stock and out-of-stock states. A master product is considered out of stock when all its variants are out of stock. Otherwise, the product is considered in stock. The label for the value is retrieved from the [inventory level](inventory-buffers-levels.md) definition. If no inventory level is defined, the default labels (in English) are **Available** and **Out of stock**.

You can configure the **Inventory settings for product list pages** setting in Commerce site builder to control how the category and search results page displays out-of-stock products. For more information, see [Apply inventory settings](inventory-settings.md).

[!INCLUDE[footer-include](../includes/footer-banner.md)]
