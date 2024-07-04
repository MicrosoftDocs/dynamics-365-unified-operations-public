---
title: Warehouse handling of outbound loads for sales, transfer, and outbound shipment orders
description: This article describes the warehouse handling process for outbound loads for sales, transfer, and outbound shipment orders.
author: perlynne
ms.author: perlynne
ms.reviewer: kamaybac
ms.search.form: WHSLoadTable, WHSLoadPlanningListPage, WHSLoadPlanningWorkbench, WHSOutboundLoadPlanningWorkbench, WHSOutboundShipmentOrder, WHSPackingSlipPostingParameters, WHSShipPlanningListPage, WHSShipmentDetails, WHSWaveTemplateTable, WHSPostMethod, WHSWorkTemplateTable, WHSLocDirTable, WHSEWManagementSystem, InventLocations 
ms.topic: how-to
ms.date: 05/10/2024
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Warehouse handling of outbound loads for sales, transfer, and outbound shipment orders

[!include [banner](../includes/banner.md)]

This article describes the warehouse handling process for outbound loads.

An outbound load is a set of shipments from a warehouse destined for various locations, such as customer addresses or other warehouses. Usually, it's linked to a physical delivery vehicle like a shipping container or truck. It's a component of the warehouse management's outbound procedure, which involves organizing, picking, packaging, and sending goods to complete orders. Outbound loads can be formed both manually or automatically, and their creation depends on predefined outbound operations that influence their dependencies and functional effects.

Each outbound load can be associated with one or more order line quantities for sales orders, transfer orders, and outbound shipment orders. Your system might also contain transportation plans. For more information about how to create and manage outbound transportation, see [Transportation management overview](../transportation/transportation-management-overview.md).

## <a name="outbound-shipment-policies"></a> Outbound shipment processing policies
To manage the process of shipping out your orders, you need to apply an *Outbound shipment processing policy* that has the desired flow set up to your shipments.

The following options are set up as part of the **Warehouse management \> Setup \> Shipping \> Outbound shipment processing policies**:

 - One shipment per order - This limits the association of one shipment and one demand order. It is a prerequisite when using [Warehouse management only mode with externally managed warehouse processing](wms-only-mode-external-shared-warehouse.md), as it needs to be set up on the source system related to the externally managed warehouse.
 - Fill entire shipment - This configuration allows you to confirm that warehouse wave processing will only proceed with shipments when it is possible to create warehouse work for the full quantities of the shipment lines. The default value is "Respect customer settings" which adheres to the fill entire shipment setting defined for a customer.

### How to define the *Outbound shipment processing policy* defaulting
The outbound shipment processing policy is a property assigned to shipments. However, it can be defaulted in multiple ways:
 - Orders - Policy can be set up on the outbound orders, and it will then be assigned to all shipments created from those orders.
 - Customer - Policy can be assigned to customers, and all orders created for that customer will have that policy, which will then propagate to shipments created from those orders.
 - Source systems - This is related to [Warehouse only mode](wms-only-mode-overview.md). All shipments coming from a source system will inherit the policy that was set up on it.

## Overview: How outbound loads are created, registered, and shipped

This illustration offers an overview of how outbound loads for sales orders (as an example) are managed. If the order lines must be processed by an externally managed warehouse, then the outbound flow will separate and proceed exclusively under the Warehouse management only mode process through *outbound shipment orders*. For more information about on this method, see [Warehouse management only mode with external shared warehouses](wms-only-mode-external-shared-warehouse.md).

:::image type="content" source="media/outbound-load-process.svg" alt-text="The outbound load handling process." lightbox="media/outbound-load-process.svg":::

**Sales order creation**

The commencement of the process involves [entering sales orders](../sales-marketing/tasks/create-sales-orders.md) into the system. [Reservations](../inventory/reserve-inventory-quantities.md) for order lines can be set up to occur automatically, performed manually, or delayed according to system setup preferences.

**Create load before release to warehouse**

An existing sales order is required to generate an outbound load. Nonetheless, it's possible to establish the outbound loads prior to executing the [release to warehouse](#release-to-warehouse) procedure.

The [Outbound load planning workbench](tasks/use-load-planning-workbench-plan-loads-shipments.md) and the [Load building workbench](../transportation/tasks/load-building-workbench.md) processes are available for choosing the order lines and quantities that will comprise a load.

<a name="release-to-warehouse"></a> **Release to warehouse**

The [release to warehouse](release-to-warehouse-process.md) process creates *load lines* and groups them into shipments. The shipment consolidation process allows for automated [shipment consolidation](about-shipment-consolidation-policies.md). Shipments related to an [externally managed warehouse](wms-only-mode-external-shared-warehouse.md) are locked with **Outbound shipment processing ownership** set to *External* until order data updates is returned.

**Wave and warehouse work processing**

The system generates picking work through [*wave processing*](wave-processing.md) and can create loads when required. There needs to be an available [*wave template*](wave-templates.md) which determines whether the [advanced load building](advanced-load-building-during-wave.md) method is utilized.
The *work templates* determine how work is performed for each warehouse process, and the *location directives* specify the pick and put locations for inventory movements. For more information, see [Control warehouse work by using work templates and location directives](control-warehouse-location-directives.md).
Warehouse *work* is used to control any warehouse operation performed by a warehouse worker or [material handling system](mhax.md). Typically, warehouse work operations consist of at least two consecutive actions: a pick and a put of inventory.

**Outbound load shipment confirmation**

Once the warehouse tasks are finished for a load, a subsequent shipment confirmation procedure can be executed, updating the **Load status** to *Shipped* and the **Load packing slip background posting status** will be updated from *None* to *Queued*. This process may function as part of an automated [background process](confirm-outbound-shipments-from-batch-jobs.md), depending on the configuration.

> [!NOTE]
> When using the [Confirm and transfer](confirm-and-transfer.md) capability a new load can get created for the load lines that weren't fully picked.

<a name="load-packing-slip-posting"></a> **Load packing slip posting**

Processing the *Packing slip* from a load updates the related sales order line transactions to *Deducted*, allowing the invoicing process to commence. The background process **Warehouse management \> Periodic \> Load packing slip posting** runs for *Shipped* outbound loads with **Load packing slip background posting status** setting *Queued*. Upon successful posting, the status shifts to *None*. Should any errors occur during posting, the status alters to *Error*, requiring attention to the details in the generated batch job info log. The background posting procedure requires a status marked as *Queued*, yet it's possible to manually post a load packing slip even if an *Error* is indicated. Upon successful posting, the status will change to *None*.

For the *Load packing slip posting* to operate in the background, proper configuration of **Warehouse management \> Setup \> Inventory \> Packing slip posting parameters** is needed. Remember that if printing is included in this process, avoid printing to screen since this task will execute in the background within a batch job.

> [!TIP]
> By setting the **Packing slip creation policy** to *Shipment* for the load, and supplying each associated shipment with a **Preallocated packing slip id** and **Preallocated packing slip document date** in the *PACKING SLIP POSTING PARAMETERS* section, enables automatic distribution of sales packing slips for each shipment based on the predetermined values.
> This process will automatically apply when running the [externally managed warehouse](wms-only-mode-external-shared-warehouse.md) process.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]