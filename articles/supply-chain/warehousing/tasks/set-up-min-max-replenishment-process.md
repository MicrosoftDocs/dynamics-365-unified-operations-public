---
title: Set up a min-max replenishment process
description: Learn how to set up a replenishment process that uses the minimum/maximum replenishment strategy, including a step-by-step process.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ai-usage: ai-assisted
ms.search.form: WHSInventFixedLocation, WHSLocDirTable, WHSWorkTemplateTable, WHSReplenishmentTemplates, SysRecurrence
ms.topic: how-to
ms.date: 10/30/2026
ms.custom:
  - bap-template
---

# Set up a min-max replenishment process

[!INCLUDE [banner](../../includes/banner.md)]

This article shows how to set up a replenishment process that uses the minimum/maximum replenishment strategy. When inventory falls below the minimum level, the system creates work to replenish the location. This article also shows how to use fixed picking locations to allow restocking even if inventory falls below the minimum level, and how to run the replenishment process regularly by using a batch job. A warehouse manager typically carries out these tasks.

You can run these procedures by using the USMF demo data company with the example values provided here, or you can run them on your own data. If you're using your own data, ensure that you have a warehouse that's enabled for warehouse management processes (WMS).

The setup consists of four parts, which you must complete in order, because each part refers to the previous one:

1. An optional fixed picking location, which lets the system replenish a location that has no inventory left.
1. A location directive, which determines where inventory is picked from.
1. A work template, which creates the pick and put work.
1. A replenishment template, which defines the items, quantities, and locations to replenish.

> [!CAUTION]
> When the following conditions are met, the system might create replenishment work that results in a conflict when processing that work:
>
> - The system is replenishing batch-tracked items.
> - Your reservation hierarchy has the *Batch number* dimension below the *Location* dimension.
> - Mixing of batch numbers isn't allowed at the put location.
>
> The conflict might occur because only *batch above location* items are assigned batch-number information on work lines and the *Replenishment* location directive's *Put* work type isn't used.

## Create a fixed picking location

This task is optional. However, if you use a fixed picking location, the system can replenish the location even when no inventory is left there because it can determine which item belongs at the location.

1. Go to **Warehouse management** > **Setup** > **Warehouse** > **Fixed locations**.
1. On the Action Pane, select **New**.
1. Set the following fields for the new row:

    - **Item number** – Select the item that should always be stocked at the location. If you're using USMF, select item *A0001*.
    - **Site** and **Warehouse** – Select the site and warehouse where the location is. If you're using USMF, select site *2* and warehouse *24*.
    - **Location** – Select the picking location that's reserved for the item. If you're using USMF, select location *CP-003*.

1. On the Action Pane, select **Save**.

## Create a replenishment location directive

Location directives determine where items are picked from during the replenishment process.

1. Go to **Warehouse management** > **Setup** > **Location directives**.
1. In the **Work order type** field, select *Replenishment*.
1. On the Action Pane, select **New**.
1. Set the following fields for the new directive:

    - **Name** – Enter a name that identifies the purpose of the directive.
    - **Work type** – Select *Pick*.
    - **Site** and **Warehouse** – Select the site and warehouse that the directive applies to. If you're using USMF, select site *2* and warehouse *24*.

1. On the Action Pane, select **Save**.
1. On the **Lines** FastTab, select **New**, and then set the following fields:

    - **To quantity** – Enter the upper quantity limit that the line applies to. Set this value high enough to cover the quantities that you expect to replenish.
    - **Allow split** – Select this check box to let the work creation process split a work line quantity across multiple locations.

1. On the **Location directive actions** FastTab, select **New**, enter a **Name** for the action, and then select **Save**.
1. With the action selected, on the Action Pane, select **Edit query** to restrict where inventory can be picked from. For example, you can limit selection to the bulk area of the warehouse. Select **OK** when you're done.

Learn more about the settings that are available for location directives in [Work with location directives](../create-location-directive.md).

## Create a replenishment work template

The work template guides the system when it creates min/max replenishment work. At a minimum, it must include one work template line for a pick and one for a put. The template shows a status of *Invalid* until you fill in all the required information.

1. Go to **Warehouse management** > **Setup** > **Work** > **Work templates**.
1. In the **Work order type** field, select *Replenishment*.
1. On the Action Pane, select **New**.
1. In the **Work template** field, enter a name that identifies the template.
1. On the Action Pane, select **Save**.
1. On the **Work template details** FastTab toolbar, select **New**, and then set **Work type** to *Pick* and **Work class ID** to a work class that's set up for replenishment. If you're using USMF, select work class *Replenish*.
1. Select **New** on the toolbar again, and then set **Work type** to *Put* and **Work class ID** to the appropriate work class.
1. On the Action Pane, select **Save**.

> [!NOTE]
> When you use a replenishment template where the **Replenishment type** field is set to *Minimum or maximum*, you define the location to replenish as part of the replenishment template setup, not by the location directive's *Put* work type.

## Create a replenishment template

The replenishment template defines the items and quantities to replenish, and the locations to replenish them to.

1. Go to **Warehouse management** > **Setup** > **Replenishment** > **Replenishment templates**.
1. On the Action Pane, select **New**.
1. Set the following fields for the new template:

    - **Replenish template** – Enter a name that identifies the template as a min/max template.
    - **Description** – Enter a short description of the template's purpose.
    - **Replenishment type** – Select *Minimum or maximum*.
    - **Allow wave demand to use unreserved quantities** – Select this check box to let wave demand replenishment consume quantities that min/max replenishment work already created but didn't reserve. This setting is useful when min/max replenishment work isn't processed immediately, because it prevents unnecessary demand replenishment work from being created.

1. On the **Replenishment template details** FastTab toolbar, select **New**, and then set the following fields for the new line:

    - **Sequence number** – Enter a number that sets the order in which lines are evaluated when replenishment runs. You can't change this number after you save the line, and it can't be negative.
    - **Description** – Enter a short description of what the line replenishes.
    - **Replenishment unit** – Select the unit that replenishment work is created in. This field is required. It lets you replenish in a different unit than the one that the minimum and maximum levels are expressed in. For example, you can set minimum and maximum levels in pieces but replenish in boxes.
    - **Demand increment** – Select whether a calculated replenishment quantity that doesn't divide evenly into whole replenishment units is rounded up or down.
    - **Request type** – Optionally, select a request type to categorize the replenishment requests that the line generates.
    - **Directive code** – Optionally, select the directive code that identifies which location directive to use. If you leave this field blank but the location directive has a directive code, the location directive is ignored, even if its query matches.
    - **Work template** – Select the replenishment work template that you created earlier.
    - **Minimum quantity** – Enter the quantity that triggers replenishment when on-hand inventory falls below it. You can leave this value at 0 if you're replenishing a fixed location and you set **Replenish empty fixed locations** to *Yes*.
    - **Maximum quantity** – Enter the quantity to replenish up to. This value can't be less than the minimum quantity.
    - **Unit** – Select the unit that the minimum and maximum quantities are expressed in.
    - **Replenish empty fixed locations** – Select this check box to replenish fixed locations when they're empty. Otherwise, only locations that have an on-hand quantity are replenished.
    - **Replenish only fixed locations** – Select this check box to limit replenishment to fixed locations. This setting is recommended for performance reasons when you replenish fixed locations.

1. On the Action Pane, select **Save**.
1. Select **Select products** to define which products the line replenishes. You can define criteria per product or per product variant.
1. Select the **Items** row, and then, in the **Criteria** field, enter the items to replenish. For example, enter *A\** to select all item numbers that begin with *A*.
1. To restrict replenishment to fixed picking locations in a specific area of the warehouse, select **Add** to add the **Locations** table to the query (unless it's already there). Then set **Field** to *Location profile ID* and enter the profile to restrict to in the **Criteria** field.
1. Select **OK**.

> [!NOTE]
> If you set the **Replenishment threshold scope** field to *Zone*, the line can't use **Replenish only fixed locations**, and it can't use product variant criteria. Use fixed locations and standard min/max replenishment instead, or switch the scope back to the location level. Learn more in [Zone threshold replenishment](../zone-threshold-replenishment.md).

## Run the replenishment process as a batch job

Use the **Replenishments** page to run replenishment as a batch job or to require that you start it manually. Typically, min/max replenishment runs once a day, so that all picking locations are filled to the maximum level before picking starts.

1. Go to **Warehouse management** > **Replenishment** > **Replenishments**.
1. Select **Filter**, set the **Criteria** field to select the replenishment templates to run, and then select **OK**.
1. Expand the **Run in the background** section, and set the **Batch processing** option to *Yes*.
1. Select **Recurrence**, and then set up the schedule to use. For example, select the **No end date** option and set the recurrence pattern to run daily.
1. Select **OK** to close the recurrence dialog, and then select **OK** to save the batch job.

## Related information

- [Replenishment overview](../replenishment.md)
- [Replenishment strategies](../replenishment-strategies.md)
- [Zone threshold replenishment](../zone-threshold-replenishment.md)
- [Immediate replenishment](../immediate-replenishment.md)
- [Replenishment over location capacity](../replenishment-over-location-capacity.md)
- [Work with location directives](../create-location-directive.md)
