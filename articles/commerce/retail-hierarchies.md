---
title: Commerce hierarchies
description: This article describes hierarchies in Dynamics 365 Commerce.
author: josaw1
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: josaw
ms.search.region: global
ms.author: josaw
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update
ms.assetid: dfa11d41-2a0c-4cde-99b6-058c49176c94
ms.search.industry: Retail
ms.search.form: OMHierarchyManager, EcoResCategoryHierarchyFactbox
---

# Commerce hierarchies

[!include [banner](includes/banner.md)]

This article describes hierarchies in Dynamics 365 Commerce.

You can create a category hierarchy to organize the products that you sell through your channels. You can use product hierarchies to categorize or group products. You can then use these products to create product assortments and customer loyalty programs. You can also assign product attributes and properties, assign a pricing structure, include the products in product promotions, and use the products for reporting. You can create one category hierarchy to represent all the products and categories in your organization, and then use that category hierarchy for multiple purposes. Alternatively, you can create multiple category hierarchies for special purposes, such as product promotions. When you create a product hierarchy, you must assign a category hierarchy type to identify the purpose of the category hierarchy. For example, only product hierarchies that are assigned the **Commerce navigation hierarchy** type are referenced when you browse products by category online or in point of sale (POS).

## Hierarchy types

The following table lists the types of category hierarchies that are available and the general purpose of each type.

| Category hierarchy type       | Purpose |
|-------------------------------|---------|
| Product hierarchy      | Use this hierarchy type to define the overall product hierarchy for your organization. You can use this hierarchy type for merchandising, pricing and promotions, reporting, and assortment planning. Only one product hierarchy can be assigned this hierarchy type. |
| Supplemental hierarchy | Use this hierarchy type for any additional category hierarchies that you want to create. For example, in the spring, you have a promotion for swimwear. Therefore, you include your swimwear products in a separate category hierarchy and apply the promotional pricing to the various product categories. |
| Navigation hierarchy   | Use this hierarchy type to group and organize products into categories so that the products can be browsed online or in POS. |

By using a category hierarchy to structure your products, you can set up and maintain product attributes and properties at the category level. These attributes and properties include settings for product dimensions and POS settings. Any products that you assign to the categories automatically inherit the attributes and properties that you define. You can also copy the property settings for any product to multiple products in a selected category at the same time.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
