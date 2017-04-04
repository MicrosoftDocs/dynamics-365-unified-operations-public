---
# required metadata

title: Retail hierarchies
description: This article describes retail hierarchies in Microsoft Dynamics AX.
author: josaw1
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: annbe
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 15851
ms.assetid: dfa11d41-2a0c-4cde-99b6-058c49176c94
ms.search.region: global
ms.search.industry: Retail
ms.author: jeffbl
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Retail hierarchies

This article describes retail hierarchies in Microsoft Dynamics AX.

You can create a retail category hierarchy to organize the products that you sell through your retail channels. You can use retail product hierarchies to categorize or group products. You can then use these products to create product assortments and customer loyalty programs. You can also assign product attributes and properties, assign a pricing structure, include the products in product promotions, and use the products for reporting. You can create one retail category hierarchy to represent all the products and categories in your organization, and then use that category hierarchy for multiple purposes. Alternatively, you can create multiple retail category hierarchies for special purposes, such as product promotions. When you create a retail product hierarchy, you must assign a category hierarchy type to identify the purpose of the category hierarchy. For example, only product hierarchies that are assigned the **Retail navigation hierarchy** type are referenced when you browse products by category online or in point of sale (POS).

## Retail hierarchy types
The following table lists the types of retail category hierarchies that are available and the general purpose of each type.

| Category hierarchy type       | Purpose                                                                                                                                                                                                                                                                                                            |
|-------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Retail product hierarchy      | Use this hierarchy type to define the overall product hierarchy for your organization. You can use this hierarchy type for merchandising, pricing and promotions, reporting, and assortment planning. Only one retail product hierarchy can be assigned this hierarchy type.                                       |
| Supplemental retail hierarchy | Use this hierarchy type for any additional retail category hierarchies that you want to create. For example, in the spring, you have a promotion for swimwear. Therefore, you include your swimwear products in a separate category hierarchy and apply the promotional pricing to the various product categories. |
| Retail navigation hierarchy   | Use this hierarchy type to group and organize products into categories so that the products can be browsed online or in POS.                                                                                                                                                                                       |

By using a retail category hierarchy to structure your products, you can set up and maintain product attributes and properties at the category level. These attributes and properties include settings for product dimensions and POS settings. Any products that you assign to the categories automatically inherit the attributes and properties that you define. You can also copy the property settings for any product to multiple products in a selected category at the same time.

