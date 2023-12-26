---
# required metadata

title: Material substitution in manufacturing
description: This article describes how to substitute materials during the production process. 
author: johanhoffmann
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: ProdBOM
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.assetid: ce3b11ef-550e-49b7-8942-2607c2ec3c5c
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: johanho
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Material substitution in manufacturing

[!include [banner](../includes/banner.md)]

This article describes how to substitute materials during the production process. 

There are three methods for substituting materials during the production process:

-   By date, when one material is substituted for another after a specific date
-   During master planning, when a material in a formula is substituted with a different material, because it's out of stock
-   During production, when a material is unexpectedly out of stock and is substituted with a different material

## Substituting material by date
Consider following scenario: A machine that a company is manufacturing contains a component that will expire from the vendor's catalog in two months. From the expiration date onward, the vendor will offer a new component that can be substituted for the old component. From and to validity dates can be set up on bill of materials (BOM) lines. For this example, you set up the old component to expire by entering the expiration date in the **To-date** field. Then, on the BOM, you set up the new, replacement component so that it's valid from the day after the old component expires. To do this, enter the start date in the **From-date** field.

## Substituting material by planning
You can substitute materials during planning only when you're using formulas, not when you're using a BOM. Consider following scenario: A food manufacturing company is making a sauce from a formula that has 20 ingredients. One ingredient in the formula can be substituted by one of two other ingredients. However, because these two ingredients are more expensive than the preferred ingredient, substitution is used only if the preferred ingredient is out of stock. The material that can be substituted is called A, whereas the two materials that can replace it are called B and C. Material substitution by planning is controlled by the **Plan group** and **Priority** fields on the formula lines. For this example, you create formula lines for the three materials, and associate the formula lines with the same plan group. In the setup, the formula line for material A has the highest priority (lowest number), the formula line for material C has the lowest priority, and the formula line for material B has a priority that is between the priority of the other two lines. If you have demand for the finished item, master planning first determines whether the demand for material A can be covered. If the demand can't be covered, master planning looks at materials B and C, in order of priority. If material B is on hand, it will be used after a planned batch order is firmed for the formula. If none of the materials are on hand, master planning creates a planned order for material A. **Note:** When you set up formula lines in a plan group, you should specify a quantity only on the material that has the highest priority. This quantity will be used to calculate the demand of all materials in the plan, even the materials that have lower priority. You can't specify different quantities on lower-priority items in the plan group.

## Substituting material during production
Consider the following scenario: A piece of metal plate is required for a welding operation. During the operation, a warehouse worker informs the machine operator that the plate is out of stock. However, it's decided that the plate can be substituted with a plate that is slightly thicker. That way, the operation can be finalized. Material can be added to the BOM for an open production order. If the production order has a status of **Started**, users are asked to re-estimate the order when they add a new item to the production BOM. After the material is added, a new picking list can be created for the new item. You don't have to add the new material to the production BOM. Instead, you can add it directly to the production picking list. Then, when the picking list is posted, the system adds the material to the production BOM.





[!INCLUDE[footer-include](../../includes/footer-banner.md)]