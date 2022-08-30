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

This article explains how organizations could configure their e-commerce website product listing pages (such as category landing page, search results page) to be inventory aware.

## Overview

Shoppers generally expect product discovery throughout the e-commerce website to be inventory aware, so that they can decide what to do if a product is out-of-stock. In our [e-commerce module library](starter-kit-overview), the **category** and **search results** modules can be configured to incorporate inventory data and provide the following experiences:

- Display inventory level labels alongside products.
- Hide out-of-stock products from the product list.
- Display out-of-stock products at the end of the product list.
- Support inventory-based product filtering.

To enable these experiences, you must first enable the **Enhanced e-Commerce product discovery to be inventory-aware** feature in Commerce headquarters.

> [!NOTE]
> In Commerce version **10.0.29** and later, the **Enhanced e-Commerce product discovery to be inventory-aware** feature is enabled by default.

## Set up product attribute for inventory availability

Inventory-aware product listing leverages product attributes framework. As prerequisite, a dedicated product attribute needs to be created to capture inventory availability data. To do so, follow these steps in Commerce headquarters.

1. Go to **Retail and Commerce \> Retail and Commerce IT \> Products and inventory**.
1. Select **Populate product attributes with inventory level**.
1. In the prompt dialog, enter the following information:
   - On the **Product attribute and type name** field, specify a custom name for the dedicated product attribute that will be created to capture inventory data.
   - On the **Inventory availability based on** field, select a quantity type (**Available physical** or **Total available**) that the inventory level calculation should be based on.
   - Run the job as a **batch process**.

> [!NOTE]
> For a consistent inventory level calculation across pages on your e-commerce website, be sure to select the same quantity type for both the **Inventory availability based on** setting in **Populate product attributes with inventory level** job and the **Inventory level based on** setting in Commerce site builder.

After the dedicated product attribute is created, the next step is to configure the attribute for online channel. To do so, follow these steps in Commerce headquarters.

1. Go to **Retail and Commerce \> Channel setup \> Channel categories and product attributes**.
1. Select an online channel that you want to enable the inventory-aware product listing experience.
1. Select and open an associated attribute group, and then add the newly created product attribute to it.
1. Go to **Retail and Commerce \> Retail and Commerce IT \> Distribution schedule**, and run the **1150 (Catalog)** job. We recommend that you schedule the 1150 job as a batch process that runs at the same frequency as the **Populate product attributes with inventory level** job.

> [!NOTE]
> In Commerce version **10.0.26** and earlier, after adding the inventory availability product attribute to an attribute group, you need to additionally select **Set attribute metadata**, and then turn on the **Show attribute on channel**, **Retrievable**, **Can be refined**, and **Can be queried** options on the newly added product attribute.


## Configure out-of-stock product display behavior in product listing pages

After all the preceding configuration steps are completed, the refiners on category and search results page would have an inventory-based filter option, and each product tile displayed on the page would have an inventory level label displayed together with it. 

The category and search results page displays products at **master** level not variant level. Thus, the inventory level displayed alongside each product is an **aggregated** inventory level by considering the inventory level of all its variants. The inventory level of a variant is calculated based on the on-hand inventory of that variant in the **default warehouse** of the online channel in Commerce headquarters. The inventory level of a master product has two possible values that represent in-stock and out-of-stock. A master product is considered out-of-stock when all its variants are out-of-stock. Otherwise, it's considered in-stock. The actual label for the value is retrieved from the [inventory level](inventory-buffers-levels) definition. If no inventory level is defined, the default labels are **Available** and **Out of stock** in English language.

You can configure the **Inventory settings for product list pages** setting in Commerce site builder to control how the category and search results page displays out-of-stock products. For more information, see [Apply inventory settings](inventory-settings).

[!INCLUDE[footer-include](../includes/footer-banner.md)]
