---
# required metadata

title: Work order types
description: This topic explains work order types in Asset Management.
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

# Work order types


A work order type is used to categorize a work order, for example relating to preventive maintenance or corrective maintenance. A work order type defines the work order lifecycle model affiliation. **Work order lifecycle model** defines which work order lifecycle states can be set on a work order, for example, "Created", "In Process", and "Finished".

Refer to [Work order lifecycle states](../setup-for-work-orders/work-order-stages.md) for more information about work order lifecycle states and project stages.

1. Click **Asset management** > **Setup** > **Work orders** > **Work order types**.
2. Click **New** to create a new work order type.
3. Insert the work order type ID in the **Work order type** field and a name in the **Name** field.
4. Select a lifecycle model in the **Work order lifecycle model** field.
5. Select "Yes" on the **One maintenance worker** toggle button if all work order jobs related to a work order of this type should be scheduled to the same maintenance worker.
6. In the **Cost type** field, select cost type, "Corrective", "Preventive", or "Investment". All work order jobs on a work order must contain the same cost type.
7. In the **Mandatory** section, select "Yes" on the toggle buttons for which you want to ensure that information relating to faults or maintenance downtime is added to the work order.
8. Click **Save**.

>[!NOTE]
>The toggle buttons in the **Mandatory** section relate to the toggle buttons on the **Validate** FastTab in **Work order lifecycle states** (**Asset management** > **Setup** > **Work orders** > **Lifecycle states**).


![Figure 1](media/16-setup-for-work-orders.png)

