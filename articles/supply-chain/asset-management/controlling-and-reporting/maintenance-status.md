---
# required metadata

title: Maintenance status
description: This topic explains how to calculate maintenance status in Enterprise Asset Management.
author: josaw1
manager: AnnBe
ms.date: 07/01/2019
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

# Maintenance status

This topic explains how to calculate maintenance status in Enterprise Asset Management. In Enterprise Asset Management, you can make a calculation to see an overview of new, active, and completed requests, work orders, and production stops for a specific period. You can also see the number of completed condition assessments for the same period. You can use these calculations to get an overview of workload regarding incoming and completed requests and work orders.

## Make a maintenance status calculation

1. Click **Enterprise asset management** > **Inquiries** > **Maintenance status**.

2. Click **Maintenance status** > **Status**.

3. Select the period for which you want to make the calculation.

>[!NOTE]
>You can use the **Level** field to indicate how detailed you want the maintenance lines to be regarding functional locations. For example, if you insert the number "1" in the field, and you have a multi-level functional location hierarchy, all maintenance lines for a functional location will be shown on the top level, and therefore the status on a line may be added up from functional locations located at a lower level. If you insert the number "0" in the **Level** field, you will see a detailed result showing all maintenance lines on all the functional location levels to which they are related.

4. Click **OK** to start the calculation.

5. In the **Group by...** action pane groups, click the relevant buttons to show the required detail level of the calculation. The selected action pane group buttons are highlighted in orange color. Click on a button to activate or deactivate it.

6. Remember to click the **Update** button to update the calculation each time you make changes by activating or deactivating **Group by...** buttons, or by making a calculation for a new period.

>[!NOTE]
>The results shown in **Maintenance status** only include requests and work orders that have an actual start and date and time. End date and time may be blank.

*Example 1:*

In the figure below, only the **Year** and **Month** fields have been activated. Here you can get a general overview on a monthly basis of workload and throughput related to requests and work orders.

![Figure 1](media/17-controlling-and-reporting.png)

*Example 2:*

In the figure below, information about functional locations has been added. Now, it is possible to compare workload and throughput across functional locations, which may represent, for example, geographical locations, factories, or different work areas.

![Figure 2](media/18-controlling-and-reporting.png)
