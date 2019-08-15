---
# required metadata

title: Calculate item forecast
description: This topic explains how to calculate item forecast in Asset Management.
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

# Calculate item forecast

Just as you can make capacity load calculations, which are described in the previous section, you can also make item forecast calculations on

- Maintenance schedule lines  
- Work orders that have not yet been scheduled  
- Scheduled work orders

This is useful if you want to get an overview of expected item consumption (spare parts as well as other items required for completing work orders) for a specific period. Calculation of item forecast can be done on all assets or selected assets. You can also make a calculation on a maintenance downtime activity (**All maintenance downtime activities** or **Active maintenance downtime activities**), or on a work order pool (**All work order pools** or **Active work order pools**).

1. Click **Asset management** > **Inquiries** > **Item forecast**, or **Asset management** > **Common** > **Work order pools** > **All work order pools** / **Active work order pools** > select work order pool in the list > **Item forecast** button, or **Asset management** > **Common** > **Maintenance downtime activities** > **All maintenance downtime activities** / **Active maintenance downtime activities** > select maintenance downtime activity in the list > **Item forecast** button.

2. In the **Calculate item forecast** dialog, select a period for the calculation in the **Start date/time** and **End date/time** fields.

3. Select "Yes" on the **Include maintenance schedule** toggle button if you want to include maintenance schedule lines in the forecast calculation.

4. Select "Yes" on the **Include work order** toggle button if you want to include work order jobs in the forecast calculation.

5. You can use the **Level** field to indicate how detailed you want the item forecast lines to be regarding functional locations. For example, if you insert the number "1" in the field, and you have a multi-level functional location structure, all object calendar lines and work orders for a functional location will be shown on the top level, and therefore the hours on a line may be added up from functional locations located at a lower level. If you insert the number "0" in the **Level** field, you will see a detailed result showing all object calendar lines and all work orders on all the functional location level to which they are related.

6. Click **OK** to start the calculation.

7. In the **Group by...** action pane groups, click the relevant buttons to show the required detail level of the calculation. The selected action pane group buttons are highlighted. Click on a button to activate or deactivate it.

8. Click the **Display dimensions** button if you want to see one or more dimensions related to the items. Select the relevant check boxes, and click **OK**.

The figure below shows a screenshot of the interface.

![Figure 1](media/02-capacity-planning.png)
