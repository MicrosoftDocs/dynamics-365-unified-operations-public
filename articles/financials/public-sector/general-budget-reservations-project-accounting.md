---
# required metadata

title: Project accounting with general budget reservations
description: This topic provides information about project accounting with general budget reservations for public sector in Microsoft Dynamics 365 for Finance and Operations.
author: ShylaThompson
manager: AnnBe
ms.date: 02/20/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
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

If your organization uses project accounting, you can include references to your project in general budget reservations. This can affect budgeting, committed costs, and funding-source reservations and consumption.

Certain expenditures are planned to be charged to projects. When you create a general budget reservation, you can specify that the planned purchase is for a specific project and project category. You can also specify other project-related information, such as the expected sales price (for public sector entities, this typically is the cost price). These values are all included on the subsequent purchasing documents for projects.

If the general budget reservation contains a project distribution, then the purchase order, purchase requisition, or vendor invoice that references the reservation must include the project distribution and all project information. This information is copied automatically to the source document from the general budget reservation.

## Enable committed cost tracking for general budget reservations

Project committed costs are created when purchasing documents are approved, confirmed, or posted. The costs represent amounts that will be spent on a project. Project managers can view pending costs for a project in order to track accurate information about their project's costs.

1.  Go to **Project management and accounting \> Setup \> Project management and accounting parameters**.
2.  Select the **Cost control** tab.
3.  Under **Cost commitments** section, select the **General budget reservation** check box.

    -   The Purchase requisition, Purchase order and Vendor invoice check boxes will be automatically selected.
    -   When the general budget reservation is posted, it will be counted in the project’s committed costs.

## Specify project information in a general budget reservation

1.  Go to **Budgeting \> General budget reservations**.
2.  Create a general budget reservation.
3.  Under **General budget reservation lines**, add a project ID and project category for each applicable reservation line. Information from the project will be copied automatically to the reservation.

4.  Optional: To see the project details, expand the **Line details** section, and then click the **Project** tab.

## View project committed costs for a general budget reservation

When you post a general budget reservation for a project, a committed cost (the total amount of the distributions to that project) is created for the reservation amount against that project.

1.  Go to **Budgeting \> General budget reservations**.

2.  Open the posted general budget reservation that you want, and then select a reservation line.

3.  In the **Line details** section, click the **Committed costs**. The **Committed costs** page opens, displaying the committed costs related to the selected line.

    > Committed costs for general budget reservations are based on amount, regardless of whether the committed cost includes a discrete quantity and unit cost. The committed cost quantity will always be 1.
