---
title: Master planning with supply forecasts
description: This article describes how supply forecasts are considered during master planning
author: t-benebo
ms.date: 09/21/2022
ms.topic: article
ms.search.form:
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: benebotg
ms.search.validFrom: 2022-09-21
ms.dyn365.ops.version: 10.0.30
---

# Master planning with supply forecasts

[!include [banner](../../includes/banner.md)]

Supply forecasts let you specify the supply you expect to need during some future period. You'll typically base this estimate on last year's sales  history and then use the forecast for budgeting purposes. You can also set up your master plans to consider forecasts during planning.

## Set up a master plan to consider supply forecasts

For each master plan, you can choose whether or not to consider forecasts when that plan runs. Use the following procedure to set forecasting options for each plan.

1. Go to **Master planning \> Setup \> Plans \> Master plans**.
1. Either select an existing plan from the list pane or select **New** on the Action Pane to create a new one.
1. On the **General** FastTab, make the following settings:
    - **Forecast model** – Select the model that contains the supply and/or demand forecasts to be considered by this master plan.
    - **Include supply forecast** –  Set to *Yes* to set this master plan to consider supply forecasts.
    - **Include demand forecast** –  Set to *Yes* to set this master plan to consider demand forecasts. This setting is independent of the **Include supply forecast** setting, but some of the other settings on this page  apply to both supply and demand forecast. For more information about planning with demand forecasts, see [Master planning with demand forecasts](demand-forecast.md).
    - **Method used to reduce forecast requirements**: select a method to use to reduce forecast requirements during master planning. Choose one of the following values
        - *None*: Forecast requirements won't be reduced during master planning.
        - *Percent - reduction key*: Forecast requirements will be reduced according to the percentages and time periods that are defined in the reduction key.
        - *Transactions – reduction key*: Forecast requirements will be reduced by the transactions that occur during the time periods defined by the reduction key.
        - *Transactions – dynamic period*: Forecast requirements will be reduced by the order transactions that occur during the dynamic period. The dynamic period covers the current forecast dates and ends with the start of the next forecast. The *Transactions – dynamic period* method doesn't use or require a reduction key and, when you use it, the following conditions apply:
            - If the forecast is reduced completely, the forecast requirements for the current forecast become zero.
            - If there's no future forecast, forecast requirements from the last forecast that was entered are reduced.
            - Time fences are included in the forecast reduction calculation.
            - Positive days are included in the forecast reduction calculation.
            - If actual order transactions are greater than the forecasted requirements, the remaining transactions aren't forwarded to the next forecast period.
        > [!NOTE]
        > The **Method used to reduce forecast requirements** setting also applies to demand forecasts if you have enabled them for this mater plan, and affects them in a similar way. For more information, see [Master planning with demand forecasts](demand-forecast.md).

## Set reduction options for coverage groups

To set options for how a coverage group will reduce its forecast requirements for master plans that use transaction-based reduction, follow these steps.

1. Go to **Master planning \> Setup \> Plans \> Coverage groups**.
1. Either select an existing coverage group from the list pane or select **New** on the Action Pane to create a new one.
1. Expand the **Other** FastTab.
1. Set the **Reduce forecast by** field to control how supply forecast requirements will be reduced for items in this coverage group for master plans where the **Method used to reduce forecast requirements** field is set to *Transactions - reduction key* or *Transactions - dynamic period*. Select one of the following values:

    - *All transactions* – All transactions should reduce the forecast.
    - *Orders* – Only orders of the same type should reduce the forecast.

    For example, suppose the default order settings for an item indicates that it should be produced, and there's a supply forecast line for quantity 50, and there's an existing purchase order for quantity 20. If **Reduce forecast by** is set to *Orders*, then a planned production order will be created for a quantity of 50. If **Reduce forecast by** is set to *All transactions*, the planned production order will be reduced to 30.

    This setting also applies for demand forecasting reduction. See also [Master planning with demand forecasts](demand-forecast.md).

## Enter a supply forecast for a product

To enter a supply forecast for a product, follow these steps.

1. Go to **Product information management \> Products \> Released products**.
1. Select the product you want to enter a forecast for.
1. On the Action Pane, open the **Plan** tab and select **Supply forecast**.
1. The **Supply forecast** page opens. On the Action Pane, select **New** to add a new forecast to the grid.
1. Fill out the new line as required to specify your forecast.

## Plan for an item with supply forecast lines

When you run a master plan that includes an item for which a supply forecast exists, the system will create a purchase order for the entered supply lines. Default order settings for the item are respected. If the **Default order settings** for the item specify a **Default order type** of *Purchase order* and no vendor account is specified in the supply forecast line, the system will use the default vendor for the item.

## Check whether a planned order is a supply forecast order

Use the following procedure to find out whether a planned order was created as a result of a supply forecast.

1. Go to Master planning \> Master planning \> Planned orders.
1. Open the planned order you want to inspect.
1. Expand the **General** FastTab.
1. Check the value of the **Supply forecast** setting. If the order was created to cover a supply forecast, this setting will show a value of *Yes*.

## Examples of master planning with supply forecasts

This section provides several examples that illustrate how supply forecasting affects master planning.

### Example 1: Supply forecast for an item

Suppose you have an item with a default order type of *Purchase order*, a default vendor of *US-002* and the supply forecast lines shown in the following table.

| Model    | Date     | Vendor account | Vendor group | Quantity | Unit | Site | Warehouse |
|----------|----------|----------------|--------------|----------|------|------|-----------|
| CurrentF | 10/10/22 |                |              | 35       | ea   | 1    | 11        |

When you run master planning, a planned purchase order will be created for *35 ea* from vendor *US-002*.

### Example 2: Several supply forecast lines, with and without a vendor

Suppose you have an item with a default order type of *Purchase order*, a default vendor of *US-002* and the supply forecast lines shown in the following table.

| Model    | Date     | Vendor account | Vendor group | Quantity | Unit | Site | Warehouse |
|----------|----------|----------------|--------------|----------|------|------|-----------|
| CurrentF | 10/10/22 |                |              | 35       | ea   | 1    | 11        |
| CurrentF | 10/10/22 | US-101         |              | 25       | ea   | 1    | 11        |

In this case, the system assumes that the line without a vendor is a generic forecast and the line that specifies a vendor should be taken (subtracted) from the generic forecast. Therefore master planning will create the following planned purchase orders for this item:

- A planned purchase order for *25 ea* from vendor *US-101* (the vendor and quantity specified in the forecast line)
- A planned purchase order for *10 ea* from vendor *US-002* (no vendor was specified in the other forecast line, so the default vendor is used and the quantity of this forecast line is reduced by the quantity of the vendor-specific forecast line).

### Example 3: Plans using the "Transactions - dynamic period" reduction method with a single forecast period

For master plans that use a forecast reduction method of *Transactions - dynamic period*, master planning will reduce forecast quantities if there are existing transactions that match those supply characteristics.

Suppose you have an item with a default order type of *Purchase order* and the supply forecast line shown in the following table.

| Model    | Date     | Vendor account | Vendor group | Quantity | Unit | Site | Warehouse |
|----------|----------|----------------|--------------|----------|------|------|-----------|
| CurrentF | 10/10/22 | US-101         |              | 25       | ea   | 1    | 11        |

There's only one forecast period because there's only one supply forecast line.

When you run a master plan set to use a reduction method of *Transactions – dynamic period*. One of the following results could occur:

- If a purchase order exists for vendor *US-101*, quantity *10 ea* (with **Supply forecast** set to *Yes*), then master planning will create a new planned purchase order for the remaining quantity of *10 ea*. The forecast line is reduced because the vendor matches the existing purchase order.
- If a purchase order exists for another vendor *US-102*, site *1*, warehouse *11*, quantity *10 ea* (with **Supply forecast** set to *Yes*), then master planning will create a new planned purchase order for the full quantity of *25 ea*. The forecast line can't be reduced because it has a different vendor than the existing purchase order.

> [!NOTE]
> This situation can occur for planned purchase orders because they have a vendor associated. However, for transfer orders and production orders, the supply forecast amounts will always be reduced by existing orders because no vendor is specified for these types of orders.

### Example 4: Plans using the "Transactions - dynamic period" reduction method over several forecast periods

Suppose you have an item with a default order type of *Purchase order* and the supply forecast lines shown in the following table.

| Model    | Date     | Vendor account | Vendor group | Quantity | Unit | Site | Warehouse |
|----------|----------|----------------|--------------|----------|------|------|-----------|
| CurrentF | 10/10/22 | US-101         |              | 25       | ea   | 1    | 11        |
| CurrentF | 10/15/22 | US-101         |              | 25       | ea   | 1    | 11        |

In this example, there are two forecast lines with different dates, so those dates establish the boundaries of the forecast periods. The first period is 10/10/22 - 10/14/22 and the second is 10/15/22 onwards.

There is an existing purchase order for vendor *US-101*, quantity *10 ea*, date *10/12/22*. Then you run a master plan set to use a reduction method of *Transactions – dynamic period*, which results in the following orders:

- Planned order for quantity *15 ea*, date *10/10/22* (reduced by the existing purchase order dated within this same forecast period)
- Planned order for quantity *25 ea*, date *10/15/22* (full quantity of the forecast)

### Example 5: Plans using no reduction

When you run a plan with with a forecast reduction method of *None*, master planning will always create planned supply for all supply forecast lines. Once that planned supply has been approved, it will reduce future planned orders. However, purchase orders won't reduce the supply forecast lines.

Suppose you have an item with a default order type of *Purchase order* and the supply forecast line shown in the following table.

| Model    | Date     | Vendor account | Vendor group | Quantity | Unit | Site | Warehouse |
|----------|----------|----------------|--------------|----------|------|------|-----------|
| CurrentF | 10/10/22 | US-101         |              | 25       | ea   | 1    | 11        |

A purchase order exists for vendor *US-101*, site *1*, warehouse *11*, quantity *25 ea*, date *10/10/22*. 

When you run a master plan set to use a reduction method of *None*, it will create a planned purchase order for vendor *US-101*, site *1*, warehouse *11*, quantity *25 ea*, date *10/10/22*. In other words, the existing purchase order won't be reduces because the forecast reduction method is none.

Suppose you now edit the planned purchase order created after the last planning run so that it has a quantity of *15 ea*, and then approve that order. The next time you run the master plan, it will create a planned purchase order for vendor *US-101*, site *1*, warehouse *11*, quantity *10 ea*, date *10/10/22*. This time, the quantity was reduced to reflect the quantity of the existing approved order from the previous planning run.

## Differences between Planning Optimization and the built-in planning engine

Supply forecasts work slightly differently depending on which planning engine you're using (built-in master planning or Planning Optimization). The differences are detailed in the following subsections.

### Vendor group

When you add a forecasted line, you can specify a vendor and vendor group. In the built-in planning engine, created planned orders are grouped by the combination of vendor and vendor group values, while in Planning Optimization they're grouped by vendor.

The following table provides a few example supply forecast lines for an item.

| Model    | Date     | Vendor account | Vendor group | Quantity | Unit | Site | Warehouse |
|----------|----------|----------------|--------------|----------|------|------|-----------|
| CurrentF | 10/10/22 |                | VendorGroupA | 5        | ea   | 1    | 11        |
| CurrentF | 10/10/22 |                | VendorGroupA | 6        | ea   | 1    | 11        |
| CurrentF | 10/10/22 |                |              | 7        | ea   | 1    | 11        |

VendorA is the default vendor for VendorGroup A, and is also the default vendor for the item.

The built-in planning engine will create the following orders:

- Planned purchase order for quantity 11, VendorA, VendorGroupA
- Planned purchase order for quantity 7, VendorA

Planning Optimization will create just one order:

- Planned purchase order for quantity 18, VendorA, VendorGroupA

### Reduction of general forecasts with a more specific one

With the built-in master planning engine, the result is unpredictable when you have some forecasts with a vendor and some without a vendor. In Planning Optimization general forecast quantities will always be reduced by more specific ones, as illustrated in the following example.

In the Planning Optimization, general forecasts are reduced by the more specific ones.

The following table provides a few example supply forecast lines for an item.

| Date       | Quantity | Vendor   | Vendor group  |
|------------|----------|----------|---------------|
| 02/11/2022 | 5.00     | Vendor-A | VendorGroup-A |
| 02/11/2022 | 6.00     | Vendor-A | VendorGroup-A |
| 02/11/2022 | 15.00    |          |               |

The general forecast (for 15.00 pieces) is reduced by the more specific forecasts (for 5.00 + 6.00 = 11.00 pieces), with the remainder assigned to the default vendor. The following table shows the planned orders.

| Date       | Quantity | Vendor   | Vendor group  |
|------------|----------|----------|---------------|
| 02/11/2022 | 11.00    | Vendor-A | VendorGroup-A |
| 02/11/2022 | 4.00     | Vendor-A | VendorGroup-A |

### Respect default order settings when generating planned orders

Each item can have default order settings, such as to establish a minimum purchase order quantity and so on. Planning Optimization respects these settings when it comes to generating planned orders from supply forecasts. However, the built-in planning engine ignores these settings and therefore translates forecasts into planned orders with the same quantity.

### Reduction by approved orders aggregates planned orders

The built-in master planning engine assumes that only one order will reduce the existing supply forecast, so if there are several orders matching a supply forecast line, only the first one will reduce.

In Planning Optimization, all orders matching the supply forecast line will reduce it.

### Forecasts are reduced only by matching vendor

When the built-in master planning engine reduces a forecast by existing released purchase orders, it doesn't make sure that the vendor on the purchase order matches the one from the forecast.

Planning Optimization only reduces forecasts by purchase orders that have a matching vendor field value.

For transfer and production orders, the vendor field is always ignored because it isn't relevant for those order types.

### Reducing forecasts by transfer orders

If the default order type for an item is *Transfer*, then forecasts can only be reduced by existing planned transfer orders. However, for production orders and purchase orders, only released orders reduce the supply forecast.

Planning Optimization only reduces forecasts by transfer orders that are *Released*, while the built-in planning engine reduces for all transfer order states.
