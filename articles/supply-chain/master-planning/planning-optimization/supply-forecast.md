---
title: Master planning with supply forecasts
description: Learn how supply forecasts are considered during master planning, including an outline and process for setting up a master plan to consider supply forecasts.
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 11/18/2025
ms.custom:
  - bap-template
---

# Master planning with supply forecasts

[!include [banner](../../includes/banner.md)]

Supply forecasts let you specify the supply that you expect to need during a future period. Typically, you base the estimate on the previous year's sales history and then use the forecast for budgeting purposes. You can also set up your master plans to consider forecasts during planning.

## Set up a master plan to consider supply forecasts

You can specify whether each master plan should consider forecasts when it runs. Use the following procedure to set forecasting options for each plan.

1. Go to **Master planning \> Setup \> Plans \> Master plans**.
1. Either select an existing master plan in the list pane, or select **New** on the Action Pane to create a new one.
1. On the **General** FastTab, set the following fields:

    - **Forecast model** – Select the model that contains the supply and demand forecasts that the master plan should consider.
    - **Include supply forecast** – Set this option to *Yes* if the master plan should consider supply forecasts.
    - **Include demand forecast** – Set this option to *Yes* if the master plan should consider demand forecasts. Although this setting is independent of the **Include supply forecast** setting, some of the other settings on the page apply to both supply forecasts and demand forecasts. For more information about planning that considers demand forecasts, see [Master planning with demand forecasts](demand-forecast.md).
    - **Method used to reduce forecast requirements** – Select the method to use to reduce forecast requirements during master planning:

        - *None* – Forecast requirements aren't reduced during master planning.
        - *Percent - reduction key* – Forecast requirements are reduced according to the percentages and time periods that are defined in the reduction key.
        - *Transactions – reduction key* – Forecast requirements are reduced by the transactions that occur during the time periods that are defined in the reduction key.
        - *Transactions – dynamic period* – Forecast requirements are reduced by the order transactions that occur during the dynamic period. The dynamic period covers the current forecast dates, and it ends when the next forecast begins. The *Transactions – dynamic period* method doesn't use or require a reduction key, and when you use it, the following conditions apply:

            - If the forecast is completely reduced, the forecast requirements for the current forecast become 0 (zero).
            - If there's no future forecast, forecast requirements from the last forecast that you entered are reduced.
            - Time fences are included in the forecast reduction calculation.
            - Positive days are included in the forecast reduction calculation.
            - If actual order transactions exceed the forecasted requirements, the remaining transactions aren't forwarded to the next forecast period.

        > [!NOTE]
        > The **Method used to reduce forecast requirements** setting also applies to demand forecasts if you enable them for the master plan, and it affects them in a similar way. Learn more in  [Master planning with demand forecasts](demand-forecast.md).

## Set reduction options for coverage groups

To set options that control how a coverage group reduces its forecast requirements for master plans that use transaction-based reduction, follow these steps.

1. Go to **Master planning \> Setup \> Plans \> Coverage groups**.
1. Select an existing coverage group in the list pane, or select **New** on the Action Pane to create a new one.
1. On the **Other** FastTab, in the **Reduce forecast by** field, specify how supply forecast requirements should be reduced for items in the coverage group, for master plans where the **Method used to reduce forecast requirements** field is set to *Transactions - reduction key* or *Transactions - dynamic period*. Select one of the following values:

    - *All transactions* – All transactions reduce the forecast.
    - *Orders* – Only orders of the same type reduce the forecast.

    For example, the default order settings for an item indicate that it should be produced. There's a supply forecast line for a quantity of 50, and there's an existing purchase order for a quantity of 20. If you set the **Reduce forecast by** field to *Orders*, a planned production order is created for a quantity of 50. If you set it to *All transactions*, the planned production order is reduced to a quantity of 30.

    This setting also applies to demand forecasting reduction. Learn more in [Master planning with demand forecasts](demand-forecast.md).

## Enter a supply forecast for a product

To enter a supply forecast for a product, follow these steps.

1. Go to **Product information management \> Products \> Released products**.
1. Select the product that you want to enter a forecast for.
1. On the Action Pane, on the **Plan** tab, select **Supply forecast**.
1. On the **Supply forecast** page, on the Action Pane, select **New** to add a forecast to the grid.
1. Fill out the new line to specify your forecast.

## Plan for an item with supply forecast lines

When you run a master plan that includes an item that has a supply forecast, the system creates a purchase order for the supply lines that you entered. The system respects the default order settings for the item. If those default order settings specify a **Default order type** value of *Purchase order*, and you don't specify a vendor account on the supply forecast line, the system uses the default vendor for the item.

## Check whether a planned order is a supply forecast order

Use the following procedure to check whether a planned order was created as a result of a supply forecast.

1. Go to **Master planning \> Master planning \> Planned orders**.
1. Open the planned order that you want to inspect.
1. On the **General** FastTab, check the value of the **Supply forecast** field. If the order was created to cover a supply forecast, this field is set to *Yes*.

## Examples of master planning with supply forecasts

This section provides several examples that show how supply forecasting affects master planning.

### Example 1: Supply forecast for an item

You have an item where the default order type is *Purchase order* and the default vendor is *US-002*. It has the following supply forecast line.

| Model    | Date     | Vendor account | Vendor group | Quantity | Unit | Site | Warehouse |
|----------|----------|----------------|--------------|----------|------|------|-----------|
| CurrentF | 10/10/22 |                |              | 35       | ea   | 1    | 11        |

When you run master planning, a planned purchase order is created for *35 ea* from vendor *US-002*.

### Example 2: Several supply forecast lines, with and without a vendor

You have an item where the default order type is *Purchase order* and the default vendor is *US-002*. It has the following supply forecast lines.

| Model    | Date     | Vendor account | Vendor group | Quantity | Unit | Site | Warehouse |
|----------|----------|----------------|--------------|----------|------|------|-----------|
| CurrentF | 10/10/22 |                |              | 35       | ea   | 1    | 11        |
| CurrentF | 10/10/22 | US-101         |              | 25       | ea   | 1    | 11        |

In this case, the system treats the line that doesn't specify a vendor as a generic forecast, and it assumes that the line that does specify a vendor should be subtracted from the generic forecast. Therefore, master planning creates the following planned purchase orders for the item:

- A planned purchase order for a quantity of *25 ea* from vendor *US-101* (The vendor and quantity that are specified on the forecast line are used.)
- A planned purchase order for a quantity of *10 ea* from vendor *US-002* (Because no vendor was specified on the other forecast line, the default vendor is used, and the quantity of this forecast line is reduced by the quantity of the vendor-specific forecast line.)

### Example 3: Plans that use the Transactions - dynamic period reduction method in a single forecast period

For master plans that use *Transactions - dynamic period* as the forecast reduction method, master planning reduces forecast quantities if existing transactions match those supply characteristics.

For example, you have an item where the default order type is *Purchase order*. It has the following supply forecast line.

| Model    | Date     | Vendor account | Vendor group | Quantity | Unit | Site | Warehouse |
|----------|----------|----------------|--------------|----------|------|------|-----------|
| CurrentF | 10/10/22 | US-101         |              | 25       | ea   | 1    | 11        |

Because there's only one supply forecast line, there's only one forecast period.

When you run a master plan that uses *Transactions – dynamic period* as the reduction method, one of the following results can occur:

- If a purchase order exists for vendor *US-101* and a quantity of *10 ea*, and the **Supply forecast** field is set to *Yes*, master planning creates a new planned purchase order for the remaining quantity of *15 ea*. The forecast line is reduced, because the vendor matches the existing purchase order.
- If a purchase order exists for vendor *US-102*, site *1*, warehouse *11*, and a quantity of *10 ea*, and the **Supply forecast** field is set to *Yes*, master planning creates a new planned purchase order for the full quantity of *25 ea*. The forecast line can't be reduced, because it has a different vendor than the existing purchase order.

> [!NOTE]
> This situation can occur for planned purchase orders, because a vendor is associated with them. However, for transfer orders and production orders, the supply forecast amounts are always reduced by existing orders, because no vendor is specified for these types of orders.

### Example 4: Plans that use the Transactions - dynamic period reduction method over several forecast periods

You have an item where the default order type is *Purchase order*. It has the following supply forecast lines.

| Model    | Date     | Vendor account | Vendor group | Quantity | Unit | Site | Warehouse |
|----------|----------|----------------|--------------|----------|------|------|-----------|
| CurrentF | 10/10/22 | US-101         |              | 25       | ea   | 1    | 11        |
| CurrentF | 10/15/22 | US-101         |              | 25       | ea   | 1    | 11        |

In this example, two forecast lines each have a different date. Therefore, the dates establish the boundaries of the forecast periods. The first period is from October 10 through October 14, 2022 (10/10/22–10/14/22). The second is from October 15, 2022 (10/15/22) onward.

A purchase order exists for vendor *US-101*, a quantity of *10 ea*, and the date *10/12/22* (October 12, 2022). When you run a master plan that is set up to use *Transactions – dynamic period* as the reduction method, it creates the following orders:

- A planned order for a quantity of *15 ea* and the date *10/10/22* (The quantity is reduced by the existing purchase order that is dated during the same forecast period.)
- A planned order for a quantity of *25 ea* and the date *10/15/22* (The quantity is the full quantity of the forecast.)

### Example 5: Plans that use no reduction

When you run a plan where the forecast reduction method is *None*, master planning always creates planned supply for all supply forecast lines. After you approve that planned supply, it reduces future planned orders. However, purchase orders don't reduce the supply forecast lines.

For example, you have an item where the default order type is *Purchase order*. It has the following supply forecast line.

| Model    | Date     | Vendor account | Vendor group | Quantity | Unit | Site | Warehouse |
|----------|----------|----------------|--------------|----------|------|------|-----------|
| CurrentF | 10/10/22 | US-101         |              | 25       | ea   | 1    | 11        |

There's an existing purchase order for vendor *US-101*, site *1*, warehouse *11*, a quantity of *25 ea*, and the date *10/10/22*. 

When you run a master plan that uses *None* as the reduction method, it creates a planned purchase order for vendor *US-101*, site *1*, warehouse *11*, a quantity of *25 ea*, and the date *10/10/22*. In other words, the existing purchase order isn't reduced, because the forecast reduction method is *None*.

You edit the planned purchase order that was created after the last planning run, and change the quantity to *15 ea*. You then approve the order. The next time that you run the master plan, it creates a planned purchase order for vendor *US-101*, site *1*, warehouse *11*, a quantity of *10 ea*, and the date *10/10/22*. This time, the quantity is reduced to reflect the quantity of the existing approved order from the previous planning run.

## Differences between Planning Optimization and the deprecated master planning engine

Supply forecasts work slightly differently, depending on the planning engine that you're using (Planning Optimization or the deprecated master planning engine). This section describes the differences.

### Vendor groups

When you add a forecasted line, you can specify a vendor and a vendor group. In the deprecated master planning engine, planned orders that you create are grouped by the combination of the vendor and vendor group values. In Planning Optimization, planned orders are grouped by vendor.

The following table provides some examples of supply forecast lines for an item.

| Model    | Date     | Vendor account | Vendor group | Quantity | Unit | Site | Warehouse |
|----------|----------|----------------|--------------|----------|------|------|-----------|
| CurrentF | 10/10/22 |                | VendorGroupA | 5        | ea   | 1    | 11        |
| CurrentF | 10/10/22 |                | VendorGroupA | 6        | ea   | 1    | 11        |
| CurrentF | 10/10/22 |                |              | 7        | ea   | 1    | 11        |

Vendor *VendorA* is the default vendor for vendor group *VendorGroupA*. It's also the default vendor for the item.

The deprecated master planning engine creates the following orders:

- A planned purchase order for vendor *VendorA*, vendor group *VendorGroupA*, and a quantity of *11*
- A planned purchase order for vendor *VendorA* and a quantity of *7*

Planning Optimization creates just one order:

- A planned purchase order for vendor *VendorA*, vendor group *VendorGroupA*, and a quantity of *18*

### Reduction of general forecasts by more specific forecasts

In the deprecated master planning engine, the result is unpredictable if some forecasts have a vendor but others don't.

In Planning Optimization, more specific forecasts always reduce general forecasts, as the following example shows.

The following table provides some examples of supply forecast lines for an item.

| Date       | Quantity | Vendor   | Vendor group  |
|------------|----------|----------|---------------|
| 02/11/2022 | 5.00     | Vendor-A | VendorGroup-A |
| 02/11/2022 | 6.00     | Vendor-A | VendorGroup-A |
| 02/11/2022 | 15.00    |          |               |

The more specific forecasts (for 5.00 + 6.00 = 11.00 pieces) reduce the general forecast (for 15.00 pieces). The remainder is assigned to the default vendor. The following table shows the planned orders.

| Date       | Quantity | Vendor   | Vendor group  |
|------------|----------|----------|---------------|
| 02/11/2022 | 11.00    | Vendor-A | VendorGroup-A |
| 02/11/2022 | 4.00     | Vendor-A | VendorGroup-A |

### Respect for default order settings when planned orders are generated

Each item can have default order settings, such as a minimum purchase order quantity. The deprecated master planning engine ignores these settings, and therefore translates forecasts into planned orders that have the same quantity. Planning Optimization respects these settings when planned orders are generated from supply forecasts. 

### Aggregation of planned orders as a result of reduction by approved orders

The deprecated master planning engine assumes that only one order reduces the existing supply forecast. Therefore, if several orders match a supply forecast line, only the first order reduces it. In Planning Optimization, all orders that match the supply forecast line reduce it.

### Reduction of forecasts by matching vendors only

When the deprecated master planning engine reduces a forecast by existing released purchase orders, it doesn't ensure that the vendor on the purchase order matches the vendor from the forecast. Planning Optimization reduces forecasts only by purchase orders that have a matching value in the vendor field.

For transfer and production orders, the vendor field is always ignored, because it isn't relevant for those order types.

### Reduction of forecasts by transfer orders

If the default order type for an item is *Transfer*, forecasts can be reduced only by existing planned transfer orders. However, for production orders and purchase orders, only released orders reduce the supply forecast.

The deprecated master planning engine reduces forecasts for all transfer order states, whereas Planning Optimization reduces forecasts only by transfer orders that are in the *Released* state.
