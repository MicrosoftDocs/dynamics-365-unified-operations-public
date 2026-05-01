---
title: Safety stock fulfillment for items
description: Learn about safety stock fulfillment and how to set up safety stock quantity for items with a process for setting the safety stock level for an item. 
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form: ReqSafetyKey, ReqItemTableSetup, ReqItemJournalName, ReqItemTable, EcoResProductDetailsExtended, ReqSafetyKeyDefaultDataWizard
ms.topic: how-to
ms.date: 03/26/2026
ms.custom: 
  - bap-template
---

# Safety stock fulfillment for items

[!include [banner](../includes/banner.md)]

Safety stock is an item quantity that you hold in inventory to reduce the risk that the item runs out of stock. Use safety stock when the demand from sales orders is more than planned for final goods, and when a supplier can't deliver additional units in the expected time.

The system always tries to prevent the accumulated quantity of an item from falling below its safety stock limit. Whenever the master planning engine detects that the accumulated on-hand inventory for an item will fall below its minimum, it creates a planned order to replenish the item and schedules the order to arrive before the minimum threshold is crossed. Therefore, the system fulfills safety stock on *Today's date* + *Procurement time*.

During planning, if there's actual demand, the system pegs it against a planned order generated for safety stock provided it enables the demand to be fulfilled on time and strict [safety stock pegging](safety-stock-pegging.md) isn't enforced. Because the system always tries to keep the accumulated on-hand inventory level above the safety stock level, it creates a new planned order to cover the safety stock that the actual demand claimed. When strict safety stock pegging is enforced, actual demand isn't pegged against a planned order generated for safety stock.  

> [!NOTE]
> Because safety stock isn't really demand, any demand is prioritized over the safety stock when strict safety stock pegging is off. Therefore, the system can create a planned order to fulfill safety stock, but if actual demand arrives later, that demand can claim the safety stock quantity. (The new demand is pegged against the original planned order.)

## Set the safety stock level for an item

To define safety stock for an item at a specific location, follow these steps:

1. Go to **Product information management** \> **Products** \> **Released products**.
1. Select the relevant product in the grid.
1. On the Action Pane, on the **Plan** tab, select **Item coverage**.
1. While you're on the **Overview** tab, select **New** on the Action Pane to add a line to the grid.
1. For the new line, specify the relevant product dimensions (**Site**, **Warehouse**, and other dimensions as required, such as **Color** or **Style**).
1. In the **Minimum** field, enter the safety stock value. The master planning engine always generates planned orders to prevent the accumulated inventory level from falling below this limit. The value is expressed in inventory units. If you leave the field blank, a default value of **0** (zero) is used.

> [!NOTE]
> The **General** tab of the **Item coverage** page includes a **Fulfill minimum** field. When you use Planning Optimization, the setting of this field is ignored. (Instead, the system always behaves as though **Fulfill minimum** is set to *Today's date + procurement time*.) For information about how the **Fulfill minimum** setting works when you use the deprecated master planning engine, see [Safety stock fulfillment with the deprecated planning engine](safety-stock-replenishment-in-deprecated-engine.md).

## Example: Safety stock

Set up your system as follows:

- The warehouse has 30 units of total on-hand inventory of item Z0001.
- A demand forecast shows that 2 units of item Z0001 are consumed every day.
- The safety stock for item Z0001 is set to 20 units.
- The lead time for item Z0001 is five days.

When you run master planning, it creates several orders to ensure that the accumulated on-hand inventory stays above the safety stock threshold. The following table provides an example.

| Reference | Item number | Requirement date | Requirement quantity | Accumulated |
|---|---|---|---|---|
| Demand forecast | Z0001 | 3/31/2023 | -6.00 | 24 |
| Demand forecast | Z0001 | 4/3/2023 | -2.00 | 22 |
| Demand forecast | Z0001 | 4/4/2023 | -2.00 | 20 |
| Planned purchase orders | Z0001 | 4/5/2023 | 2.00 | 22 |
| Demand forecast | Z0001 | 4/5/2023 | -2.00 | 20 |

Therefore, the **Net requirements** page for item Z0001 might resemble the following example.

:::image type="content" source="media/safety-stock-example.png" alt-text="Example of safety stock on the Net requirements page.":::

## Example: Minimum key

Use minimum keys to handle seasonal fluctuations in demand. For example, you can decrease the minimum inventory level for an item during the off-season and then gradually increase it during the other months.

To create a minimum key, go to **Master planning** \> **Setup** \> **Coverage** \> **Minimum/maximum keys**. You can then specify the minimum key to adjust the safety stock level by seasonality by setting the **Minimum key** field on the **General** tab of the **Item coverage** page.

If you're using minimum keys, set the **Minimum periods** option to *Yes* to fulfill the minimum inventory level for all the periods that are set up in the minimum key. If you set the option to *No*, the minimum inventory is fulfilled for the current period only.

The following procedure shows an example of how to set up a minimum key that accounts for increased seasonal demand during the spring and summer months.

1. Go to **Master planning** \> **Setup** \> **Coverage** \> **Minimum/maximum keys**.
1. Select **New** to create a minimum/maximum key.
1. In the **Minimum or maximum key** field, enter an identifier for the key. In the **Name** field, enter a name for the key.
1. Set the **Use the effective date** option to *Yes* and leave the **Effective date** field blank to make the key valid from the first day of the current year.

    > [!NOTE]
    > The combination of the **Use the effective date** and **Effective date** settings defines the date that the key is valid from.
    >
    > - When the **Use the effective date** option is set to *No*, the key is valid from the current date or system date.
    > - When the **Use the effective date** option is set to *Yes*, the key is valid from the date defined in the **Effective date** field.

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

    Your settings now resemble the settings in the following illustration.

    :::image type="content" source="media/min-max-key-periods.png" alt-text="Minimum or maximum key periods." lightbox="media/min-max-key-periods.png":::

> [!NOTE]
> You can also use a wizard to create a minimum/maximum key. On the **Minimum or maximum keys** page, on the Action Pane, select **Wizard** to open the **Minimum/Maximum Keys** wizard. The wizard guides you step by step through the process of creating and setting up the minimum/maximum key.

If the coverage code is *Min/Max*, you can also specify the maximum inventory quantity that you want to maintain for an item. The value is also expressed in inventory units. If the projected available inventory falls below the minimum quantity, master planning generates a planned order to fulfill all open requirements and brings the available inventory up to the specified maximum quantity. Just as when you set up the minimum inventory quantity, you must define all other planned coverage dimensions before you can set the **Maximum** field.

## Example: Min/max coverage code

The minimum quantity is 10, and the maximum quantity is 15. Current on-hand inventory is 4. This situation gives a minimum quantity requirement of 6. However, because the maximum quantity is 15, master planning generates a planned order for 11 items.

For items that follow seasonal demands, you might need to maintain different maximum levels. To set up these levels, define **Maximum keys** by going to **Master planning** \> **Setup** \> **Coverage** \> **Minimum/maximum keys**. Fill in the **Maximum key** field on the **Item coverage** page. You can view the information about the safety stock levels, defined through minimum keys on the **Min/Max** tab, on the **Item coverage** page. Make sure that, for a certain period, the minimum and the maximum values stay in sync.

## Plan safety stock replenishment for FEFO items

At any point in time, the inventory receipt with the latest expiry date is used for safety stock. This approach ensures that real demand, such as sales lines or BOM lines, is fulfilled in the first expired, first out (FEFO) order.

To see how this process works, consider the following scenario:

:::image type="content" source="media/fefo-scenario.png" alt-text="Diagram of FEFO inventory scenario showing stock levels, batch expiry dates, safety limit, and sales orders over four days." lightbox="media/fefo-scenario.png":::

When you run planning, it covers the first sales order from the existing on-hand inventory and an additional purchase order for the remaining quantity.

:::image type="content" source="media/fefo-example-1.png" alt-text="Screenshot of inventory planning screen showing sales order pegged to on-hand stock and planned purchase orders." lightbox="media/fefo-example-1.png":::

A planned order is created to bring the available inventory back to the safety limit.

:::image type="content" source="media/fefo-example-2.png" alt-text="Screenshot of inventory planning screen showing a planned purchase order created to cover safety stock, with pegging details displayed." lightbox="media/fefo-example-2.png":::

When you plan the second sales order, the previously created planned order that covers the safety stock is used to cover this quantity. Hence, the safety stock is constantly rolling.

:::image type="content" source="media/fefo-example-3.png" alt-text="Screenshot of inventory planning screen showing sales order pegged to safety stock replenishment with planned orders listed." lightbox="media/fefo-example-3.png":::

Finally, another planned order is created to cover the safety stock.

:::image type="content" source="media/fefo-example-4.png" alt-text="Screenshot of Net requirements page showing planned purchase orders and safety stock requirement for batch items." lightbox="media/fefo-example-4.png":::

All the batches expire accordingly, and planned orders are created to refill the safety stock after it expires.

## How master planning handles the safety stock constraint

The system tracks safety stock as a requirement type, just like sales lines or BOM requirements. You can see the safety stock requirement line on the **Net requirements** page if you remove the default filter on the **Requirement type** column.

If fulfilling the safety stock requirement causes delays in the fulfillment of real demand, such as sales lines, BOM lines, transfer requirements, or demand forecast lines, the system deprioritizes it. Otherwise, making sure that the available inventory is above the safety stock quantity has the same priority as any other demand types. This approach ensures no delays for real transactions and helps prevent over-replenishment and early replenishment of safety stock.

During the coverage phase of master planning, the system no longer deprioritizes safety stock replenishment. The system can use on-hand inventory before any other demand types. During the delay calculation, new logic goes over the delayed sales lines, BOM line requirements, and all the other demand types to determine whether they can be delivered on time, provided that the safety stock is used. If the system identifies that it can minimize delays by using safety stock, the sales lines or BOM lines replace their initial coverage with the safety stock, and the system triggers the replenishment for the safety stock instead.

If you don't set up the plan or the item for delayed calculation, the safety stock constraint has the same priority as any other demand types. This priority means there's a reserve of on-hand and other available inventory before other demand types.

## Related information

- [Use the safety stock journal to update minimum coverage for items](safety-stock-journal.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
