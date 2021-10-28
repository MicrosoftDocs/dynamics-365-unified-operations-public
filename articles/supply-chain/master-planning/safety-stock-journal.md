---
title: Use the safety stock journal to update minimum coverage for items
description: This topic discusses how to use safety stock journal to update safety stock quantity for items by calculating minimum coverage proposals based on historical transactions. 
author: ChristianRytt
ms.date: 10/28/2021
ms.topic: article
ms.search.form: ReqItemJournalName, ReqItemJournalSafetyStock, EcoResProductInformationDialog, ReqItemTableSetup, ReqItemTable, EcoResProductDetailsExtended
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: crytt
ms.search.validFrom: 2021-10-28
ms.dyn365.ops.version: 10.0.22
---

# Use the safety stock journal to update minimum coverage for items

[!include [banner](../../includes/banner.md)]

Safety stock indicates an additional quantity of an item held in inventory to reduce the risk that it will go out of stock. Safety stock is used as a buffer in case sales orders come in and the supplier is unable to meet the customer's requested ship date.

This topic discusses how to use the safety stock journal to calculate minimum coverage proposals based on historical transactions and then update the item coverage with the proposals.

## Overview of minimum coverage usage

Safety stock is set up on the **Item coverage** page for each item. Various types of replenishment are represented by different coverage codes (see also [Safety stock fulfillment for items](safety-stock-replenishment.md)). However, all coverage codes use the value set in the **Minimum** field on the **Item coverage** page for each item. There are two major approaches for using the **Minimum** field:

- **Minimum quantity for Min/Max purposes** – This approach uses the minimum quantity together with min/max logic. It applies when the **Coverage code** is set to *Min/Max* for the relevant item or coverage group. The **Minimum** quantity represents the average daily usage multiplied by the item's lead time.
- **Minimum quantity for inventory plan purposes** – This approach uses the minimum quantity to represent an inventory plan in combination with demand forecasts. It applies when the **Coverage code** is set to *Period* or *Requirement* for the relevant item or coverage group. The **Minimum** quantity represents an inventory plan reflecting the desired customer service level to reduce stock outs, partial shipments, and delivery lead times. The minimum quantity reflects a percentage of forecast accuracy for a given item; it does not represent a desired inventory position.

The **Minimum** value can be set manually on the **Item coverage** page, by data management framework (*Item coverage* data entities), or by safety stock calculation done by safety stock journals.

## Calculate minimum coverage based on historical usage

Safety stock journals are used to calculate a proposed minimum quantity based on an item's historical usage, either for min/max purposes or for inventory plan purposes. Historical usage represents all issue transactions during a specified time period, including sales order transactions, inventory adjustments, and other issue transactions. The calculations also identify the impact of the proposed minimum quantity on inventory value, and the change in inventory value compared to the current minimum quantities.

Each safety stock journal line represents an item and its coverage dimensions. These journal lines are created and displayed on the **Safety stock journal lines** page (available at **Master planning > Master planning > Run > Safety stock calculation**). The business process for using the safety stock journals to calculate the proposed minimum quantities is described later in this topic.

The planner uses a safety stock journal to calculate proposed minimum quantities for selected items based on historical usage during selected periods. The proposed minimums can be manually overridden if needed, and you can review the potential impact on inventory value of the proposed minimums. Posting the journal automatically updates the associated minimum quantities in item coverage.

### Create a new safety stock journal name

You must create at least one safety stock journal name before you can generate this type of journal. You might typically use several journal names to help separate your safety stock calculations.

1. Go to **Master planning \> Setup \> Safety stock journal names**.
1. On the Action Pane, select **New**.
1. Make the following settings for the new line:
    - **Name** – Enter a short name for the journal.
    - **Description** – Enter a description for the journal.
    - **Journal type** – Preset to *Safety stock* (read-only).
    - **Private for user group** – To limit the audience for the current journal name, select a user group here.
    - **Delete lines after posting** – Select this check box to clean up the journal lines as you post them (by default). Clear this box to keep all posted lines.
1. Close the page.

### Create a safety stock journal and lines

This step creates a journal and automatically adds lines to it, where each line identifies an item, its coverage dimensions, and several calculated quantities from the usage history. The calculated quantities include average issues per the item's lead time, average issues per month, and the monthly standard deviation.

#### Generate journal lines automatically

Journal lines can only be created automatically when no lines exist for the currently displayed journal.

Use the following steps to generate journal lines automatically.

1. Go to **Master planning > Master planning > Run > Safety stock calculation**.
1. On the Action Pane, select **New**. A new safety stock journal is created.
1. Make the following settings on the **Journal header details** FastTab:
    - **Journal** – This read-only field shows the ID number for the journal you are about to create and add lines to.
    - **Name** – Select the safety stock journal name that you want to add the line to.
    - **Description** – Defaults to the description for the journal name that you selected, but you can edit it if needed.
    - **Delete lines after posting** – Select this check box to clean up the journal lines as you post them. Clear this box to keep all posted lines. This setting is inherited from the selected journal **Name**.
1. On the **Journal lines** FastTab, select **Create lines** from the toolbar.
1. The **Create journal lines for proposed minimum inventory levels** dialog opens. Make the following settings:
    - **From date** – Select the start date for the period during which issues should be included in this calculation.
    - **To date** – Select the end date for the period during which issues should be included in this calculation. There must be at least two months between the start and end date.
    - **Calculate standard deviation** – Set this to *Yes* to calculate the standard deviation. You must enable this option if you want to use the **Use service level** option when calculating the proposal (as described later in this topic).
    - **Records to include** – On this FastTab, you can set up filters and constraints to define which items to include (such as by **Coverage group**). Select **Filter** to open a standard query editor dialog, where you can define selection criteria, sorting criteria, and joins. The fields work just as they do for other types of queries in Supply Chain Management.
    - **Run in the background** – On this FastTab, choose whether to run the job in batch mode and/or set up a recurrent schedule. The fields work just as they do for other types of [background jobs](../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md) in Supply Chain Management.
1. Select **OK**. This will create lines for the dimensions that have inventory transactions.

#### Add or remove journal lines manually

You can add and/or remove journal lines manually at any time (either after or instead of generating lines automatically) by using the following buttons on the **Journal lines** FastTab toolbar:

- **New** – Add a new line. Then enter values in each column to define the product you want to calculate and apply new minimums for. Proposed minimum calculations aren't available for manually added lines, so now new **Calculated minimum quantity** values are shown for them, which means that you must enter the **New minimum quantity** values manually. However, you can still view the potential impact on inventory value of the **New minimum quantity**, and also the potential change in inventory compared to the currently specified minimum.
- **Delete** – Delete the selected line.
- **Delete journal lines** – Delete all lines in the journal.

### Calculate a proposal

This step calculates a proposed minimum (shown as the **Calculated minimum quantity**) for each journal line and the line's potential impact on inventory value. If needed, you can perform the calculation multiple times, with calculation updating the **Calculated minimum quantity** shown for all journal lines. The calculations shown won't affect the actual minimum quantity values for each product until you select **Post** on the Action Pane, at which time the **New minimum quantity** values will be applied to each product.

1. Go to **Master planning > Master planning > Run > Safety stock calculation**.
1. Open the journal you want to calculate a proposal for (or create a new one as described in the previous section).
1. On the **Journal lines** FastTab, select **Calculate proposal** from the toolbar. (You don't need to select any lines.)
1. The **Calculate proposal for minimum inventory level** dialog opens. Make the following settings:
    - **Use average issue during lead time** – Select this radio button to generate **Calculated minimum quantity** values based on the average issue during the specified period. Then, enter a value in a **Multiplication factor** to adjust the result as needed. For example, enter a **Multiplication factor** of 1.0 to use the exact calculated average, or enter 1.1 to add an extra buffer of 10%.
    - **Use service level** – Select this radio button to calculate a proposed minimum based on the desired service level. Then select your preferred service level using the **Service level** field.
    - **Lead time margin** – Enter a value to extend the normal lead time, for example to allow for administration.
    - **Use the calculated minimum quantity as the new minimum quantity** – Set this to *Yes* to automatically copy values from the **Calculated minimum quantity** column to the **New minimum quantity** column for all rows after the calculation is complete. If you set this to *No*, then the **Current minimum quantity** will instead be copied to the **New minimum quantity** column for all rows, which means that you will need to manually edit the **New minimum quantity** values as required.
    - **Run in the background** – On this FastTab, choose whether to run the job in batch mode and/or set up a recurrent schedule. The fields work just as they do for other types of [background jobs](../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md) in Supply Chain Management.
1. Select **OK**. The results of the calculation are now shown in the **Calculated minimum quantity** column of the **Journal lines** FastTab. For now, these are only proposed values that have not yet been applied to your products.

### Update minimum quantity

You can select any line in a safety stock journal and manually override the value for its **New minimum quantity** field.

1. Go to **Master planning > Master planning > Run > Safety stock calculation**.
1. Open the journal you want to edit (or create a new one as described previously).
1. On the **Journal lines** FastTab, find the line you want to adjust and then edit the value in the **New minimum quantity** column. For example, you might set the **New minimum quantity** to match the value in the **Calculated minimum quantity**. If the **Calculated minimum quantity** is zero, you can enter the desired future value.

### Post the new minimum quantity and validate the result

Use the following procedure to post the new minimum quantity and validate the result.

1. Go to **Master planning > Master planning > Run > Safety stock calculation**.
1. Open the journal you want to post new minimum quantities for (or create a new one as described in the previous section).
1. On the Action Pane, select **Post**.
1. The **Post journal** dialog opens. 
1. Set the **Transfer all posting errors to a new journal** as required and then select **OK** to post the journal.
1. If you changed the **New minimum quantity** setting for a row on the **Journal lines** FastTab, you can confirm the change by doing the following steps:
    1. For the row you edited, select the link in the **Item number** column.
    1. The **Product information** dialog opens. Select the link in the **Item number** field to open the related released product record.
    1. On the Action Pane, open the **Plan** tab and, from the **Coverage** group, select **Item coverage**.
    1. Notice that the **Minimum** value for the site and warehouse that you adjusted using the posted safety stock journal has now been updated to match your edit.

## Additional resources

- [Safety stock fulfillment for items](safety-stock-replenishment.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]