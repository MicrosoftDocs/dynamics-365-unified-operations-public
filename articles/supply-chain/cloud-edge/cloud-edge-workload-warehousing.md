---
# required metadata

title: Warehouse management workloads for cloud and edge scale units
description: This feature allows edge scale units to run selected processes from your warehouse management workload. Cloud scale units run their workloads in the cloud using dedicated processing capacity in your selected Azure region. With edge scale units, you can run certain workloads independently on premises, even while temporarily disconnected from the cloud.
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
> Not all business functionality is fully supported in the public preview when using workload scale units. Be sure only to use the processes specifically described in this topic as being supported.  

## Warehouse execution for edge scale units

This feature allows edge scale units to run selected processes from your warehouse management workload. Cloud scale units run their workloads in the cloud using dedicated processing capacity in your selected Azure region. With edge scale units, you can run certain workloads independently on premises, even while temporarily disconnected from the cloud.

In this topic, warehouse management executions within a warehouse defined as an edge scale unit are called a *Warehouse execution system (WES)*.

## Prerequisites

You must have a fully deployed cloud and edge scale unit set up. For more information about the architecture and deployment process, see [Cloud and Edge scale units for manufacturing and warehouse management workloads](cloud-edge-landing-page.md).

## How the WES edge scale unit functions

For the selected warehouse management processes, the data will get synchronized between the cloud and the edge scale units where the needed data includes ownership information.

Only the data within the ownership of a specific scale unit can get maintained by the dedicated scale unit. Therefore, to avoid data update conflicts, it is important to understand which processes are supported for each of the deployments.

The following data will be maintained by the edge scale unit ownership:

- **Wave processing data** - Selected wave process methods are handled as part of the edge scale unit wave processing.

- **Work processing data** - The following types of work order processing are supported:
  - Inventory movements (manual and movement by template work)
  - Purchase orders (putaway work via a warehouse order)
  - Sales orders (simple picking and loading work)

- **Warehouse order receipt data** - Only used for purchase orders manually released to warehouse.

- **License plate data** - This data isn't warehouse specific and therefore is shared with the cloud scale unit.

## Outbound process flow

All source documents, such as sales and transfer orders, are handled in the ownership of the cloud scale units. The same goes for order allocation and outbound load processing.

The release to warehouse, shipment creation, and wave creation processes are also taken care of at the cloud scale unit.

The edge scale unit, and only the edge scale unit, does the actual wave processing (such as work allocation, replenishment work, and demand work creation) following the release of the wave. This lets warehouse workers process outbound work using the warehouse app signed in to the edge scale unit.

![Outbound process flow](./media/WES_Outbound_flow.png)

## Inbound process flow

All source documents, such as purchase and sales return orders, are handled in the ownership of the cloud scale units. The same goes for inbound load processing.
The inbound purchase order flow is conceptually different from the outbound flow, where the scale unit doing the processing depends on whether the order has been released to a warehouse or not.

At release to warehouse, warehouse orders are created and ownership of the related receiving flow gets passed to the edge scale unit.

The warehouse app receiving process is recorded at the edge scale unit against the inbound warehouse order, and the subsequent putaway work creation and processing can also be handled by the edge scale units.

Without the *release to warehouse* process&mdash;and therefore without *warehouse orders*&mdash;the cloud scale unit can process warehouse receiving and work processing.
![Inbound process flow](./media/WES_Inbound_flow.png)

## Supported processes and roles

Not all warehouse management processes can be supported for a WES deployment. Therefore we recommend using dedicated roles as part of the warehouse management processes to avoid confusing users.

To ease this process, a sample role called *Warehouse manager on workload* is included with demo data in **System administration \> Security \> Security configuration**. This role is intended to enable warehouse managers to access the WES at the edge scale unit. The role grants access to the forms that are relevant within the context of a workload hosted on the edge.

The assignment of roles to users is part of the initial full data synchronization from the cloud scale unit to the edge scale unit.

To trim a user role assignment, go to **System administration \> Security \> Assign users to roles** on the edge scale unit. Assign the *Warehouse manager on workload* role, and only this role, to users who acts as warehouse managers on the edge scale unit, as this will ensure that this user has access only to the supported functionality. Remove any other roles assigned to the user.

We recommend using the existing *Warehouse worker* role for warehouse management execution on both cloud and edge scale unit tasks. Be aware, however, that the role currently grants warehouse workers access to create and update actions using the client UI on the edge scale unit, including actions that aren't currently supported (such as transfer order processing).

## Supported WES processes

The following list describes the warehouse execution processes supported for a deployed edge scale unit:

- Enable selected wave methods processing for sales orders and demand replenishment.
- Enable warehouse workers to execute sales and demand replenishment warehouse work using the warehouse app.
- Enable warehouse workers to perform inquiries into on-hand inventory using the warehouse app.
- Enable warehouse workers to create and execute inventory movements using the warehouse app.
- Enable warehouse workers to register purchase orders and conduct putaway using the warehouse app.

The current work order types supported for WES scale unit deployments are:

- Sales orders
- Replenishment
- Inventory movement
- Purchase orders linked to Warehouse orders

No other source documents processing is currently supported. This means that it won't be possible, for example, to release a transfer order to an edge scale unit warehouse or process the outbound warehouse picking and shipping operations on edge scale unit deployments, nor will it be possible to run the process on a cloud scale unit deployment.

Additional limitations that apply to the supported processes at edge scale units are:

- Inbound and outbound processing for items having any active tracking dimensions (such as batch or serial number dimensions) isn't supported.
- Inventory status change processes and processing with a blocking inventory status value aren't supported.
- Integration to quality management isn't supported.
- Integration to production isn't supported.
- Catch weight item processing isn't supported.
- Over- and under-delivery processing isn't supported.
- Negative inventory on-hand processing isn't supported.

### Outbound (only support for sales orders and demand replenishment)

>[!Warning]
> Because only sales order processing is supported, it isn't possible to use outbound warehouse management processing for transfer orders.

|Process                                      |Cloud scale unit  |Edge scale unit  |
|---------------------------------------------|----------------|-------------------|
|Source document processing                   |Yes             |No                 |
|Load and transportation management processing |Yes             |No                 |
|Release to warehouse                         |Yes             |No                 |
|Shipment consolidation                   |No          |No             |
|Cross docking (picking work)             |No          |No             |
|Shipment wave processing                     |<p>(No):</p>But the finalization of the wave status is handled in the cloud.</p>       |<p>(Yes):</p>But without:<ul><li>Parallel work creation</li><li>Load building, sorting</li> <li>Containerization</li><li>Wave label printing</li></li></ul><p><b>Note: </b>Cloud access is needed to finalize the Wave status as part of the wave processing.</p>|
|Warehouse work processing (incl. license plate print)   | No             |<p>(Yes):</p>But only for:<ul><li>Sales picking</li><li>Sales loading</li><li>Without the use of active tracking dimensions</li></ul>|
|Cluster picking                          |No          |No             |
|Packing processing                       |No          |No             |
|Outbound sorting processing              |No          |No             |
|Printing of load related documents           |Yes             |No                 |
|Bill of lading and ASN generation            |Yes             |No                 |
|Ship confirmation and packing slip processing|Yes             |No                 |
|Short picking (sales orders)             |No          |No             |
|Work cancellation                        |No          |No             |
|Change of work locations (sales orders)  |No          |No             |
|Complete work (sales orders)             |No          |No             |
|Block and unblock work                   |No          |No             |
|Change user                              |No          |No             |
|Print work report                        |No          |No             |
|Wave label                               |No          |No             |
|Reverse work                             |No          |No             |

### Inbound

|Process                                      |Cloud scale unit  |Edge scale unit  |
|---------------------------------------------|----------------|-------------------|
|Source document processing                   |Yes             |No                 |
|Load and transportation management processing                      |Yes             |No                 |
|Shipment confirmation                        |Yes             |No                 |
|Purchase order release to warehouse (warehouse order processing)|Yes  |No         |
|Purchase order item receiving and put away   |<p>Yes:<br>Without&nbsp;warehouse&nbsp;order<p>No:<br>With warehouse order|<p>Yes:<br>With warehouse order and without purchase order being part of a <i>load</i>.<p><b>Note: </b>Only when using two mobile device menu items&mdash;one for receiving (<i>Purchase order item receiving</i>) and another with <i>Use existing work</i> to process the putaway.<p>No:<br>Without warehouse order|
|Purchase order line receiving and put away|<p>Yes:<br>Without warehouse order<p>No:<br>With warehouse order|No|
|Return order receiving and put away          |Yes              |No                 |
|Mixed license plate receiving and put away|<p>Yes:<br>Without warehouse order<p>No:<br>With warehouse order|No|
|Load item receiving|<p>Yes:<br>Without warehouse order<p>No:<br>With warehouse order|No|
|License plate receiving and put away|<p>Yes:<br>Without warehouse order<p>No:<br>With warehouse order|No|
|Transfer order item receiving and put away   |Yes               |No                |
|Transfer order line receiving and put away   |Yes               |No                |
|Work cancellation|<p>Yes:<br>Without warehouse order<p>No:<br>With warehouse order|<p>(Yes):</p> Without <b>Unregister receipt when canceling work</b>|
|Purchase order product receipt processing    |Yes              |No                 |
|Cross docking work creation as part of receiving|<p>Yes:<br>Without warehouse order<p>No:<br>With warehouse order|No|

### Warehouse operations and exception handing

|Process                                      |Cloud scale unit|Edge scale unit  |
|---------------------------------------------|----------------|-----------------|
|License plate inquire                        |Yes             |Yes              |
|Item inquire                                 |Yes             |Yes              |
|Location inquire                             |Yes             |Yes              |
|Change warehouse                             |Yes             |Yes              |
|Movement                                     |No              |Yes              |
|Movement by template                         |No              |Yes              |
|Adjustment (in/out)                          |Yes             |No               |
|Cycle counting and Counting discrepancy processing|Yes        |No               |
|Reprint label (license plate printing)       |Yes             |No               |
|License plate build                          |Yes             |No               |
|License plate break                          |Yes             |No               |
|Driver check in                              |Yes             |No               |
|Driver check out                             |Yes             |No               |
|Change batch disposition code                |Yes             |No               |
|Display open work list                       |Yes             |No               |
|Consolidate license plates               |No          |No           |
|Remove container from group              |No          |No           |
|Cancel work                              |No          |No           |
|Min/max replenishment processing         |No          |No           |
|Slotting replenishment processing        |No          |No           |

### Production

Warehouse management integration for production scenarios is currently not supported.

|Process                                      |Cloud scale unit|Edge scale unit  |
|---------------------------------------------|----------------|-----------------|
|<p>All warehouse management processes related to production, including:</p><li>Release to warehouse</li><li>Production wave processing</li><li>Raw material picking</li><li>Finished goods put away</li><li>Co-product and by-product put away</li><li>Kanban put away</li><li>Kanban picking</li><li>Start production order</li><li>Production scrap</li><li> Production last pallet</li><li>Register material consumption</li><li>Empty kanban</li>|No|No |

## How to maintain scale units for WES

Several batch jobs run on both the cloud and edge scale units.
On the cloud scale unit deployments, you can manually maintain the batch jobs under
**Warehouse management \> Periodic tasks \> Back-office workload management**, where three jobs can be maintained:

- Process work status update events
- Process wave execution control transfer events
- Register source order receipts

On the edge scale units, you can manually maintain the batch jobs under **Warehouse management \> Periodic tasks \> Workload management**, where two jobs can be maintained:

- Process wave table records
- Process wave execution control transfer events

