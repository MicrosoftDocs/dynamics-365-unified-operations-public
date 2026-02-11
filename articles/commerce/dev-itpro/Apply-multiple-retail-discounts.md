---
title: Apply multiple Retail discounts to a product
description: Learn about the factors considered when multiple discounts can be applied to a product in Microsoft Dynamics 365 Commerce.
author: ShalabhjainMSFT
ms.date: 02/11/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: global
ms.author: shajain
ms.search.validFrom: 2018-10-23
ms.assetid: b1b57734-1406-4ed6-8e28-21c705ee17e2
ms.custom: 
  - bap-template
---

# Apply multiple Retail discounts to a product

[!include [banner](../includes/banner.md)]

This article explains the factors considered when multiple discounts can be applied to a product in Microsoft Dynamics 365 Commerce.

In this scenario, the Commerce pricing engine applies as many discounts as it can, to maximize the total discount amount on a product. Multiple options affect the order in which the discounts are applied. Throughout this article, it's noted when a setting affects the order of discount application and exclusivity of a discount. The following settings affect how multiple discounts, applicable on a product, are processed.

- **Discount concurrency control model**
- **Pricing Priority**
- **Discount type** (**Simple**, **Mix and Match**, **Quantity**, and **Threshold**)
- **Discount concurrency mode** (**Exclusive**, **Best price**, and **Compound**)
- **Multiple occurrences mode**, when it's set to **Favor retailer** (for mix-and-match least-expensive discounts only)

The following section describes the **Discount concurrency control model** in detail. For the rest of the properties, see [Retail discounts](../retail-discounts-overview.md).

## Discount concurrency control model

The discount concurrency control model changes when and how multiple discounts are applied to products in a transaction. The **Best price and compound concurrency control model** option on the **Discounts** tab on the **Commerce parameters** page is different from the **Discount concurrency mode** property on each discount.

In earlier versions of the app, you could apply multiple discounts in only one way. That way depended on the **discount type**, **discount concurrency mode**, and **pricing priority** (if used) properties of discounts. Now, the discount concurrency control model setting affects how all discounts compete and compound together.

### Background on why this change was made

In previous versions of the app, you could directly customize the price engine by overlaying your custom business logic in the price engine. By transitioning to an online service and improving overall application lifecycle management, Microsoft sealed the Dynamics 365 application and no longer allows overlaying customizations. Microsoft added new extensibility points to enable the same types of customizations that were the most common. Most discount customizations fall into one of the following categories.

- **Minor changes to existing discounts:** For example, moving the start date and end date from the discount header to the discount lines.
- **New discount types:** In some cases, companies need to introduce a new type of discount. For example, capping the total discount amount for a simple discount.
- **Changing the when and how (the flow) of multiple discounts being applied:** For example, having all mix and match discounts applied on top of quantity or simple discounts while still having quantity and simple discounts compete for best price or having store-specific and customer-specific discounts compete for best price and then compound the winning discount with loyalty program discounts.

The first two types of customizations are handled by providing a new extensibility model within the price engine that enables these scenarios. To address the third type of customization, Microsoft expanded the functional capabilities of the system by introducing this setting. A discount's concurrency mode and pricing priority already gave you significant flexibility over the order of discount application. By introducing a new configuration setting that affects how a discount's concurrency mode and pricing priority interact, all discount ordering customization is covered, which results in the concurrency model option.

### Best price and compound within priority, never compound across priorities

This option is the default and is the legacy way in which multiple discounts are processed. When you select this option, the system combines all compound discounts within the same pricing priority, and the combined result competes with any best price discounts in the same pricing priority. After a discount is applied to a product, the system ignores all discounts at lower pricing priorities.

### Best price only within priority, always compound across priority

This option is the new way multiple discounts can be processed. When you select this option, the system treats discounts with **Discount concurrency mode** set to **Best price** and **Compound** as "best price" within a single pricing priority. When applied, the best price discount within a priority, is compounded with the best price and compound discounts at lower pricing priorities. In this concurrency control model, only a single discount can be applied to a product per pricing priority, and if that single discount is a best price or compound discount, then it compounds with all additional best price or compound discounts at lower pricing priorities.

### Examples

The following examples show how the pricing engine processes a pool of discounts for different concurrency control models.

#### Example 1

In the first scenario, you select **Best price and compound within priority, never compound across priorities** as the discount concurrency control model. The pricing engine has two pricing priorities. For each pricing priority, the engine has one discount of each discount type, such as **Simple**, **Mix and Match**, **Quantity**, and **Threshold**. Assume the engine has discounts at two priorities 5 and 10 and all products have multiple discounts at both these priorities. The price groups and discounts that can be applied to the product determine the pool of possible pricing priorities.

1. Given that you select a discount concurrency control model, for each product, the pricing engine next considers the highest pricing priority of the discounts that are applicable on the product. Thus, the pricing engine evaluates and applies the simple, quantity, and mix-and-match discounts with priority 10.

    > [!NOTE]
    > The pricing engine doesn't yet evaluate threshold discounts because, as indicated by their name, the evaluation happens against the transaction amount after all the other discounts are applied.

    The following image shows a concise view of how the pricing algorithm loops through the discounts across various priorities. This diagram applies for both the discount concurrency control models, but the difference is in the way in which the pricing algorithm treats discounts at different priorities. This difference is elaborated using the following example.

    :::image type="content" source="../media/Simplified-pricing-logic.png" alt-text="Screenshot of the simplified pricing logic flow for discount processing across priorities.":::

1. Within priority 10, the pricing engine first considers the discounts that have the concurrency mode set to **Exclusive**. If more than one exclusive discount applies to the product, the pricing engine applies the best exclusive discount. When a product gets an exclusive discount, no other discounts can be applied to this product at any priority.

    > [!NOTE]
    > The pricing engine skips mix-and-match, least-expensive discounts that have the **Multiple occurrences mode** property set to **Favor retailer** in this step. After the pricing engine applies all the **Exclusive** discounts (**Simple**, **Quantity**, **Mix and Match**) at pricing priority 10, it applies the exclusive mix-and-match **Favor retailer** discounts, at pricing priority 10, to any undiscounted products.

1. Within priority 10, the pricing engine then considers the discounts that have the discount concurrency mode set to **Best price** and **Compound**. If multiple **Compound** discounts apply to a product, the pricing engine compounds them, and the resulting total discount amount competes against the other **Best price** discounts. Either one of the **Best price** discounts or the combination of **Compound** discounts gets applied to the product, depending on which discount gives the most benefit to the customer. Like the previous step, the pricing engine skips mix-and-match least-expensive discounts that have the **Multiple occurrences mode** property set to **Favor retailer** in this step. Once the pricing engine applies all the **Best price** and **Compound** discounts at pricing priority 10, it evaluates **Best price** and **Compound** mix-and-match **Favor retailer** discounts against each other and gets applied. A **Best price** discount applies only to undiscounted products, but a **Compound** discount applies to undiscounted products and products that are discounted with another **Compound** discounts at the same pricing priority.
1. Because the discount concurrency control mode is set to **Best price and compound within priority, never compound across priorities** the simple, quantity, and mix-and-match discounts applicable to the product, at pricing priority 5 don't compete with the applied discounts. At this point, for a product, the pricing engine evaluates all the simple, quantity, and mix-and-match discounts at the highest priority.
1. Next, within priority 10, the pricing engine evaluates threshold discounts that have the concurrency mode set to **Exclusive**. An **Exclusive** threshold discount can't be applied to a product that already has a discount applied, so a threshold amount is applied and evaluated only on the undiscounted products. If more than one of these discounts applies to the transaction, the discounts compete, and the largest discount is applied.
1. Next, within priority 10, the pricing engine evaluates threshold discounts that have the concurrency mode set to **Best price** and **Compound**. The pricing engine evaluates and applies threshold discounts at pricing priority 10. **Compound** threshold discounts are compounded with other **Compound** threshold discounts and compete against the other **Best price** discounts within the same pricing priority. A **Best price** threshold discount applies only to undiscounted products, but a **Compound** threshold discount applies to undiscounted products and products that are discounted with another **Compound** (**Simple**, **Quantity**, and **Mix and Match**) discount.

    > [!NOTE]
    > If there were threshold discounts set at a higher priority, for example if it's set to 11, and all the other discount types were at priority 10 and 5, then the threshold discounts would be evaluated at priority 11 and then compounded with the simple, quantity, and mix and match discounts at priority 10. This evaluation is important because the pricing engine evaluates simple, quantity, and mix and match discounts within their highest priority and evaluates threshold discounts within their highest priority and then compounds them. The pricing engine ignores any threshold discounts at the lower priority.

At this point, the pricing engine evaluates all the discounts at the highest priorities.

The following image shows a detailed view of how the pricing algorithm loops through the discounts across various priorities. This diagram applies for both the discount concurrency control models, but the difference is in the way in which the pricing algorithm treats discounts at different priorities.

:::image type="content" source="../media/Detailed-pricing-logic.png" alt-text="Screenshot of the detailed pricing logic flow for discount processing across priorities.":::

In this example, assume the following setup.

**Product information**

| Product \# | Product price |
|---|---|
| Prod1 | $10 |
| Prod2 | $20 |
| Prod3 | $10 |

**Discount setup**

| Discount \# | Discount concurrency | Priority | Discount amount | Discount type | Applicable on products |
|---|---|---|---|---|---|
| BP1 | Best price | 10 | 15% | Simple, Quantity, or Mix and Match | Prod1, Prod2 |
| BP2 | Best price | 5 | 20% | Simple, Quantity, or Mix and Match | All products |
| C1 | Compound | 10 | $1 | Simple, Quantity, or Mix and Match | Prod1, Prod2 |
| C2 | Compound | 10 | 10% | Simple, Quantity, or Mix and Match | Prod1, Prod2 |
| C3 | Compound | 5 | 25% | Simple, Quantity, or Mix and Match | All products |
| C4 | Compound | 5 | 10% | Threshold only | All products |

**Step 1:** For each product, determine the highest priority where a Simple, Quantity, or Mix and Match discount exists. In this case, for prod1 it's priority 10, for prod2 it's priority 10 and for prod3 it's priority 5.

**Step 2:** For each product, find **Simple**, **Quantity**, or **Mix and Match** discounts, with discount concurrency as **Exclusive**, at the highest priority applicable to individual products. In this case, the pricing engine finds none for prod1 and prod2 at priority 10 and similarly, the engine finds none for prod3 at priority 5.

**Step 3:** For each product, evaluate **Simple**, **Quantity**, or **Mix and Match** discounts, with discount concurrency as **Best price** and **Compound**, at the highest priority applicable to individual products. The following table illustrates this evaluation.

> [!NOTE]
> Two asterisks (\*\*) indicate the discount that gets applied to a product.

| Transaction quantity | Product | Price | Priority 10 (C1 + C2) | Priority 10 (BP1) | Priority 5 (C3) | Priority 5 (BP2) | Total | Explanation |
|---|---|---|---|---|---|---|---|---|
| 1 | Prod1 | $10 | $1.90\*\* | $1.50 | (NA) | (NA) | $10 – 1.90 = $8.1 | Because the combination of compound discounts is more than the best price discount, C1 and C2 are applied on the product. The discounts at lower priority, such as 5, are ignored. |
| 1 | Prod2 | $20 | $2.90 | $3\*\* | (NA) | (NA) | $20 – 3 = $17.00 | Because the best price discount is more than the combination of compound discounts, BP1 is applied on the product. The discounts at lower priority, such as 5, are ignored. |
| 1 | Prod3 | $10 | | | $2.50\*\* | $2.0 | $10 – 2.50 = $7.5 | Priority 5 is highest applicable priority for this product. The compound discount is more than the best price discount, so C3 is applied on the product. |

**Step 4:** Evaluate **Threshold** discounts applicable to the individual products at the highest priority. For this example, it's priority 5 for all the products.

| Transaction quantity | Product | Discount applied | Discounted price | Priority 5 (C4) | Amount due | Explanation |
|---|---|---|---|---|---|---|
| 1 | Prod1 | C1, C2 | $8.1 | $0.81\*\* | 8.1 – 0.81 = $7.29 | For Threshold discounts, Priority 5 is the highest applicable priority for this product, so any applicable threshold discounts at priority 5 compound with the applied discounts if the applied discounts are of discount concurrency mode **Compound**. Because Prod1 has compound discounts only, the compound threshold discounts can be compounded. |
| 1 | Prod2 | BP1 | $17 | (NA) | $17 | For Threshold discounts, Priority 5 is the highest applicable priority for this product, so any applicable threshold discounts at priority 5 compound with the applied discounts if the applied discounts are of discount concurrency mode **Compound**. Because Prod2 has a "Best price" discount, other discounts CANNOT be applied to this product.|
| 1 | Prod3 | C3 | $7.5 | $0.75\*\* | 7.5 – 0.75 = $6.75 | For Threshold discounts, Priority 5 is highest applicable priority for this product, so any applicable threshold discounts at priority 5 compound with the applied discounts if the applied discounts are of discount concurrency mode **Compound**. Because Prod3 has compound discounts only, the compound threshold discounts can be compounded. |

The final amount due for Prod1 is $7.29, Prod 2 is $17, and Prod 3 is $6.75.

#### Example 2

In the second scenario, select **Best price only within priority, always compound across priorities** as the discount concurrency control model while keeping the rest of the discounts as is.

1. Given that **Discount concurrency control model** is selected, for each product the pricing engine next considers the highest pricing priority of the discounts that are applicable on a product. If, for a product, discounts from more than one priority are applicable, the pricing engine evaluates each priority independently, and in descending order. Thus, the pricing engine first evaluates and applies the simple, quantity, and mix-and-match discounts with priority 10 followed by the discounts at priority 5.

    > [!NOTE]
    > Like the previous discount concurrency control model, the **Threshold** discounts aren't evaluated yet.

1. Within priority 10, the pricing engine first considers the discounts that have the concurrency mode set to **Exclusive**. If more than one exclusive discount is applicable to the product, the pricing engine applies the best exclusive discount. When a product gets an exclusive discount, no other discounts can be applied to this product at any priority.

    > [!NOTE]
    > The pricing engine skips mix-and-match, least-expensive discounts that have the **Multiple occurrences mode** property set to **Favor retailer** in this step. After the pricing engine applies all the **Exclusive** discounts (**Simple**, **Quantity**, and **Mix and Match**) at pricing priority 10, it then applies the **Exclusive** mix-and-match **Favor retailer** discounts, at pricing priority 10, to any undiscounted products.

1. Within priority 10, the pricing engine then considers the discounts that have the discount concurrency mode set to **Best price** and **Compound**. As stated before, for this discount concurrency control model, discounts with **Discount concurrency mode** set to **Best price** and **Compound** are all treated as "best price"; within a single pricing priority. So, if multiple **Compound** and **Best price** discounts apply to a product, all these discounts compete for best price and only the best discount wins within a priority. Like the previous step, the pricing engine skips mix-and-match least-expensive discounts that have the **Multiple occurrences mode** property set to **Favor retailer**. When the pricing engine applies the **Best price** and **Compound** discounts at pricing priority 10, it then evaluates and applies **Best price** and **Compound** mix-and-match **Favor retailer** discounts against each other. Because both **Best price** and **Compound** are treated as best price, only one discount can be applied per product at a given priority.
1. The pricing engine repeats steps 1 through 3 for any simple, quantity, and mix-and-match discounts at pricing priority 5.

    > [!NOTE]
    > The pricing engine completes steps 1 through 3, one time, for every pricing priority that applies to the transaction. Therefore, keep the number of pricing priorities to a minimum, based on your business requirements.

    At this point, all the simple, quantity, and mix-and-match discounts at all priorities are evaluated and applied.

1. Next, within priority 10, the pricing engine evaluates threshold discounts that have the concurrency mode set to **Exclusive**. An **Exclusive** threshold discount can't be applied to a product that already has a discount applied, so the pricing engine applies and evaluates a threshold amount only on undiscounted products. If more than one of these discounts applies to the transaction, the discounts compete, and the largest discount is applied.
1. Next, within priority 10, the pricing engine evaluates threshold discounts that have the concurrency mode set to **Best price** and **Compound**. Because **Best price** and **Compound** are all treated as "best price", these discounts compete for the best discount. The selected threshold discount gets applied to those products that don't have any other types of discounts already applied at priority 10. If there are other discounts, then the threshold discount isn't applied because both Best price and Compound discounts are treated as Best price, and only one discount per priority is allowed with this discount concurrency control.

    > [!NOTE]
    > If threshold discounts were set at a higher priority, for example, if they're set to 11 and all the other discount types were at priority 10 and 5, then the threshold discounts are evaluated at priority 11 and the best threshold discount is applied at priority 11 (assuming there's no **Exclusive** discount (**Simple**, **Quantity**, or **Mix and Match**) applied at a lower priority).

1. The pricing engine repeats steps 5 and 6 for threshold discounts at pricing priority 5.

Let's use the same example as before.

**Product information**

| Product \# | Product price |
|---|---|
| Prod1 | $10 |
| Prod2 | $20 |
| Prod3 | $10 |

**Discount setup**

| Discount \# | Discount concurrency | Priority | Discount amount | Discount type | Applicable on products |
|---|---|---|---|---|---|
| BP1 | Best price | 10 | 15% | Simple, Quantity, or Mix and Match | Prod1, Prod2 |
| BP2 | Best price | 5 | 20% | Simple, Quantity, or Mix and Match | All products |
| C1 | Compound | 10 | $1 | Simple, Quantity, or Mix and Match | Prod1, Prod2 |
| C2 | Compound | 10 | 10% | Simple, Quantity, or Mix and Match | Prod1, Prod2 |
| C3 | Compound | 5 | 25% | Simple, Quantity, or Mix and Match | All products |
| C4 | Compound | 5 | 10% | Threshold only | All products |

**Step 1:** For each product, determine the highest priority where a **Simple**, **Quantity**, or **Mix and Match** discount exists. In this case, for prod1 it's priority 10, for prod2 it's priority 10, and for prod3 it's priority 5.

**Step 2:** For each product, find **Simple**, **Quantity**, or **Mix and Match** discounts, with discount concurrency as **Exclusive**, at the highest priority applicable to individual products. In this case, there are none for prod1 and prod2 at priority 10 and there are none for prod3 at priority 5.

**Step 3:** For each product, evaluate **Simple**, **Quantity**, or **Mix and Match** discounts, with discount concurrency as **Best price** and **Compound**, at the highest priority applicable to individual products. See the following table.

> [!NOTE]
> Two asterisks (\*\*) indicate the discount that gets applied to a product.

| Transaction quantity | Product | Price | Priority 10 (C1) | Priority 10 (C2) | Priority 10 (BP1) | Total | Explanation |
|---|---|---|---|---|---|---|---|
| 1 | Prod1 | $10 | $1 | $1 | $1.50\*\* | $10 – 1.50 = $8.50 | Because the compound discounts are treated as the "Best price" for discounts for this discount concurrency control model, the compound discounts don't combine. Rather they all compete for the best discount. Because BP1 gives the highest discount, BP1 gets applied at priority 10. |
| 1 | Prod2 | $20 | $1 | $2 | $3\*\* | $20 – 3 = $17.00 | Same as above. Because BP1 gives the highest discount, BP1 gets applied at priority 10. |
| 1 | Prod3 | $10 | | | | $10 | No discounts applicable at priority 10. |

**Step 4:** For each product, determine the next highest priority where a **Simple**, **Quantity**, or **Mix and Match** discount exists. In this case, it's priority 5 for all three products.

**Step 5:** At priority 5, find **Simple**, **Quantity**, or **Mix and Match** discounts with discount concurrency mode as **Exclusive**. In this case, none.

> [!NOTE]
> If an exclusive discount existed at priority 5, the system ignores it as exclusive discounts can't coexist with other discounts that are applied at a higher priority.

**Step 6:** At priority 5, evaluate **Simple**, **Quantity**, or **Mix and Match** discounts. The following table illustrates this scenario.

| Transaction quantity | Product | Discounted Price | Priority 5 (C3) | Priority 5 (BP2) | Total | Explanation |
|---|---|---|---|---|---|---|
| 1 | Prod1 | $8.50 | $2.13\*\* | $1.7 | $8.50 – 2.13 = $6.37 | Because the discounts across priorities are compounded, the discounts at priority 5 are compounded on the discounts applied at priority 10. C3 gives the highest discount so C3 gets applied at priority 5. |
| 1 | Prod2 | $17 | $4.25\*\* | $3.40 | $17.00 – 4.25 = $12.75 | Same as above. Because C3 gives the highest discount, C3 gets applied at priority 5. |
| 1 | Prod3 | $10 | $2.5\*\* | $2.0 | $10 – 2.5 = $7.5 | Same as above. Because C3 gives the highest discount, C3 gets applied at priority 5. |

**Step 7:** Evaluate **Threshold** discounts.

| Transaction quantity | Product | Discount applied at priority 10 | Discount applied at priority 5 | Discounted price | Priority 5 (C4) | Amount due | Explanation |
|---|---|---|---|---|---|---|---|
| 1 | Prod1 | BP1 | C3 | $6.37 | (NA) | $6.37 | For Threshold discounts, Priority 5 is highest applicable priority for this product. But the threshold discount at priority 5 only gets applied if there's no other discount applied at the priority 5. This condition exists because both best price and compound discounts are treated as "Best price" and only one discount per priority is allowed with this discount concurrency control. So, the threshold discount is ignored. |
| 1 | Prod2 | BP1 | C3 | $12.75 | (NA) | $12.75 | Same as above |
| 1 | Prod3 | | C3 | $7.5 | (NA) | $7.5 | Same as above |

The final amount due for prod1 is 6.37, Prod 2 is 12.75, and Prod 3 is 7.5.

> [!NOTE]
> For the same discount setting, the results vastly differ depending on which discount concurrency control model is selected.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
