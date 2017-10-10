
---
# Product category management

title: Product category management 
description: This topic describes how merchandising managers can use Retail product categories to manage relationships between Retail product hierarchy and released product details. 
author: ashishmsft
manager: AnnBe
ms.date: 09/01/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, AX 7.0.0, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: Global
# ms.search.industry: retail
ms.author: asharchw
ms.search.validFrom: 2017-09-01
ms.dyn365.ops.version: 
---

# Product category management

[!include[banner](./includes/banner.md)]

Merchandising managers can use Retail product categories to manage relationships between Retail product hierarchy and released product details. To view product categories, in the **Category & product management**  workspace, select **Retail product hierarchy** to open the **New structure of Retail product category** page. 

![Category & product management workspace](media/LaunchRetailProductHierarchy.png)

Product properties are divided into basic product properties and Retail product properties, based on the scope of their applicability. Retail product properties are *global*, which means that for a given product property, the same value is shared across all legal entities. Basic product properties are *legal entity–specific*. In other words, a given product property might differ across legal entities, based on individual business requirements.

For product properties in the Retail product category, the fields are separated based on their applicability within a group, to reflect the released product details form structure.

![Grouping of fields based on their scope of applicability](media/NoticeGroupingOfFieldsBasedOnTheirScope.PNG)

You can switch between managing legal-entity specific properties across all legal entities and managing them for a specific legal entity. To do this, select either **View/Edit for all legal entities** or **View/Edit for a specific legal entity**.

![Toggle view between an individual and all Legal entities](media/ToggleBackToEditForSpecificLegalEntity.PNG)

![Toggle view between an individual and all Legal entities](media/ToggleToEditForAllLegalEntities.PNG)  

Merchandising managers can also define default values for an additional set of product properties at the individual category level. These property values are inherited by a product, based on their association with a category at the time of product creation. These inherited product properties can be modified for each product, to meet individual business requirements.

## Select properties to update products

You can use logical grouping properties to select which updated product properties should be pushed to associated products. 

![New enhanced view of Update products](media/NewUpdateProductsEnhancedView.PNG)


