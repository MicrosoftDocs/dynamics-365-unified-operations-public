---
# required metadata

title: Create and process nonconformances
description: This article describes how to perform nonconformance management based on an existing quality order.
author: yufeihuang
ms.date: 03/23/2021
ms.topic: how-to
ms.prod:  
ms.technology:  

# optional metadata

# ms.search.form:   
audience: Application User
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Distribution
ms.author: yufeihuang
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: AX 7.0.0
---
# Create and process nonconformances

[!include [banner](../../includes/banner.md)]

This article describes how to perform nonconformance management based on an existing quality order. Typically, nonconformance management is done by a quality clerk. As a prerequisite, you must have a quality order available. (For information about how to create a quality order, see [Inspect the quality of goods](inspect-quality-goods.md).)

Before a user can process the approval of a nonconformance, a worker must be assigned to them in the **Person** field on the **Users** page. Additionally, before the user can use the document notes, the **Enable document handling** option must be set to *Yes* in their user options.

## Create a nonconformance

To create a nonconformance, follow these steps.

1. Go to **Inventory management \> Periodic tasks \> Quality management \> Non conformances**.
1. On the Action pane, select **New**.
1. In the **Create non conformance** dialog box, in **Problem type** field, select the type of problem that was found during the inspection process.
1. Select **OK**.

## Approve or reject a nonconformance

To approve or reject a nonconformance, follow these steps.

1. Go to **Inventory management \> Periodic tasks \> Quality management \> Non conformances**.
1. In the list, select the nonconformance that you want to update.

    > [!NOTE]
    > You can add a correction only to nonconformances that are approved.

1. On the Action Pane, select **Functions \> Approve non conformance** to approve the nonconformance or **Functions \> Refuse non conformance** to reject it. You can associate approved nonconformances with [related operations](../quality-operations.md). In this way, you can record work that is done as part of the nonconformance handling and the processing of correction handling.
1. You're prompted to confirm your selection. Select **Yes** to continue.

## Add operations and other details to nonconformances

After you've created a nonconformance, you can start to add related operations and specify additional information about those operations. You can add related operations only to nonconformances that are approved.

Besides the basic information, you can add the following details to an operation:

- **Items** – You can create a list of items that are consumed to perform the correction. For example, the items might be products that are required to repair equipment or ingredients that are required to rework a finished product.
- **Quality charges** – You can create a list of charges that are incurred or billed out to external sources.
- **Timesheet** – You can create a log of the time that each worker spends on the operation.

The remaining settings are optional. The cost for each item, quality charges, and the timesheet are summed and shown on the operation. You can't directly edit the **Cost** field on the operation.

### Create an operation for a nonconformance

To create an operation for a nonconformance, follow these steps.

1. Go to **Inventory management \> Periodic tasks \> Quality management \> Non conformances**.
1. In the list, select the nonconformance that you want to update.

    > [!NOTE]
    > You can add or update operations only for nonconformances that are approved.

1. On the Action Pane, select **Related operations**.
1. On the **Related operations** page, on the Action pane, select **New** to add a row to the grid. Then set the following fields for the new row:

    - **Operation** – Select the code of the operation that will be performed for the nonconformance.
    - **Reason** – Enter a detailed description that explains why the operation is required.
    - **Sales order** – If the selected operation code is related to the sales order type, select the sales order that you're linking the operation to.
    - **Purchase order** – If the selected operation code is related to the purchase order type, select the purchase order that you're linking the operation to.

1. Close the pages.

### Add items to an operation

To add items to an operation, follow these steps.

1. Go to **Inventory management \> Periodic tasks \> Quality management \> Non conformances**.
1. In the list, select the nonconformance that you want to update.

    > [!NOTE]
    > You can add or update operations only for nonconformances that are approved.

1. On the Action Pane, select **Related operations**.
1. On the **Related operations** page, select the operation that you want to add items to.
1. On the Action Pane, select **Items**.
1. On the **Related operations** page, on the Action pane, select **New** to add a row to the grid. Then set the following fields for new row:

    - **Item number** – Select the product that will be consumed as part of the selected operation.
    - **Quantity** – Enter the number of items that will be consumed.

    > [!NOTE]
    > You can view the cost for the item in the **Cost** field on the **General** tab. The cost that is shown there comes from the cost that is set up on the **Released product** page. The cost can't be updated directly on the **Related operation item** page. The cost of all items that are added on the **Related operation items** page is automatically added to the **Cost** field on the **Related operations** page.

1. Repeat the previous step for each additional item that you must add.
1. Close the pages.

### Add quality charges to an operation

To add quality charges to an operation, follow these steps.

1. Go to **Inventory management \> Periodic tasks \> Quality management \> Non conformances**.
1. In the list, select the nonconformance that you want to update.

    > [!NOTE]
    > You can add or update operations only for nonconformances that are approved.

1. On the Action Pane, select **Related operations**.
1. On the **Related operations** page, select the operation that you want to add quality charges to.
1. On the Action Pane, select **Quality charges**.
1. On the **Related operation charges** page, on the Action pane, select **New** to add a row to the grid. Then set the following fields for the new row:

    - **Charges code** – Select the quality charge that you want to add.
    - **Description** – Enter a detailed description of the charge.
    - **Charges value** – Enter the amount of the charge.

1. Repeat the previous step for each additional charge that you must add.
1. Close the pages.

> [!NOTE]
> The amount in the **Charges value** field is automatically summed for all quality charges and added to any other amounts in the **Cost** field on the **Related operations** page.

### Create a timesheet on an operation

To add a timesheet to an operation, follow these steps.

1. Go to **Inventory management \> Periodic tasks \> Quality management \> Non conformances**.
1. In the list, select the nonconformance that you want to update.

    > [!NOTE]
    > You can add or update operations only for nonconformances that are approved.

1. On the Action Pane, select **Related operations**.
1. On the **Related operations** page, select the operation that you want to add a timesheet to.
1. On the Action Pane, select **Timesheet**.
1. On the **Related operation time sheets** page, on the Action pane, select **New** to add a row to the grid. Then set the following fields for the new row:

    - **Date** – Specify the date when work was done. By default, this field is set to the current date.
    - **Worker** – Select the worker who did the work. By default, this field is set to the worker that is assigned to the current user.
    - **Operation hours** – Enter the number of hours that were worked on the selected operation.
    - **Invoiced** – Select this check box if the time has been charged to a customer or vendor on an invoice.

    > [!NOTE]
    > You can view the cost in the **Cost** field on the **General** tab. The cost is calculated by using the rate that you define on the **Inventory management parameters** page.

1. Repeat the previous step for each additional timesheet line that you must add.
1. Close the pages.

> [!NOTE]
> The amount in the **Cost** field is summed for all timesheet lines and added to any other amounts in the **Cost** field on the **Related operations** page.

## Add a correction to a nonconformance

To add a correction to a nonconformance, follow these steps.

1. Go to **Inventory management \> Periodic tasks \> Quality management \> Non conformances**.
1. In the list, select the nonconformance that you want to update.

    > [!NOTE]
    > You can add a correction only to nonconformances that are approved.

1. On the Action Pane, select **Corrections**.
1. On the **Corrections** page, on the Action Pane, select **New** to add a row to the grid. Then set the following fields for the new row:

    - **Diagnostic** – Select the diagnostic type that identifies the type of correction that you're creating.
    - **Worker** – Select the person who is responsible for the correction.
    - **Correction priority** – Select an option to indicate how the correction should be prioritized (*Low*, *Normal*, or *High*).
    - **Requested date** – Enter the date when the corrective action was requested.
    - **Planned date** – Enter the date when the correction is expected to be completed.
    - **Short term solution** – Select this check box if the corrective action corrects the nonconformance only for a short time.

1. Close the pages.

## Mark a correction as completed

To mark a nonconformance correction as completed, follow these steps.

1. Go to **Inventory management \> Periodic tasks \> Quality management \> Non conformances**.
1. In the list, select the nonconformance that you want to update.

    > [!NOTE]
    > You can add a correction only to nonconformances that are approved.

1. On the Action Pane, select **Corrections**.
1. On the **Corrections** page, in the grid, select the correction that you want to mark as completed.
1. On the Action Pane, select **Mark complete**.
1. You're prompted to confirm your selection. Select **OK** to continue. The **Completion date and time** field is set to the current date and time, and the **Completed** check box is selected.
1. Close the page.

## Reopen a completed correction

To reopen a completed correction, follow these steps.

1. Go to **Inventory management \> Periodic tasks \> Quality management \> Non conformances**.
1. In the list, select the nonconformance that you want to update.
1. On the Action pane, select **Corrections**.
1. On the **Corrections** page, in the grid, select the correction that you want to reopen.
1. On the Action Pane, select **Reopen**.
1. You're prompted to confirm your selection. Select **OK** to continue. The value is cleared from the **Completion date and time** field, and the **Completed** check box is cleared.
1. Close the page.

You can now make additional edits or updates to the correction. When you've finished, you can mark the correction as completed again.

## Close a nonconformance

To close a nonconformance, follow these steps.

1. Go to **Inventory management \> Periodic tasks \> Quality management \> Quality orders**.
1. Select a quality order in the grid.
1. On the Action Pane, select **Inquiries \> Non conformances**.
1. On the **Non conformances** page, select the target nonconformance in the grid.
1. On the Action Pane, select **Functions \> Close non conformance**.
1. You're prompted to confirm your selection. Select **Yes** to continue.
1. Close the pages.

## Additional resources

- [Quality management overview](../quality-management-processes.md)
- [Enable quality and nonconformance management](../enable-quality-management.md)
- [Workers responsible for approving nonconformances](../quality-responsible-workers.md)
- [Quarantine zones for nonconformances](../quality-quarantine-zones.md)
- [Diagnostic types for nonconformances](../quality-diagnostic-types.md)
- [Quality charges for nonconformances](../quality-charges.md)
- [Operations for nonconformances](../quality-operations.md)
- [Quality management for warehouse processes](../quality-management-for-warehouses-processes.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
