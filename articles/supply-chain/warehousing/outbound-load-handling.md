---
title: Warehouse handling of outbound loads for sales, transfer, and outbound shipment orders
description: This article describes the warehouse handling process for outbound loads for sales, transfer, and outbound shipment orders.
author: perlynne
ms.author: perlynne
ms.reviewer: kamaybac
ms.search.form: WHSLoadTable, WHSLoadPlanningListPage, WHSLoadPlanningWorkbench, WHSOutboundLoadPlanningWorkbench, WHSOutboundShipmentOrder, WHSPackingSlipPostingParameters, WHSShipPlanningListPage, WHSShipmentDetails, WHSWaveTemplateTable, WHSPostMethod, WHSWorkTemplateTable, WHSLocDirTable, WHSEWManagementSystem, InventLocations 
ms.topic: conceptual
ms.date: 07/29/2024
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Warehouse handling of outbound loads for sales, transfer, and outbound shipment orders

[!include [banner](../includes/banner.md)]

This article describes the warehouse handling process for outbound loads.

An *outbound load* is a set of shipments from a warehouse destined for various locations, such as customer addresses or other warehouses. Usually, it's linked to a physical delivery vehicle like a shipping container or truck. It's a component of the warehouse management outbound procedure, which involves organizing, picking, packaging, and sending goods to complete orders. Outbound loads can be formed either manually or automatically, and their creation depends on predefined outbound operations that influence their dependencies and functional effects.

Each outbound load can be associated with one or more order line quantities for sales orders, transfer orders, and outbound shipment orders. Your system might also contain transportation plans. For more information about how to create and manage outbound transportation, see [Transportation management overview](../transportation/transportation-management-overview.md).

## <a name="outbound-shipment-policies"></a> Outbound shipment processing policies

To manage the process of shipping out your orders, you must apply an *Outbound shipment processing policy* that has the desired flow set up for your shipments.

The following options are set up on the **Outbound shipment processing policies** page (**Warehouse management \> Setup \> Shipping \> Outbound shipment processing policies**):

- **Enforce shipment to order matching** – Set to *Yes* to allow just one shipment to be associated to each demand order. You must set this to *Yes* when using [Warehouse management only mode with externally managed warehouse processing](wms-only-mode-external-shared-warehouse.md) because that functionality is set up on the source system related to the externally managed warehouse.
- **Fill entire shipment** – This setting lets you control whether warehouse wave processing will only proceed with shipments when it's possible to create warehouse work for the full quantities of the shipment lines. The default value is *Respect customer settings*, which adheres to the **Fill entire shipment** setting defined for each customer.

## Define outbound shipment processing policy defaults

Each shipment can be assigned an *outbound shipment processing policy*. The default policy can be assigned in any of several ways:

- **By order** – Policies set up on outbound orders are assigned to all shipments created from those orders.
- **By customer** – When a policy is assigned to a customer, then outbound orders created for that customer will inherit that policy, which will then propagate to shipments created from those orders.
- **By source system** – This is related to [Warehouse management only mode](wms-only-mode-overview.md). All shipments coming from a source system will inherit the policy that was assigned to that system.

## How outbound loads are created, registered, and shipped

The following illustration provides an overview of how outbound loads for sales orders (as an example) are managed. If the order lines must be processed by an externally managed warehouse, then the outbound flow will separate and proceed exclusively under the Warehouse management only mode process through *outbound shipment orders*. For more information about  this method, see [Warehouse management only mode with external shared warehouses](wms-only-mode-external-shared-warehouse.md).

:::image type="content" source="media/outbound-load-process.svg" alt-text="The outbound load handling process." lightbox="media/outbound-load-process.svg":::

### Sales order creation

This process begins when [sales orders are created](../sales-marketing/tasks/create-sales-orders.md). [Reservations](../inventory/reserve-inventory-quantities.md) for order lines can be set up to occur automatically, performed manually, or delayed according to system setup preferences.

### Create load before release to warehouse

An existing sales order is required to generate an outbound load. Nonetheless, it's possible to establish the outbound loads prior to executing the [release to warehouse](#release-to-warehouse) procedure.

The [Outbound load planning workbench](tasks/use-load-planning-workbench-plan-loads-shipments.md) and the [Load building workbench](../transportation/tasks/load-building-workbench.md) processes are available for choosing the order lines and quantities that will comprise a load.

### <a name="release-to-warehouse"></a>Release to warehouse

The [release to warehouse](release-to-warehouse-process.md) process creates *load lines* and groups them into *shipments*. The shipment consolidation process allows for automated [shipment consolidation](about-shipment-consolidation-policies.md). Shipments related to an [externally managed warehouse](wms-only-mode-external-shared-warehouse.md) are locked by setting **Outbound shipment processing ownership** to *External* until updated order data is returned.

### Wave and warehouse work processing

The system generates picking work through [*wave processing*](wave-processing.md) and can create loads when required. An available [*wave template*](wave-templates.md) must exist to determines whether the [advanced load building](advanced-load-building-during-wave.md) method is used.

*Work templates* determine how work is performed for each warehouse process, and *location directives* specify the pick and put locations for inventory movements. For more information, see [Control warehouse work by using work templates and location directives](control-warehouse-location-directives.md).

Warehouse *work* is used to control any warehouse operation performed by a warehouse worker or [material handling system](mhax.md). Typically, warehouse work operations consist of at least two consecutive actions: a *pick* and a *put* of inventory.

### Outbound load shipment confirmation

When all the warehouse tasks for a load have been completed, a subsequent shipment confirmation procedure can be executed, which updates the **Load status** to *Shipped* and changes the **Load packing slip background posting status** from *None* to *Queued*. This process can function as part of an automated [background process](confirm-outbound-shipments-from-batch-jobs.md), depending on the configuration.

> [!NOTE]
> When using the [confirm and transfer](confirm-and-transfer.md) capability, the system can create a new load for any load lines that weren't fully picked.

### <a name="load-packing-slip-posting"></a>Load packing slip posting

When the *Packing slip* from a load is processed, the system updates the related sales order line transactions to *Deducted*, which makes it possible to start the invoicing process. The *Load packing slip posting* scheduled task (**Warehouse management \> Periodic \> Load packing slip posting**) processes *Shipped* outbound loads that have **Load packing slip background posting status** set to *Queued*. Upon successful posting, the system change the status to *None*. If any errors occur during posting, the status is instead changed to *Error* (you can check the details in the generated batch job info log for more information about failed postings). The background posting procedure requires a status of *Queued*, but it's possible to manually post a load packing slip even if an *Error* is indicated. Upon successful posting, the status is changed to *None*.

For the *Load packing slip posting* task to operate in the background, you must make appropriate settings on the **Packing slip posting parameters** page (**Warehouse management \> Setup \> Inventory \> Packing slip posting parameters**). Remember that if printing is included in this process, you should avoid printing to screen because this task executes in the background within a batch job.

> [!TIP]
> By setting the **Packing slip creation policy** to *Shipment* for the load, and supplying each associated shipment with a **Preallocated packing slip ID** and **Preallocated packing slip document date** in the *Packing slip posting parameters* section, enables automatic distribution of sales packing slips for each shipment based on the predetermined values.
> This process applies automatically when running the [externally managed warehouse](wms-only-mode-external-shared-warehouse.md) process.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]