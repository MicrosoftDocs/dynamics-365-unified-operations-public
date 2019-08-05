---
# required metadata

title: Scheduled execution
description: This topic explains scheduled execution in Asset Management.
author: josaw1
manager: AnnBe
ms.date: 06/27/2019
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

# Scheduled execution


Work order service levels, which are described in the previous section, can be used to set up scheduled execution. You can use scheduled execution to provide flexibility in work planning for the maintenance worker by setting up more detailed or less detailed requirements regarding the interval during which a work order should be completed. For example, if a maintenance worker has completed a job faster than expected in a production facility, the worker may be able to complete a job nearby, not necessarily planned for the current day, but for the current week. This approach provides the possibility of optimizing worker planning and job completion.

Scheduled execution can be set up for various levels related to a work order. You can set up generic lines - as shown in the figure below - that are not limited to specific work order types, asset types, and so on. Or you can create specific scheduled execution lines that apply to a work order type, asset type, job type, and so on, or a combination.

1. Click **Asset management** > **Setup** > **Work orders** > **Scheduled execution**.
2. Click **New** to create a new scheduled execution line.
3. Make selections as required in the **Functional location**, **Work order type**, **Asset type**, **Manufacturer**, **Model**, **Maintenance job type category**, **Maintenance job type**, **Maintenance job type variant**, or **Trade** fields.
4. Select a work order service level in the **Service level** field. If you leave this field blank, you can make the most generic scheduled execution line - as shown in the first record in the figure below. That line is set up to allow all work orders that have no work order service level to be scheduled for a specific date and time.
5. Select the time interval in the **Scheduled execution** field.
6. Click **Save**.


![Figure 1](media/20-setup-for-work-orders.png)

