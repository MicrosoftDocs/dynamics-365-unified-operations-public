---
# required metadata

title: Creating work orders
description: This topic explains how to create work orders in Enterprise Asset Management.
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

# Creating work orders

This topic explains how to create work orders in Enterprise Asset Management. When you have scheduled preventive maintenance jobs, next step is to create work orders for the jobs. This is done in one of the object calendars. The scheduled jobs in an object calendar can have different reference types:

| Maintenance sequences | Preventive maintenance jobs based on maintenance sequence types "Time" or "Counter".                       |
|-----------------------|------------------------------------------------------------------------------------------------------------|
| Rounds                | Preventive maintenance job including several objects that require a similar type of maintenance.           |
| Requests              | Manually created request for maintenance or repair of an object, which can be converted into a work order. |

1. Click **Enterprise asset management** > **Common** > **All object calendars** or **Open object calendar lines** or **Open object calendar pools**.

2. Select the scheduled maintenance jobs for which you want to create a work order and click **Work order**. The total number of forecast hours for the selected lines is shown in the **Forecast hours** field.

3. In the **Parameters** section, select how many work orders should be created. You can create one work order per line or several work orders, based on date or various groups or types.

4. Select a **Work order type** to be used on all the work orders you create.

5. Click **OK**. One or more work orders are created.

The figure below shows a screenshot of the interface.

![Figure 1](media/17-preventive-maintenance.png)
