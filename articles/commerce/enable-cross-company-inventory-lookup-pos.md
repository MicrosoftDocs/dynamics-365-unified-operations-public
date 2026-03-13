---
title: Enable cross-company inventory lookup for POS (preview)
description: Learn how to enable and configure the cross-company inventory lookup feature in Microsoft Dynamics 365 Commerce point of sale (POS) to view inventory availability across different legal entities.
author: yufeih
ms.date: 02/25/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: global
ms.author: yufeih
ms.search.validFrom: 2026-02-11
ms.custom: 
  - bap-template
---

# Enable cross-company inventory lookup for POS (preview)

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This article explains how to enable and configure cross-company inventory lookup feature in Microsoft Dynamics 365 Commerce point of sale (POS). This feature allows retail associates to view real-time inventory availability across multiple legal entities and warehouse locations, enabling better customer service and informed purchase decisions.

Cross-company inventory lookup extends the standard POS inventory lookup functionality to search for product availability across different legal entities (also known as companies) within your organization. This capability addresses scenarios where organizations operate with multiple legal entities for intercompany businesses, such as:

- **Stock-keeping companies**: Inventory is owned and stored in one legal entity.
- **Selling entities**: Multiple other legal entities operate retail stores and sales channels.
- **Cross-entity visibility**: Store associates need to check inventory in warehouses that belong to different legal entities.

This feature is valuable for European retailers and other organizations with complex multientity structures. It enables store associates to get a holistic inventory view across the entire organization within a single POS application, helping them guide customers to the nearest available store regardless of the legal entity.

Additionally, this feature supports warehouse location breakdown for organizations that configure warehouses with multiple locations and track inventory at the location level for more granular control.

### Business scenarios

Store associates can use cross-company inventory lookup to:

- Check product availability across warehouses and stores in different legal entities.
- View aggregated inventory across all locations in a fulfillment group.
- Guide customers to the nearest available store, even if it belongs to a different legal entity.

> [!NOTE]
> This feature currently supports inventory visibility only. Cross-company order fulfillment (placing orders to warehouses in different legal entities) is planned for a future release.

## Prerequisites

Before enabling the cross-company inventory lookup feature, ensure that:

- Your environment is running Dynamics 365 Commerce version 10.0.47 or later.
- Commerce Scale Unit (CSU) is properly configured and running.
- Inventory Visibility Service (IVS) integration is enabled and configured. For more information, see [Enable Inventory Visibility for Commerce](/dynamics365/supply-chain/inventory/inventory-visibility-commerce-enable).
- The Commerce-IVS integration is using API version 2.0 (not version 1.0).
- The standard POS inventory lookup operation is already configured and working.
- Appropriate security roles and permissions are set up for cross-entity access.

## Enable cross-company inventory view

Cross-company inventory view is disabled by default to minimize disruption to existing POS operations. Administrators must explicitly enable the feature when needed.

To enable cross-company inventory view, follow these steps:

1. In Commerce headquarters, go to **System administration > Workspaces > Feature management**.
1. Search for and select **Enable cross-company inventory view on Commerce**.
1. Select **Enable now**.

When this feature is enabled:
- POS and can query cross-company inventory (prerequisite: Commerce-IVS integration enabled with API v2.0).
- UI elements such as the **Cross-company inventory** tab and **Company** column are activated in POS.

When this feature is disabled:
- POS falls back to current behavior (single-company inventory lookup only).
- Cross-company UI elements are hidden.

## Configure fulfillment groups with cross-entity warehouses

Fulfillment groups determine which warehouses and stores are included in inventory lookups. To support cross-company inventory lookup, you must configure fulfillment groups to include warehouses from different legal entities.

### Add cross-entity warehouses to fulfillment groups

To add cross-entity warehouses to fulfillment groups, follow these steps:

1. In headquarters, go to **Retail and Commerce > Channels > Fulfillment groups**.
1. Select an existing fulfillment group, or select **New** to create a new one.
1. On the **Fulfillment group** page, select **Add line** to add warehouses.
1. In the **Company** column, select the legal entity that owns the warehouse.
1. In the **Warehouse** column, select the warehouse to add.
1. Repeat steps 3-5 to add warehouses from multiple legal entities.
1. Select **Save**.

> [!TIP]
> You can now add warehouses from different legal entities without switching between entity UIs. All cross-entity warehouses can be configured from a single fulfillment group page.

### Link stores to fulfillment groups

To link stores to fulfillment groups, follow these steps:

1. In headquarters, go to **Retail and Commerce > Channels > Stores > All stores**.
1. Select the store to configure.
1. On the **General** FastTab, in the **Fulfillment group** field, select the fulfillment group that includes the cross-entity warehouses.
1. Select **Save**.
1. Run distribution schedule **1070** (Channel configuration) to sync the changes to Commerce Scale Unit.

## Use cross-company inventory lookup in POS

Once configured, store associates can use the cross-company inventory lookup feature to check product availability across legal entities.

### View cross-company inventory

To view cross-company inventory, follow these steps:

1. In POS, search for a product using the search bar or by scanning a barcode.
1. From the product details page, select the **Inventory lookup** operation.
1. On the **Inventory lookup** page, select the **Cross-company inventory** tab. The system displays inventory availability for the product across all warehouses and stores in different legal entities that are configured in the fulfillment group linked to the current store.

The cross-company inventory view displays:
- **Company**: The legal entity that owns the warehouse or store
- **Warehouse/Store**: The name of the location
- **Inventory**: Available inventory quantity
- **Reserved**: Reserved inventory quantity
- **Ordered**: Ordered inventory quantity
- **Unit**: Unit of measure

> [!NOTE]
> If a fulfillment group isn't configured for the current store, the system doesn't show cross-company results.

## Feature limitations

Be aware of the following feature limitations as of the Commerce version 10.0.47 release.

### Cross-company stores hidden from order fulfillment

While store associates can view cross-company inventory, cross-company stores and warehouses are hidden from the following POS screens:
- Order fulfillment location selection
- Pick-up store selection
- Ship-from location selection

This means store associates can see inventory availability in cross-company locations, but they can't yet select those locations for order fulfillment directly in POS.

> [!IMPORTANT]
> Support for cross-company order fulfillment (inventory reservation and offset across legal entities) is planned for a future release.

## Distribution schedules

After you configure cross-company inventory lookup, run the distribution schedules in the following table to sync the changes to Commerce Scale Unit and POS.

| Schedule | Description |
|----------|-------------|
| **1070** | Channel configuration (for fulfillment group changes) |
| **1110** | Global configuration (for feature toggle and API settings) |
| **1040** | Products (if assortment changes are made) |

## Additional resources

[Enable Inventory Visibility for Commerce](/dynamics365/supply-chain/inventory/inventory-visibility-commerce-enable)

[Inventory lookup operation in POS](pos-inventory-lookup-operation.md)

[Calculate inventory availability for retail channels](calculated-inventory-retail-channels.md)

[Configure channel-side inventory calculation](inventory-lookup-channel-side-calc.md)

[Inventory Visibility public API version 2.0](/dynamics365/supply-chain/inventory/inventory-visibility-api)

[Work with store inventory](work-with-store-inventory.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
