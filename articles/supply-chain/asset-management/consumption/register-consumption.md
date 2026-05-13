---
title: Register consumption
description: Learn how to register consumption in Asset Management, including a step-by-step process for splitting hours on work orders with several work order jobs.
author: jodahlMSFT
ms.author: jodahl
ms.reviewer: kamaybac
ms.search.form: EntAssetWorkOrderJournal, EntAssetWorkOrderAddSparePart 
ms.topic: how-to
ms.date: 05/13/2026
ai-usage: ai-assisted
ms.custom:
  - bap-template
---

# Register consumption

[!include [banner](../../includes/banner.md)]

When a maintenance job on a work order is complete, the next step is to register consumption and post the journals. Register consumption for the following types: hours, items, and expenses. Register and post the different consumption types on the **Work order journals** page. The journal setup in **Asset Management** is used for creating and posting separate journals for hours, items, and expenses in the **Project management and accounting** module.

In some cases, you can add or delete forecast lines on a work order. The setup of a work order lifecycle state, the related project type, and the stage rules related to the project type determine if you can add or edit journal lines. Learn more about work order lifecycle states and related project stages in [Forecasts, work orders, and projects](../integration-to-project-management-and-accounting/forecasts-work-orders-and-projects.md).

> [!NOTE]
> You can set up automatic posting of journals on a work order lifecycle state. Learn more in [Work order lifecycle states](../setup-for-work-orders/work-order-lifecycle-states.md).

1. Select **Asset management** \> **Work orders** \> **All Work orders** or **Active work orders**.
1. Select the work order, and select **Journals**.
1. Select **Copy from forecast** to transfer any forecast lines that might be connected to the work order. You can select which consumption types you want to transfer.
1. If necessary, add more consumption lines on the relevant FastTab by selecting **Add line** and filling out data on the line.
1. Select **Validate journals** to validate the journal lines before posting.
1. Select **Post journals** to post the journal lines.
1. After you post the consumption journals, you can update the work order lifecycle state. For example, to indicate that the work order is complete, update the lifecycle state to **Ended**.
    - In the **Show** field at the top of the **Work order journals** page, select which journal lines you want to see: **All**, **Not posted**, or **Posted**. Posted journals have a check mark in the **Posted** check box.  
    - When you create item lines in the work order journal, product dimensions and tracking dimensions related to the item automatically transfer to the journal line.  

The following screenshot shows an example of hour and item registrations on a work order in **Work order journals**.

:::image type="content" source="media/01-consumption.png" alt-text="Screenshot of Work order journals page showing Hours and Items sections with registration lines for posting." lightbox="media/01-consumption.png":::

## Split hours on work orders with several work order jobs

If a work order contains several work order jobs, use the **Split hours** functionality to register work hours. You can distribute one hour registration line evenly across each work order job.

1. Select **Asset management** \> **Work orders** \> **All Work orders** or **Active work orders**.
1. Select the work order and select **Journals**.
1. Select the hour registration line you want to split, and select **Split hours**.
1. In the **Split hours on work order maintenance jobs** dialog, the name of the worker who is signed in automatically appears in the **Worker** field. If required, select another worker.
1. Select a category for the hour registration in the **Category** field.
1. Enter the number of work hours to split in the **Hours** field.

    :::image type="content" source="media/02-consumption.png" alt-text="Screenshot of the Split hours on work order maintenance jobs dialog with Worker, Category, and Hours fields." lightbox="media/02-consumption.png":::

1. Select **OK**.

*Example:* The following screenshot shows journal lines for a work order containing three work order jobs. The first line, which contains three work hours, is split, and one work hour is registered on each work order job. After the three hour registration lines are created, you decide what to do with the original hour registration line (the first line in the example). You can keep it as-is or delete it.

:::image type="content" source="media/03-consumption.png" alt-text="Screenshot of Work order journals page with split hour registration lines highlighted for three work order jobs." lightbox="media/03-consumption.png":::

## Financial dimensions on consumption registrations

When you make consumption registrations, the system adds financial dimensions related to the different registration types to the registrations in a specific sequence.

- *Hour and Expense registrations:* First, the system adds financial dimensions from the journal header, if any. Next, it adds financial dimensions from the related work order project. Finally, it adds financial dimensions from the resource (worker).
- *Item registrations:* First, the system adds financial dimensions from the related work order project. Next, it adds financial dimensions from the site. Finally, it adds financial dimensions from the item.

> [!IMPORTANT]
> If the [dimension link](../../cost-management/financial-dimension-links.md) feature is active (on **Inventory management** \> **Setup** \> **Posting** \> **Dimension link**) and a financial dimension is linked to the inventory site, the linked dimension values from the site take precedence on item registrations. In this case, the values from the dimension attributes override the values that came from the related work order project.

>[!NOTE]
>For all three registration types, the system validates the financial dimension combination and blanks invalid combinations.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
