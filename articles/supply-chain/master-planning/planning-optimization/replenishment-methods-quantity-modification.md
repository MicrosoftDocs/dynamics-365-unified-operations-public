---
title: Replenishment methods and quantity modification
description: This article provides information about replenishment methods in Planning Optimization and includes details on how product multiple order quantity affects the result. 
author: crytt
ms.date: 6/1/2021
ms.topic: article
ms.search.form: ReqGroup, ReqItemTable, InventItemOrderSetup
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: crytt
ms.search.validFrom: 2021-06-01
ms.dyn365.ops.version: AX 7.0.0
---

# Replenishment methods and quantity modification

[!include [banner](../../includes/banner.md)]

This topic provides information about replenishment methods in Planning Optimization and includes details on how product multiple order quantity affects the result.

## Coverage codes

Planning Optimization can be configured to use different replenishment methods. The replenishment methods or lot-sizing methods are the techniques the system uses to calculate requirements for a product. Replenishment methods are defined by coverage codes that you can set up on the coverage group or on the product.

The following coverage codes can be used in Planning Optimization:

- **Period** - A coverage method that combines all the demand for a period into one order for the product. The order will be planned for the first day of the period and its quantity will fulfill the net requirements during the established period. The period starts with the first demand of the product and covers the defined length in time. The next period will start with the next requirements of the product. This coverage code is often used for non-predictable inventory draw, season influenced products, or high-cost products. The following image shows an example.

    ![Period coverage code usage example](./media/coverage-code-period.png "Period coverage code usage example")

- **Requirement** - A coverage method in which the system creates a planned purchase, transfer, or production order per requirement for the product. This method is used for expensive products with intermittent demand. It is often used for configurable products or make to order scenarios. The following image shows an example.

    ![Requirement coverage code usage example](./media/coverage-code-requirement.png "Requirement coverage code usage example")

- **Min./Max.** - An inventory level-based coverage method that contains the replenishment of inventory up to a certain level when the predicted on-hand is below a certain threshold. The replenishment quantity will be the difference between the maximum level and the predicted on-hand level. It is often used for predictable inventory draw, high runners, or less expensive products.  The following image shows an example.

    ![Min./Max. coverage code usage example](./media/coverage-code-min-max.png "Min./Max. coverage code usage example")

- **Manual** - A coverage method where the system does not suggest purchased, transfer, or production orders for the product. The planner for the product will be in charge of creating the required orders for the replenishment of the product. It is often used for products where it is not desired to get system generated planned orders.

## Impact of order quantity from default order settings

On the **Default order setting** page for a released product, you can specify a each of following quantity settings in the **Purchase order**, **Inventory** (used for both transfer and production), and **Sales order** FastTabs.

- **Multiple** - Planned orders will be a multiple of this quantity.  
For example, **Multiple** = *5* means that an order can be for a quantity of 5, 10, 15, 20 and so on.

- **Min. order quantity** - Planned orders will not be less than the value defined.  
For example, **Min. order quantity** = *10* will result in a planned order for 10, even if only 4 is required to fulfill the demand.

- **Max. order quantity** - Planned orders will not exceed the value entered. For demand higher than the **Max. order quantity**, multiple planned orders will be created to cover the demand.  
For example, if **Max. order quantity** = *100* and demand is 450, the result will be four planned orders of 100 and one for 50.

## Examples of replenishment that uses the Min./Max. coverage code

When you do not specify a value for the **Multiple** field for a product on the **Default order setting** page, and you are using the *Min./Max.* method, Planning Optimization will replenish the inventory up to a certain level when the predicted on-hand is below a certain threshold.

When you define multiple quantity for a product, the *Min./Max.* coverage method changes its behavior and considers the **Multiple** setting value.

To put it another way, Planning Optimization will still replenish the inventory up to the defined maximum when the predicted on-hand is below the defined minimum, but with the deviation that the replenishment quantity must be a multiple of the **Multiple** value.

If the replenishment quantity (calculated as the difference between the maximum and predicted on-hand) is not a multiple of the defined multiple quantity, Planning Optimization will use the first possible value that, together with predicted on-hand, would be below the maximum. If this sum falls below the minimum, Planning Optimization will use the first value that, together with predicted on-hand, would be above the maximum.

The following subsections provide some examples that illustrate how the product multiple order quantity affects the result of the *Min./Max.* replenishment method.

### Example 1

A product has the following configuration:

- **Coverage code**: *Min./Max.*  
- **Minimum**: *15*
- **Maximum**: *22*
- **Multiple**: *0*

There are 10 pieces of on-hand inventory for the product and no other demand or supply.

When master planning runs, a planned order for 12 pieces is created to replenish inventory to the maximum quantity.

### Example 2

A product has the following configuration:

- **Coverage code**: *Min./Max.*
- **Minimum**: *15*
- **Maximum**: *22*
- **Multiple**: *5*

There are 10 pieces of on-hand inventory for the product and no other demand or supply.

When master planning runs, a planned order for 10 pieces is created (because 15 pieces of replenishment + 10 pieces of on-hand would be above maximum).

### Example 3

A product has the following configuration:

- **Coverage code**: *Min./Max.*
- **Minimum**: *21*
- **Maximum**: *24*
- **Multiple**: *5*

There are 10 pieces of on-hand inventory for the product and no other demand or supply.

When master planning runs, the planned order for 15 pieces is created (because 10 pieces of replenishment + 10 pieces of on-hand would be below minimum).


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
