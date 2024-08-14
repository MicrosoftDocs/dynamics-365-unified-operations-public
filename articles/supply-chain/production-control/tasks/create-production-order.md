---
title: Create a production order
description: Learn how to create a production order, including step-by-step processes for creating production orders and validating production orders. 
author: johanhoffmann
ms.author: johanho
ms.topic: how-to
ms.date: 05/22/2024
ms.custom:
  - bap-template
  - evergreen
ms.reviewer: kamaybac
ms.search.form: ProdTableListPage, ProdTableCreate, ProdTable, ProdBOM, ProdRoute, ProdJournalCreate
---

# Create a production order

[!include [banner](../../includes/banner.md)]

This procedure shows how to create a production order. The demo data company used to create this procedure is USMF. This is the first of seven procedures that together explain the production-order lifecycle.

## Create a production order

1. Go to **Production control** \> **Production orders** \> **All production orders**.
2. Select **New production order**.
3. In the **Item number** field, type *D0001*.
4. In the **Delivery** field, enter a date. The delivery date indicates when the production order should end in order to deliver on time. This date can be used in the scheduling process. For example, you can schedule the order backward from the delivery date.  
5. Set **Quantity** to *20*.
6. Select Create.

> [!NOTE]
> The **BOM number** field automatically displays the number of any active BOM for the current item, but you can change the BOM for the production order by selecting an active BOM from the list of approved BOM versions. The **Route number** field automatically displays the number of any active route for the current item, but you can change the route for the production order by selecting an active route from the list of approved route versions.

## Validate the production order

1. In the list, select the link in the selected row. Select the link for the production order number that you have just created. This opens the details page for the order.  
2. Select **Edit**.
3. In the **Delivery** field, enter a date. For example, you can change the delivery date for the production order.  
4. Select **Save**.
5. Close the page.

## Update the BOM

1. On the Action Pane, select **Production order**.
2. Select **BOM**. Open the BOM page to validate the BOM data that was copied from the default data when the production order was created. In this procedure, you need to update the quantity for a BOM.  
3. Select **Edit**.
4. In the **Quantity** field, enter a number. Changing the quantity on the BOM line affects the cost estimate of material consumption for the production order.  
5. Select **Save**.
6. Close the page.

## Update the production route

1. On the Action Pane, select **Production order**.
2. Select **Route**. Open the **Route** page to validate the data of the production route that was copied from the default data when the order was created. In this procedure, you need to update the quantity for one of the operations in the production route.  
3. In the list, find and select the desired record.
4. Select **Edit**.
5. In the **Process qty.** field, enter a number. Changing the process time affects the estimated route consumption and the cost of the production order.  
6. Select **Save**.
7. Close the page.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
