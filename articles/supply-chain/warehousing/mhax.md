---
# required metadata

title: Material handling equipment interface (MHAX)
description: This topic describes how to set up the material handling equipment interface, which lets you connect to external physical material handling systems
author: Mirzaab
manager: tfehr
ms.date: 03/04/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: mirzaab
ms.search.validFrom: 2021-03-04
ms.dyn365.ops.version: Release 10.0.17
---

# Material handling equipment interface (MHAX)

[!include [banner](../includes/banner.md)]

Use the *material handling equipment interface* (MHAX) to connect external physical material handling (MH) systems to a warehouse managed by advanced warehouse management (WMS) in Supply Chain Management. The interface between the WMS and MH systems consists of two queues – one for outbound (WMS to MH) and another one for inbound (MH to WMS) events. The WMS system creates outbound events based on work lines created during various work creation and execution processes. MH then regularly polls WMS for new events and processes the responses. After MH completes handling in accordance with work instructions, it sends inbound events, such as work line completion and short picking.

The following illustration shows the various elements and the order in which various processes occur when you use MHAX integration.

![AltText](media/mhax-components.png "AltText")

The following interactions are indicated in the illustration:

1. During work creation or work execution, outbound events are created in the outbound queue.
2. The Material handling equipment connects to the Material handling equipment service and polls for any new events that are relevant for it and processes the them.
3. When ready to report back, the Material handling equipment connects to the service again and submits inbound events, which are immediately processed by the queue processor.
4. Based on the inbound event data, the queue processor may execute existing work, modify it or create new work.

## Turn on the MHAX feature

Before you can use this feature, it must turn on both its feature and its configuration key.

1. Go to **System administration \> Workspaces \> Feature management**.
2. Turn on the feature named *Material handling equipment interface* in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
3. Put your system into maintenance mode, as described in [Maintenance mode](../../fin-ops-core/dev-itpro/sysadmin/maintenance-mode.md).
4. Go to **System administration \> Setup \> License configuration**.
5. Expand the **Trade \> Warehouse and Transportation management** node and then select the **Material handling equipment interface** check box.
6. Turn off maintenance mode, as described in [Maintenance mode](../../fin-ops-core/dev-itpro/sysadmin/maintenance-mode.md).

## Material handling equipment interface parameters

Use the **Material handling equipment interface parameters** page to make a few general settings for how the feature works. To open the page, go to **Material handling equipment interface \> Setup \> Material handling equipment interface parameters** and then make the following settings:

- On the **General** tab, make the following settings:
  - **User ID** - All work operations (picks and puts) processed through the inbound queue are executed using the worker selected here.
  - **Enable inbound message ID** - When set to *Yes*, if a duplicate inbound message ID is received, the message will be rejected with an error that the message already exists. When set to *No*, duplicate inbound message IDs will be allowed.
- On the **Number sequences** tab, choose the system-wide number sequences to use when generating unique IDs for the inbound queue items, outbound queue items, and work line pairs, respectively.

## Outbound events

At specific points during work creation or work execution, the system will check whether it needs to generate outbound events to send to the material handling system. If a subscription is configured for that specific point in warehouse processing, the system will generate the event according to the setup on the subscription.

### Structure of the outbound event

Each outbound event is uniquely identified by an outbound queue ID. The outbound transaction type determines the type of the event and, in addition, the warehouse and the ID of the subscription that generated the event are also recorded on the event.

To carry data to the material handling system, the outbound event contains 10 fields for data (named data01 to data10) which are extracted from fields in the work line and work header tables. The fields can be freely chosen and you will set them up when creating the subscription.

In addition to the 10 fields that have a 1:1 mapping to existing database fields, the event can also carry an additional data field (called the payload), the contents of which are generated by custom X++ code (called a payload generator). The payload generator to be used (if any) is also set up in the subscription.

To ensure that the material handling system only receives each ID once, a status field is used to specify whether an event is ready to be sent to the external system or whether it has already been sent.

### Outbound queue subscriptions

Before any events are generated, a subscription must be set up that tells the MHAX feature whether and how to generate events. Generated events are tagged by the subscription identifier, which allows multiple MH systems to connect to the same WMS while keeping their events separate. When polling the MHAX service for new events, using a subscription is one of the options available to retrieve new events.

To create a subscription, go to **Material handling equipment interface \> Setup \> Subscriptions**. Each subscription is set up with the following parameters:

- **Subscription ID** - A unique name to identify the subscription.
- **Description** - A free text description of the subscription.
- **Warehouse** - Filters events by specific warehouses.
- **Outbound transaction type** - Identifies the events this subscription should contain.
- **Payload generator** - An optional code extension that can fill additional information in the **Payload** field on the outbound event.

In addition to this, each subscription can have a query associated with it that filters work lines and headers to further restrict which work will generate events using this subscription. To add a query to a subscription, select the **Run query** check box for the relevant subscription on the **Subscriptions** page and then select **Edit query** from the Action Pane. This opens the standard Supply Chain Management query editor.

The subscription also includes a *subscription map*, which maps fields from either the work header or work line to some or all of the 10 free data fields on the outbound event, as needed. To return information back to the MHAX service, you would typically include the work line record ID or the work line pair ID (which is a new field that allows the system to process pick and put lines using a single return command). The rest of the fields are use-case dependent; some examples are provided later in this topic.

To set up a subscription map, select the relevant subscription on the **Subscriptions** page and then select **Subscription map** on the Action Pane. The Subscription map dialog box opens, where you can assign a table and field for each available data field as needed.

### Outbound event types

This section describes the various types of events types (also known as *transaction types*) available and when they are created in WMS.

#### Work creation events

Work creation events are created after work is generated by the application. This applies to most types of work creation processes, most notably picking and replenishment work. Generally, if work is created in an *Open* state (ready to be executed by a worker), a work creation event will be generated. In addition, work creation events will also be generated for basic movement work (not movement by template work), even though this work would not be created as open work.

A notable exception is cycle counting work, which is currently not supported. Performing the count of the stock in the material handling system would be outside of the scope of the MHAX interface and the results of counts would need to be imported into an inventory counting journal.

After the work has been created, the MHAX service processes the generated work lines and assigns a *work line pair ID* to all generated work lines for each work header. The objective is to group all the pick work lines with the successive puts (corresponding to pick/put pairs in work templates) under one work line pair ID, to enable easier reporting of work completion for all related pick and put lines using a single ID. It starts with the first line and then proceeds with the same ID until it encounters a successive pair of put/pick work lines. The put line of the pair is assigned the running ID and from the pick line onwards, a new ID is used. The process continues until it has processed all lines belonging to the work header.

As a special feature of work creation events, the events will be generated in status *Blocked* (as opposed to the usual status of *Ready* for sending to the material handling system) if the work header has the field **Blocked wave** set to *Yes* (meaning that it is not yet ready for workers to execute, perhaps due to unfinished replenishment work). When the **Blocked wave** flag is cleared, the already generated events are unblocked and available for the MH system to retrieve from the queue.

#### Work initiation events

Work initiation events are triggered on work update when the work status changes from *Open* to *In process*.

#### Work completion events

Work completion events are triggered on work update when the work status changes from *In process* to *Closed*.

#### Work cancellation events

Work cancellation events are triggered on work update when the work status changes to *Cancelled* from any status other than *Cancelled*. In addition to this event being created, cancelling work will also delete all other events related to this work header from the queue for all subscriptions. This will prevent external systems from processing unneeded events.

#### Pick/put completion events

Pick/put completion events are triggered on work line update when the status of the pick/put line changes from *In process* to *Closed*.

### Monitor the outbound queue

To review your outbound queue, go to **Material handling equipment interface \> Common \> Outbound queue**. This page provides a list of each outbound queue item and its status. Select a queue item to see its details, which include its transaction type, the subscription it used, and values for each data field (Data 1 - Data 10) and the payload.

### Clean up the outbound queue

After some time, your outbound queue will begin to fill full of sent queue items. If you'd like to remove these, then go to **Material handling equipment interface \> Periodic tasks \> Cleanup \> Outbound queue cleanup**.

## Inbound events

This section describes the kinds of inbound events the MH system can report back to WMS, what data needs to be supplied by the MH system, and what each inbound event does in WMS.

### Structure of the inbound event

When submitting an inbound event, the external system must supply the inbound transaction type along with up to 10 parameters (called data01 to data10). Optionally, it is possible to validate that the MHAX service has not received the same inbound event twice. In order to check for duplicates, each inbound event must have a unique message ID. If a duplicate message ID is received (and **Enable inbound message ID** is set to *Yes* on the **Material handling equipment interface parameters** page), the message will be rejected with an error that the message already exists.

In addition to the incoming fields, the system also assigns a unique inbound queue ID to the event.

### Inbound event types

This section describes the supported inbound event types, also known as *transaction types*, and the data that must be supplied for the event to be processed.

#### Work confirm events

Work confirm events require the following to be included in the incoming data fields:

- **data01** - The work line pair ID (*either* this or data02 must be present)
- **data02** - The work line record ID (RecId) (*either* this or data01 must be present)
- **data03** - The license plate ID to pick from
- **data04** - The work header's target license plate ID

If a work line record ID (RecId) is provided, it must be a pick, put, or custom work line with status *Open* or *In process*.

If the work line pair ID is provided, all pick, put, or custom work lines in status *Open* or *In process* marked by the work line pair ID are executed sequentially.

Pick lines (specified either by work line record ID or work line pair ID) from license-plate-controlled locations require that the license plate to be picked from be specified in **data03**. The work header's target license plate for the pick must be specified in **data04**.

Put lines do not accept further information and are executed only based on the current work line's location and the work's target license plate. If the put must be executed to a different location, change the location of the work line as described in [Override events](#override-events), later in this topic.

Custom work lines do not require, and do not support, any additional information in the inbound event.

#### Short pick events

Short pick events require the following to be included in the incoming data fields:

- **data01** - (Not used)
- **data02** - The work record ID (`RecId`)
- **data03** - The license plate ID to pick from
- **data04** - The quantity to pick
- **data05** - The short pick exception code
- **data06** - The work header's target license plate ID

This event is similar to the work confirmation event, but only applies to pick lines.

<a name="override-events"></a>

#### Override events

Override events require the following to be included in the incoming data fields:

- **data01** - The work record ID (`RecId`)
- **data02** - The new location ID

The work line status must be either *Open* or *In process* and the new location must exist.

#### License plate receipt events

License plate receipt events require the following to be included in the incoming data fields:

- **data01** - The inbound license plate ID to receive

The system performs a license plate receiving operation based on the license plate passed in as **data01**.

### Monitor the inbound queue

To review your inbound queue, go to **Material handling equipment interface \> Common \> Inbound queue**. This page provides a list of each inbound queue item and its status. Select a queue item to see its details, which include its transaction type, message ID, and values for each data field (Data 1 - Data 10).

If an error, or other type of log item, occurred while processing inbound events, you can inspect the log by selecting **Error log** from the Action Pane.

### Inbound event processing

Inbound events are first written to the database and then immediately (synchronously) executed. Should an error occur during processing, the event will still be written to the queue, but the status will be set to *Errored*. The MHAX service will return the error message to the MH system and store the error log in the inbound event record for later investigation.

Errored events can be reprocessed later if the error condition is resolved. You can reprocess them by doing one of the following:

- Go to **Material handling equipment interface \> Common \> Inbound queue**. Then select the relevant inbound queue and select **Reprocess** on the Action Pane.
- Go to **Material handling equipment interface \> Common \> Reprocess errored inbound queue**. This opens a standard batch job dialog box opens where you can set up a record filter and schedule or run a batch job to reprocess the queue.

All work operations (picks and puts) are executed using the worker selected as the **User ID** on the **Material handling equipment interface** parameters page.

### Clean up the inbound queue

After some time, your inbound queue will begin to fill full of processed queue items. If you'd like to remove these, then go to **Material handling equipment interface \> Periodic tasks \> Cleanup \> Inbound queue cleanup**.

## Get a quick overview with the queue manager

To get a quick overview of everything that is happening with your inbound and outbound queues, go to **Material handling equipment interface \> Workspaces \> Queue manager**. This page provides set of tabs and tiles for monitoring and exploring your queues, plus handy links to most of the other pages described in this topic.

## Connect to the MHAX service

The MHAX interface is implemented as a custom service and is therefore accessible via SOAP and REST calls. The addresses for the SOAP and REST endpoint are:

- **SOAP**: [https://base\_environment\_URL/soap/services/WMHEServices](https://base\_environment\_URL/soap/services/WMHEServices)
- **REST**: [https://base\_environment\_URL/api/services/WMHEServices/WMHEService](https://base_environment_URL/api/services/WMHEServices/WMHEService)

## Retrieve messages from the outbound queue

To retrieve messages from the outbound queue, use one of the following methods:

- Use `readOutboundSubscriptionQueue` to retrieve the events based on the subscription ID.
- Use `readOutboundWarehouseQueue` to retrieve the events based on event type and warehouse ID across multiple subscriptions.
