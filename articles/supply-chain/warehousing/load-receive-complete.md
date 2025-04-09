---
title: Mark loads as completely received
description: Learn about the receive complete process for inbound loads for purchase and inbound shipment orders, including a step-by-step process.
author: Atapiabailon
ms.author: atapiabailon
ms.reviewer: kamaybac
ms.search.form: WHSLoadTable, WHSLoadPlanningListPage, WHSLoadPlanningWorkbench, WHSRFMenu, WHSRFMenuItem, WHSParameters, WHSInboundLoadPlanningWorkbench, WHSInboundShipmentOrder, WHSInboundLoadPlanningWorkbench, WhsInboundReceivingCompleted
ms.topic: how-to
ms.date: 04/09/2025
ms.custom: 
  - bap-template
---

# Mark loads as completely received

[!include [banner](../includes/banner.md)]

This article describes the options for marking loads as receive complete and how the *Receiving completed* periodic task works.

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
1. If you set the **Load receiving completed confirmation policy for purchase orders** field to *Enabled* or *Enabled with auto post* and want the *Receiving completed* process to run automatically, set up the *Receiving completed* periodic task described in this article.

> [!NOTE]
> When you set up the *Update product receipts* cost update periodic task, you can use the **Load status** and **Product receipt processing status** field values as filter criteria. In addition, depending on how the **Capture receiving completed packing slip** option is set on the **Warehouse management parameters** page, the purchase order product receipt process might be able to use the recorded packing slip ID as part of the *Update product receipts* periodic task.

## <a name="receiving-completed-periodic-task"></a>Automatically run the receiving completed process

The *Receiving completed* periodic task runs the receiving completed process of loads for purchase orders automatically. To set up the task to run automatically, follow these steps.

1. On the Warehouse management parameters page, set the **Load receiving completed confirmation policy for purchase orders** field to *Enabled* or *Enabled with auto post*. The *Receiving completed* periodic task is only available if this field is set to one of these values. Learn more in [Mark a load as receive complete](#receive-complete-confirm).
1. Go to **Warehouse management** \> **Periodic tasks** \> **Receiving completed**. The **Receiving completed** dialog opens.
1. On the **Parameters** FastTab, use the **Accept quantity exceptions** setting to choose whether to accept any differences between the quantities you received and the quantities on the load line. Select *No* to reject the differences and cancel the confirmation process. Select *Yes* to continue processing.
1. On the **Records to include** FastTab, set up filters and constraints to define which loads to process. Select **Filter** to open a standard query editor dialog, where you can define selection criteria, sorting criteria, and joins. The fields work just as they do for other types of queries in Supply Chain Management.
1. On the **Run in the background** FastTab, specify how, when, and how often to run the task. The fields work just as they do for other types of [background jobs](../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md) in Supply Chain Management.
1. Select **OK**.

## Example: Only include loads with fully completed work

To set up the *Receiving completed* periodic task to only include loads with fully completed work, configure the task as follows:

1. Go to **Warehouse management** \> **Periodic tasks** \> **Receiving completed**.
1. Expand the **Records to include** FastTab.
1. Select the **Filter** button to open the query editor dialog.
1. Open the **Joins** tab.
1. Select the *Loads* join in the list.
1. In the toolbar, select **Add table join**.
1. Set **Show details** to *Yes*.
1. Select the row with **Join mode** *NotExist* and **Table relation description** *WHSLoadTable -> WHSWorkTable*.
1. In the toolbar, select **Select**.
1. Open the **Range** tab.
1. In the toolbar, select **Add** to add a new line and make the following settings for the new line.
    - **Table** – Select *Work (NotExist)*.
    - **Field** – Select *Work status*.
    - **Criteria** – Select all the statuses that don't denote an open work record (for example, *Open*, *In process*, *Pending review*, and *Combined*). <!-- KFM: Those look like statuses that DO denote an open work record. I might misunderstand something here. Please confirm this list, thanks. -->
1. In the toolbar, select **Add** to add a new line and make the following settings for the new line.
    - **Table** – Select *Load*.
    - **Field** – Select *Load receiving completed date and time*.
    - **Criteria** – Enter two double quotes to denote an empty value.

    > [!TIP]
    > Because the query only finds records that have an empty value in the *Load receiving completed date and time* field, the task won't consider already received loads. If you don't include this setting, the task will get slower each time it runs.

1. Select **OK**.
1. Set other options for the task as described in the previous section.
1. Select **OK** to save and run the task.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
