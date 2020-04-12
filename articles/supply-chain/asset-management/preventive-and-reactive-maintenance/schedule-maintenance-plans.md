---
# required metadata

title: Schedule maintenance plans
description: This topic explains schedule maintenance plans in Asset Management.
author: josaw1
manager: tfehr
ms.date: 08/27/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: mkirknel
ms.search.validFrom: 2019-08-31
ms.dyn365.ops.version: 10.0.5

---

# Schedule maintenance plans

[!include [banner](../../includes/banner.md)]

 

Preventive maintenance scheduling generates calendar entries on assets, based on the maintenance plans set up on the assets. You can schedule calendar entries based on selected maintenance plans, asset types, and assets.

1. Click **Asset management** > **Periodic** > **Preventive maintenance** > **Schedule maintenance plans**.

2. You can select a time interval in the **Period** and **Period frequency** fields.

>[!NOTE]
>The **Period** and **Period frequencey** fields indicate how far ahead in time you want maintenance schedule lines to be created, based on the maintenance plans you have created (time-based or counter-based). In the figure below, maintenance schedule lines (= work order proposals) are created from the current date and three months onwards.

3. Select "Yes" on the **Auto create if specified in the line** toggle button if work orders should automatically be created according to the maintenance plan line.

>[!NOTE]
>If this toggle button is set to "Yes", *and* the **Auto create** check box is also selected on maintenance plan lines in **Maintenance plans**, work orders are created based on the maintenance plan lines, and maintenance schedule lines with status "Work order created" are also created. If only one option is selected (**Auto create if specified in the line** toggle button in this dialog or **Auto create** check box in **Maintenance plans** form), only maintenance schedule lines are created with status "Created". In that case, no work orders are created.

4. It is possible to generate calendar entries based on maintenance plans (time or counter), assets, asset types, functional locations, and functional location types. Click the **Filter** button and make your selections, if required.

- Regarding scheduling of maintenance plans on functional locations: If you update the setup of asset types, manufacturers, and models on maintenance plans in **All functional locations** > **Maintenance plans** FastTab after you have scheduled maintenance plans, existing maintenance schedule entries related to that functional location are automatically deleted. In order to create new calendar entries, which correspond with the updated maintenance plan setup on the functional location, you must run a new maintenance plan schedule for that functional location. Read more about the setup of asset types, manufacturers, and models on functional locations in [Create functional locations](../functional-locations/create-functional-locations.md).

>*Example:* You want to create a maintenance plan for a specific functional location, meaning all assets set up on that functional location at any given time will be included when you schedule the maintenance plan. In that case, you create a maintenance plan and select the specific functional location, but you do NOT add any assets in the maintenance plan. The result is that when you schedule that maintenance plan, maintenance schedule lines will be created for all the assets related to the functional location at that time.

- If you make changes to asset types, manufacturers and models in **Asset types**, those changes only affect new assets that use the updated asset type. Read more about asset type setup in [Asset types](../setup-for-objects/object-types.md).  

5. Click **OK** to start the generation of maintenance schedule entries on assets. The generated entries will be shown in the **All maintenance schedule** list page. The following illustration shows an example of the **Schedule maintenance plans** dialog.

![Figure 1](media/09-preventive-maintenance.png)

- In the **Schedule maintenance plans** dialog, you can set up batch jobs on the **Run in the background** FastTab to automatically generate calendar entries at regular intervals.  
- When you schedule preventive maintenance, maintenance schedule lines with expected start date and time earlier than the system date and time will not be created.  

The figure below provides a graphic illustration of a time-based maintenance plan calculation.  

![Figure 2](media/10-preventive-maintenance.jpg)

Regarding counter-based maintenance plans: In the figures below, two different counter registration cycles are shown. They are based on a maintenance plan set up for asset "V0001", expecting the asset (a car) to run approx. 2,000 km every month.

In the first example, the expected 2,000 km are not reached every month. According to the counter-based maintenance plan, the threshold is 2,000 km, meaning when you run a maintenance plan scheduling, a maintenance schedule line should be created each time the 2,000-kilometer threshold is reached. In example 1, there are 4 registration lines, but the 2,000-kilometer threshold is only reached once. This means that when you run schedule maintenance plans this asset, for example for a 3-month period, only one maintenance schedule line will be created.

In the next figure, 2,000 km or more are registered every month. Therefore, three maintenance lines would be created if you schedule maintenance plans for this asset for a 3-month period. 

The examples described here show that all counter registrations made on an asset show a trend describing wear and tear on the asset. That trend is used as calculation basis at the time of maintenance plan scheduling.

![Figure 3](media/11-preventive-maintenance.png)

![Figure 4](media/12-preventive-maintenance.png)

