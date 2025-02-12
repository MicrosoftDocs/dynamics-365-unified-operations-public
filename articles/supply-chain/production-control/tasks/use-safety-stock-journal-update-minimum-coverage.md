--- 
title: Use the safety stock journal to update minimum coverage
description: Learn how to calculate minimum coverage proposals based on historical transactions and then update the item coverage with the proposals.
author: johanhoffmann
ms.author: johanho
ms.topic: how-to
ms.date: 08/09/2019
ms.custom:
ms.reviewer: kamaybac   
ms.search.form: ReqItemJournalName, ReqItemJournalSafetyStock, EcoResProductInformationDialog, EcoResProductDetailsExtended, ReqItemTable
---

# Use the safety stock journal to update minimum coverage

[!include [banner](../../includes/banner.md)]

This procedure shows how to calculate minimum coverage proposals based on historical transactions and then update the item coverage with the proposals. This is done using the safety stock journal. The demo data company used to create this task is USMF. This task is intended for the production planner, to help maintain minimum coverage.

## Create a new safety stock journal name

1. Go to **Master planning > Setup > Safety stock journal names**.
2. Select **New**.
3. In the **Name** field, type *Material*.
4. In the **Description** field, type *Material*.
5. Close the page.

## Create a safety stock journal

1. Go to **Master planning > Master planning > Run > Safety stock calculation**.
2. Select **New**.
3. In the **Name** field, enter or select a value. Select the safety stock journal name that you created, for example, Material.  
4. Select **Create lines**.
5. In the **From date** field, enter a date.  
6. In the **To date** field, enter a date.
7. Select **OK**. This will create lines for the dimensions that have inventory transactions.  

## Calculate proposal

1. Select **Calculate proposal**.
2. Select the **Use average issue during lead time** option.
3. Set **Multiplication factor** to *10*. The Multiply factor is used to adjust the proposal. Because demo data only has a few transactions, you will need to set the factor to get a realistic proposal.  
4. Select **OK**. Scroll down to find M0002 and M0003. View the **Calculated minimum** quantity column.

## Update minimum quantity

1. In the **New minimum quantity** field, enter a number. Update the New minimum quantity to match the value in the Calculated minimum quantity. If the Calculated minimum is zero,  you can enter the desired future value. For example, you can enter the Calculated minimum quantity in this field for M0002 that has warehouse 12.  
2. In the list, find and select the desired record. For example, you can select M0002 that has warehouse 12.  
3. In the **New minimum quantity** field, enter a number. Update the New minimum quantity to match the value in the Calculated minimum quantity. If the Calculated minimum is zero you can enter the desired future value.  

## Post the new minimum quantity and validate the result

1. Select **Post**.
2. Select **OK**.
3. Select to follow the link in the **Item number** field.
4. Select to follow the link in the **Item number** field.
5. On the Action Pane, select **Plan**.
6. Select **Item coverage**. Notice that the **Minimum quantity** has been updated with the new minimum quantity from the safety stock journal.  

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
