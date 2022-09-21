---
title: Plan based on supply forecasts
description: This article describes how to consider supply forecasts during master planning
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

# Plan based on supply forecasts

[!include [banner](../../includes/banner.md)]

Using a supply forecast you can enter in the system what you expect supply to be during a future period. It is usually based on last year's sales history and used for enterprises for budgeting.

## Set up supply forecast

For master planning to consider the planned supply forecast, there are some parameters that must be set for the given **master** **plan** (Master planning&gt; Setup&gt; Plans&gt; Master plans)

- The **forecast** **model** that will contain the supply and/or demand forecast must be selected
- The **Include supply forecast** parameter must be set to yes
- The **Include demand forecast** can be set to yes/no depending on if you would like to create supply for the forecasted demand. This setting is independent of the supply forecast but note that some following parameters will apply to both supply and demand forecast.
- **Method used to reduce forecast requirements**: select a method to use to reduce forecast requirements during master scheduling. If you choose:

  - **None**: forecast requirements are not reduced during master scheduling
  - **Percent reduction key**: forecast requirements are reduced according to the percentages and time periods that are defined in the reduction key
  - **Transactions** – reduction key: forecast requirements are reduced by the transactions that occur during the time periods that are defined by the reduction key.
  - **Transactions** – dynamic period: forecast requirements are reduced by the actual order transactions that occur during the dynamic period. The dynamic period covers the current forecast dates and ends with the start of the next forecast. The Transactions – dynamic period method does not use or require a reduction key and when you select this option:

    - **If the forecast is reduced completely**: the forecast requirements for the current forecast become zero.
    - **If there is no future forecast**: forecast requirements from the last forecast that was entered are reduced
    - **Time fences**: are included in the forecast reduction calculation
    - **Positive days**: are included in the forecast reduction calculation
    - **If actual order transactions are greater than the forecasted requirements:** the remaining transactions are not forwarded to the next forecast period

  - **Note that this setting also applies for demand forecasting reduction.** More information on how this setting affects and the reduce demand forecasts can be found on [Master planning with demand forecasts](demand-forecast.md). Note that it will work in a similar way for supply forecasts

- **Select which types of orders should be used for the reduction:** in the coverage group, under the Other tab, on the Forecast plan group, select if it should be **orders** (matching orders of the same type) or **transactions** (all transactions, no matter the type) what should reduce the supply forecast lines.

  - For example, in the case that the default order settings for the item indicates that it should be produced, and there is a supply forecast line for quantity 50. And there is an existing purchase order for quantity 20. If orders is selected, then a planned production order will be created for quantity 50, but if transactions is selected, the planned production order will be reduced and for an amount of 30.
  - Note that this setting also applies for demand forecasting reduction.

## Enter the supply forecast for an item

To add the supply forecast for an item, from the **Released products page**, select the desired item and go to **Plan&gt;Supply forecast** on the upper pane.

By clicking New, enter lines for the supply forecast, and for each indicate its forecast **Model**, **date**, **vendor** **group**, **quantity** and **currency**.

## Planning for an item with supply forecast

When a supply forecast has been entered for the item and master planning for the plan is run, the system will create a purchase order for the entered supply lines. Default order settings for the item are respected. If default order settings is purchase and no vendor is specified in the line, the vendor will be the default vendor for the given item.

## Examples

In this section several examples will be shown for how supply forecasting works on the system.

### Example 1: Supply forecast for an item

Given an item with default order setting purchase, default vendor US-002 and the following supply forecast lines

| Model    | Date     | Vendor account | Vendor group | Quantity | Unit | Site | Warehouse |
|----------|----------|----------------|--------------|----------|------|------|-----------|
| CurrentF | 10/10/22 |                |              | 35       | ea   | 1    | 11        |

When running planning, a planned purchase order will be created for 35 units for vendor US-002.

### Example 2: Several supply forecast lines - with and without a vendor

Given an item with default order setting purchase, default vendor US-002 and where there are two supply forecast lines for a future date set as follows:

| Model    | Date     | Vendor account | Vendor group | Quantity | Unit | Site | Warehouse |
|----------|----------|----------------|--------------|----------|------|------|-----------|
| CurrentF | 10/10/22 |                |              | 35       | Ea   | 1    | 11        |
| CurrentF | 10/10/22 | US-101         |              | 25       | Ea   | 1    | 11        |

In general it is not common to use supply forecasts with and without a vendor or set of vendors for the same item, as either the vendor(s) is/are known and the supply forecasts are created according to their existing capacity and agreements or general supply forecasts are entered in the system before the vendor is known.

So, for this case it is assumed that the line without a vendor is a generic forecast and whenever a specific vendor line is entered, it should "take" or subtract from the generic forecast. Thus, the result of planning will be:

- A planned purchase order for quantity 25 for vendor US-101
- A planned purchase order for quantity 10 for vendor US-002

It is possible to view that these orders came from a supply forecast as in the planned purchase order the parameter **Supply forecast** is set to yes.

### Example 3: Forecast with reduction method – transactions dynamic period

When setting as forecast reduction method Transactions dynamic period, instead of creating planned orders to fulfill the supply forecast lines quantity lines as specified in the item, the quantities will be reduced if there are existing transactions matching those supply characteristics.

Given an item with default order setting purchase, default vendor US-002 and where there are two supply forecast lines for a future date set as follows:

| Model    | Date     | Vendor account | Vendor group | Quantity | Unit | Site | Warehouse |
|----------|----------|----------------|--------------|----------|------|------|-----------|
| CurrentF | 10/10/22 | US-101         |              | 25       | Ea   | 1    | 11        |

And forecast reduction method set to Transactions – dynamic period in the master plan.

**2A)** if there is an existing purchase order (with the supply forecast set to yes) for the 12/10/22 vendor *US-101* for site 1 warehouse 11 for 10 ea. When running planning it will create a planned purchase order *for the remaining quantity*, 10 ea on the 10/10/22 as it is the start of the period (only existing period as there is only one supply forecast line)

**2B**) if there is an existing purchase order (with supply forecast set to yes) for the 12/10/22 *for another vendor*(e.g. US-002), planning will create a new planned purchase order *for the whole amount*, as the existing forecast line cannot be reduced because of having a different vendor. In this case, a planned purchase order for 25 ea for 10/10/22 will be created for vendor US-101.

Note that this is the case for planned production orders, as they have a vendor associated. For transfer orders and production orders, the supply forecast amounts will always be reduced by existing orders.

### Example 4: forecast with reduction method – transactions dynamic period and several periods

Let's evolve the same example by including one more period to illustrate how the periods are created. Each period is from the **Date** of the supply forecast line until the next supply forecast line Date. If there is no further future dates, then the last period will take all the future time.

| Model    | Date     | Vendor account | Vendor group | Quantity | Unit | Site | Warehouse |
|----------|----------|----------------|--------------|----------|------|------|-----------|
| CurrentF | 10/10/22 | US-101         |              | 25       | Ea   | 1    | 11        |
| CurrentF | 15/10/22 | US-101         |              | 25       | ea   | 1    | 11        |

And there is an existing purchase order for quantity 10 on the 12/10/22 for vendor US-101.

In this case the periods are defined by the lines, so there will be two periods as 10/10/22-15/15/22 and 15/10/22-onwards. So, when running master planning the following orders will be created:

- Planned order for quantity 15 for the 10/10/22

- Planned order for quantity 25 on the 15/10/22

### Example 5: forecast with reduction method – none

If forecast reduction method is none, master planning will always create planned supply for the supply forecast lines. That supply can then be approved and then it will reduce the orders. But note purchase orders will not reduce the lines.

| Model    | Date     | Vendor account | Vendor group | Quantity | Unit | Site | Warehouse |
|----------|----------|----------------|--------------|----------|------|------|-----------|
| CurrentF | 10/10/22 | US-101         |              | 25       | Ea   | 1    | 11        |

And there is a purchase order for US-101 for quantity 25 site 1 wh 11 10/10/22

When master planning is run, it will create a planned purchase order for quantity for US-101 for quantity 25 site 1 wh 11 10/10/22. In other words, the existing purchase order will not reduce as forecast reduction method is none.

If that planned order is firmed or part of it, then it will reduce. For example, let's modify the quantity of the order to 15 and then approve it.

Then when running master planning again, it will create a planned purchase order for quantity for US-101 for quantity 10 site 1 wh 11 10/10/22.

## Check that an order is supply forecast order

You can always check if an order is coming from a supply forecast by seeing that on the planned orders the checkmark "Supply forecast" on the General tab in the Planned order is set to "yes".

## Differences between classic planning and planning optimization

There are some differences between supply forecasts in classic planning and planning optimization, considered after industry standards and use of the feature. They are detailed in the following sections.

### Vendor group

While adding forecasted lines, vendor and vendor group can be specified. In classic master planning, the created planned orders are grouped by the combination of those two values, while in Planning Optimization they are grouped by vendor.

For example, given the supply forecast lines for an item:

| Model    | Date     | Vendor account | Vendor group | Quantity | Unit | Site | Warehouse |
|----------|----------|----------------|--------------|----------|------|------|-----------|
| CurrentF | 10/10/22 |                | VendorGroupA | 5        | Ea   | 1    | 11        |
| CurrentF | 10/10/22 |                | VendorGroupA | 6        | Ea   | 1    | 11        |
| CurrentF | 10/10/22 |                |              | 7        | ea   | 1    | 11        |

And default vendor vendorA for the VendorGroup A. And default vendorA for the item.

With classic master planning, the following orders will be created:

- Planned purchase order for quantity 11 VendorA VendorGroupA

- Planned purchase order for quantity 7 Vendor A

With Planning Optimization, the following orders will be created:

- Planned purchase order for quantity 18 for VendorA VendorGroupA

### Reduction of general forecasts with a more specific one

In classic planning, the result is non-deterministic when having different forecasts, with and without a vendor. In planning optimization general forecasts will always be reduced by more specific ones, as in the example:

In the planning service, general forecasts are reduced by the more specific ones:

| Date       | Quantity | Vendor   | Vendor group  |
|------------|----------|----------|---------------|
| 02/11/2022 | 5.00     | Vendor-A | VendorGroup-A |
| 02/11/2022 | 6.00     | Vendor-A | VendorGroup-A |
| 02/11/2022 | 15.00    |          |               |

will result in:

| Date       | Quantity | Vendor   | Vendor group  |
|------------|----------|----------|---------------|
| 02/11/2022 | 11.00    | Vendor-A | VendorGroup-A |
| 02/11/2022 | 4.00     | Vendor-A | VendorGroup-A |

because general forecast 15.00 is reduced by the more specific one (5.00+6.00) and assigned a default vendor afterwards.

### Respect default order settings when generating planned orders

An item can have different default order settings, for example we can set minimum purchase order quantity etc.

These settings are respected when it comes to generating planned orders from supply forecasts.  
In classic planning, these settings are ignored, and we just translate forecast into planned order with the same quantity.

### Reduction by approved orders aggregates planned orders

In classic planning it is assumed that only one order will reduce the existing supply forecast, and if there are several orders matching the supply forecast line, only the first one will reduce.

In planning optimization, all orders matching the supply forecast line will reduce it.

### Forecasts are reduced only by matching vendor

In classic planning, when we reduce by existing released purchase orders, we do not make sure that vendor field from the purchase orders matches the one from the forecast.  
In Planning Service, we reduce forecasts only by purchase orders that have the same vendor field value.

For transfer and production orders, vendor field is ignored as it is not specified anyway for those orders

### Reducing forecasts by transfer orders

If default order type for the item is transfer, forecasts can only be reduced by existing planned transfer orders. However, for production and purchase only released orders reduce the supply forecast.

In the Planning Service we reduce only by transfer orders that are *released*.

