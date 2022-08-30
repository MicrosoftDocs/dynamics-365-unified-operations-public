---
# required metadata

title: Inventory-aware product listing
description: This article describes how organizations can configure their Microsoft Dynamics 365 Commerce e-commerce website product listing pages to be inventory aware.
author: boycez
ms.date: 08/30/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: boycez
ms.search.validFrom: 2022-08-23

---

# Inventory-aware product listing

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This article describes how organizations can configure their Microsoft Dynamics 365 Commerce e-commerce website product listing pages (such as category landing and search results pages) to be inventory aware.

Shoppers generally expect product discovery throughout an e-commerce website to be inventory aware, so that they can decide what to do if a product is out of stock. In the [Commerce module library](starter-kit-overview.md), the category and search results modules can be configured to incorporate inventory data to allow the following experiences:

- Display inventory level labels alongside products.
- Hide out-of-stock products from the product list.
- Move out-of-stock products to the bottom of product list pages.
- Support inventory-based product filtering.

To enable these experiences, you must first enable the **Enhanced e-Commerce product discovery to be inventory-aware** feature in Commerce headquarters.

> [!NOTE]
> In Commerce version 10.0.29 and later, the **Enhanced e-Commerce product discovery to be inventory-aware** feature is enabled by default.

## Set up product attribute for inventory availability

Inventory-aware product listing uses the product attributes framework. As a prerequisite, a dedicated product attribute must be created to capture inventory availability data. 

To set up product attribute for inventory availability in Commerce headquarters, follow these steps.

1. Go to **Retail and Commerce \> Retail and Commerce IT \> Products and inventory**.
1. Select **Populate product attributes with inventory level**.
1. In the dialog box, enter the following information:
    1. For **Product attribute and type name**, specify a custom name for the dedicated product attribute that will be created to capture inventory data.
    1. For **Inventory availability based on** field, select a quantity type (**Available physical** or **Total available**) that the inventory level calculation should be based on.
    1. Run the job as a **batch process**.

> [!NOTE]
> For a consistent inventory level calculation across the pages of your e-commerce website, be sure to select the same quantity type for both the **Inventory availability based on** setting in **Populate product attributes with inventory level** job and the **Inventory level based on** setting in Commerce site builder.

After the dedicated product attribute is created, the next step is to configure the attribute for online channel. 

To configure the attribute for online channel in Commerce headquarters, follow these steps.

1. Go to **Retail and Commerce \> Channel setup \> Channel categories and product attributes**.
1. Select an online channel for which you want to enable the inventory-aware product listing experience.
1. Select and open an associated attribute group, and then add the newly-created product attribute to it.
1. Go to **Retail and Commerce \> Retail and Commerce IT \> Distribution schedule**, and run the **1150 (Catalog)** job. It is recommended that you schedule the 1150 job as a batch process that runs at the same frequency as the **Populate product attributes with inventory level** job.

> [!NOTE]
> In Commerce version 10.0.26 and earlier, after adding the inventory availability product attribute to an attribute group, you must also select **Set attribute metadata** and then turn on the **Show attribute on channel**, **Retrievable**, **Can be refined**, and **Can be queried** options on the newly-added product attribute.

## Configure out-of-stock product display behavior on product listing pages

After all of the preceding configuration steps are completed, the refiners on category and search results pages will have an inventory-based filter option, and each product tile displayed on the page will have an inventory level label displayed with it. 

The category and search results page displays products at the master level and not the product variant level. The inventory level displayed alongside each product is an aggregated inventory level determined by the inventory level of all a product's variants. The inventory level of a variant is calculated based on the on-hand inventory of that variant in the default warehouse of the online channel in Commerce headquarters. The inventory level of a master product has two possible values that represent in-stock and out-of-stock states. A master product is considered to be out of stock when all of its variants are out of stock. Otherwise, the product is considered to be in stock. The actual label for the value is retrieved from the [inventory level](inventory-buffers-levels.md) definition. If no inventory level is defined, the default labels are **Available** and **Out of stock** (in English).

You can configure the **Inventory settings for product list pages** setting in Commerce site builder to control how the category and search results page displays out-of-stock products. For more information, see [Apply inventory settings](inventory-settings.md).

[!INCLUDE[footer-include](../includes/footer-banner.md)]
