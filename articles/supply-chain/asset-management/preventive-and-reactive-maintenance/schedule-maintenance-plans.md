---
# required metadata

title: Schedule maintenance plans
description: This topic explains schedule maintenance plans in Asset Management.
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

# Schedule maintenance plans

Preventive maintenance scheduling generates calendar entries on assets, based on the maintenance plans set up on the assets. You can schedule calendar entries based on selected maintenance plans, asset types, and assets.

1. Click **Asset management** > **Periodic** > **Preventive maintenance** > **Schedule maintenance plans**.

2. You can select a time interval in the **Period** and **Period frequency** fields.

>[!NOTE]
>The **Period** and **Period frequencey** fields indicate how far ahead in time you want maintenance schedule lines to be created, based on the maintenance plans you have created (time-based or counter-based). In the figure below, maintenance schedule lines (= work order proposals) are created from the current date and three months onwards.

3. Select "Yes" on the **Auto create if specified in the line** toggle button if work orders should automatically be created according to the maintenance plan line.

>[!NOTe]
>If this toggle button is set to "Yes", and the **Auto create** toggle button is also set to "Yes" on maintenance sequence lines in **Maintenance sequences**, work orders are created based on the maintenance sequence lines, and object calendar lines with status "Work order created" are also created. If only one of the **Auto create** toggle buttons is set to "Yes", in this form or in **Maintenance sequences**, only object calendar lines are created with status "Created". In that case, no work orders are created.

4. It is possible to generate calendar entries based on maintenance sequences (time or counter), objects, object types, functional locations, and functional location types. Click the **Filter** button and make your selections, if relevant.

- Regarding scheduling of maintenance sequences on functional locations: If you update the setup of object types, products, and models on maintenance sequences in **All functional locations** > **Maintenance sequences** FastTab after you have scheduled maintenance sequences, existing object calendar entries related to that functional location are automatically deleted. In order to create new calendar entries, which correspond with the updated maintenance sequence setup on the functional location, you must run a new maintenance sequence schedule for that functional location. Read more about the setup of object types, products, and models on functional locations in [Create functional locations](../functional-locations/create-functional-locations.md).

>*Example:* You want to create a maintenance sequence for a specific functional location, meaning all objects set up on that functional location at any given time will be included when you run the sequence. In that case, you create a maintenance sequence and select the specific functional location, but you do NOT add any objects in the maintenance sequence. The result is that when you run that maintenance sequence, object calendar lines will be created for all the objects related to the functional location at that time.

- If you make changes to object types, products and models in **Object types**, those changes only affect new objects that use the updated object type. Read more about object type setup in [Object types](../setup-for-objects/object-types.md).  

5. Click **OK** to start the generation of calendar posts on objects. The generated calendar posts will be displayed in the **Object calendar**.

The figure below shows a screenshot of the interface.

![Figure 1](media/09-preventive-maintenance.png)

- In **Schedule maintenance sequences**, you can set up batch jobs on the **Run in the background** FastTab to automatically generate calendar entries at regular intervals.  
- When you schedule preventive maintenance, maintenance schedule lines with expected start date and time earlier than the system date and time will not be created.  

The figure below provides a graphic illustration of a time-based maintenance plan calculation.  

![Figure 2](media/10-preventive-maintenance.png)

Regarding counter-based maintenance sequences: In the figures below, two different counter registration cycles are shown. They are based on a maintenance sequence set up for object "V0001", expecting the object (a car) to run approx. 2,000 km every month.

In the first example, the expected 2,000 km are not reached every month. According to the counter-based maintenance sequence, the threshold is 2,000 km, meaning when you run a maintenance sequence scheduling, an object calendar line should be created each time the 2,000-kilometer threshold is reached. In example 1, there are 4 registration lines, but the 2,000-kilometer threshold is only reached once. This means that when you run schedule maintenance sequences for this object, for example for a 3-month period, only one object calendar line will be created.

In the next figure, 2,000 km or more are registered every month. Therefore, three object calendar lines would be created if you schedule maintenance sequences for this object for a 3-month period.

The examples described here show that all counter registrations made on an object show a trend describing wear and tear on the object. That trend is used as calculation basis at the time of maintenance sequence scheduling.

![Figure 3](media/11-preventive-maintenance.png)

![Figure 4](media/12-preventive-maintenance.png)
