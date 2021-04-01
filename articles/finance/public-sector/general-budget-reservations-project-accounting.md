---
# required metadata

title: Project accounting with general budget reservations
description: This topic provides information about project accounting that uses general budget reservations for Public sector.
author: AlexRenney
ms.date: 04/25/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: BudgetReservation_PSN 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: Global
ms.search.industry: Public sector
ms.author: brpotter
ms.search.validFrom: 2018-10-31
ms.dyn365.ops.version: 8.1

---

# Project accounting with general budget reservations

[!include [banner](../includes/banner.md)]

If your organization uses project accounting, you can include references to your project in general budget reservations. These references can affect budgeting, committed costs, and the reservation and consumption of funding sources.

Some expenditures are planned to be charged to projects. When you create a general budget reservation, you can specify the project and project category that a planned purchase is for. You can also specify other project-related information, such as the expected sales price. (For public sector entities, the expected sales price is typically the cost price.) All this information is included on the purchasing documents that are generated for projects later.

If the general budget reservation contains a project distribution, the purchase order, purchase requisition, or vendor invoice that references the reservation must include the project distribution and all project information. This information is automatically copied to the source document from the general budget reservation.

## Turn on tracking of committed costs for general budget reservations

Project committed costs are created when purchasing documents are approved, confirmed, or posted. The costs represent amounts that will be spent on a project. Project managers can view pending costs for a project to track accurate information about their project's costs.

1. Go to **Project management and accounting \> Setup \> Project management and accounting parameters**.
2. On the **Cost control** tab, on the **Cost commitments** FastTab, set the **General budget reservation** option to **Yes**.

    - The **Purchase requisition**, **Purchase order**, and **Vendor invoice** options will automatically be set to **Yes**.
    - When the general budget reservation is posted, it will be counted in the project's committed costs.

## Specify project information in a general budget reservation

1. Go to **Budgeting \> General budget reservations**.
2. Create a general budget reservation.
3. On the **General budget reservation lines** FastTab, add a project ID and project category for each applicable reservation line. Information from the project will automatically be copied to the reservation.
4. Optional: To view the project details, on the **Line details** FastTab, select the **Project** tab.

## View project committed costs for a general budget reservation

When you post a general budget reservation for a project, a committed cost is created for the reservation amount against that project. The committed cost represents the total amount of the distributions to that project.

1. Go to **Budgeting \> General budget reservations**.
2. Open the posted general budget reservation that you want, and select a reservation line.
3. Select **Committed costs**. The **Committed costs** page appears and shows the committed costs that are related to the selected line.

    Committed costs for general budget reservations are based on amount, regardless of whether the committed cost includes a discrete quantity and unit cost. The committed cost quantity will always be 1.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]