---
# required metadata

title: Use the safety stock journal to update minimum coverage for items
description: This topic discusses how to use safety stock journal to update safety stock quantity for items by calculating minimum coverage proposals based on historical transactions. 
author: ChristianRytt
ms.date: 08/09/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: ReqItemJournalName, ReqItemJournalSafetyStock, EcoResProductInformationDialog, ReqItemTableSetup, ReqItemTable, EcoResProductDetailsExtended
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: 
ms.author: crytt
ms.dyn365.ops.version: 7.3 
ms.search.validFrom: 2021-09-01

---
# Use the safety stock journal to update minimum coverage for items

[!include [banner](../../includes/banner.md)]

Safety stock indicates an additional quantity of an item held in the inventory in order to reduce the risk that the item will be out of stock. Safety stock is used as a buffer stock in case sales orders come in and the supplier is unable to deliver the additional items to meet the customer's requested ship date.

Safety stock is set up as part of item coverage on the **Item coverage** page under **Released products** > **Plan** > **Coverage**. The different types of replenishment are represented as different coverage codes (see [Safety stock fulfillment for items](safety-stock-replenishment.md) for details and how the master planning handles the safety stock constraint later). However, all coverage codes are using the value set in the **Minimum** field.

## Overview of minimum coverage usage

There are two major approaches for using the **Minimum** field. One approach uses the minimum quantity as part of min/max logic (when you select **Min/Max** in the **Coverage code** list), and the second approach uses the minimum quantity to represent an inventory plan in combination with demand forecasts (when you select **Period** or **Requirement** in the **Coverage code** list).  

1. Minimum quantity for Min/Max purposes. When using a min/max replenishment logic, the minimum quantity represents the average daily usage multiplied by the item's lead time.
1. Minimum quantity for inventory plan purposes. The second approach involves demand forecasts, where the minimum quantity represents an inventory plan reflecting the desired customer service level in order to reduce stock outs, partial shipments, and delivery lead times. This minimum quantity reflects a percentage of forecast accuracy for a given item; it does not represent a desired inventory position.

The definition of an item's minimum quantity provides the starting point for further explanation about calculation of proposed minimum quantities to support the two different purposes.

The **Minimum** value can be maintained manually on the item coverage, by data management framework (*Item coverage* data entities) or by safety stock calculation done by safety stock journals.

This topic discusses how to use safety stock journal to calculate minimum coverage proposals based on historical transactions and then update the item coverage with the proposals.

## Calculating minimum coverage based on historical usage

Safety stock journals are used to calculate proposed minimum quantity based on an item's historical usage, either for min/max purposes or for inventory plan purposes. Historical usage represents all issue transactions during a specified time period, including sales order transactions, inventory adjustments and other issue transactions. The calculations also identify the impact of the proposed minimum quantity on inventory value, and the change in inventory value compared to the current minimum quantities.

Each safety stock journal line represents an item and its coverage dimensions. These journal lines are created and displayed on the safety stock journal lines page. The business process for using the safety stock journals to calculate the proposed minimum quantities is described below.

The planner uses a safety stock journal to calculate proposed minimum quantities for selected items based on historical usage during selected periods. The proposed minimums can be manually overridden if needed, and you can review the potential impact on inventory value of the proposed minimums. Posting the journal automatically updates the associated minimum quantities in item coverage.

### Create a new safety stock journal name

1. In the **Navigation pane**, go to **Master planning > Setup > Safety stock journal names**.
2. Click **New**.
3. In the **Name** field, type a name, for example, 'Material'.
4. In the **Description** field, type a description, for example, 'Material'.
5. Close the page.

### Create a safety stock journal and lines

 This step results in the automatic creation of journal lines, where each line identifies an item and its coverage dimensions and several calculated quantities from the usage history. The calculated quantities include average issues per the item's lead time, average issues per month, and the monthly standard deviation.

You can only perform the automatic creation of journal lines when no lines exist.

1. In the **Navigation pane**, go to **Master planning > Master planning > Run > Safety stock calculation**.
2. Click **New**.
3. In the **Name** field, enter or select a value. Select the safety stock journal name that you created, for example, Material.  
4. Click **Create lines**.
5. In the **From date** field, enter a date.  
6. In the **To date** field, enter a date. You need to select a period of at least, two months.
7. **Select** other selection criteria for items if needed (such as **Coverage group**).
8. Click **OK**. This will create lines for the dimensions that have inventory transactions.

### Calculate proposal

This step results in calculation of a proposed minimum for each journal line and also its potential impact on inventory value. If needed, you can perform the calculation multiple times, but each calculation will update the proposed minimum for all journal lines.

1. Click **Calculate proposal**.
2. Select the **Use average issue during lead time** option.
3. Set **Multiplication factor** to '10'. The Multiplication factor is used to adjust the proposal. If you are using demo data, it only has a few transactions, you will need to set the factor to get a realistic proposal. Usually, it represents a service level you want to maintain.
4. Click **OK**. Scroll down to find M0002 and M0003. View the **Calculated minimum** quantity column.

### Update minimum quantity

You can select a line and manually override the value for the new minimum quantity field. You can also manually create journal lines.  This approach prevents calculation of a proposed minimum so that it must be manually entered. However, you can still view the potential impact on inventory value of the proposed minimum, and also the potential change in inventory value compared to the currently specified minimum.

1. In the **New minimum quantity** field, enter a number. Update the New minimum quantity to match the value in the Calculated minimum quantity. If the Calculated minimum is zero, you can enter the desired future value. For example, you can enter the Calculated minimum quantity in this field for M0002 that has warehouse 12.  
2. In the list, find and select the desired record. For example, you can select M0002 that has warehouse 12.  
3. In the **New minimum quantity** field, enter a number. Update the New minimum quantity to match the value in the Calculated minimum quantity. If the Calculated minimum is zero you can enter the desired future value.  

### Post the new minimum quantity and validate the result

1. Click **Post**.
2. Click **OK**.
3. Click to follow the link in the **Item number** field.
4. Click to follow the link in the **Item number** field.
5. On the **Action Pane**, click Plan.
6. Click **Item coverage**. Notice that the **Minimum quantity** has been updated with the new minimum quantity from the safety stock journal.  

## Additional resources

[Safety stock fulfillment for items](safety-stock-replenishment.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]