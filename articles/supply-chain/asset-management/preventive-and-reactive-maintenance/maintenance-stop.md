---
# required metadata

title: Maintenance downtime
description: This topic explains maintenance downtime in Asset Management.
author: josaw1
manager: AnnBe
ms.date: 06/28/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: CatProcureCatalogEdit, CatProcureCatalogListPage
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 2214
ms.assetid: 2f3e0441-414d-402b-b28b-7ab0d650d658
ms.search.region: Global
# ms.search.industry: 
ms.author: mkirknel
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Maintenance downtime

Maintenance downtime is used to get an overview of the capacity required to carry out maintenance jobs on specific assets during a specific period. For example, you can create a maintenance downtime registration for Production line 10 in Production Hall 29-A on production site 02. The maintenance downtime registration has a start and end time indicating the period in which the assets related to the maintenance stop are not available for production.

**Maintenance downtime activities** is an overview of maintenance schedule lines and work order maintenance jobs on related assets during a specified period. The lines related to work order maintenance jobs all have an expected start date within the maintenance stop period. You can extract useful information and make adjustments to planned maintenance jobs:

- Get an overview of required shut-down periods of production equipment (assets).  
- Get an overview of planned maintenance (hours), grouped by competencies (responsible maintenance worker groups or maintenance workers), for example capacity load on electricians, smiths, or other maintenance work groups required to do the planned maintenance jobs.  
- Make adjustments to maintenance schedule lines or work order maintenance jobs related to the assets, for example, change expected start and end times on a line, or select other maintenance workers to optimize the workflow for maintenance workers and maintenance worker groups.

When assets have been selected on a maintenance downtime registration, all open maintenance schedule lines and work order maintenance jobs relating to active work orders are included in the maintenance downtime registration.

## Maintenance downtime activities

Click **Asset management** > **Common** > **Maintenance downtime activities** > **All maintenance downtime activities** to open a list of all maintenance downtime activities and see some of the information related to the activities. Click on a link in the **Maintenance downtime activities** column to open the details view.

![Figure 1](media/19-preventive-maintenance.png)


## Create a maintenance downtime registration

1. Click **Asset management** > **Common** > **Maintenance downtime activities** > **All maintenance downtime activities** or **Active maintenance downtime activities**.

2. Click **New**.

3. Insert an ID in the **Maintenance downtime activities** field and a name in the **Name** field.

4. Insert the period for the maintenance stop in the **Start date/time** and **End date/time** fields.

5. On the**Maintenance downtime activities assets** FastTab> click **Add line** to add assets, one at a time, to the maintenance downtime activity.

6. Click **Save** when all objects have been added.

7. The work order lines and open object calendar lines related to the selected objects are shown on the tabs on the **Related** FastTab. On the **General** FastTab > **Forecast hours** fields, you see the total number of hours forecasted for object calendar lines and work order lines.

>[!NOTE]
>The object calendar lines and work order lines related to the selected objects are automatically updated if new work orders or object calendar lines have been created after you created the maintenance stop. For example, if you schedule maintenance sequences or rounds on the related objects two days after the maintenance stop was created, new object calendar lines are automatically added to the maintenance stop record.

8. In **All maintenance stops** > **Maintenance stop** tab > click **Capacity load** > **Capacity load** > **Calculate capacity load** to calculate forecasted hours and group them to get an overview of capacity load on, for example, by date, object, object type and job type. Click **OK** in the **Capacity load** drop-down. Note that the dates shown in the Capacity load drop-down are the start and end dates selected in **All maintenance stops**. This calculation only includes the objects related to the maintenance stop.

9. The total number of hours is shown in the **Capacity load** overview.

10. On the **Capacity load** tab > the **Group by...** action pane groups, click the relevant buttons to get a more detailed overview of the allocation of forecasted hours.

11. After you get an overview of the capacity load, if you want to make adjustments on object calendar lines or work order lines, return to **All maintenance stops** detail view and select the lines you want to adjust on the **Related** FastTab.

12. Click the **Adjust** button and update expected start/end dates, priority, or responsible workers for the selected object calendar lines or work order lines.

13. Click **OK** when you have made the required adjustments. Object calendar lines or work order lines that are not included in the maintenance stop period after you have made adjustments are automatically removed from **All maintenance stops**.

>[!NOTE]
>When you make adjustments to work order lines, you change the related work order.

14. In **All maintenance stops** > **Maintenance stop** tab > click **Item forecast** > **Item forecast** > **Calculate item forecast** to calculate forecasts for items (spare parts and other required items) and group them to get an overview, for example, by date, object, object type and job type. Click **OK** in the **Calculate item forecast** drop-down. Note that the dates shown in the **Item forecast** calculation form are the start and end dates selected in **All maintenance stops**. This calculation only includes the objects related to the maintenance stop.

15. The total number of item forecasts is shown in **Item forecast**, and you can now select the relevant check boxes to get a more detailed overview of the allocation of forecasted items.

![Figure 2](media/20-preventive-maintenance.png)


- You can copy objects from one maintenance stop to another. In **All maintenance stops**, select the **Copy maintenance stop** button, and make your selections in the **From maintenance stop** and **To maintenance stop** fields, and click **OK**.
- In **All maintenance stops**, click the **Object calendar lines** button or the **Active work orders** button to open the related lists and view the lines related to the selected maintenance stop.

![Figure 3](media/21-preventive-maintenance.png)

![Figure 4](media/22-preventive-maintenance.png)

![Figure 5](media/23-preventive-maintenance.png)

