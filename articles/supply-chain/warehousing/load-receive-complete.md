---
title: Load receive complete
description: Learn about the receive complete process for inbound loads for purchase and inbound shipment orders, including a step-by-step process.
author: Atapiabailon
ms.author: atapiabailon
ms.topic: how-to
ms.date: 05/03/2024
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form: WHSLoadTable, WHSLoadPlanningListPage, WHSLoadPlanningWorkbench, WHSRFMenu, WHSRFMenuItem, WHSParameters, WHSInboundLoadPlanningWorkbench, WHSInboundShipmentOrder, WHSInboundLoadPlanningWorkbench, WhsInboundReceivingCompleted
---

# Load receive complete

[!include [banner](../includes/banner.md)]

This article describes the load receive complete options and how the receiving completed periodic task works

## <a name="receive-complete-confirm"></a>Mark a load as receive complete

Background processes, workers, and users can run the *Receiving completed* process to indicate that nothing more needs to be registered against a specific load. Admins can schedule automatic processing by setting up a batch job as described in the following procedure. Web client users can do it by using the **Load** or **Inbound load planning workbench** page. Workers who use the Warehouse Management mobile app can do it by using a menu item that is set up with an **Activity code** value of *Receiving completed confirmation*. In addition to updating the **Load status** and **Load receiving completed date and time** fields for the load, workers, and users might also be able (or required) to enter a packing slip ID and document date during the *Receiving completed* process (depending on how the **Capture receiving completed packing slip** option is set on the **Warehouse management parameters** page).

Follow these steps to choose how loads related to purchase orders are finalized.

1. Go to **Warehouse management \> Setup \> Warehouse management parameters**.
1. Open the **Loads** tab.
1. In the **Capture receiving completed packing slip** field, choose whether a user or worker needs to enter a packing slip ID when confirming that receiving is complete. Select one of the following options:
    - *Never* – The worker or user is never required to enter a packing slip ID when confirming that receiving is complete.
    - *Always* – The worker or user is always required provide a packing slip ID and a document date for each received shipment.
    - *Optional* – The worker or user can choose whether to enter packing slip ID when confirming that receiving is complete. The document date can also be left blank (it automatically defaults to today's date).
1. Set **Load receiving completed confirmation policy for purchase orders** to one of the following values:
    - *Disabled* – Loads won't indicate whether inbound receiving is complete. With this setting, you run the risk that the *Update product receipts* cost update periodic task could run in the middle of an inbound registration process.
    - *Enabled* – After the *Receiving completed* process is run, loads are updated with a **Load receiving completed date and time** value (and related shipments are assigned a **Packing slip ID**). The *Update product receipts* cost update periodic task checks for these values to make sure it only processes loads that are received, which is especially important if you allow over-receiving or under-receiving.
    - *Enabled with auto post* – This option works just like the *Enabled* option, but the **Load status** value is also updated to *Received*, and the **Product receipt processing status** field on the load becomes available for use with the subsequent *Product receipt* posting process. You can't use this setting if you allow multiple product receipts per load.
1. If you set the **Load receiving completed confirmation policy for purchase orders** field to *Enabled* or *Enabled with auto post* and want the *Receiving completed* process to run automatically, setup the **Receiving completed periodic task** described in this article.

## <a name="receiving-completed-periodic-task"></a> Receiving completed periodic task

Use the **Receiving completed**  periodic task to run the receiving completed process of loads for purchase orders automatically.

The **Receiving completed** periodic task is only available if the value of the **Load receiving completed confirmation policy for purchase orders** is set to *Enabled* or *Enabled with auto post*.

The **Receiving completed** periodic task comes with the following options:

|Parameter                 |Description|
|--------------------------|-----------|
|Accept quantity exceptions| Choose whether to accept any differences between the quantities you received and the quantities on the load line: select No to reject the differences and cancel the confirmation process. Select Yes to continue processing.|
|Records to include        | Choose which loads should be included in the periodic task. Customize this value by clicking on the *filter* button and using user-configurable queries. For more information about user-configurable queries, see [User configurable queries in warehouse management](user-configurable-queries-in-warehouse-management.md). |
|Run in the background     | Choose if you want the task to run in the background as a batch process, and set up its recurrence. |

> [!NOTE]
> You can use the **Load status** and **Product receipt processing status** field values as filter criteria for the *Update product receipts* cost update periodic task. In addition, depending on how the **Capture receiving completed packing slip** option is set on the **Warehouse management parameters** page, the purchase order product receipt process might be able to use the recorded packing slip ID as part of the *Update product receipts* periodic task.

To set up the **Receiving completed** periodic task, follow the next steps:

1. Navigate to **Warehouse management \> Periodic tasks  \> Receiving completed**
1. A dialog box is shown in the screen, with different parameters that you can set up according to your business processes.
1. Select whether you want to accept quantity exceptions or no by toggling the check box with title **Accept quantity exceptions**.
1. Select the records to include, you can set up custom conditions by clicking on the **filter** button.
1. Select if the periodic task should run in the background and its recurrence.

## Example user-configurable query for the Receive completed periodic task

### Example: Only include loads with fully completed work

To only include loads with fully completed work, you need to configure the user-configurable query in the following way:
1. Access the user-configurable query by clicking the *filter* button under the *Records to include* section on the **Received completed** dialog box.
1. Select the *Joins* tab.
1. Select the *Loads* join, use the *NotExist* join mode with WHSLoadTable -> WHSWorkTable relation, confirm the selection.
1. Select the *Range* tab.
1. Select the *Add* button, and set the following values: Table as *Work (NotExist)*, Field as *Work status* and as the Criteria select all the statuses that don't denote an open work, for example, Open, In process, Pending review and Combined.
1. Select the *Add* button, and set the following values: Table as *Load*, Field as *Load receiving completed date and time* and as the Criteria select two double quotes, the two double quotes denote an empty value.
1. Select the ok button and run the **Receive completed periodic task**.


> [!IMPORTANT]
>
> Add the *Load receiving completed date and time* in the query range to avoid already received loads to be part of the process every time the **Receive completed** periodic task runs. If you don't add this value to the query range, the process is going to be slower every time.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]