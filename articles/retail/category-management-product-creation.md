---
# Product category management and creation

title: Product category management and creation
description: This topic describes the enhancements that have been made to the management experience for Retail product categories. These enhancements let merchandising managers have a correlation between Retail product hierarchy and released product details.
author: ashishmsft
manager: AnnBe
ms.date: 09/01/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-retail
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
# ms.reviewer: josaw
ms.search.scope: Core, Retail
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: retail
ms.author: asharchw
ms.search.validFrom: 2017-09-01
ms.dyn365.ops.version: 
---

# Product category management and creation

[!include[banner](./includes/banner.md)]

Enhancements that have been made to the management experience for Retail product categories let merchandising managers have a correlation between Retail product hierarchy and released product details. To view these enhancements, in the **Category & product management**  workspace, select **Retail product hierarchy** to open the **New structure of Retail product category** page. 

In previous releases, product properties were divided into Basic product properties and Retail product properties, based on the scope of their applicability. Retail product properties were *global*. In other words, for a given product property, the same value is shared across all legal entities. Basic product properties were *legal entity–specific*. In other words, a given product property might differ across legal entities, based on individual business requirements.

With these enhancements, for product properties in the Retail product category, we continue to separate the fields, based on their applicability within a group, to reflect the released product details form structure.

You can switch between managing legal-entity specific properties across all legal entities and managing them for a specific legal entity. Just select **View/Edit for all legal entities** or **View/Edit for a specific legal entity** as you require.

Merchandising managers can also define default values for an additional set of product properties at the level of an individual category. These property values are inherited by a product, based on their association with a category at the time of product creation.

## Select properties to update products from the Retail product category form

You can use logical grouping properties to select which updated product properties should be pushed to associated products.

Merchandising managers can modify these inherited product properties for each product, to meet individual business requirements.
