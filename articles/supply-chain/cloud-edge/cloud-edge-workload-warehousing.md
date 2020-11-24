---
# required metadata

title: Warehouse management workloads for cloud and edge scale units
description: This topic provides information about the feature that enables scale units to run selected processes from your warehouse management workload.
author: perlynne
manager: tfeyr
ms.date: 10/06/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: PurchTable, SysSecRolesEditUsers
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid:
ms.search.region: global
ms.search.industry: SCM
ms.author: perlynne
ms.search.validFrom: 2020-10-06
ms.dyn365.ops.version: 10.0.15
---

# Warehouse management workloads for cloud and edge scale units

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

> [!WARNING]
> Not all warehouse management business functionality is fully supported for a warehouse running in a work load on a scale unit. Be sure to use only the processes that this topic explicitly describes as supported.

## Warehouse execution on scale units

This feature enables scale units to run selected processes from the warehouse management capabilities. Cloud scale units run their workloads in the cloud by using dedicated processing capacity in your selected Microsoft Azure region. For edge scale units, you can run some workloads independently on premises, even while the scale units are temporarily disconnected from the cloud.

In this topic, warehouse management executions in a warehouse that is defined as a scale unit are known as a *Warehouse execution system* (*WES*).

## Prerequisites

You must have a Dynamics 365 Supply Chain Management hub and a scale unit that has been deployed with the warehouse management workload. For more information about the architecture and deployment process, see [Cloud and edge scale units for manufacturing and warehouse management workloads](cloud-edge-landing-page.md).

## How the WES workload works on scale units

For the processes in the warehouse management workload, the data is synced between the hub and the scale units.

A scale unit can maintain only the data that it owns. The data ownership concept for scale units helps prevent multi-master conflicts. Therefore, it's important that you understand which processes are owned by the hub and which are owned by the scale units.

The scale units own the following data:

- **Wave processing data** – Selected wave process methods are handled as part of the scale unit wave processing.
- **Work processing data** – The following types of work order processing are supported:

    - Inventory movements (manual movement and movement by template work)
    - Purchase orders (putaway work via a warehouse order)
    - Sales orders (simple picking and loading work)
    - Transfer orders (only outbound with simple picking and loading work)

- **Warehouse order receipt data** – This data is used only for purchase orders that are manually released to a warehouse.
- **License plate data** – License plates can be created on the hub and the scale unit. Dedicated conflict handling has been provided. Note that this data isn't warehouse-specific.

## Outbound process flow

The hub owns the following data:

- All source documents, such as sales orders and transfer orders
- Order allocation and outbound load processing
- The release to warehouse, shipment creation, wave creation, and wave finalization processes.

The scale units own the actual wave processing (such as work allocation, replenishment work, and demand work creation) after the release of the wave. Therefore, warehouse workers can process outbound work by using a warehouse app that is connected to the scale unit.

![Wave processing flow](./media/wes-wave-processing-ga.png "Wave processing flow")

## Inbound process flow

The hub owns the following data:

- All source documents, such as purchase orders and sales return orders
- Inbound load processing

> [!NOTE]
> The inbound purchase order flow is conceptually different from the outbound flow, where the scale unit that does the processing depends on whether the order has been released to a warehouse.

If you're using the *release to warehouse* process, [**Warehouse orders**](cloud-edge-warehouse-order.md) are created, and ownership of the related receiving flow is assigned to the scale unit. The hub won't be able to register inbound receiving.

The worker can run the receiving process by using a warehouse app that is connected to the scale unit. The data is then recorded by the scale unit and reported against the inbound warehouse order. The creation and processing of the subsequent putaway will also be handled by the scale unit.

If you aren't using the *release to warehouse* process, and therefore aren't using *warehouse orders*, the hub can process warehouse receiving and work processing independently from scale units.

![Inbound process flow](./media/wes-inbound-ga.png "Inbound process flow")

## Supported processes and roles

Not all warehouse management processes are supported in a WES workload on a scale unit. Therefore, we recommend that you assign roles that match the functionality that is available to each user.

To facilitate this process, a sample role that is named *Warehouse manager on workload* is included in the demo data at **System administration \> Security \> Security configuration**. The purpose of this role is to enable warehouse managers to access the WES on the scale unit. The role grants access to the pages that are relevant in the context of a workload that is hosted on a scale unit.

User roles on a scale unit are assigned as part of the initial data synchronization from the hub to the scale unit.

To modify the roles that are assigned to a user, go to **System administration \> Security \> Assign users to roles**. Users who act as warehouse managers only on scale units should be assigned only the *Warehouse manager on workload* role. This approach will ensure that those users have access only to the supported functionality. Remove any other roles that are assigned to those users.

Users who act as warehouse managers on both the hub and scale units should be assigned the existing *Warehouse worker* role. Be aware that this role grants warehouse workers access to features (such as transfer order receiving processing) that appear in the user interface (UI) but aren't currently supported on scale units.

## Supported WES processes

The following warehouse execution processes can be enabled for a WES workload on a scale unit:

- Selected wave methods for sales and transfer orders (allocation, demand replenishment, containerization, work creation, and wave label printing)
- Processing sales and transfer order warehouse work by using the warehouse app (including replenishment work)
- Querying on-hand inventory by using the warehouse app
- Creating and running inventory movements by using the warehouse app
- Registering purchase orders and doing putaway work by using the warehouse app

The following work order types are currently supported for WES workloads on scale unit deployments:

- Sales orders
- Transfer issue
- Replenishment
- Inventory movement
- Purchase orders (linked to warehouse orders)

No other processing of source documents and warehouse work types are currently supported on scale units. For example, for a WES workload on a scale unit, you can't perform a transfer order receiving process (Transfer receipt) or process a cycle counting work.

> [!IMPORTANT]
> If you use a workload on a scale unit, you can't run unsupported processes for the specific warehouse on the hub.

The following warehouse management functionality isn't currently supported on scale units:

- Inbound processing of purchase order lines assigned to a load
- Inbound and outbound processing for items that have active tracking dimensions **Owner** and/or **Serial number**
- Processing of inventory that has a blocking status value
- Integration with quality management
- Processing of catch-weight items
- Processing of negative on-hand inventory

### Outbound (supported only for sales and transfer orders)

The following table shows which outbound features are supported, and where they are supported, when the warehouse management workloads are used in cloud and edge scale units.

> [!WARNING]
> Some warehouse functionality won't be available at warehouses that are running the warehouse management workloads in a scale unit.

| Process                                                      | Hub | WES workload on a scale unit |
|--------------------------------------------------------------|-----|------------------------------|
| Source document processing                                   | Yes | No |
| Load and transportation management processing                | Yes | No |
| Release to warehouse                                         | Yes | No |
| Shipment consolidation                                       | No  | No |
| Cross docking (picking work)                                 | No  | No |
| Shipment wave processing                                     | Yes, but finalization of the wave status is handled in the hub |<p>Yes, but initialization and finalization gets handled by the hub and the **Load building and sorting** are not supported<p><b>Note:</b> Access to the hub is required to finalize the wave status as part of the wave processing.</p> |
| Warehouse work processing (incl. license plate print)     | No  | <p>Yes, but only for the above mentioned supported capabilities. |
| Cluster picking                                              | No  | Yes|
| Packing processing                                           | No  | No |
| Outbound sorting processing                                  | No  | No |
| Printing of load related documents                           | Yes | No |
| Bill of lading and ASN generation                            | Yes | No |
| Ship confirmation and packing slip processing                | Yes | No |
| Short picking (sales and transfer orders)                    | No  | No |
| Work cancellation                                            | No  | Yes|
| Change of work locations (sales and transfer orders)         | No  | Yes|
| Complete work (sales and transfer orders)                    | No  | Yes|
| Block and unblock work                                       | No  | No |
| Change user                                                  | No  | Yes|
| Print work report                                            | No  | No |
| Wave label                                                   | No  | Yes|
| Reverse work                                                 | No  | No |

### Inbound

The following table shows which inbound features are supported, and where they are supported, when the warehouse management workloads are used in cloud and edge scale units.

| Process                                                          | Hub | WES workload on a scale unit |
|------------------------------------------------------------------|-----|------------------------------|
| Source&nbsp;document&nbsp;processing                                       | Yes | No |
| Load and transportation management processing                    | Yes | No |
| Shipment confirmation                                            | Yes | No |
| Purchase order release to warehouse (warehouse order processing) | Yes | No |
| Purchase order item receiving and put away                        | <p>Yes,&nbsp;when&nbsp;there&nbsp;isn't a warehouse order</p><p>No, when there is a warehouse order</p> | <p>Yes, when there is a warehouse order, and when a purchase order isn't part of a <i>load</i>.</p><p>No, when there isn't a warehouse order.</p> |
| Purchase order line receiving and put away                        | <p>Yes, when there isn't a warehouse order</p><p>No, when there is a warehouse order</p> | <p>Yes,&nbsp;when&nbsp;there&nbsp;isn't a warehouse order</p><p>No, when there is a warehouse order</p> |
| Return order receiving and put away                               | Yes | No |
| Mixed license plate receiving and put away                        | <p>Yes, when there isn't a warehouse order</p><p>No, when there is a warehouse order</p> | No |
| Load item receiving                                              | <p>Yes, when there isn't a warehouse order</p><p>No, when there is a warehouse order</p> | No |
| License plate receiving and put away                              | <p>Yes, when there isn't a warehouse order</p><p>No, when there is a warehouse order</p> | No |
| Transfer order item receiving and put away                        | Yes | No |
| Transfer order line receiving and put away                        | Yes | No |
| Work cancellation                                                | <p>Yes, when there isn't a warehouse order</p><p>No, when there is a warehouse order</p> | <p>Yes, but the <b>Unregister receipt when canceling work</b> option (on the <b>Warehouse management parameters</b> page) isn't supported.</p> |
| Purchase order product receipt processing                        | Yes | No |
| Cross docking work creation as part of receiving                 | <p>Yes, when there isn't a warehouse order</p><p>No, when there is a warehouse order</p> | No |

### Warehouse operations and exception handing

The following table shows which warehouse operations and exception handing features are supported, and where they are supported, when the warehouse management workloads are used in cloud and edge scale units.

| Process                                            | Hub | WES workload on a scale unit |
|----------------------------------------------------|-----|------------------------------|
| License plate inquire                              | Yes | Yes                          |
| Item inquire                                       | Yes | Yes                          |
| Location inquire                                   | Yes | Yes                          |
| Change warehouse                                   | Yes | Yes                          |
| Movement                                           | No  | Yes                          |
| Movement by template                               | No  | Yes                          |
| Adjustment (in/out)                                | Yes | No                           |
| Cycle counting and Counting discrepancy processing | Yes | No                           |
| Reprint label (license plate printing)             | Yes | Yes                           |
| License plate build                                | Yes | No                           |
| License plate break                                | Yes | No                           |
| Driver check in                                    | Yes | No                           |
| Driver check out                                   | Yes | No                           |
| Change batch disposition code                      | Yes | Yes                          |
| Display open work list                             | Yes | Yes                           |
| Consolidate license plates                         | No  | No                           |
| Remove container from group                        | No  | No                           |
| Cancel work                                        | No  | Yes                           |
| Min/max replenishment processing                   | No  | Yes                           |
| Slotting replenishment processing                  | No  | Yes                           |

### Production

Warehouse management production scenarios isn't currently supported on scale unit workloads as indicated in the following table.

| Process | Hub | WES workload on a scale unit |
|---------|-----|------------------------------|
| <p>All warehouse management processes that are related to production. Here are some examples:</p><li>Release to warehouse</li><li>Production wave processing</li><li>Raw material picking</li><li>Finished goods put away</li><li>Co-product and by-product put away</li><li>Kanban put away</li><li>Kanban picking</li><li>Start production order</li><li>Production scrap</li><li>Production last pallet</li><li>Register material consumption</li><li>Empty kanban</li></ul> | Yes | No |

## Maintaining scale units for WES

Several batch jobs run on both the hub and scale units.

On the hub deployment, you can manually maintain the batch jobs. You can manage the following three jobs at **Warehouse management \> Periodic tasks \> Back-office workload management**:

- Process work status update events
- Process wave execution control transfer events
- Register source order receipts

On the workload in scale units, you can manage the following two batch jobs at **Warehouse management \> Periodic tasks \> Workload management**:

- Process wave table records
- Process wave execution control transfer events
