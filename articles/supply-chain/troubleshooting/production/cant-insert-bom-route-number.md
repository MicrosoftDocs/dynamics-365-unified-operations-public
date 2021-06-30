---
title: Can't insert active version of BOM and route numbers  
description: If the default site and warehouse are already defined for a selected product, you won't be prompted to insert the active version of BOM and route numbers. 
author: SmithaNataraj 
ms.date: 06/24/2021 
ms.topic: troubleshooting 
# ms.search.form:  
audience: Application User 
ms.reviewer: kamaybac 
ms.search.region: Global 
ms.author: smnatara 
ms.search.validFrom: 2021-06-24 
ms.dyn365.ops.version: 10.0.20 
--- 
 
# Can't insert bill of material and route when creating a new production order

## Symptoms

When you create a new production order, after you enter the item number, the **Site** and **Warehouse** fields are automatically set to the default site and warehouse that are defined on the **Default order settings** page for the finished goods item. Additionally, the active BOM number and route number are automatically entered, so you don't receive the following message that prompts you for those values:

> Insert active version for bill of material and route?

## Resolution

You aren't prompted to insert BOM and route numbers if you select a product for which a site and warehouse are already on the **Default order settings** page. You're prompted only if those values aren't defined for the selected product.
