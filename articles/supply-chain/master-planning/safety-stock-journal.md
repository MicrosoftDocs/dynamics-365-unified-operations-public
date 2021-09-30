---
title: Use the safety stock journal to update minimum coverage for items
description: This topic discusses how to use safety stock journal to update safety stock quantity for items by calculating minimum coverage proposals based on historical transactions. 
author: ChristianRytt
ms.date: 09/30/2021
ms.topic: article
ms.search.form: ReqItemJournalName, ReqItemJournalSafetyStock, EcoResProductInformationDialog, ReqItemTableSetup, ReqItemTable, EcoResProductDetailsExtended
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: crytt
ms.search.validFrom: 2021-09-30
ms.dyn365.ops.version: 10.0.22
---

# Use the safety stock journal to update minimum coverage for items

[!include [banner](../../includes/banner.md)]

Safety stock indicates an additional quantity of an item held in inventory to reduce the risk that it will go out of stock. Safety stock is used as a buffer in case sales orders come in and the supplier is unable to meet the customer's requested ship date.

This topic discusses how to use the safety stock journal to calculate minimum coverage proposals based on historical transactions and then update the item coverage with the proposals.

## Overview of minimum coverage usage

Safety stock is set up on the **Item coverage** page for each item. Various types of replenishment are represented by different coverage codes (see also [Safety stock fulfillment for items](safety-stock-replenishment.md)). However, all coverage codes use the value set in the **Minimum** field on the **Item coverage** page for each item. There are two major approaches for using the **Minimum** field:

- **Minimum quantity for Min/Max purposes** – This approach uses the minimum quantity together with min/max logic. It applies when the **Coverage code** is set to *Min/Max* for the relevant item or coverage group. The **Minimum** quantity represents the average daily usage multiplied by the item's lead time.
- **Minimum quantity for inventory plan purposes** – This approach uses the minimum quantity to represent an inventory plan in combination with demand forecasts. It applies when the **Coverage code** is set to *Period* or *Requirement* for the relevant item or coverage group. The **Minimum** quantity represents an inventory plan reflecting the desired customer service level to reduce stock outs, partial shipments, and delivery lead times <!-- KFM: This sentence isn't clear. Please revise. -->. The minimum quantity reflects a percentage of forecast accuracy for a given item; it does not represent a desired inventory position <!-- KFM: This sentence isn't clear. Please revise. -->.

The definition of an item's minimum quantity provides the starting point for further explanation about calculation of proposed minimum quantities to support the two different purposes. <!-- KFM: This sentence isn't clear. Please revise. -->

The **Minimum** value can be set manually on the **Item coverage** page, by data management framework (*Item coverage* data entities), or by safety stock calculation done by safety stock journals.

## Calculating minimum coverage based on historical usage

Safety stock journals are used to calculate a proposed minimum quantity based on an item's historical usage, either for min/max purposes or for inventory plan purposes. Historical usage represents all issue transactions during a specified time period, including sales order transactions, inventory adjustments, and other issue transactions. The calculations also identify the impact of the proposed minimum quantity on inventory value, and the change in inventory value compared to the current minimum quantities.

Each safety stock journal line represents an item and its coverage dimensions. These journal lines are created and displayed on the safety stock journal lines page <!-- KFM: Is this the actual page name? I couldn't find it. -->. The business process for using the safety stock journals to calculate the proposed minimum quantities is described later in this topic.

The planner uses a safety stock journal to calculate proposed minimum quantities for selected items based on historical usage during selected periods. The proposed minimums can be manually overridden if needed, and you can review the potential impact on inventory value of the proposed minimums. Posting the journal automatically updates the associated minimum quantities in item coverage.

### Create a new safety stock journal name

<!-- KFM: Intro is needed. Why do we need this? Describe what a "name" is and how it is different from the journal itself. Why might I have more than one of these? -->

1. Go to **Master planning \> Setup \> Safety stock journal names**.
1. On the Action Pane, select **New**.
1. Make the following settings for the new line:
    - **Name** – Enter a short name for the journal.
    - **Description** – Enter a description for the journal.
    - **Journal type** – Preset to *Safety stock* (read-only).
    - **Private for user group** – <!-- KFM: Description needed. -->
    - **Delete lines after posting** – <!-- KFM: Description needed. -->
1. Close the page.

### Create a safety stock journal and lines

This step creates a journal and automatically adds lines to it, where each line identifies an item, its coverage dimensions, and several calculated quantities from the usage history. The calculated quantities include average issues per the item's lead time, average issues per month, and the monthly standard deviation.

Journal lines can only be created automatically when no lines exist. <!-- KFM: You mean when creating a new journal? -->

1. Go to **Master planning > Master planning > Run > Safety stock calculation**.
1. On the Action Pane, select **New**. A new safety stock journal is created.
1. Make the following settings on the **Journal header details** FastTab:
    - **Journal** – This read-only field shows the ID number for the journal you are about to create and add lines to. <!-- KFM: I assumed this. Please confirm. -->
    - **Name** – Select the safety stock journal name that you want to add the line to.
    - **Description** – Defaults to the description for the journal name that you selected, but you can edit it if needed.
    - **Delete lines after posting** – <!-- KFM: Description needed. Defaults from selected name? -->
1. On the **Journal lines** FastTab, select **Create lines** from the toolbar.
1. The **Create journal lines for proposed minimum inventory levels** dialog opens. Make the following settings:
    - **From date** – <!-- KFM: Description needed. -->
    - **To date** – <!-- KFM: Description needed. --> You must select a period of at least two months <!-- KFM: You mean between the from and to dates? --> .
    - **Calculate standard deviation** – <!-- KFM: Description needed. -->
    - **Records to include** – On this FastTab, you can set up filters and constraints to define which items to include (such as by **Coverage group**). Select **Filter** to open a standard query editor dialog, where you can define selection criteria, sorting criteria, and joins. The fields work just as they do for other types of queries in Supply Chain Management.
    - **Run in the background** – On this FastTab, choose whether to run the job in batch mode and/or set up a recurrent schedule. The fields work just as they do for other types of [background jobs](../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md) in Supply Chain Management.
1. Select **OK**. This will create lines for the dimensions that have inventory transactions.

### Calculate a proposal

This step calculates a proposed minimum for each journal line and the line's potential impact on inventory value. If needed, you can perform the calculation multiple times, but each calculation will update the proposed minimum for all journal lines. <!-- KFM: Is "proposed minimum" tha same as the "calculated minimum"? How are those different from the "New minimum"? . -->

1. Go to **Master planning > Master planning > Run > Safety stock calculation**.
1. Open the journal you want to calculate a proposal for (or create a new one as described in the previous section).
1. On the **Journal lines** FastTab, select **Calculate proposal** from the toolbar. <!-- KFM: Should I select any lines? Does that have any effect? -->
1. The **Calculate proposal for minimum inventory level** dialog opens. Make the following settings:
    - **Use average issue during lead time** – Select this radio button to <!-- KFM: Description needed. -->. Then, enter a **Multiplication factor** to use to adjust the proposal (usually, the factor represents a service level you want to maintain <!-- KFM: Some practical advice for how to set this would help. What is reasonable?-->). <!-- KFM: Default is zero! What does that mean? -->
    - **Use service level** – <!-- KFM: Description needed. Also explain how to use the **Service level** field enabled when this is selected -->
    - **Lead time margin** – <!-- KFM: Description needed. -->
    - **Use the calculated minimum quantity as the new minimum quantity** – <!-- KFM: Description needed. -->
    - **Run in the background** – On this FastTab, choose whether to run the job in batch mode and/or set up a recurrent schedule. The fields work just as they do for other types of [background jobs](../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md) in Supply Chain Management.
1. Select **OK**. The results of the calculation are now shown in the **Calculated minimum quantity** column of the **Journal lines** FastTab. <!-- KFM: Is this correct? For me, nothing changed. What does the **Calculated minimum** tell me? Are other calculations results shown here, such as **New minium quantity**? Where do I find other info mentioned, such as the impact on inventory value? Has anything changed so far, or did we just get some calculations? -->

### Update minimum quantity

You can select any line in a safety stock journal and manually override the value for its **New minimum quantity** field. You can also manually create journal lines <!-- KFM: When mention manual lines here? It never comes up again. Should probably instead be mentioned in the section about creating journals and lines. -->. This approach prevents calculation of a proposed minimum, which means that you must enter it manually <!-- KFM: Which approach? Creating manual lines? -->. However, you can still view the potential impact on inventory value of the proposed minimum <!-- KFM: Where do I find the "proposed minimum"? -->, and also the potential change in inventory value compared to the currently specified minimum.

1. Go to **Master planning > Master planning > Run > Safety stock calculation**.
1. Open the journal you want to edit (or create a new one as described previously).
1. On the **Journal lines** FastTab, find the line you want to adjust and then edit the value in the **New minimum quantity** column. For example, you might set the **New minimum quantity** to match the value in the **Calculated minimum quantity**. If the **Calculated minimum quantity** is zero, you can enter the desired future value <!-- KFM: What if it isn't zero? -->.

### Post the new minimum quantity and validate the result

<!-- KFM: An intro is needed. What are we doing here? What do we need to have done first? How does this section relate to the rest of the sections on this page? -->.

1. Go to **Master planning > Master planning > Run > Safety stock calculation**.
1. Open the journal you want to post new minimum quantities for (or create a new one as described in the previous section).
1. On the Action Pane, select **Post**.
1. The **Post journal** dialog opens. Make the following setting:
    - **Transfer all posting errors to a new journal** – <!-- KFM: Description needed. -->
1. Select **OK** to post the journal.
1. If you changed the **New minimum quantity** setting for a row on the **Journal lines** FastTab, you can confirm the change by doing the following: <!-- KFM: The original was hard to follow. Please confirm that the following steps are what we mean to describe here. -->
    1. For the row you edited, select the link in the **Item number** column.
    1. The **Product information** dialog opens. Select the link in the **Item number** field to open the related released product record.
    1. On the Action Pane, open the **Plan** tab and, from the **Coverage** group, select **Item coverage**.
    1. Notice that the **Minimum** value for the site and warehouse that you adjusted using the posted safety stock journal has now been updated to match your edit.

## Additional resources

- [Safety stock fulfillment for items](safety-stock-replenishment.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]