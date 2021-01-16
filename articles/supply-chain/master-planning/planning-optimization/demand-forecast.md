---
# required metadata

title: Master planning with demand forecasts
description: This topic explains how to include demand forecasts during master planning with Planning Optimization.
author: ChristianRytt
manager: tfehr
ms.date: 12/02/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: MpsIntegrationParameters, MpsFitAnalysis
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: crytt
ms.search.validFrom: 2020-12-02
ms.dyn365.ops.version: AX 10.0.13

---
# Master planning with demand forecasts

[!include [banner](../../includes/banner.md)]

You can use a demand forecast together with Planning Optimization to account for expected demand in your master planning. You can manually create a demand forecast, import it, or generate it by using the demand forecasting functionality in Microsoft Dynamics 365 Supply Chain Management. For more information about demand forecasting, see [Demand forecasting overview](../introduction-demand-forecasting.md).

> [!NOTE]
> Separate forecast planning isn't supported with Planning Optimization. Therefore, the **Current forecast plan** setting on the **Master planning parameters** page has no effect when you use Planning Optimization.

## Set up a master plan to include a demand forecast

To configure a master plan so that it includes a demand forecast, follow these steps.

1. Go to **Master planning \> Setup \> Plans \> Master plans**.
1. Select an existing plan, or create a new plan.
1. On the **General** FastTab, set the following fields:

    - **Forecast model** – Select the forecast model to apply. This model will be considered when a supply suggestion is generated for the current master plan.
    - **Include demand forecast** – Set this option to *Yes* to include the demand forecast in the current master plan. If you set it to *No*, demand forecast transactions won't be included in the master plan.
    - **Method used to reduce forecast requirements** – Select the method that should be used to reduce forecast requirements. For more information, see the [Forecast reduction keys](#reduction-keys) section later in this topic.

1. On the **Time fence in days** FastTab, you can set the following fields to specify the period that the demand forecast is included during:

    - **Forecast plan** – Set this option to *Yes* to override the forecast plan time fence that originates from the individual coverage groups. Set it to *No* to use the values from the individual coverage groups for the current master plan.
    - **Forecast time period** – If you set the **Forecast plan** option to *Yes*, specify the number of days (from today's date) that the demand forecast should be applied.

    > [!IMPORTANT]
    > The **Forecast plan** setting isn't yet supported with Planning Optimization.

## Set up a coverage group to include a demand forecast

To configure a coverage group so that it includes a demand forecast, follow these steps.

1. Go to **Master planning \> Setup \> Plans \> Coverage groups**.
1. Select an existing coverage group, or create a new group.
1. On the **Other** FastTab, set the following fields:

    - **Forecast plan time fence** – Enter the number of days (from today's date) that the demand forecast should be applied for. This value can be overridden by using the **Forecast plan** option on the master plan, as described in the previous section.
    - **Reduction key** – Select the reduction key to apply. For more information, see the [Create and set up a forecast reduction key](#create-reduction-key) and [Use a reduction key](#use-reduction-key) sections later in this topic.
    - **Reduce forecast by** – For master plans where the **Method used to reduce forecast requirements** field is set to *Transactions - reduction key* or *Transactions - dynamic period*, specify which transactions should reduce the forecast. Select one of the following values:

        - **All transactions** – All transactions should reduce the forecast.
        - **Orders** – Only sales orders should reduce the forecast.

        > [!NOTE]
        > If you select *All transactions*, transactions that have both demand and supply in the same inventory dimensions are considered neutral and are ignored during the forecast reduction. For example, if the planning dimension is set to site only, not warehouse, a transfer order between site 1, warehouse 11, and site 1, warehouse 13, will be ignored and won't reduce the remaining demand forecast.

    - **Include intercompany orders** – Set this option to *Yes* if intercompany orders should be included when the forecast is reduced. Otherwise, set it to *No*.
    - **Include customer forecast in the demand forecast** – Specify whether a customer forecast should be included in the overall forecast. This option determines how actual demand reduces the forecasted demand. You can use it to ensure that master planning covers the supply of items that are purchased by specific customers.

        - Set this option to *Yes* to include a customer forecast in the overall forecast. In this case, actual customer demand reduces both the customer forecast and the overall forecast. Master planning generates planned orders to cover only the overall forecast quantity.
        - Set this option to *No* if you don't want to include a customer forecast in the overall forecast. In this case, actual customer demand reduces only the customer forecast. Master planning generates planned orders to cover both the overall forecast quantity and the forecast for each customer quantity.

## <a name="reduction-keys"></a>Forecast reduction keys

This section provides information about the different methods that are used to reduce forecast requirements. It includes examples of the results of each method. It also explains how to create, set up, and use a forecast reduction key. Some methods use a forecast reduction key to reduce forecast requirements.

### Methods that are used to reduce forecast requirements

When you include a forecast in a master plan, you can select how the forecast requirements are reduced when actual demand is included. Note that master planning excludes forecast requirements from the past, which means all forecast requirements before today's date.

To include a forecast in a master plan and select the method that is used to reduce forecast requirements, go to **Master planning \> Setup \> Plans \> Master plans**. In the **Forecast model** field, select a forecast model. In the **Method used to reduce forecast requirements** field, select a method. The following options are available:

- None
- Percent – reduction key
- Transactions – reduction key (not yet supported with Planning Optimization)
- Transactions – dynamic period

The following sections provide more information about each option.

#### None

If you select **None**, the forecast requirements aren't reduced during master scheduling. In this case, master planning creates planned orders to supply the forecasted demand (forecast requirements). These planned orders maintain the suggested quantity, regardless of other types of demand. For example, if sales orders are placed, master planning creates additional planned orders to supply the sales orders. The quantity of the forecast requirements isn't reduced.

#### Percent – reduction key

If you select **Percent - reduction key**, the forecast requirements are reduced according to the percentages and periods that are defined by the reduction key. In this case, master planning creates planned orders where the quantity is calculated as forecasted quantity × reduction key in each period. If there are other types of demand, master planning also creates planned orders to supply that demand.

##### Example: Percent – reduction key

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

#### Transactions – reduction key

If you select **Transactions - reduction key**, the forecast requirements are reduced by the transactions that occur during the periods that are defined by the reduction key.

##### Example: Transactions – reduction key

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

#### Transactions – dynamic period

If you select **Transactions - dynamic period**, the forecast requirements are reduced by the actual order transactions that occur during the dynamic period. The dynamic period covers the current forecast dates and ends at the start of the next forecast. In this case, master planning creates planned orders to supply the forecasted demand (forecast requirements). However, when actual order transactions are placed, the forecast requirements are reduced. The actual transactions consume part of the forecasted requirements.

When this option is used, the following behavior occurs:

- Reduction keys aren't required or used. 
- If the forecast is completely reduced, the forecast requirements for the current forecast become 0 (zero).
- If there is no future forecast, forecast requirements from the last forecast that was entered are reduced.
- Time fences are included in the forecast reduction calculation.
- Positive days are included in the forecast reduction calculation.
- If actual order transactions exceed the forecasted requirements, the remaining transactions aren't forwarded to the next forecast period.

##### Example 1: Transactions – dynamic period

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

##### Example 2: Transactions – dynamic period

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

### <a name="create-reduction-key"></a>Create and set up a forecast reduction key

A forecast reduction key is used in the **Transactions - reduction key** and **Percent- reduction key** methods for reducing forecast requirements. Follow these steps to create and set up a reduction key.

1. Go to **Master planning \> Setup \> Coverage \> Reduction keys**.
2. Select **New** or press **Ctrl+N** to create a reduction key.
3. In the **Reduction key** field, enter a unique identifier for the forecast reduction key. Then, in the **Name** field, enter a name. 
4. Define the periods and the reduction key percentage in each period:

    - The **Effective date** field indicates the date when creation of the periods starts. When the **Use the effective date** option is set to **Yes**, the periods start on the effective date. When it's set to **No**, the periods start on the date when master planning is run.
    - Define the periods that the forecast reduction should occur during.
    - For a specific period, specify the percentages that the forecast requirements should be reduced by. You can enter positive values to decrease requirements or negative values to increase requirements.

### <a name="use-reduction-key"></a>Use a reduction key

A forecast reduction key must be assigned to the coverage group of the item. Follow these steps to assign a reduction key to an item's coverage group.

1. Go to **Master planning \> Setup \> Coverage \> Coverage groups**.
2. On the **Other** FastTab, in the **Reduction key** field, select the reduction key to assign to the coverage group. The reduction key then applies to all items that belong to the coverage group.
3. To use a reduction key to calculate forecast reduction during master scheduling, you must define this setting in the setup of the forecast plan or the master plan. Go to one of the following locations:

    - Master planning \> Setup \> Plans \> Forecast plans
    - Master planning \> Setup \> Plans \> Master plans

4. On the **Forecast plans** or **Master plans** page, on the **General** FastTab, in the **Method used to reduce forecast requirements** field, select either **Percent - reduction key** or **Transactions - reduction key**.

### Reduce a forecast by transactions

When you select **Transactions - reduction key** or **Transactions - dynamic period** as the method for reducing forecast requirements, you can specify which transactions reduce the forecast. On the **Coverage groups** page, on the **Other** FastTab, in the **Reduce forecast by** field, select **All transactions** if all transactions should reduce the forecast or **Orders** if only sales orders should reduce the forecast.
