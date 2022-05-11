---
title: Safety stock fulfillment for items
description: This topic discusses safety stock fulfillment and how to set up safety stock quantity for items. 
author: t-benebo
ms.date: 8/23/2021
ms.topic: article
ms.search.form: ReqSafetyKey, ReqItemTableSetup, ReqItemJournalName, ReqItemTable, EcoResProductDetailsExtended, ReqSafetyKeyDefaultDataWizard
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: benebotg
ms.dyn365.ops.version: 7.3 
ms.search.validFrom: 2017-12-31
---

# Safety stock fulfillment for items

[!include [banner](../includes/banner.md)]

Safety stock indicates an additional quantity of an item held in the inventory in order to reduce the risk that the item will be out of stock. Safety stock is used as a buffer stock in case sales orders come in and the supplier is unable to deliver the additional items to meet the customer's requested ship date. When safety stock is used to fulfill a sales order, the safety stock will be reduced. You can use Master planning to automatically bring the inventory back to the safety level.

## Set up safety stock levels for items

Safety stock is set up as part of item coverage on the **Item coverage** page under **Released products \> Plan \> Coverage**.

In the **Minimum** field, enter the safety stock level that you want to maintain for the item. The value is expressed in inventory units. If you leave the field blank, the default value is zero. This field is available when you select **Period**, **Requirement**, or **Min/Max** in the **Coverage code** list. The stock level limit applies to the available inventory, which means that reservations and markings may trigger safety stock replenishment before the physical quantity goes below the specified minimum level.

> [!NOTE]
> You must define all other planned coverage dimensions before you can define the **Minimum** field. This prevents an invalid record from being used during master planning. This situation can occur if, for example, a dimension group is extended with an additional planned coverage dimension for which the minimum and maximum inventory quantities are not yet defined.

You can use minimum keys to handle seasonal fluctuations in demand. For example, you can decrease the minimum inventory level for an item in the off-season, and then gradually increase the level during the other months. You create a minimum key by going to **Master planning \> Setup \> Coverage \> Minimum/maximum keys**. You specify the minimum key to adjust the safety stock level by seasonality in the **Minimum key** field on the **Item coverage** page.

## Example: Minimum key

The following procedure is an example that shows how to set up a minimum key that accounts for increased seasonal demand during the spring and summer months.

1. Go to **Master planning \> Setup \> Coverage \> Minimum/maximum keys**.
1. Select **New** to create a minimum/maximum key.
1. In the **Minimum or maximum key** field, enter an identifier for the key. In the **Name** field, enter a name for the key.
1. Set the **Use the effective date** option to *Yes* and leave the **Effective date** field blank to make the key valid from the first day of the current year.

    > [!NOTE]
    > The combination of the **Use the effective date** and **Effective date** settings defines the date that the key is valid from.
    >
    > - When the **Use the effective date** option is set to *No*, the key is valid from the current date or system date.
    > - When the **Use the effective date** option is set to *Yes*, the key is valid from the date that is defined in the **Effective date** field.

1. In the **Periods** section, create 12 lines, and set the following values for them:

    - **Change** – Assign each line a unique number from 1 through 12. This field indicates the incremental change in the unit of time that is defined by the **Unit** field.
    - **Unit** – Select *Months* for every line.
    - **From date**, **To date**, and **Month** – These fields are automatically set, based on the **Change** and **Unit** settings. Monthly periods start from the first day of the current year.
    - **Factor** – Enter the values that are described in the following table. This field defines the factor that you want to multiply the minimum inventory by.

        | Line (Change) | Factor | Result |
        |---|---|---|
        | 1–3 | 1 | Minimum inventory is based on the setting for January through March on the **Item coverage** page. |
        | 4–5 | 2 | Minimum inventory is multiplied by a factor of 2 for April through May. |
        | 6–8 | 2.5 | Minimum inventory is multiplied by a factor of 2.5 for June through August. |
        | 9–12 | 1 | Minimum inventory reverts to the setting for September through December on the **Item coverage** page. |

    Your settings should now resemble the settings in the following illustration.

    ![Minimum or maximum key periods.](media/min-max-key-periods.png "Minimum or maximum key periods")

> [!NOTE]
> You can also use a wizard to create a minimum/maximum key. On the **Minimum or maximum keys** page, on the Action Pane, select **Wizard** to open the **Minimum/Maximum Keys** wizard. The wizard will guide you step by step through the process of creating and setting up the minimum/maximum key.

If the coverage code is *Min/Max*, you can also specify the maximum inventory quantity that you want to maintain for an item. The value is also expressed in inventory units. If the projected available inventory falls below the minimum quantity, master planning generates a planned order to fulfill all open requirements and brings the available inventory up to the specified maximum quantity. Just as when you set up the minimum inventory quantity, you must define all other planned coverage dimensions before you can set the **Maximum** field.

## Example: Min/Max coverage code

The minimum quantity is 10, and the maximum quantity is 15. Current on-hand inventory is 4. This gives a minimum quantity requirement of 6. However, because the maximum quantity is 15, master planning generates a planned order for 11 items.

For items that follow seasonal demands, you may need to maintain different maximum levels. To do that, you need to define **Maximum keys** by going to **Master planning \> Setup \> Coverage \> Minimum/maximum keys**. Fill in the **Maximum key** field on the **Item coverage** page. You can view the information about the safety stock levels, defined via minimum keys on the **Min/Max** tab, on the **Item coverage** page. You need to make sure that, for a certain period, the minimum and the maximum values are kept in sync.

## Safety stock fulfillment

The **Fulfill minimum** parameter allows you to select the date or the period during which the inventory level must meet the quantity that you specified in the **Minimum** field. This field is available when you select **Period**, **Requirement**, or **Min/Max** in the **Coverage code** list.

If **Minimum keys** are used, select the **Minimum periods** check box to fulfill the minimum inventory level for all the periods that are set up in the minimum key. If you clear the check box, the minimum inventory is fulfilled for the current period only.

The following scenario shows how this parameter works and what are the differences between its values.

> [!NOTE]
> For all the illustrations in this topic, the x-axis represents inventory, the y-axis represents days, the bars represent the inventory level, the arrows represent transactions, such as sales order lines, purchase order lines, or planned orders.

[![Common scenario for safety stock fulfillment.](media/Scenario1.png)](media/Scenario1.png)

The **Fulfill minimum** parameter can have the following values:

### Today's date

The specified minimum quantity is met on the date when master planning is run. The system tries to fulfill the safety stock limit as soon as possible, even though it may be unrealistic due to the lead time.

[![Requirement on today's date.](media/TodayReq.png)](media/TodayReq.png)

Planned order P1 is created for today's date to bring the available inventory above the safety stock level on this date. The sales order lines S1 to S3 continue to lower the inventory level. Planned orders P2 to P4 are generated by master planning so that the inventory level is brought back to the safety limit after each sales order requirement.

When the **Requirement** coverage code is used, multiple planned orders are created. It is always a good idea to use either **Period** or **Min/Max** coverage for items and materials in frequent demand, to bundle the replenishment. The following illustration shows an example for coverage code **Period**.

[![Period. Today's date.](media/TodayPeriod.png)](media/TodayPeriod.png)

The following illustration shows an example for coverage code **Min/Max**.

[![Min/Max. Today's date.](media/TodayMinMax.png)](media/TodayMinMax.png)

### Today's date + procurement time

The specified minimum quantity is met on the date when master planning is run, plus the purchase or production lead time. This time includes any safety margins. If the item carries a trade agreement, and the **Find trade agreements** check box is selected on the **Master planning parameters** page, the delivery lead time from the trade agreement is not considered. Lead times are taken from the item's coverage settings or from the item.

This fulfillment mode will create plans with less delays and fewer planned orders, regardless of the coverage group set up on the item.

The following illustration shows the outcome of the plan if the coverage code is **Requirement** or **Period**.

[![Requirement or Period. Today's date and lead time.](media/TodayPLTReq.png)](media/TodayPLTReq.png)

The following illustration shows the outcome of the plan if the coverage code is **Min/Max**.

[![Min/max. Today's date and lead time.](media/TodayPLTMinMax.png)](media/TodayPLTMinMax.png)

### First issue

The specified minimum quantity is met on the date when the available inventory goes below the minimum level, as shown in the following illustration. Even if the available inventory is below the minimum level on the date when master planning is run, **First issue** will not attempt to cover it until the next requirement comes in.

The following illustration shows an example for coverage code **Requirement**.

[![Planning an item with Requirement coverage code and First issue fulfillment.](media/FirstIssueReq.png)](media/FirstIssueReq.png)

The following illustration shows an example for coverage code **Period**.

[![Planning an item with Period coverage code and First issue fulfillment.](media/FirstIssuePeriod.png)](media/FirstIssuePeriod.png)

The following illustration shows an example for coverage code **Min/Max**.

[![Planning an item with MinMax coverage code and First issue fulfillment.](media/FirstIssueMinMax.png)](media/FirstIssueMinMax.png)

On the date when master planning is run, if the available inventory is already under the safety stock limit, **Today's date** and **Today's date + procurement time** will trigger the replenishment immediately. **First issue** will wait until there is another issue transaction, such as sales order and BOM line requirement, for the item, and then it will trigger the replenishment on the date of this transaction.

On the date when master planning is run, if the available inventory isn't under the safety stock limit, **Today's date** and **First issue** will provide exactly the same result, as shown in the following illustration.

[![Not under limit.](media/ReqFirstIssue.png)](media/ReqFirstIssue.png)

On the date when master planning is run, if the available inventory is not under the safety stock limit, **Today's date + procurement time** will provide the following result, because it postpones the fulfillment until the end of the procurement lead time.

![Fulfillment postponed until the end of the procurement lead time.](media/ReqTodayLT.png)

### Coverage time fence

The specified minimum quantity is met during the period that is specified in the **Coverage time fence** field. This option is useful when master planning does not allow available inventory to be used for real orders, such as sales or transfers, in the attempt to maintain the safety level. However, in a future release, this mode of replenishment will no longer be needed, and this option will be deprecated.

## Plan safety stock replenishment for First Expired, First Out (FEFO) items

At any point in time, the inventory receipt with the latest expiry date will be used for safety stock to allow real demand, such as sale lines or BOM lines, to be fulfilled in the FEFO (First Expired, First Out) order.

To show how this works, consider the following scenario.

[![FEFO Scenario.](media/FEFOScenario.png)](media/FEFOScenario.png)

When planning is run, it will cover the first sales order from the existing on-hand inventory and an additional purchase order, for the remaining quantity.

[![FEFO 1.](media/FEFO1.png)](media/FEFO1.png)

A planned order is created to make sure that the available inventory is brought back to the safety limit.

[![FEFO 2.](media/FEFO2.png)](media/FEFO2.png)

When the second sales order is planned, the previously created planned order that covers the safety stock is used to cover this quantity. Hence, the safety stock is constantly rolling.

[![FEFO 3.](media/FEFO3.png)](media/FEFO3.png)

Finally, another planned order is created to cover the safety stock.

[![FEFO 4.](media/FEFO4.png)](media/FEFO4.png)

All the batches expire accordingly, and planned orders are created to refill the safety stock after it has expired.

## How master planning handles the safety stock constraint

Safety stock is tracked in the system as a requirement type, just like sales lines or BOM requirements. You can see the safety stock requirement line on the **Net requirements** page if you remove the default filter on the **Requirement type** column.

Fulfilling the safety stock requirement transaction is deprioritized if the system determines that this causes delays in the fulfillment of real demand, such as sales lines, BOM lines, transfer requirements, or demand forecast lines. Otherwise, making sure that the available inventory is above the safety stock quantity has the same priority as any other demand types. This ensures no delays for real transactions and helps to prevent over-replenishment and early-replenishment of safety stock.

During the coverage phase of master planning, safety stock replenishment is no longer deprioritized. On-hand inventory can be used before any other demand types. During the delay calculation, new logic will be added to go over the delayed sales lines, BOM line requirements, and all the other demand types, to determine whether they could be delivered on time, provided that the safety stock is used. If the system identifies that it can minimize delays by using safety stock, then the sales lines or BOM lines will replace their initial coverage with the safety stock, and the system will trigger the replenishment for the safety stock instead.

If the plan or the item is not set up for delayed calculation, then the safety stock constraint will have the same priority as any other demand types. This means there is a reserve of on-hand and other available inventory before other demand types.

## Additional resources

- [Use the safety stock journal to update minimum coverage for items](safety-stock-journal.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
