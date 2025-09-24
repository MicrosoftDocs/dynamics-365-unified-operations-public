---
title: Material substitution in manufacturing
description: Learn how to substitute materials during the production process, including outlines on substituting material by date and substituting material by planning. 
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form: ProdBOM
ms.topic: how-to
ms.date: 09/19/2025
ms.custom:
  - bap-template
---

# Material substitution in manufacturing

[!include [banner](../includes/banner.md)]

This article describes how to substitute materials during the production process. There are three methods for doing so:

- By date, when one material is substituted for another after a specific date
- During master planning, when a material in a formula is substituted with a different material because it's out of stock
- During production, when a material is unexpectedly out of stock and is substituted with a different material

## Substituting material by date

Consider the following scenario: A machine that a company is manufacturing contains a component that expires from the vendor's catalog in two months. From the expiration date onward, the vendor offers a new component that you can substitute for the old component. Set up **From** and **To** validity dates on bill of materials (BOM) lines. For this example, set up the old component to expire by entering the expiration date in the **To-date** field. Then, on the BOM, set up the new replacement component so that it's valid from the day after the old component expires. To do this, enter the start date in the **From-date** field.

## Substituting material by planning

You can substitute materials during planning only when you're using formulas, not when you're using a BOM. Consider the following scenario: A food manufacturing company is making a sauce from a formula that has 20 ingredients. One ingredient in the formula can be substituted by one of two other ingredients. However, because these two ingredients are more expensive than the preferred ingredient, substitution is used only if the preferred ingredient is out of stock. The material that you can substitute is called A, whereas the two materials that can replace it are called B and C. Material substitution by planning is controlled by the **Plan group** and **Priority** fields on the formula lines. For this example, you create formula lines for the three materials, and associate the formula lines with the same plan group. In the setup, the formula line for material A has the highest priority (lowest number), the formula line for material C has the lowest priority, and the formula line for material B has a priority that is between the priority of the other two lines. If you have demand for the finished item, master planning first determines whether the demand for material A can be covered. If the demand can't be covered, master planning looks at materials B and C, in order of priority. If material B is on hand, it will be used after a planned batch order is firmed for the formula. If none of the materials are on hand, master planning creates a planned order for material A. 

> [!TIP]
> When you set up formula lines in a plan group, specify a quantity only on the material that has the highest priority. This quantity calculates the demand of all materials in the plan, even the materials that have lower priority. You can't specify different quantities on lower-priority items in the plan group.

## Substituting material during production

Consider the following scenario: A piece of metal plate is required for a welding operation. During the operation, a warehouse worker informs the machine operator that the plate is out of stock. However, it's decided that the plate can be substituted with a plate that is slightly thicker. That way, the operation can be finalized. You can add the material to the production picking list. Then, when the picking list is posted, the system adds the material to the production BOM.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
