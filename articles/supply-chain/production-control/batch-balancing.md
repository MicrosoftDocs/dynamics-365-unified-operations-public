---
title: Batch balancing
description: Learn about the batch balancing process, including outlines on products that have an active ingredient, ingredient types, and their interactivity.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form: BOMTable, WHSReservationHierarchy, WHSInventTableReservationHierarchy
ms.topic: how-to
ms.date: 09/19/2025
ms.custom:
  - bap-template
---

# Batch balancing

[!include [banner](../includes/banner.md)]

This article describes how the batch balancing process works.

For more information, watch a [video on batch balancing](https://www.youtube.com/watch?v=4SNLWsU9KyI&feature=youtu.be).

In the batch balancing process, you calculate the amount of ingredients to use in a production batch from the concentration of active ingredients in selected product batches.

## Products that have an active ingredient

You can define a product by its concentration of an active ingredient. Model the active ingredient of a product by using a product-specific batch attribute that has a minimum value, a maximum value, and a target level.

The target level of a batch attribute represents the estimated percentage of an active ingredient in a product. The minimum and maximum values represent the accepted deviation from the target level. Use these values, for example, as an accepted tolerance for batches at product receipt.

A product can have only one active ingredient. To specify the active ingredient of a product, first define a product-specific batch attribute. Then associate the attribute as a base attribute of the product.

On the product level, specify how the level of the active ingredient for a batch of the product should be recorded: as part of the purchase receipt process or as part of a quality order process.

To associate a base attribute with a product, complete the following setup steps:

1. Make the product batch-controlled by assigning a tracking dimension group to the product that has an active Batch dimension.
1. Define the attribute that indicates the ingredient levels as a product-specific batch attribute for the product.

To look up and edit the actual value of the active ingredient for a batch:

1. Go to **Inventory management** \> **Inquiries and reports** \> **Tracking dimensions** \> **Batches**.
1. Select a batch number from the grid.
1. On the Action Pane, open the **View** tab and then select **Inventory batch attributes**.

## Ingredient types and how they interact in the batch balancing process

Formula lines that you create can have one of these ingredient types:

- None
- Active
- Compensating
- Filler

The rest of this section provides examples that show how each ingredient type works. The examples are based on the following formula that has a total batch size of 100 liters.

| Ingredient type | Item number | Formula line quantity | Unit |
|--|--|--|--|
| None | A | 20 | Liter |
| Active | B | 30 | Liter |
| Compensating | C | 10 | Liter |
| Filler | D | 40 | Liter |

The following table provides an overview of the results of each example.

| Item number | Ingredient type | Estimated quantity | Balanced quantity | Active quantity | Unit | Base value |
|--|--|--|--|--|--|--|
| A | None | 20 | 20 |  | Liter |  |
| B | Active | 30 | 25.71 | 9.00 | Liter | 30.00 |
| C | Compensating | 10 | 14.72 |  | Liter |  |
| D | Filler | 40 | 39.57 |  | Liter |  |

### Active ingredients

When you add a product with a base attribute to a formula line, you add an *active ingredient* to the formula. You can use batch orders with formulas that include active ingredients for the batch balancing process. For each ingredient in the formula, the batch balancing process estimates the amount needed to produce the product. The estimate is based on the concentration of active ingredients in the selected batches.

#### Active ingredient example

Ingredient B has base attribute X and a target level of 30. It's included in a formula that requires 30 liters of ingredient B for every 100 liters of the product. You create a batch order with a batch size of 100 liters. You start the batch order, and during the batch balancing process, you select a batch of ingredient B that has a potency level of 35. Because the potency level of 35 is higher than the target level of 30, the batch balancing process reduces the balanced quantity of ingredient B by using the ratio of the potency value to the target level of the batch, which is multiplied by the estimated quantity. The calculation of the balanced quantity looks like this:

(30 ÷ 35) × 30 liters = 25.71 liters

### None ingredients

When you apply the batch balancing process and set the **Ingredient type** to *None*, the estimated quantity and the balanced quantity of the formula line in the batch order are the same.

#### None ingredient example

You assign ingredient A to an ingredient of the *None* type and add it to a formula for a finished product. The formula requires 10 liters of ingredient A for every 100 liters of the finished product. When a batch order requires 200 liters, both the estimated quantity and the balanced quantity of ingredient A are 20 liters.

### Compensating ingredients

A compensating ingredient can either offset or complement the effect of the active ingredient in a product. Therefore, the quantity of a compensating ingredient that you consume depends on the potency of the product:

- **Opposing effect** – If the amount of the active ingredient is more than anticipated, you must add less of the compensating ingredient.
- **Complementary effect** – If the amount of the active ingredient is less than anticipated, you must add more of the compensating ingredient.

The relation between an active ingredient and a complementary ingredient is set up on the **Compensating principle** page.

Follow these steps to set up relations between ingredients.

1. Select **Product information management** \> **Bills and materials and formulas** \> **Formulas**.
1. Open a formula line, and then select **Ingredients** to open the **Compensating principle** page.
1. Select the line that represents a compensating principle, and then select the active ingredient to compensate.

In the compensating principle, enter a positive or negative compensating factor to specify how much to compensate for, and whether the principle should be opposing or complementary. A positive factor indicates a complementary effect, and a negative factor indicates an opposing effect.

#### Compensating ingredient example

Ingredient B is an active ingredient that has base attribute X and a target level of 30. It's included in a formula that requires 30 liters of ingredient B for every 100 liters of the product. Ingredient C is a compensating ingredient, and a quantity of 10 is included in the same formula. A compensating factor of 1.10 is set up for the compensating principle. Therefore, the balanced quantity of the compensating ingredient is reduced by the difference between the active ingredient's balanced quantity and the estimated required quantity multiplied by 1.10.

In the example for the *Active* ingredient type, the balanced quantity of the required active ingredient is calculated as 25.71, and the estimated required quantity is calculated as 30. In this case, the balanced quantity of the compensating ingredient is calculated like this:

1. Determine the difference between the estimated and the balanced quantity:  
    25.71 – 30 = –4.29

1. Multiply the result by the compensating factor:  
    4.29 × 1.10 = –4.72

1. Reduce the estimated compensating quantity by –4.72 to determine the balanced compensating quantity:  
    10 – (–4.72) = 14.72

Because 1.10 is a positive compensating factor, this compensating principle has a complementary effect. In this case, the active ingredient is more potent than anticipated. Therefore, you need more of the compensating ingredient.

### Filler ingredients

A *filler ingredient* is a neutral ingredient that you use to reach the desired output quantity of the finished product. Adjustments to filler quantities are based on variations in the active ingredient and the compensating ingredient compared to the standard quantity.

#### Filler ingredient example

You formulate a product that includes ingredients A, B, C, and D for a formula size of 100 liters. You calculate the balanced quantity of all the ingredient types except the *Filler* ingredient type that you use on one line. You calculate the balanced quantity of the filler ingredient as the difference between the batch size of 100 liters and the sum of ingredients A, B, and C:

100 – (20 + 25.71 + 14.72) = 39.57

## The batch balancing process

You perform the batch balancing process from the **Batch balancing** page. Select **Cost management** \> **Batch orders**, then, on the **Process** tab, select **Batch balancing**. Batch balancing is available for batch orders that have a status of *Started*.

In general, you can apply batch balancing to batch orders if the formula has at least one formula line where the **Ingredient type** is *Active*. (For the exception to this rule, see the "Batch orders that aren't applicable for batch balancing" section later in this article.)

You can divide the batch balancing process into two subprocesses:

1. Balance batch ingredients
1. Confirm and release the formula

### Balance batch ingredients

In the Balance batch ingredients subprocess, the system calculates the amount of ingredients to use for the production batch based on the selected batches that have active ingredients. As a rule, you can complete the calculation only if there's full coverage of all ingredients. You can't balance only part of the batch that the batch order is set up to produce.

> [!NOTE]
> You can't save a calculation and then complete the batch balancing process later. If you close the **Batch balancing** page, you must repeat the calculation to complete the process.

### Confirm and release the formula

After you calculate the ingredient quantities, confirm and release the formula. The release process differs, depending on whether the products are enabled for warehouse management processes (WMS):

- For WMS-enabled products, the formula line is released to the warehouse according to the principles for WMS. The formula line is released in quantities that match the balanced quantities, and it's released for the specific batches that are selected for the active ingredients. Formula lines can be released to warehouse only as part of the batch balancing process. Although there are other options for releasing materials for production to warehouse, those options can't be used for formula lines.

- For non-WMS products, a production picking list is created for the product when you confirm and release the formula.

A single formula can include both WMS-enabled products and non-WMS products. In this case, the WMS-enabled products are released to warehouse. For the non-WMS products, a picking list is created when the formula is confirmed and released.

### Batch orders that aren't applicable for batch balancing

Batch orders usually apply batch balancing when the formula has at least one formula line where the **Ingredient type** is *Active*. However, the following exceptions apply:

- If a formula contains an active ingredient for a product that is enabled for the WMS, but batch number is below location in the reservation hierarchy, the batch order isn't applicable for batch balancing.
- If the formula unit of measure is different from the inventory unit of measure of the active ingredient, the batch order isn't applicable for batch balancing.

A batch order that isn't applicable for batch balancing goes through the regular process cycle for batch orders.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
