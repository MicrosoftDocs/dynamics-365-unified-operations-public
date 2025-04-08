---
title: Warehouse handling of outbound loads for sales, transfer, and outbound shipment orders
description: This article describes the warehouse handling process for outbound loads for sales, transfer, and outbound shipment orders.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ms.search.form: WHSLoadTable, WHSLoadPlanningListPage, WHSLoadPlanningWorkbench, WHSOutboundLoadPlanningWorkbench, WHSOutboundShipmentOrder, WHSPackingSlipPostingParameters, WHSShipPlanningListPage, WHSShipmentDetails, WHSWaveTemplateTable, WHSPostMethod, WHSWorkTemplateTable, WHSLocDirTable, WHSEWManagementSystem, InventLocations 
ms.topic: conceptual
ms.date: 07/29/2024
ms.custom: bap-template
---

# Warehouse handling of outbound loads for sales, transfer, and outbound shipment orders

[!include [banner](../includes/banner.md)]

This article describes the warehouse handling process for outbound loads for sales orders, transfer orders, and outbound shipment orders.

An *outbound load* is a set of shipments from a warehouse that are destined for various locations, such as customer addresses or other warehouses. Usually, outbound loads are linked to a physical delivery vehicle, such as a shipping container or truck.

An outbound load is a component of the warehouse management outbound procedure, which involves organizing, picking, packaging, and sending goods to complete orders. Outbound loads can be formed either manually or automatically. Their creation depends on predefined outbound operations that influence their dependencies and functional effects.

Each outbound load can be associated with one or more order line quantities for sales orders, transfer orders, and outbound shipment orders. Your system might also contain transportation plans. Learn more about how to create and manage outbound transportation in [Transportation management overview](../transportation/transportation-management-overview.md).

## <a name="outbound-shipment-policies"></a>Outbound shipment processing policies

To manage the process of shipping your orders, you must apply an *outbound shipment processing policy* where the desired flow is set up for your shipments.

The following settings are configured on the **Outbound shipment processing policies** page (**Warehouse management** \> **Setup** \> **Shipping** \> **Outbound shipment processing policies**):

- **Enforce shipment to order matching** – Set this option to *Yes* to allow just one shipment to be associated with each demand order. If you use [Warehouse management only mode with externally managed warehouse processing](wms-only-mode-external-shared-warehouse.md), you must set this option to *Yes*, because that functionality is set up on the source system that is related to the externally managed warehouse.
- **Fill entire shipment** – Use this field to control whether warehouse wave processing proceeds with shipments only when warehouse work can be created for the full quantities of the shipment lines. The default value is *Respect customer settings*. When that value is used, the **Fill entire shipment** setting that is defined for each customer is respected.

## Define default outbound shipment processing policies

An outbound shipment processing policy can be assigned to each shipment. The default policy can be assigned in any of the following ways:

- **By order** – Policies that are set up on outbound orders are assigned to all shipments that are created from those orders.
- **By customer** – A policy that is assigned to a customer is inherited by outbound orders that are created for that customer. It's then propagated to shipments that are created from those orders.
- **By source system** – This method is related to [Warehouse management only mode](wms-only-mode-overview.md). All shipments that come from a source system inherit the policy that is assigned to that system.

## How outbound loads are created, registered, and shipped

The following illustration provides an overview of the outbound load handling process. It uses outbound loads for sales orders as an example. If the order lines must be processed by an externally managed warehouse, the outbound flow branches off and proceeds exclusively through the Warehouse management only mode process via *outbound shipment orders*. Learn more about this method in [Warehouse management only mode with external shared warehouses](wms-only-mode-external-shared-warehouse.md).

:::image type="content" source="media/outbound-load-process.svg" alt-text="Diagram of the outbound load handling process." lightbox="media/outbound-load-process.svg":::

### Sales order creation

This process begins when [sales orders are created](../sales-marketing/tasks/create-sales-orders.md). [Reservations](../inventory/reserve-inventory-quantities.md) for order lines can be set up to occur automatically, they can be performed manually, or they can be delayed according to system setup preferences.

### Create a load before the release to a warehouse

A sales order must exist before an outbound load can be generated. Nevertheless, outbound loads can be defined before the [release to warehouse](#release-to-warehouse) procedure is run.

The [Outbound load planning workbench](tasks/use-load-planning-workbench-plan-loads-shipments.md) and [Load building workbench](../transportation/tasks/load-building-workbench.md) processes can be used to select the order lines and quantities that comprise a load.

### <a name="release-to-warehouse"></a>Release to warehouse

The [release to warehouse](release-to-warehouse-process.md) process creates *load lines* and groups them into *shipments*. The shipment consolidation process allows for automated [shipment consolidation](about-shipment-consolidation-policies.md). Shipments that are related to an [externally managed warehouse](wms-only-mode-external-shared-warehouse.md) are locked by setting the **Outbound shipment processing ownership** value to *External* until updated order data is returned.

### Wave and warehouse work processing

The system generates picking work through [*wave processing*](wave-processing.md) and can create loads as required. An available [*wave template*](wave-templates.md) must exist to determine whether the [advanced load building](advanced-load-building-during-wave.md) method is used.

*Work templates* determine how work is performed for each warehouse process. *Location directives* specify the pick and put locations for inventory movements. Learn more in [Control warehouse work by using work templates and location directives](control-warehouse-location-directives.md).

Warehouse *work* is used to control any warehouse operation that a warehouse worker or [material handling system](mhax.md) performs. Typically, warehouse work operations consist of at least two consecutive actions: a *pick* and a *put* of inventory.

### Outbound load shipment confirmation

When all the warehouse tasks for a load are completed, a shipment confirmation procedure can be run. This procedure updates the **Load status** value to *Shipped*. It also changes the **Load packing slip background posting status** value from *None* to *Queued*. This process can be run as part of an automated [background process](confirm-outbound-shipments-from-batch-jobs.md), depending on the configuration.

> [!NOTE]
> When the [confirm and transfer](confirm-and-transfer.md) capability is used, the system can create a new load for any load lines that weren't fully picked.

### <a name="load-packing-slip-posting"></a>Load packing slip posting

When the *packing slip* from a load is processed, the system updates the related sales order line transactions to *Deducted*. At that point, the invoicing process can begin. The *Load packing slip posting* scheduled task (**Warehouse management** \> **Periodic** \> **Load packing slip posting**) processes *Shipped* outbound loads where the **Load packing slip background posting status** value is set to *Queued*. After successful posting, the system changes the status to *None*. If any errors occur during posting, the status is changed to *Error* instead. (For more information about failed postings, you can review the details in the information log that is generated for the batch job.)

Although the background posting procedure requires a status of *Queued*, a load packing slip can be manually posted even if the status is *Error*. After successful posting, the status is changed to *None*.

To enable the *Load packing slip posting* task to work in the background, you must configure appropriate settings on the **Packing slip posting parameters** page (**Warehouse management** \> **Setup** \> **Inventory** \> **Packing slip posting parameters**). Because this task is run in the background, within a batch job, you should avoid printing to the screen if printing is included in the process.

> [!TIP]
> To enable automatic distribution of sales packing slips for each shipment, based on the predetermined values, set the **Packing slip creation policy** value to *Shipment* for the load, and supply **Preallocated packing slip ID** and **Preallocated packing slip document date** values for each associated shipment in the *Packing slip posting parameters* section.
>
> This process automatically applies when the [externally managed warehouse](wms-only-mode-external-shared-warehouse.md) process is run.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
