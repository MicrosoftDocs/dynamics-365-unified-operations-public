
---
# Enhanced product and category management

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


# Enhanced product and category management

[!include[banner](./includes/banner.md)]

This topic describes the enhanced way of managing Retail product categories and products in Dynamics 365 for Retail. These enhancements let merchandising managers to view a common structure of product properties between Retail product hierarchy and released product details form of this solution.

To learn more about enhanced way of managing Retail product categories we will navigate to **Retail product hierarchy ** from **Category & product management**  workspace, and notice the **enhanced structure of Retail product category page**.

![Category & product management workspace](media/LaunchRetailProductHierarchy.png)

In the previous version, product properties were divided into **Basic product properties** and **Retail product properties**, based on the **scope of their applicability**. **Retail product properties** were **global** by scope of applicability, which means that for a given **Retail product property**, the same value is **shared across all legal entities**. Whereas, **Basic product properties** are **legal entity specific**. In other words, for a given **Basic product property** it's value can differ across legal entities, based on individual business requirements.

In the new **enhanced** structure of Retail product category, **product properties** continue to be **logically separated** based on their applicability within a group, to reflect the released product details form structure.

![Grouping of fields based on their scope of applicability](media/NoticeGroupingOfFieldsBasedOnTheirScope.PNG)

You can switch between managing legal-entity specific properties across all legal entities and managing them for a specific legal entity. To do this, select either **View/Edit for all legal entities** or **View/Edit for a specific legal entity**.

![Toggle view between an individual and all Legal entities](media/ToggleBackToEditForSpecificLegalEntity.PNG)

![Toggle view between an individual and all Legal entities](media/ToggleToEditForAllLegalEntities.PNG)  

Compared to the previous version, in the **new Retail product category structure** a merchandising manager can also define **default values** for an **additional set of product properties** at an individual category level. At time product creation these default product property values are inherited by a product, based on their association with an individual category from Retail product hierarchy. And these inherited product properties can be modified for each product, to meet individual business requirements.

## New style to select properties to update products from the Retail product category form 
 
You can use this new enhanced structure for product properties to select which updated product properties must be pushed to associated products. 

![New enhanced view of Update products](media/NewUpdateProductsEnhancedView.PNG) 





