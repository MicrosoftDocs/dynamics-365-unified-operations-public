---
# required metadata

title: Inventory-aware product listing
description: This article explains how organizations could configure their e-commerce website product listing pages to be inventory aware.
author: boycez
ms.date: 08/23/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail, Commerce
ms.author: boycez
ms.search.validFrom: 2022-08-23
ms.dyn365.ops.version: Application update 10.0.29

---

# Inventory-aware product listing

This article explains how organizations could configure their e-commerce website product listing pages to be inventory aware.

## Overview

Shoppers generally expect the product listing pages in an e-commerce website to be inventory aware, so that they can decide what to do if a product is out of stock. In our [e-commerce module library](https://docs.microsoft.com/dynamics365/commerce/starter-kit-overview), the **category** and **search results** modules can be configured to incorporate inventory data and provide the following experiences:

- Show an inventory availability label together with the product.
- Hide out-of-stock products from the product list.
- Show out-of-stock products at the end of the product list.
- Filter products in search results by inventory level.

To enable these experiences, you must first enable the **Enhanced e-Commerce product discovery to be inventory-aware** feature in the **Feature management** workspace.

## Create product attributes for inventory availability

Inventory-aware product listing leverages product attributes framework to source inventory availability information. As a prerequisite for the feature, you need to create dedicated product attributes for inventory availability and populate the attributes with calculated inventory level data. Follow these steps in Commerce headquarters.

1. Go to **Retail and Commerce \> Retail and Commerce IT \> Products and inventory**.
1. Select and open **Populate product attributes with inventory level**.
1. In the dialog box, enter the following information:
   - In the **Product attribute and type name** field, specify a name for the dedicated product attribute that will be created to capture inventory data.
   - In the **Inventory availability based on** field, select the quantity type that the inventory level calculation should be based on. This field currently supports two quantity types: **Available physical** and **Total available**.
   - Run the job in the background as a **batch process**.

> [!NOTE]
> For a consistent inventory level calculation across pages and modules on your e-commerce website, be sure to select the same quantity type for both the **Inventory availability based on** setting in Commerce headquarters and the **Inventory level based on** setting in Commerce site builder.

## Configure inventory availability product attributes for online channel

After the dedicated product attributes are created, the next step is to configure the attributes for online channel. Follow these steps in Commerce headquarters.

1. Go to **Retail and Commerce \> Channel setup \> Channel categories and product attributes**.
1. Select an online channel to enable the inventory-aware search results module for.
1. Select and open an associated attribute group, and then add the newly created product attribute to it.
1. In Commerce version **10.0.26** and earlier, select **Set attribute metadata**, select the newly added product attribute, and then turn on the **Show attribute on channel**, **Retrievable**, **Can be refined**, and **Can be queried** options.
1. Go to **Retail and Commerce \> Retail and Commerce IT \> Distribution schedule**, and run the **1150 (Catalog)** job. We recommend that you schedule the 1150 job as a batch process that runs at the same frequency as the **Populate product attributes with inventory level** job.

## Configure desired display behavior of out-of-stock products in product listing pages

After all the preceding configuration steps are completed, the refiners on category and search results page would have an inventory-based filter, and each product displayed on the page would have an inventory level label displayed together with it. 

The category and search results page displays products at master level not variant level. Thus, the inventory level displayed together with the product is an **aggregated** inventory level by considering the inventory level of all its variants. The inventory level of a variant is calculated based on the on-hand inventory of that variant in the default warehouse of the online channel in Commerce headquarters. The inventory level of a master has two possible values that represent in stock and out of stock. A master product is considered out of stock when all its variants are out of stock. The actual label for the value is retrieved from the [inventory level]( https://docs.microsoft.com/dynamics365/commerce/inventory-buffers-levels) definition. If no inventory level is defined, the default labels are **Available** and **Out of stock**.

You can then configure the **Inventory settings for product list pages** setting in Commerce site builder to control how the category and search results page displays out-of-stock products. For more information, see [Apply inventory settings](https://docs.microsoft.com/dynamics365/commerce/inventory-settings)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
