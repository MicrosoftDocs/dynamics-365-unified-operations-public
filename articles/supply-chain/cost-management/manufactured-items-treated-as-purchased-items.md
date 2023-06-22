---
# required metadata

title: Set up products that can be produced or procured
description: Products can be sourced in various ways -  they can be produced (manufactured) or procured (purchased). This article describes some typical points to consider when you configure products to support multi-sourcing. 
author: JennySong-SH
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: ReqGroup, ReqItemTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.assetid: acc608b7-2cad-4fba-afee-9b7cc93761ec
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: yanansong
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Set up products that can be produced or procured

[!include [banner](../includes/banner.md)]

Products can be sourced in various ways -  they can be produced (manufactured) or procured (purchased). This article describes some typical points to consider when you configure products to support multi-sourcing. 

Multi-sourcing is typically used for a purchased item that is occasionally manufactured, or when an item that was primarily a manufactured item is changed so that it's now primarily a purchased item. The item is first designated as a manufactured item, so that bill of materials (BOM) and route information can be defined, and to support production orders for the item. The production type should be set to **BOM** (or, for process manufacturing, **Formula** or **Co-Product**).

When you use standard cost, the item cost record can be calculated for the manufactured item. However, the item cost record might not match the standard cost that you want for purchasing purposes. In this case, the standard cost must be manually entered and activated for the item cost record. For the cost calculation, consider using a special BOM and route that represent the supply mix of the product over the course of a fiscal period, to minimize the variances over time. Additionally, a manufactured item at one site can be transferred to another site. Therefore, the item's cost must be manually entered and activated for the site that the item is transferred to. When you use the manufactured item as a component in higher-level products, the component's costs should be treated as a purchased item. This guideline applies, regardless of whether the component’s costs were calculated or manually entered. In other words, a BOM calculation should treat the item's costs as a purchased component instead of using the item's BOM and route information to calculate costs. 

To prevent the calculation from occurring, select the **Stop explosion** flag that is embedded in the BOM calculation group that is assigned to the item. To prevent master scheduling calculations from exploding requirements through the item, set the explosion fence to 0 (zero) days in item coverage or in the coverage group. The master scheduling calculation will then treat the item as a purchased item and won't perform more calculations for the item's BOM and route information.







[!INCLUDE[footer-include](../../includes/footer-banner.md)]