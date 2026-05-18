---
title: Warehouse handling of outbound loads for sales, transfer, and outbound shipment orders
description: This article describes the warehouse handling process for outbound loads for sales, transfer, and outbound shipment orders.
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ms.search.form: WHSLoadTable, WHSLoadPlanningListPage, WHSLoadPlanningWorkbench, WHSOutboundLoadPlanningWorkbench, WHSOutboundShipmentOrder, WHSPackingSlipPostingParameters, WHSShipPlanningListPage, WHSShipmentDetails, WHSWaveTemplateTable, WHSPostMethod, WHSWorkTemplateTable, WHSLocDirTable, WHSEWManagementSystem, InventLocations 
ms.topic: article
ms.date: 5/11/2026
ms.custom: bap-template
---

# Warehouse handling of outbound loads for sales, transfer, and outbound shipment orders

[!include [banner](../includes/banner.md)]

This article describes the warehouse handling process for outbound loads for sales orders, transfer orders, and outbound shipment orders.

An *outbound load* is a set of shipments from a warehouse that are destined for various locations, such as customer addresses or other warehouses. Usually, outbound loads are linked to a physical delivery vehicle, such as a shipping container or truck.

An outbound load is a component of the warehouse management outbound procedure, which involves organizing, picking, packaging, and sending goods to complete orders. You can form outbound loads manually or automatically. Their creation depends on predefined outbound operations that influence their dependencies and functional effects.

Each outbound load can be associated with one or more order line quantities for sales orders, transfer orders, and outbound shipment orders. Your system might also contain transportation plans. Learn more about how to create and manage outbound transportation in [Transportation management overview](../transportation/transportation-management-overview.md).

## <a name="outbound-shipment-policies"></a>Outbound shipment processing policies

To manage the process of shipping your orders, apply an *outbound shipment processing policy* where you set up the desired flow for your shipments.

The following settings are configured on the **Outbound shipment processing policies** page (**Warehouse management** \> **Setup** \> **Shipping** \> **Outbound shipment processing policies**):

- **Fill entire shipment** – Choose what to do if work creation fails for one or more lines in a shipment (for example, due to location directive failures). This feature only checks for work creation failures and doesn't check whether the full ordered quantity can be fulfilled. Choose one of the following options:
    - *Enabled*: If work creation fails for any line in a shipment, exclude that entire shipment from the wave (create no work for that shipment), regardless of the setting for each customer.
    - *Disabled*: If work creation fails for one or more lines in a shipment, skip those lines but still create work for all of the other lines, regardless of the setting for each customer.
    - *Respect customer settings*: Respect the **Fill entire shipment** setting defined for each customer.

- **Enforce shipment to order matching** – Choose whether the policy should permit just one shipment to be related to each outbound order, or whether multiple shipments per order should be allowed. Select one of the following values:
    - *No* – Allow multiple shipments per outbound order.
    - *Yes* (Supply Chain Management version 10.0.46 and later) – Allow just one shipment per outbound order. In version 10.0.46 and later, when you confirm a shipment, the policy instructs the system to update the delivery remainder on the source order line to reflect the quantity that was actually shipped. If you later reverse the shipment, the delivery remainder is restored to the original ordered quantity.
    - *Yes* (Supply Chain Management version 10.0.45 and earlier) – Allow just one shipment per outbound order. In version 10.0.45 and earlier, if the shipped quantity differs from the ordered quantity, you must manually update the delivery remainder to match the shipped quantity before you confirm the shipment.

    > [!NOTE]
    > If you use [Warehouse management only mode with external shared warehouses](wms-only-mode-external-shared-warehouse.md), your [source system](wms-only-mode-setup.md#source-systems) must be configured to use an outbound shipment processing policy where **Enforce shipment to order matching** is set to *Yes* because that functionality is set up on the source system that is related to the externally managed warehouse.

## Define default outbound shipment processing policies

Assign an outbound shipment processing policy to each shipment. Assign the default policy in any of the following ways:

- **By order** – Assign policies that you set up on outbound orders to all shipments that you create from those orders.
- **By customer** – Assign a policy to a customer. Outbound orders that you create for that customer inherit the policy. The policy then propagates to shipments that you create from those orders.
- **By source system** – This method is related to [Warehouse management only mode](wms-only-mode-overview.md). All shipments that come from a source system inherit the policy that you assign to that system.

## How outbound loads are created, registered, and shipped

The following illustration provides an overview of the outbound load handling process. It uses outbound loads for sales orders as an example. If the order lines must be processed by an externally managed warehouse, the outbound flow branches off and proceeds exclusively through the Warehouse management only mode process via *outbound shipment orders*. Learn more about this method in [Warehouse management only mode with external shared warehouses](wms-only-mode-external-shared-warehouse.md).

:::image type="content" source="media/outbound-load-process.svg" alt-text="Diagram of the outbound load handling process." lightbox="media/outbound-load-process.svg":::

### Sales order creation

This process begins when [sales orders are created](../sales-marketing/tasks/create-sales-orders.md). [Reservations](../inventory/reserve-inventory-quantities.md) for order lines can be set up to occur automatically, they can be performed manually, or they can be delayed according to system setup preferences.

### Create a load before the release to a warehouse

A sales order must exist before an outbound load can be generated. Nevertheless, you can define outbound loads before running the [release to warehouse](#release-to-warehouse) procedure.

Use the [Outbound load planning workbench](tasks/use-load-planning-workbench-plan-loads-shipments.md) and [Load building workbench](../transportation/tasks/load-building-workbench.md) processes to select the order lines and quantities that comprise a load.

### <a name="release-to-warehouse"></a>Release to warehouse

The [release to warehouse](release-to-warehouse-process.md) process creates *load lines* and groups them into *shipments*. The shipment consolidation process allows for automated [shipment consolidation](about-shipment-consolidation-policies.md). Shipments that are related to an [externally managed warehouse](wms-only-mode-external-shared-warehouse.md) are locked by setting the **Outbound shipment processing ownership** value to *External* until updated order data is returned.

### Wave and warehouse work processing

The system generates picking work through [*wave processing*](wave-processing.md) and can create loads as required. An available [*wave template*](wave-templates.md) must exist to determine whether the [advanced load building](advanced-load-building-during-wave.md) method is used.

*Work templates* determine how work is performed for each warehouse process. *Location directives* specify the pick and put locations for inventory movements. Learn more in [Control warehouse work by using work templates and location directives](control-warehouse-location-directives.md).

Warehouse *work* controls any warehouse operation that a warehouse worker or [material handling system](mhax.md) performs. Typically, warehouse work operations consist of at least two consecutive actions: a *pick* and a *put* of inventory.

### Outbound load shipment confirmation

When you complete all the warehouse tasks for a load, run the shipment confirmation procedure. This procedure updates the **Load status** value to *Shipped*. It also changes the **Load packing slip background posting status** value from *None* to *Queued*. Depending on the configuration, you can run this process as part of an automated [background process](confirm-outbound-shipments-from-batch-jobs.md).

> [!NOTE]
> When you use the [confirm and transfer](confirm-and-transfer.md) capability, the system can create a new load for any load lines that aren't fully picked.

### Generate an outbound ASN

When you ship a load, the system can generate an *outbound advanced shipping notice (ASN)* to notify a customer or downstream warehouse about the shipment. By default, the outbound ASN is generated from the load's *shipments* and *load lines*, which reference the originating sales order lines as they were defined when the order was released. This default generation is true even when the warehouse is enabled for [warehouse management processes](warehouse-management-overview.md) (WMS). Downstream warehouse execution work, such as picking, sorting, or packing into containers, doesn't change the packing structure of the outbound ASN.

> [!NOTE]
> When a transfer order ships from one WMS-enabled warehouse to another, the system uses the outbound shipment data to create a corresponding [inbound ASN](import-asn-data-entity.md) at the destination warehouse. The inbound ASN includes the license plate packing structure to support [license plate receiving](warehousing-mobile-device-app-license-plate-receiving.md) when the goods arrive.

### <a name="load-packing-slip-posting"></a>Load packing slip posting

When you process the *packing slip* from a load, the system updates the related sales order line transactions to *Deducted*. At that point, the invoicing process can begin. The *Load packing slip posting* scheduled task (**Warehouse management** \> **Periodic** \> **Load packing slip posting**) processes *Shipped* outbound loads where the **Load packing slip background posting status** value is set to *Queued*. After successful posting, the system changes the status to *None*. If any errors occur during posting, the status is changed to *Error* instead. For more information about failed postings, you can review the details in the information log that is generated for the batch job.

Although the background posting procedure requires a status of *Queued*, you can manually post a load packing slip even if the status is *Error*. After successful posting, the status is changed to *None*.

To enable the *Load packing slip posting* task to work in the background, you must configure appropriate settings on the **Packing slip posting parameters** page (**Warehouse management** \> **Setup** \> **Inventory** \> **Packing slip posting parameters**). Because this task runs in the background, within a batch job, avoid printing to the screen if printing is included in the process.

> [!TIP]
> To enable automatic distribution of sales packing slips for each shipment, based on the predetermined values, set the **Packing slip creation policy** value to *Shipment* for the load, and supply **Preallocated packing slip ID** and **Preallocated packing slip document date** values for each associated shipment in the *Packing slip posting parameters* section.
>
> This process automatically applies when the [externally managed warehouse](wms-only-mode-external-shared-warehouse.md) process is run.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
