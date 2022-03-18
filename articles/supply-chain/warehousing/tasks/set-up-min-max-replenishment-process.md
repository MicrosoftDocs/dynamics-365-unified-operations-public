--- 
# required metadata 
 
title: Set up a min-max replenishment process
description: This procedure shows you how to set up a new replenishment process which uses the minimum/maximum replenishment strategy. 
author: perlynne
ms.date: 10/02/2019
ms.topic: business-process 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: WHSInventFixedLocation, InventItemIdLookupSimple, WMSLocationIdLookup, WHSLocDirTable, InventLocationIdLookup, SysQueryForm, WHSWorkTemplateTable, WHSReplenishmentTemplates, UnitOfMeasureLookup, SysQueryTableLookUp, SysQueryFieldLookUp, SysRecurrence, WHSInventFixedLocation
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Distribution
ms.author: perlynne
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Set up a min-max replenishment process

[!include [banner](../../includes/banner.md)]

This procedure shows you how to set up a new replenishment process which uses the minimum/maximum replenishment strategy. When inventory falls below the minimum level, work will be created to replenish the location. The procedure also shows how to use fixed picking locations to allow restocking even if inventory falls below the minimum level, and how to enable the replenishment process to run regularly using a batch job. These tasks would typically be carried out by a warehouse manager. You can run this procedure in the USMF demo data company using the example values below, or can run it on your own data. If you're using your own data, make sure that you have a warehouse that's enabled for Warehouse management processes.


## Create a fixed picking location
1. Go to **Navigation pane > Modules > Warehouse management > Setup > Warehouse > Fixed locations**. This is an optional task for min-max replenishment, but if you use fixed picking location, this allows stock to be replenished even if it falls below the minimum level, because the system can determine which items need to be replenished, even if there aren't any left.
2. Click **New**.
3. In the **Item number** field, enter or select a value. If you're using USMF, you can select item A0001.  
4. In the **Site** field, enter or select a value. If you're using USMF, you can select site 2.  
5. In the **Warehouse** field, enter or select a value. If you're using USMF, you can select warehouse 24.  
6. In the **Location** field, enter or select a value. If you're using USMF, you can select CP-003.  
7. Close the page.

## Create a replenishment location directive
1. Go to **Warehouse management > Setup > Location directives**. Location directives are used to determine where items should be picked from in the replenishment process.
2. In the **Work order type** field, select 'Replenishment'.
3. On the **Action Pane**, click **New**.
4. In the **Name** field, type a value.
5. In the **Work type** field, select 'Pick'.
6. In the **Site** field, enter or select a value. If you're using USMF, you can select site 2.  
7. In the **Warehouse** field, enter or select a value. If you're using USMF, you can select warehouse 24.  
8. Click **Save**.
9. In the **Lines** section, click **New**.
10. In the list, mark the selected row.
11. In the **To quantity** field, enter a number. For example, you can set it to 9999.  
12. Select the **Allow split** check box. If you select this option, the work creation process will allow work line quantities to be split across multiple locations.  
13. Click **Save**.
14. In the **Location directive Actions** section, click **New**.
15. In the list, mark the selected row.
16. In the **Name** field, type a value.
17. Click **Save**.
18. On the **Action Pane**, click **Edit query**. You can edit this query to add restrictions where inventory can be selected from in the replenishment process. For example, it could be that inventory should only be used from the Bulk area of the warehouse.
19. Click **OK**.
20. Close the page.

## Create a replenishment work template
1. Go to **Warehouse management > Setup > Work > Work templates**. The work template is use to guide the system as to how the min/max replenishment work must be created. As a minimum, there must be a work template line for a pick and a put. The work template will say that it's Invalid until all the necessary information has been filled in. 
2. In the **Work order type** field, select 'Replenishment'.
3. On the **Action Pane**, click **New**.
4. In the **Work template** field, type a value.
5. Click **Save**.
6. In the **Work template details**, click **New**.
7. In the **Work type** field, select 'Pick'.
8. In the **Work class ID** field, enter or select a value. This should be a work class related to replenishment. If you're using USMF, select Replenish.  
9. In the **Work template details**, click **New**.
10. In the list, mark the selected row.
11. In the **Work type** field, select 'Put'.
12. In the **Work class ID** field, enter or select a value.
13. Click **Save**.
14. Close the page.

## Create a new replenishment template
1. Go to **Warehouse management > Setup > Replenishment > Replenishment templates**. The replenishment template is used to define the items and quantities, and the location to replenish.
2. On the **Action Pane**, click **New**.
3. In the **Replenish template** field, type a value. Give the template a name to indicate that it's for min/max replenishment.  
4. In the **Description** field, type a value.
5. Select the **Allow wave demand to use unreserved quantities** check box. If you select this option, it enables wave demand replenishment to consume quantities that are related to min/max replenishment. For example, this might be useful if the min/max replenishment work isn't processed immediately, to avoid unnecessary demand replenishment work from being created.
6. In the **Replenishment template details**, click **New**.
7. In the **Sequence number** field, enter a number.
8. In the **Description** field, type a value.
9. In the list, mark the selected row.
10. In the **Replenishment unit** field, enter or select a value. For example, select pcs. This setting is mandatory. It allows you to specify a different unit of measurement for replenishment work compared to the unit specified for the minimum and maximum stock levels in this template.
11. In the **Work template** field, enter or select a value. Choose the work template that you created earlier.  
12. In the **Minimum quantity** field, enter a number. Select the minimum quantity that should trigger the replenishment. For example, set this to 50. It is possible to leave this set to zero, if you're replenishing a fixed location and the **Replenish empty fixed locations** option is set to 'Yes'. We also recommend that you select the **Replenish only fixed locations** option for performance reasons.
13. In the **Maximum quantity** field, enter a number. For example, set this to 100.  
14. In the **Unit** field, enter or select a value. Assign the unit for the minimum and maximum quantities. For example, set this to pcs.  
15. Select the **Replenish empty fixed locations** check box. Select this check box to replenish fixed locations when they are empty. Otherwise, only the locations where there is a quantity on hand will be replenished.
16. Select the **Replenish only fixed locations** check box.
17. Click **Select products**. This is the place to define which products should be replenished. If the Fixed picking locations option is selected, you also need to define the locations in this query. Variant-specific queries are available as well product-specific queries.
18. Select the **Items** row.
19. In the **Criteria** field, type a value. Select the items that should be replenished at the fixed locations. For example, type A* to select all item numbers beginning with A.
20. Click **Add**. Add the Location entity (unless it already exists) to be able to restrict the replenishment work to the fixed picking locations within a specific area of the warehouse.
21. In the list, mark the selected row.
22. Set the **Table** field to 'Locations'.
23. In the **Field** field, select 'Location profile ID'.
24. In the **Criteria** field, enter or select a value.
25. Click **OK**.
26. Close the page.

## Set the replenishment process to run as a batch job
1. Go to **Warehouse management > Replenishment > Replenishments**. The Replenishments page allows you to set up replenishment to run as a batch job, or to require that it's started manually.
2. Click **Filter**.
3. In the list, mark the selected row.
4. In the **Criteria** field, enter or select a value.
5. Click **OK**.
6. Expand the **Run in the background** section.
7. Set the **Batch processing** option to 'Yes'.
8. Click **Recurrence**.
9. Select the **No end date** option.
10. Set the **Recurrance pattern**. For example, select Days.  
11. Click **OK**.
12. Click **OK**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]