---
# required metadata

title: Register consumption
description: This topic explains how to register consumption in Enterprise Asset Management.
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

# Register consumption

This topic explains how to register consumption in Enterprise Asset Management. When a maintenance job has been completed on a work order, the next step is to make consumption registrations and post the journals. You can make registrations on the following consumption types: Hours, items, and expenses. The different consumption types are registered and posted in the **Journal** form. The journal setup in **Enterprise Asset Management** is used for creating and posting separate journals for hours, items, and expenses in **Project management and accounting**.

You may be able to add or delete forecast lines on a work order. The setup of a work order stage, the related project type, and the stage rules related to the project type determine if you are able to add or edit journal lines. Read more about work order stages and related project stages in [Integration to project management and accounting](../integration-to-project-management-and-accounting/objects-and-projects.md).

>[!NOTE]
>It is possible to set up automatic posting of journals on a work order stage. Refer to [Work order stages](../setup-for-work-orders/work-order-stages.md) for more information.

1. Click **Enterprise asset management** > **Common** > **Work orders** > **All Work orders** or **Active work orders**.

2. Select the work order and click **Journals**.

3. Click **Copy from forecast** to transfer any forecast lines that may be connected to the work order. You can select which consumption types you want to transfer.

4. If necessary, you can add more consumption lines on the relevant FastTab by clicking **Add** and filling out data on the line.

5. If you add a line on the **Items** FastTab, when you select the item in the **Item number** field, there are three tabs that may contain items: On the **All items** tab, all active items are shown. On the **Spare parts** tab, a list of all approved spare parts from the object type setup is shown. On the **Object BOM** tab, all items related to the object BOM is shown.

>[!NOTE]
>You may find the list of items on the **Spare parts** and **Object BOM** tabs useful if, for example, the work order was created due to a breakdown or another unplanned event. In that case, an item forecast may not be related to the work order.

6. Click **Validate journals** to validate the journal lines before posting.

7. Click **Post journals** to post the journal lines.

8. After you have posted the consumption journals, you can update the work order stage, for example to "Ended", to indicated that the work order has been completed.

- In the **Show** field placed at the top of the form, select which journal lines you want to see: All, Not posted, or Posted. Posted journals have a check mark in the **Posted** check box.  
- When item lines are created in the work order journal, product dimensions and tracking dimensions related to the item are automatically transferred to the journal line.  

The figure below shows a screenshot of the interface.

![Figure 1](media/01-consumption.png)

## Split hours on work orders with several work order lines

If a work order contains several work order lines, you can register work hours using the **Split hours** functionality, meaning the hours will be distributed evenly on each work order line.

1. Click **Enterprise asset management** > **Common** > **Work orders** > **All Work orders** or **Active work orders**.

2. Select the work order and click **Journals**.

3. Click **Split hours**.

4. The name of the worker who is logged in is automatically shown in the **Worker** field. If required, you can select another worker.

5. Select a category for the hour registration in the **Category** field.

6. Insert number of work hours in the **Hours** field.

7. Click **OK**.

*Example:* If you make a registration for three work hours, and the work order contains three work order lines, one hour will be registered on each work order line. The figure below shows a screenshot of the interface.

![Figure 2](media/02-consumption.png)

![Figure 3](media/03-consumption.png)

## Financial dimensions on consumption registrations

When you make consumption registrations, financial dimensions related to the different registration types are added to the registrations in a specific sequence.

*Hour and Expense Registrations:* First, financial dimensions from the journal header are added, if any. Next, financial dimensions from the related work order project are added. Finally, financial dimensions from the resource (worker) are added.

*Item Registrations:* First, financial dimensions from the journal header are added, if any. Then, financial dimensions from the related work order project are added. Next, financial dimensions from the site are added. Finally, financial dimensions from the item are added.

>[!NOTE]
>For all three registration types, the financial dimension combination is validated, and invalid combinations are blanked. This is standard setup in Dynamics 365 for Finance and Operations.
