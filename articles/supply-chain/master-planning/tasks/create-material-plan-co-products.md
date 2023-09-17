--- 
# required metadata 
 
title: Create a material plan for co products
description: The production planner plans the material requirements for items that are formula co-products. 
author: t-benebo
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: DefaultDashboard, SalesOrderProcessingWorkspace, SalesCreateOrder, SalesTable, ReqCreatePlanWorkspace, ReqTransPlanCard, SysQueryForm, ReqTransPo   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: benebotg
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Create a material plan for co products

[!include [banner](../../includes/banner.md)]

The production planner plans the material requirements for items that are formula co-products. The demo data company used to create this procedure is USP2.

## Create requirement for a co-product

1. Go to **Sales and marketing \> Workspaces \> Sales order processing and inquiry**.
1. Select **New**.
1. Select **Sales order**.
1. In the **Customer account** field, type a value.
    * Example: US-001  
1. Select **OK**.
1. In the **Item number** field, type a value.
    * Example: P6003  
1. In the **Quantity** field, enter a number.
    * Example: 50000  
1. Select **Save**.

## Create a material plan for co-products

1. Close the page.
1. Close the page.
1. Select **Master planning**.
1. In the **Plan** field, select the drop-down button to open the lookup.
1. In the list, select the link in the selected row.
    * Example: MasterPlan  
1. Select **Run**.
1. Expand or collapse the **Records to include** section.
1. Select **Filter**.
1. In the list, select the row for **Field** = *Item number*.
1. In the **Criteria** field, type a value.
    * Example: P6003  
1. Select **OK**.
1. Select **OK**.
1. Select **Planned orders**.
1. Use the Quick Filter to find records. For example, filter on the **Item number** field with a value of 'P6000'.
    * Filter by the formula item that has as co-product of the item that you created a sales order for.  
1. In the list, mark the selected row.
    * Select any of the rows returned by the filter.  
1. In the list, select the link in the selected row.
1. Expand the **Pegging** section.
1. In the list, select the link in the selected row.
    * The planned order is pegged to the sales order for the co-product.  
1. Close the page.

## Create a second requirement for a co-product

1. Go to **Sales and marketing \> Workspaces \> Sales order processing and inquiry**.
1. Select **New**.
1. Select **Sales order**.
1. In the **Customer account** field, type a value.
    * Example: US-001  
1. Select **OK**.
1. In the **Item number** field, type a value.
    * Example: P6003  
1. In the **Quantity** field, enter a number.
    * Example: 50000  
1. Select **Save**.

## Create a second material plan for co-products

1. In the **Plan** field, select the drop-down button to open the lookup.
2. In the list, select the link in the selected row.
    * Example: MasterPlan  
3. Select **Run**.
4. Expand or collapse the **Records to include** section.
5. Select **Filter**.
6. In the list, select the row for **Field** = *Item number*.
7. In the *Criteria* field, type a value.
    * Example: P6003  
8. Select **OK**.
9. Select **OK**.
10. Select **Planned orders**.
11. Use the Quick Filter to find records. For example, filter on the **Item number** field with a value of 'P6000'.
    * Filter by the formula item that has as co-product of the item that you created a sales order for.  
12. In the list, mark the selected row.
    * Select any of the rows returned by the filter.  
13. In the list, select the link in the selected row.
14. Expand or collapse the **Pegging** section.
15. In the list, select the link in the selected row.
    * The planned order is pegged to the sales order for the co-product.  
16. Close the page.
17. Select **Master planning**.
18. Go to **Master planning \> Setup \> Master planning parameters**.
19. Select *No* in the **Disable all planning processes** field.
20. Close the page.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]