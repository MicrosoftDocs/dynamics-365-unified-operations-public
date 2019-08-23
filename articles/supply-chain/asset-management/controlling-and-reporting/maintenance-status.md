---
# required metadata

title: Maintenance status
description: This topic explains how to calculate maintenance status in Asset Management.
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

In Asset Management, you can make a calculation to see an overview of new, active, and completed maintenance requests, work orders, and maintenance downtime activities for a specific period. You can also see the number of completed condition assessments for the same period. Use this calculation to get an overview of workload regarding incoming and completed maintenance requests and work orders.

## Make a maintenance status calculation

1. Click **Asset management** > **Inquiries** > **Maintenance status**.

2. In the **Calculate status** dialog, select the period for which you want to make the calculation in the **From date** and **To date** fields.

3. You can use the **Level** field to indicate how detailed you want the maintenance lines to be regarding functional locations. For example, if you insert the number "1" in the field, and you have a multi-level functional location structure, all maintenance lines for a functional location will be shown on the top level, and therefore the status on a line may be added up from functional locations located at a lower level. If you insert the number "0" in the **Level** field, you see a detailed result showing all maintenance lines on all the functional location levels to which they are related.

4. Click **OK** to start the calculation.

5. In the **Group by...** action pane groups, click the relevant buttons to show the required detail level of the calculation. The selected action pane buttons are highlighted. Click on a button to activate or deactivate it.

6. Remember to click the **Update** button to update the calculation each time you make changes by activating or deactivating **Group by...** buttons, or by making a calculation for a new period.

7. Click **Status** if you want to create a new maintenance status calculation.

>[!NOTE]
>The results shown in **Maintenance status** only include maintenance requests and work orders that have an actual start date and time. End date and time may be blank.

*Example 1:*

In the figure below, the **Year** and **Month** buttons have been activated. Here, you get a general overview on a monthly basis of workload and throughput related to maintenance requests and work orders. 

![Figure 1](media/13-controlling-and-reporting.png)

*Example 2:*

In the figure below, information about functional locations has been added. Now, it is possible to compare workload and throughput across functional locations, which may represent geographical locations, factories, or work areas. 

![Figure 2](media/14-controlling-and-reporting.png)

