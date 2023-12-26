---
# required metadata

title: Forecast reduction keys
description: This article provides examples that show how to set up a reduction key. It includes information about the various reduction key settings and the results of each. You can use a reduction key to define how to reduce forecast requirements.
author: t-benebo
ms.date: 04/15/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: ReqPlanSched, ReqReduceKeyDefaultDataWizard, ReqReduceKey
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.assetid: aa9e0dfb-6052-4a2e-9378-89507c02fdf2
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: benebotg
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Forecast reduction keys

[!include [banner](../includes/banner.md)]

This article provides information about the different methods that are used to reduce forecast requirements. It includes examples of the results of each method. It also explains how to create, set up, and use a forecast reduction key. Some methods use a forecast reduction key to reduce forecast requirements.

## Methods that are used to reduce forecast requirements

When you include a forecast in a master plan, you can select how the forecast requirements are reduced when actual demand is included. Note that master planning excludes forecast requirements from the past, which means all forecast requirements before today's date.

To include a forecast in a master plan and select the method that is used to reduce forecast requirements, go to **Master planning \> Setup \> Plans \> Master plans**. In the **Forecast model** field, select a forecast model. In the **Method used to reduce forecast requirements** field, select a method. The following options are available:

- None
- Percent – reduction key
- Transactions – reduction key
- Transactions – dynamic period

The following sections provide more information about each option.

### None

If you select **None**, the forecast requirements aren't reduced during master scheduling. In this case, master planning creates planned orders to supply the forecasted demand (forecast requirements). These planned orders maintain the suggested quantity, regardless of other types of demand. For example, if sales orders are placed, master planning creates additional planned orders to supply the sales orders. The quantity of the forecast requirements isn't reduced.

### Percent – reduction key

If you select **Percent - reduction key**, the forecast requirements are reduced according to the percentages and periods that are defined by the reduction key. In this case, master planning creates planned orders where the quantity is calculated as forecasted quantity × reduction key in each period. If there are other types of demand, master planning also creates planned orders to supply that demand.

#### Example: Percent – reduction key

This example shows how a reduction key reduces demand forecast requirements according to the percentages and periods that are defined by the reduction key.

For this example, you include the following demand forecast in a master plan.

| Month    | Demand forecast |
|----------|-----------------|
| January  | 1,000           |
| February | 1,000           |
| March    | 1,000           |
| April    | 1,000           |

On the **Reduction keys** page, you set up the following lines.

| Change | Unit  | Percent |
|--------|-------|---------|
| 1      | Month | 100     |
| 2      | Month | 75      |
| 3      | Month | 50      |
| 4      | Month | 25      |

You assign the reduction key to the item's coverage group. Then, on the **Master plans** page, in the **Method used to reduce forecast requirements** field, you select **Percent - reduction key**.

In this case, if you run forecast scheduling on January 1, the demand forecast requirements are consumed according to the percentages that you set up on the **Reduction keys** page. The following requirement quantities are transferred to the master plan.

| Month                | Planned order quantity | Calculation    |
|----------------------|------------------------|----------------|
| January              | 0                      | = 0% × 1,000   |
| February             | 250                    | = 25% × 1,000  |
| March                | 500                    | = 50% × 1,000  |
| April                | 750                    | = 75% × 1,000  |
| May through December | 1,000                  | = 100% × 1,000 |

### Transactions – reduction key

If you set the **Method used to reduce forecast requirements** field to *Transactions - reduction key*, the forecast requirements are reduced by the qualified demand transactions that occur during the periods that are defined by the reduction key.

The qualified demand is defined by the **Reduce forecast by** field on the **Coverage groups** page. If you set the **Reduce forecast by** field to *Orders*, only sales order transactions are considered qualified demand. If you set it to *All transactions*, any non-intercompany issue inventory transactions are considered qualified demand. If intercompany sales orders should also be considered qualified demand, set the **Include intercompany orders** option to *Yes*.

Forecast reduction starts with the first (earliest) demand forecast record in the reduction key period. If the quantity of qualified inventory transactions is more than the quantity of demand forecast lines in the same reduction key period, the balance of inventory transactions quantity will not reduce previous or future periods. 

The value of the **Percent** field on the reduction key lines isn't used when the **Method used to reduce forecast requirements** field is set to *Transactions - reduction key*. Only the dates are used to define the reduction key period.

> [!NOTE]
> Any forecast that is posted on or before today's date will be ignored and won't be used to create planned orders. For example, if your demand forecast for the month is generated on January 1, and you run master planning that includes demand forecasting on January 2, the calculation will ignore the demand forecast line that is dated January 1.

#### Example: Transactions – reduction key

This example shows how actual orders that occur during the periods that are defined by the reduction key reduce demand forecast requirements.

For this example, you select **Transactions - reduction key** in the **Method used to reduce forecast requirements** field on the **Master plans** page.

The following sales orders exist on January 1.

| Month    | Number of pieces ordered |
|----------|--------------------------|
| January  | 956                      |
| February | 1,176                    |
| March    | 451                      |
| April    | 119                      |

If you use the same demand forecast of 1,000 pieces per month that was used in the previous example, the following requirement quantities are transferred to the master plan.

| Month                | Number of pieces required |
|----------------------|---------------------------|
| January              | 44                        |
| February             | 0                         |
| March                | 549                       |
| April                | 881                       |
| May through December | 1,000                     |

### Transactions – dynamic period

If you select **Transactions - dynamic period**, the forecast requirements are reduced by the actual order transactions that occur during the dynamic period. The dynamic period covers the current forecast dates and ends at the start of the next forecast. In this case, master planning creates planned orders to supply the forecasted demand (forecast requirements). However, when actual order transactions are placed, the forecast requirements are reduced. The actual transactions consume part of the forecasted requirements.

When this option is used, the following behavior occurs:

- Reduction keys aren't required or used. 
- If the forecast is completely reduced, the forecast requirements for the current forecast become 0 (zero).
- If there is no future forecast, forecast requirements from the last forecast that was entered are reduced.
- The demand forecast reduction time fence isn't included in the forecast reduction calculation. Instead, the coverage group time fence is used for forecast reduction.
- Positive days are included in the forecast reduction calculation.
- If actual order transactions exceed the forecasted requirements, the remaining transactions aren't forwarded to the next forecast period.

#### Example 1: Transactions – dynamic period

Here a simple example that shows how the **Transactions - dynamic period** method works.

For this example, you include the following demand forecast in a master plan.

| Date       | Demand forecast |
|------------|-----------------|
| January 1  | 1,000           |
| February 1 | 1,000             |

You also create the following sales orders.

| Date        | Sales order quantity |
|-------------|----------------------|
| January 15  | 200                  |
| February 15 | 400                  |

In this case, the following planned orders are created.

| Demand forecast date | Quantity | Explanation                           |
|--------------------- |----------|---------------------------------------|
| January 1            | 800      | Forecast requirements (= 1,000 – 200) |
| January 15           | 200      | Sales orders requirements             |
| February 1           | 600      | Forecast requirements (= 1,000 – 400) |
| February 15          | 400      | Sales orders requirements             |

#### Example 2: Transactions – dynamic period

In most cases, systems are set up so that transactions reduce demand forecast in specific forecast periods: weeks, months, and so on. These periods are defined in the reduction key. However, the time between two demand forecast lines can also *imply* a period.

For this example, you create a demand forecast for the following dates and quantities.

| Date       | Demand forecast |
|------------|-----------------|
| January 1  | 1,000           |
| January 5  | 500             |
| January 12 | 1,000           |

Notice that, in this forecast, there isn't a clear period between the forecast dates. Between the first and second dates there is a four-day span, and between the second and third dates there is a seven-day span. These spans are the dynamic periods.

You also create the following sales order lines.

| Date                             | Sales order quantity |
|----------------------------------|----------------------|
| December 15 in the previous year | 500                  |
| January 3                        | 100                  |
| January 10                       | 200                  |

In this case, the forecast is reduced in the following manner:

- Because the first sales order isn't in any period, it doesn't reduce any forecast.
- Because the second sales order is between January 1 and January 5, it reduces the forecast for January 1 by 100.
- Because the third sales order is between January 5 and January 12, it reduces the forecast for January 5 by 200.

Therefore, the following planned orders are created.

| Demand forecast date             | Quantity | Explanation                                                         |
|----------------------------------|----------|---------------------------------------------------------------------|
| December 15 in the previous year | 500      | Sales order requirements                                            |
| January 1                        | 900      | Forecast requirements period January 1 to January 5 (= 1,000 – 100) |
| January 3                        | 100      | Sales order requirements                                            |
| January 5                        | 300      | Forecast requirements period January 5 to January 10 (= 500 – 200)  |
| January 12                       | 1,000    | Forecast requirements period January 12 to end                      |

## Create and set up a forecast reduction key

A forecast reduction key is used in the **Transactions - reduction key** and **Percent- reduction key** methods for reducing forecast requirements. Follow these steps to create and set up a reduction key.

1. Go to **Master planning \> Setup \> Coverage \> Reduction keys**.
2. Select **New** to create a reduction key.
3. In the **Reduction key** field, enter a unique identifier for the forecast reduction key. Then, in the **Name** field, enter a name. 
4. Define the periods and the reduction key percentage in each period:

    - The **Effective date** field indicates the date when creation of the periods starts. When the **Use the effective date** option is set to **Yes**, the periods start on the effective date. When it's set to **No**, the periods start on the date when master planning is run.
    - Define the periods that the forecast reduction should occur during.
    - For a specific period, specify the percentages that the forecast requirements should be reduced by. You can enter positive values to decrease requirements or negative values to increase requirements.

## Use a reduction key

A forecast reduction key must be assigned to the coverage group of the item. Follow these steps to assign a reduction key to an item's coverage group.

1. Go to **Master planning \> Setup \> Coverage \> Coverage groups**.
2. On the **Other** FastTab, in the **Reduction key** field, select the reduction key to assign to the coverage group. The reduction key then applies to all items that belong to the coverage group.
3. To use a reduction key to calculate forecast reduction during master scheduling, you must define this setting in the setup of the forecast plan or the master plan. Go to one of the following locations:

    - Master planning \> Setup \> Plans \> Forecast plans
    - Master planning \> Setup \> Plans \> Master plans

4. On the **Forecast plans** or **Master plans** page, on the **General** FastTab, in the **Method used to reduce forecast requirements** field, select either **Percent - reduction key** or **Transactions - reduction key**.

## Reduce a forecast by transactions

When you select **Transactions - reduction key** or **Transactions - dynamic period** as the method for reducing forecast requirements, you can specify which transactions reduce the forecast. On the **Coverage groups** page, on the **Other** FastTab, in the **Reduce forecast by** field, select **All transactions** if all transactions should reduce the forecast or **Orders** if only sales orders should reduce the forecast.

## Additional resources

- [Master plans overview](master-plans.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
