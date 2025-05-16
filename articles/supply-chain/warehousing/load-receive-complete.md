---
title: Mark loads as completely received
description: Learn about the Receiving completed process for inbound loads for purchase and inbound shipment orders, including the step-by-step process.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ms.search.form: WHSLoadTable, WHSLoadPlanningListPage, WHSLoadPlanningWorkbench, WHSRFMenu, WHSRFMenuItem, WHSParameters, WHSInboundLoadPlanningWorkbench, WHSInboundShipmentOrder, WHSInboundLoadPlanningWorkbench, WhsInboundReceivingCompleted
ms.topic: how-to
ms.date: 04/25/2025
ms.custom: 
  - bap-template
---

# Mark loads as completely received

[!include [banner](../includes/banner.md)]

This article describes the options for marking loads as completely received. It also explains how the *Receiving completed* periodic task works.

## <a name="receive-complete-confirm"></a>Mark a load as completely received

Background processes, workers, and users can run the *Receiving completed* process to indicate that nothing more has to be registered against a specific load. Admins can schedule automatic processing by setting up a batch job as described in the following procedure. Web client users can run the process by using the **Load** or **Inbound load planning workbench** page. Workers who use the Warehouse Management mobile app can run it by using a menu item that is set up with an **Activity code** value of *Receiving completed confirmation*.

During the *Receiving completed* process, workers and users update the **Load status** and **Load receiving completed date and time** fields for the load. In addition, depending on the setting of the **Capture receiving completed packing slip** field on the **Warehouse management parameters** page, they might be able (or required) to enter a packing slip ID and a document date.

Follow these steps to specify how loads that are related to purchase orders are finalized.

1. Go to **Warehouse management** \> **Setup** \> **Warehouse management parameters**.
1. On the **Loads** tab, in the **Capture receiving completed packing slip** field, select one of the following options to specify whether users or workers must enter a packing slip ID when they confirm that receiving is completed:

    - *Never* – Workers or users are never required to enter a packing slip ID when they confirm that receiving is completed.
    - *Always* – Worker or users are always required to enter a packing slip ID and a document date for every received shipment.
    - *Optional* – Worker or users can choose whether to enter a packing slip ID when they confirm that receiving is completed. They can also leave the document date blank. (It's automatically set to the current date by default).

1. In the **Load receiving completed confirmation policy for purchase orders** field, select one of the following options:

    - *Disabled* – Loads don't indicate whether inbound receiving is completed. If you select this option, there is a risk that the *Update product receipts* cost update periodic task might run in the middle of an inbound registration process.
    - *Enabled* – After the *Receiving completed* process is run, loads are updated with a **Load receiving completed date and time** value, and a **Packing slip ID** value is assigned to related shipments. The *Update product receipts* cost update periodic task checks for these values to ensure that it processes only loads that were received. This check is especially important if you allow over-receiving or under-receiving.
    - *Enabled with auto post* – This option works just like the *Enabled* option, but the **Load status** value is also updated to *Received*, and the **Product receipt processing status** field on the load becomes available for use with the subsequent *Product receipt* posting process. You can't select this option if you allow multiple product receipts per load.

1. If you set the **Load receiving completed confirmation policy for purchase orders** field to *Enabled* or *Enabled with auto post*, and you want the *Receiving completed* process to run automatically, set up the *Receiving completed* periodic task as described in the next section.

> [!NOTE]
> When you set up the *Update product receipts* cost update periodic task, you can use the **Load status** and **Product receipt processing status** field values as filter criteria. In addition, depending on the setting of the **Capture receiving completed packing slip** option on the **Warehouse management parameters** page, the purchase order product receipt process might be able to use the recorded packing slip ID as part of the *Update product receipts* periodic task.

## <a name="receiving-completed-periodic-task"></a>Automatically run the Receiving completed process

The *Receiving completed* periodic task automatically runs the *Receiving completed* process for loads for purchase orders. To set up the task so that it runs automatically, follow these steps.

1. On the **Warehouse management parameters** page, on the **Loads** tab, set the **Load receiving completed confirmation policy for purchase orders** field to *Enabled* or *Enabled with auto post*. The *Receiving completed* periodic task is available only if the field is set to one of these values. Learn more in the [Mark a load as completely received](#receive-complete-confirm) section.
1. Go to **Warehouse management** \> **Periodic tasks** \> **Receiving completed**.
1. In the **Receiving completed** dialog, on the **Parameters** FastTab, set the **Accept quantity exceptions** option to specify whether differences between the received quantities and the quantities on the load line should be accepted. Set the option to *No* to reject the differences and cancel the confirmation process. Set it to *Yes* to accept the differences and continue the processing.
1. On the **Records to include** FastTab, set up filters and constraints to define which loads to process. Select **Filter** to open a standard query editor dialog, where you can define selection criteria, sorting criteria, and joins. The fields work just as they do for other types of queries in Microsoft Dynamics 365 Supply Chain Management.
1. On the **Run in the background** FastTab, specify how, when, and how often to run the task. The fields work just as they do for other types of [background jobs](../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md) in Supply Chain Management.
1. Select **OK**.

## Example: Include only loads with fully completed work

To set up the *Receiving completed* periodic task so that it includes only loads where work was fully completed, follow these steps.

1. Go to **Warehouse management** \> **Periodic tasks** \> **Receiving completed**.
1. On the **Records to include** FastTab, select **Filter**.
1. In the query editor dialog, on the **Joins** tab, select the **Loads** join in the list.
1. On the toolbar, select **Add table join**.
1. Set the **Show details** option to *Yes*.
1. Select the row where the **Join mode** field is set to *NotExist* and the **Table relation description** field is set to *WHSLoadTable -\> WHSWorkTable*.
1. On the toolbar, select **Select**.
1. On the **Range** tab, on the toolbar, select **Add** to add a line.
1. Set the following values for the new line:

    - **Table** – Select *Work (NotExist)*.
    - **Field** – Select *Work status*.
    - **Criteria** – Select all the statuses that denote an open work record. For example, you might select *Open*, *In process*, *Pending review*, and *Combined*.

1. On the toolbar, select **Add** to add another line.
1. Set the following values for the new line:

    - **Table** – Select *Load*.
    - **Field** – Select *Load receiving completed date and time*.
    - **Criteria** – Enter two double quotation marks ("") to denote an empty value.

    > [!TIP]
    > Because of the **Criteria** setting on this line, the query finds only records that have an empty value in the **Load receiving completed date and time** field. As a result, the task doesn't consider loads that were already received. If you omit this setting, the task becomes slower each time that it runs.

1. Select **OK**.
1. Set other options for the task as described in the previous section.
1. Select **OK** to save and run the task.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
