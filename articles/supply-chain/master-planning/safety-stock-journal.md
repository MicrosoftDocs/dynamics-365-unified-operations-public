---
title: Use the safety stock journal to update minimum coverage for items
description: Learn how to use safety stock journal to update safety stock quantity for items by calculating minimum coverage proposals based on historical transactions.
author: t-benebo
ms.author: benebotg
ms.topic: article
ms.date: 10/28/2021
ms.reviewer: kamaybac
ms.search.form: ReqItemJournalName, ReqItemJournalSafetyStock, EcoResProductInformationDialog, ReqItemTableSetup, ReqItemTable, EcoResProductDetailsExtended
---

# Use the safety stock journal to update minimum coverage for items

[!include [banner](../../includes/banner.md)]

Safety stock indicates an additional quantity of an item that is held in inventory to help reduce the risk that the item will go out of stock. Safety stock is used as a buffer in case sales orders come in, but the supplier can't meet the customer's requested ship date.

This article describes how to use the safety stock journal to calculate minimum coverage proposals based on historical transactions and then update the item coverage with the proposals.

## Overview of minimum coverage usage

Safety stock is set up on the **Item coverage** page for each item. Different types of replenishment are represented by different coverage codes. (Learn more in [Safety stock fulfillment for items](safety-stock-replenishment.md).) However, all coverage codes use the value that is set in the **Minimum** field on the **Item coverage** page for each item. There are two major approaches for using the **Minimum** field:

- **Minimum quantity for min/max purposes** – This approach uses the minimum quantity together with min/max logic. It applies when the **Coverage code** field is set to *Min/Max* for the relevant item or coverage group. The **Minimum** quantity represents the average daily usage multiplied by the item's lead time.
- **Minimum quantity for inventory plan purposes** – This approach uses the minimum quantity to represent an inventory plan in combination with demand forecasts. It applies when the **Coverage code** field is set to *Period* or *Requirement* for the relevant item or coverage group. The **Minimum** quantity represents an inventory plan that reflects the desired customer service level to help reduce stock-outs, partial shipments, and delivery lead times. The minimum quantity reflects a percentage of forecast accuracy for a given item. It doesn't represent a desired inventory position.

The **Minimum** value can be set in three ways:

- Manually on the **Item coverage** page
- By the Data Management framework (*Item coverage* data entities)
- By the safety stock calculation that is done by safety stock journals

## Calculate minimum coverage based on historical usage

Safety stock journals are used to calculate a proposed minimum quantity based on an item's historical usage, either for min/max purposes or for inventory plan purposes. Historical usage represents all issue transactions during a specified period. These issue transactions include sales order transactions and inventory adjustments. The calculations also identify the impact of the proposed minimum quantity on inventory value and the change in inventory value compared to the current minimum quantities.

Each safety stock journal line represents an item and its coverage dimensions. These journal lines are created and shown on the **Safety stock journal lines** page (**Master planning \> Master planning \> Run \> Safety stock calculation**). The business process for using the safety stock journals to calculate the proposed minimum quantities is described later in this article.

The planner uses a safety stock journal to calculate proposed minimum quantities for selected items, based on historical usage during selected periods. The proposed minimums can be manually overridden as required, and you can review the potential impact of the proposed minimums on inventory value. When the journal is posted, the associated minimum quantities in the item coverage are automatically updated.

### Create a new safety stock journal name

You must create at least one safety stock journal name before you can generate this type of journal. You might typically use several journal names to help separate your safety stock calculations.

1. Go to **Master planning \> Setup \> Safety stock journal names**.
1. On the Action Pane, select **New**.
1. On the new line, set the following fields:

    - **Name** – Enter a short name for the journal.
    - **Description** – Enter a description of the journal.
    - **Private for user group** – To limit the audience for the current journal name, select a user group.
    - **Delete lines after posting** – Select this checkbox to clean up journal lines by default as you post them. Clear it to keep all posted lines.

    The **Journal type** field is read-only and is preset to *Safety stock*.

1. Close the page.

### Create a safety stock journal and lines

This step creates a journal and automatically adds lines to it. Each line identifies an item, its coverage dimensions, and several calculated quantities from the usage history. The calculated quantities include average issues per item lead time, average issues per month, and the monthly standard deviation.

#### Automatically generate journal lines

Journal lines can be automatically generated only if no lines exist for the journal that is currently shown.

Follow these steps to automatically generate journal lines.

1. Go to **Master planning \> Master planning \> Run \> Safety stock calculation**.
1. On the Action Pane, select **New**. A new safety stock journal is created.
1. On the **Journal header details** FastTab, set the following fields:

    - **Name** – Select the safety stock journal name to add the line to.
    - **Description** – The default value is the description of the journal name that you selected. However, you can edit the value as you require.
    - **Delete lines after posting** – Select this checkbox to clean up journal lines as you post them. Clear it to keep all posted lines. The setting is inherited from the selected journal name.

    The **Journal** field is read-only and shows the ID number of the journal that you're creating and adding lines to.

1. On the **Journal lines** FastTab, select **Create lines** on the toolbar.
1. In the **Create journal lines for proposed minimum inventory levels** dialog box, set the following fields:

    - **From date** – Select the start date of the period that issues should be included in the calculation for.
    - **To date** – Select the end date of the period that issues should be included in this calculation for. There must be at least two months between the start and end dates.
    - **Calculate standard deviation** – Set this option to *Yes* to calculate the standard deviation. You must set this option to *Yes* to use the **Use service level** option when you calculate the proposal (as described later in this article).

1. On the **Records to include** FastTab, you can set up filters and constraints to define which items are included. (For example, you can filter by **Coverage group** value.) Select **Filter** to open a standard query editor dialog box, where you can define selection criteria, sorting criteria, and joins. The fields work just as they do for other types of queries in Microsoft Dynamics 365 Supply Chain Management.
1. On the **Run in the background** FastTab, select whether to run the job in batch mode, and/or set up a recurrent schedule. The fields work just as they do for other types of [background jobs](../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md) in Supply Chain Management.
1. Select **OK**. Lines are created for the dimensions that have inventory transactions.

#### Manually add or remove journal lines

You can manually add and/or remove journal lines at any time (either after or instead of automatically generating lines). Use the following buttons on the toolbar of the **Journal lines** FastTab:

- **New** – Add a new line. Then enter a value in each column to define the product to calculate and apply new minimums for. Because proposed minimum calculations aren't available for manually added lines, no new **Calculated minimum quantity** values are shown for them. Therefore, you must manually enter the **New minimum quantity** values. However, you can still view the potential impact of the **New minimum quantity** value on inventory value and the potential change in inventory compared to the currently specified minimum.
- **Delete** – Delete the selected line.
- **Delete journal lines** – Delete all lines in the journal.

### Calculate a proposal

This step calculates a proposed minimum for each journal line and the line's potential impact on inventory value. (The proposed minimum is shown as the **Calculated minimum quantity** value.) You can do the calculation multiple times, as you require. The calculation updates the **Calculated minimum quantity** value that is shown for all journal lines.

The calculations that are shown won't affect the actual minimum quantity values for each product until you select **Post** on the Action Pane. At that time, the **New minimum quantity** values will be applied to each product.

1. Go to **Master planning \> Master planning \> Run \> Safety stock calculation**.
1. Open the journal to calculate a proposal for. Alternatively, create a new journal as described earlier in this article.
1. On the **Journal lines** FastTab, select **Calculate proposal** on the toolbar. (You don't have to select any lines.)
1. In the **Calculate proposal for minimum inventory level** dialog box, set the following fields:

    - **Use average issue during lead time** – Select this option to generate **Calculated minimum quantity** values based on the average issue during the specified period. Then, in the **Multiplication factor** field, enter a value to adjust the result by as required. For example, enter *1.0* to use the exact calculated average or *1.1* to add an extra buffer of 10 percent.
    - **Use service level** – Select this option to calculate a proposed minimum based on the desired service level. Then, in the **Service level** field, select your preferred service level.
    - **Lead time margin** – Enter a value to extend the normal lead time by (for example, to allow for administration).
    - **Use the calculated minimum quantity as the new minimum quantity** – Set this option to *Yes* to automatically copy values from the **Calculated minimum quantity** column to the **New minimum quantity** column for all lines after the calculation is completed. If you set this option to *No*, the **Current minimum quantity** value will be copied to the **New minimum quantity** column for all lines. You will then have to manually edit the **New minimum quantity** values as required.

1. On the **Run in the background** FastTab, select whether to run the job in batch mode, and/or set up a recurrent schedule. The fields work just as they do for other types of [background jobs](../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md) in Supply Chain Management.
1. Select **OK**. The results of the calculation are shown in the **Calculated minimum quantity** column on the **Journal lines** FastTab. For now, the values are only proposed values that haven't yet been applied to your products.

### Update minimum quantity

You can select any line in a safety stock journal and manually override the value of its **New minimum quantity** field.

1. Go to **Master planning \> Master planning \> Run \> Safety stock calculation**.
1. Open the journal to edit. Alternatively, create a new journal as described earlier.
1. On the **Journal lines** FastTab, find the line to adjust, and then edit the value in the **New minimum quantity** column. For example, you might set the **New minimum quantity** value so that it matches the **Calculated minimum quantity** value. If the **Calculated minimum quantity** value is *0* (zero), you can enter the desired future value.

### Post the new minimum quantity and validate the result

Follow these steps to post the new minimum quantity and validate the result.

1. Go to **Master planning \> Master planning \> Run \> Safety stock calculation**.
1. Open the journal to post new minimum quantities for. Alternatively, create a new journal as described earlier.
1. On the Action Pane, select **Post**.
1. In the **Post journal** dialog box, set the **Transfer all posting errors to a new journal** field as required. Then select **OK** to post the journal.
1. If you changed the **New minimum quantity** value for a line on the **Journal lines** FastTab, you can confirm the change by following these steps:

    1. For the line that you edited, select the link in the **Item number** column.
    1. In the **Product information** dialog box, select the link in the **Item number** field to open the related released product record.
    1. On the Action Pane, on the **Plan** tab, in the **Coverage** group, select **Item coverage**.
    1. Notice that the **Minimum** value for the site and warehouse that you adjusted by using the posted safety stock journal has now been updated to match your edit.

## Related information

- [Safety stock fulfillment for items](safety-stock-replenishment.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
