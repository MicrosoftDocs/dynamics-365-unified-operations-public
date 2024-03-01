---
title: External shared warehouse processing (preview)
description: This article provides information about running Warehouse management only mode with external shared warehouse processing, which enables the integration of the warehouse management (WMS) functionality in separate legal entity handling requests from multiple sales subsidiaries/LEs in Microsoft Dynamics 365 Supply Chain Management.
author: perlynne
ms.author: perlynne
ms.reviewer: kamaybac
ms.search.form:
ms.topic: overview
ms.date: 01/29/2024
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Warehouse management only mode with external shared warehouse (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

<!-- KFM: Preview until further notice -->

You can use the [*Warehouse management only mode*](wms-only-mode-overview.md) feature to handle logistic operations in a different legal entity and connect warehouses between this legal entity and the other legal entities that do all the order and financial processing.
In addition, the warehouse management processes can track which legal entity owns the inventory for items that are shared across different entities using an owner inventory dimension.

[!INCLUDE [preview-note](../includes/preview-note.md)]

## High-level implementation example

The warehouse management only mode is active with an external shared warehouse in the legal entity *WOM* that deals with logistics warehouse operations for two sales subsidiaries that manage the order and financial processing in the legal entities *LE1* and *LE2*.

:::image type="content" source="media/wms-only-shared-warehouse-high-level-set-up.svg" alt-text="High-level integration diagram." lightbox="media/wms-only-shared-warehouse-high-level-set-up.svg":::

## Inbound example process (Shared warehouse in D365)

The following illustration highlights the elements of the inbound process.

:::image type="content" source="media/wms-only-shared-warehouse-inbound-process.svg" alt-text="Inbound process for Warehouse management only mode." lightbox="media/wms-only-shared-warehouse-inbound-process.svg":::

Here's a high-level description of the inbound process:

1. *LE1*: *Purchase orders* get created and confirmed which will create **Warehouse management \> External warehouse shipment orders \> External warehouse inbound shipment order requests**, resulting in *Inbound shipment order messages* getting delivered to the *WOM* legal entity.
1. *WOM*: Processing of the *Inbound shipment order messages* resulting in the creation of *Inbound shipment orders*.
1. *WOM*: Inbound loads are created manually, automatically, or through import (depending on your configuration).
1. *WOM*: Warehouse workers uses the Warehouse Management mobile app to *register* the inbound shipment order transactions.
1. *WOM* [Receiving completed](wms-only-mode-shared-and-external-detail-use.md#receiving-completed) gets processed for the related loads. These processes update the load status to *Received*, generates *External warehouse inbound shipment order updates* for *LE1*.
1. *LE1*: During the processing of the *External warehouse inbound shipment order updates* inbound loads and shipments get created and the related purchase order line transactions updated to *Registered* enabling the further processing of the *Product receipt* and *Invoicing*. You must enable the **Warehouse management \> Periodic tasks \> Process external warehouse inbound shipment orders updates** for automatic background processing.
1. *WOM*: The *Inbound shipment order line* transactions get finalized by running the *Post shipment receipts* [batch job](../../fin-ops-core/dev-itpro/sysadmin/process-automation.md).

For a more detailed description of this process and the related processes, see [Work with warehouse management only mode in Supply Chain Management](wms-only-mode-shared-and-external-detail-use.md).

## Outbound example process (Shared warehouse in D365)

The following illustration highlights the elements of the outbound process.

:::image type="content" source="media/wms-only-shared-warehouse-outbound-process.svg" alt-text="Outbound process for Warehouse management only mode." lightbox="media/wms-only-shared-warehouse-outbound-process.svg":::

Here's a high-level description of the outbound process:

1. *ERP1*: *Sales order* gets created and released to the warehouse which will create shipments and *External warehouse outbound shipment order requests*, resulting in *Outbound shipment order messages* getting delivered to the *WOM* legal entity.
1. *WOM*: Processing of the *Outbound shipment order messages* resulting in the creation of *Outbound shipment orders*.
1. *WOM*: Inventory reservations are created either manually or automatically (depending on your configuration).
1. *WOM*: The orders are released for further warehouse processing, either manually or automatically. If you're using outbound load planning processes, you can create loads by using the outbound load planning workbench before you release the orders.
1. *WOM*: Depending on the setup of your [wave template](wave-templates.md) definitions, warehouse work might be created and released immediately.
1. *WOM*: The outbound warehouse work is processed, and the status of the related outbound shipment order line transactions is updated to *Picked*.
1. *WOM*: The loads are outbound ship confirmed. As a result, *External warehouse inbound shipment order updates* will get generated for *LE1*.
1. *LE1*: During the processing of the *External warehouse inbound shipment order updates* the outbound shipment data and the related sales order line transactions gets updated. The transactions will become *Picked* and thereby enabling the further processing of the *Packing slip* and *Invoicing* processing. You must enable the **Warehouse management \> Periodic tasks \> Process external warehouse outbound shipment orders updates** for automatic background processing.
1. *WOM*: The *Outbound shipment order line* transactions get finalized by running the *Post shipment packing slips* [batch job](../../fin-ops-core/dev-itpro/sysadmin/process-automation.md).

For a more detailed description of this process and the related processes, see [Work with warehouse management only mode in Supply Chain Management](wms-only-mode-shared-and-external-detail-use.md).

## On-hand adjustments

The data about the available inventory should match between each of the sales subseries and the legal entity that manages the warehouse. The *Warehouse inventory update log* process can help to keep the inventory on-hand data in sync when there are any changes.

<!-- TODO perlynne -->
**Warehouse \> ??? \> External warehouse inventory adjustments** data can get processed into *Counting journals* which either automatically or manually gets posted and thereby getting the inventory on-hand updates synchronized.  

:::image type="content" source="media/wms-only-shared-warehouse-inventory-process.svg" alt-text="Internal process for Warehouse management only mode." lightbox="media/wms-only-shared-warehouse-inventory-process.svg":::

## Setup requirements for external shared warehouse processing in D365

To use the Warehouse management only mode in the way shown above, you need to have at least two legal entities and you need to set up an *External warehouse management system* with the type `Legal entity` in *LE1* and link it to a [*Source system*](wms-only-mode-setup.md#source-systems) in the *WOM* legal entity. You can do this setup in the **Warehouse management \> Setup \> Warehouse management integration External warehouse management systems** page.

In the *LE1* **Warehouse management \> Setup \> Warehouse \> Warehouses** page you can now select the warehouses that you want to manage externally and specify the *External warehouse management system* that you use. You should assign a default location that does not track license plates. This location will be used for all the inventory updates from the external warehouse in the *WOM* legal entity. <!-- TODO perlynne CHECK if we manage to move the External warehouse to WOM LE setup! >


