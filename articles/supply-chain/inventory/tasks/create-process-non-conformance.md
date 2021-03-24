---
# required metadata

title: Create and process nonconformances
description: This topic shows how to perform nonconformance management based on an existing quality order.
author: perlynne
manager: tfehr
ms.date: 03/23/2021
ms.topic: business-process
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
ms.author: perlynne
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: AX 7.0.0
---
# Create and process nonconformances

[!include [banner](../../includes/banner.md)]

This topic shows how to perform nonconformance management based on an existing quality order. Typically, this procedure is performed by a quality clerk.  As a prerequisite, you must have a quality order available (for details about how to create a quality order, see [Inspect the quality of goods](inspect-quality-goods.md)).

To process the approval of a nonconformance, the user doing the task must have a **Person** assigned on their **Users** page. To use the document notes, the user must also have **Enable document handling** turned on in their **User options**.

## Create a nonconformance

To create a nonconformance:

1. Go to **Inventory management >  Periodic tasks > Quality management > Non conformances**.
1. On the Action pane, select **New** to open the **Create non conformance** dialog box.
1. In **Problem type** drop-down list, select the type of problem found during the inspection process.  
1. Select **OK**.

## Approve or reject a nonconformance

To approve or reject a nonconformance:

1. Go to **Inventory management >  Periodic tasks > Quality management > Non conformances**.
1. Select the nonconformance from the list that you want to update.
    > [!Note]
    > You can only add a correction to a nonconformance that is approved.
1. On the Action Pane, select **Functions > Approve non conformance** to approve the non conformance or **Functions > Refuse non conformance** to reject it. You can associate approved nonconformances with [related operations](../quality-operations.md) to record work that is done as part of the nonconformance handling and the processing of correction handling.  
1. You are asked to confirm your selection. Select **Yes** to continue.

## Add operations and other details for nonconformances

Once you have created a nonconformance, you can start to add related operations and specifying additional information abut the operations. You can only add related operations to a nonconformance that is approved.

In addition to the basic information, you can also add the following details to an operation:

- **Items**: You can create a list of items that are consumed to perform the correction. This might be, for example, products required to repair equipment, or ingredients required to rework a finished product.
- **Quality charges**: You can create a list of charges that are incurred or billed out to external sources.
- **Timesheet**: You can create a log of the time spent on the operation by each worker.

The remaining settings are optional. The cost for each of the items, quality charges, and the timesheet are summed and displayed on the operation. You can't directly edit the **Cost** field on the operation.

### Create an operation on a nonconformance

To create an operation on a nonconformance:

1. Go to **Inventory management >  Periodic tasks > Quality management > Non conformances**.
1. Select the nonconformance from the list that you want to update.
    > [!Note]
    > You can only add or update operations on a nonconformance that is approved.
1. Select **Related operations** in the Action Pane. The **Related operations** page opens.
1. On the Action pane, select **New** to add a new row to the grid, and then make the following settings for it:
    - **Operation** - Select the operation code that will be performed for the nonconformance.
    - **Reason** - Enter a detailed description about why the operation is required.
    - **Sales order** - If the operation code selected is related to the sales order type, then select the sales order you are linking the operation to.
    - **Purchase order** - If the operation code selected is related to the purchase order type, then select the purchase order you are linking the operation to.
1. Close the pages.

### Add items to an operation

To add items to an operation:

1. Go to **Inventory management >  Periodic tasks > Quality management > Non conformances**.
1. Select the nonconformance from the list that you want to update.
    > [!Note]
    > You can only add or update operations on a nonconformance that is approved.
1. Select **Related operations** in the Action Pane. The **Related operations** page opens.
1. Select the operation that you want to add items to.
1. Select **Items** in the Action Pane. The **Related operations** page opens.
1. On the Action pane, select **New** to add a new row to the grid, and then make the following settings for it:
    - **Item number** - Select the product that will be consumed as part of the selected operation.
    - **Quantity** - Enter the number of items that are being consumed.
    > [!Note]
    > You can view the cost for the item in the **Cost** field on the **General** tab. The cost displayed comes from the cost that is setup on the **Released product** and cannot be updated directly on the **Related operation item**. The cost of all items added in the **Related operation items** page is automatically added to the **Cost** field on the **Related operations** page.
1. Repeat the previous step for each item you need to add.
1. Close the pages.

### Add quality charges to an operation

To add quality charges to an operation:

1. Go to **Inventory management >  Periodic tasks > Quality management > Non conformances**.
1. Select the nonconformance from the list that you want to update.
    > [!Note]
    > You can only add or update operations on a nonconformance that is approved.
1. Select **Related operations** in the Action Pane. The **Related operations** page opens.
1. Select the operation that you want to add quality charges to.
1. Select **Quality charges** in the Action Pane. The **Related operation charges** page opens.
1. On the Action pane, select **New** to add a new row to the grid, and then make the following settings for it:
    - **Charges code** - Select the quality charge you want to add.
    - **Description** - Enter a detailed description for the charge.
    - **Charges value** - Enter the amount for the charge.
1. Repeat the previous step for each change you need to add.
1. Close the pages.

> [!Note]
> The amount in the **Charges value** field is automatically summed for all quality charges and added to any other amounts in the **Cost** field on the **Related operations** page.

### Create a timesheet on an operation

To add a timesheet to an operation:

1. Go to **Inventory management >  Periodic tasks > Quality management > Non conformances**.
1. Select the nonconformance from the list that you want to update.
    > [!Note]
    > You can only add or update operations on a nonconformance that is approved.
1. Select **Related operations** in the Action Pane. The **Related operations** page opens.
1. Select the operation that you want to add a timesheet to.
1. Select **Timesheet** in the Action Pane. The **Related operation time sheets** page opens.
1. On the Action pane, select **New** to add a new row to the grid, and then make the following settings for it:
    - **Date** - Specify the date work was performed. By default, this field will populate with today's date.
    - **Worker** - Select the worker who performed the work. The **Worker** field will default to the worker that is assigned to the current user.
    - **Operation hours** - Enter the number of hours worked on the selected operation.
    - **Invoiced** - Select this check box if the time has been charged to a customer or vendor on an invoice.
    > [!Note]
    > Open the **General** tab to view the **Cost**. The cost is calculated by using the rate that you define on the **Inventory management parameters** page.
1. Repeat the previous step for each timesheet line you need to add.
1. Close the pages.

> [!Note]
> The **Cost** field is summed for all timesheet lines and added to any other amounts in the **Cost** field on the **Related operations** page.

## Add a correction to a nonconformance

To add a correction to a nonconformance:

1. Go to **Inventory management >  Periodic tasks > Quality management > Non conformances**.
1. Select the nonconformance from the list that you want to update.
    > [!Note]
    > You can only add a correction to a nonconformance that is approved.
1. Select **Corrections** in the Action Pane.
1. On the Action pane, select **New** to add a new row to the grid, and then make the following settings for it:
    - **Diagnostic** - Select the diagnostic type that identifies the type of correction you are creating.
    - **Worker** - Select the person who is responsible for the correction.
    - **Correction priority** - Select an option to indicate how the correction should be prioritized (*Low*, *Normal*, or *High*).
    - **Requested date** - Enter the date the corrective action was requested.
    - **Planned date** - Enter the date the correction is expected to be completed.
    - **Short term solution** - Select this check box if the corrective action only corrects the nonconformance for a short period of time.
1. Close the pages.

## Mark a correction complete

To mark a nonconformance correction as complete:

1. Go to **Inventory management >  Periodic tasks > Quality management > Non conformances**.
1. Select the nonconformance from the list that you want to update.
    > [!Note]
    > You can only add a correction to a nonconformance that is approved.
1. On the Action pane, select **Corrections**. The **Corrections** page opens.
1. Select the correction from the grid you want to mark as complete.
1. On the Action Pane, select **Mark complete**.
1. You are asked to confirm your selection. Select **OK** to continue. This will populate the **Completion date and time** field with the current date and time. Additionally, the **Completed** check box will be selected.
1. Close the page.

## Reopen a completed correction

To reopen a completed correction:

1. Go to **Inventory management >  Periodic tasks > Quality management > Non conformances**.
1. Select the nonconformance from the list that you want to update.
1. On the Action pane, select **Corrections**. The **Corrections** page opens.
1. Select the correction from the grid you want to reopen.
1. On the Action Pane, select **Reopen**.
1. You are asked to confirm your selection. Select **OK** to continue. This clears the value in the **Completion data and time** field, and clears the **Completed** check box.
1. Close the page.

Now you can make additional edits or updates to the correction, and then mark the correction as complete again when you are finished making changes.

## Close a nonconformance

To close a nonconformance:

1. Go to **Inventory management > Periodic tasks > Quality management > Quality orders**.
1. Select a quality order on the grid.
1. On the Action Pane, select **Inquiries > Non conformances**. The **Non conformances** page opens.
1. Select the target nonconformance on the grid.
1. On the Action Pane, select **Functions > Close non conformance**.
1. You are asked to confirm your selection. Select **Yes** to continue.
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