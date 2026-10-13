---
title: Warehouse and store locator module
description: Learn how to configure the warehouse and store locator module for cross-legal-entity inventory visibility in Dynamics 365 Commerce.
author:
ms.author:
ms.reviewer: mirao
ms.search.form:
ms.topic: how-to
ms.date: 10/13/2026
ms.custom:
  - bap-template
---

# Warehouse and store locator module

[!INCLUDE [banner](includes/banner.md)]

The warehouse and store locator module helps business-to-business (B2B) buyers find stores and warehouses across legal entities. On a product details page (PDP), buyers can view inventory availability for the selected product or variant. In the site header, buyers can browse locations without selecting a product.

> [!IMPORTANT]
> The warehouse and store locator module is available as of Dynamics 365 Commerce version 10.0.50. In this release, the module supports inventory and location visibility only. It doesn't select a fulfillment source or support cross-legal-entity order fulfillment. Fulfillment capabilities will be available in a future release.

## Prerequisites

To use the warehouse and store locator module, your environment must meet the following requirements:

- You must be running Dynamics 365 Commerce version 10.0.50 or later.
- The e-commerce site must be associated with a B2B online channel. The module isn't displayed for business-to-consumer (B2C) channels.
- Cross-legal-entity inventory lookup must be turned on in Commerce site builder. Learn more in [Apply inventory settings](inventory-settings.md).
- Configure a fulfillment group that contains the stores and warehouses that buyers can view across legal entities. Include the channel's default warehouse in the fulfillment group.
- Configure latitude and longitude values for each location that you want to display on a map.
- Configure either the Azure Maps module or the Map module if you want to display locations on a map.

## Module usage

The warehouse and store locator module has two entry points. Configure a separate module instance for each entry point that you use.

| Entry point | Placement | Product context | Information shown |
|---|---|---|---|
| **Top ribbon** | **Warehouse locator** slot in the header module | No | Stores and warehouses across configured legal entities |
| **Product detail page** | **Warehouse locator** slot in the buy box module | Yes | Stores, warehouses, and inventory availability for the selected product or variant |

In PDP mode, buyers must select all required product dimensions before the module can retrieve availability for a variant.

## Warehouse and store locator module properties

The following table describes the properties that you can configure for the warehouse and store locator module.

| Property name | Value | Description |
|---|---|---|
| Entry point | **Top ribbon** or **Product detail page** | Determines where the module is used and whether it retrieves product-specific availability. |
| Dialog heading | Text | Specifies the heading that appears in the locator dialog. |
| Trigger text | Text | Specifies the text for the button or link that opens the locator. |
| Enable location search | **True** or **False** | Controls whether buyers can search by ZIP code, city, or state. |
| Enable region filter | **True** or **False** | Controls whether buyers can filter results by region. |
| Enable legal entity filter | **True** or **False** | Controls whether buyers can filter results by legal entity. |
| Enable type filter | **True** or **False** | Controls whether buyers can filter results by location type, such as warehouse or store. |
| Enable in-stock-only filter | **True** or **False** | Controls whether buyers can limit PDP results to locations that have inventory. This property applies only to the **Product detail page** entry point. |
| Search radius | Number | Specifies the radius used to search for nearby locations. |
| Search radius unit | **Miles** or **Kilometers** | Specifies the unit used for the search radius and displayed distances. |
| Terms of service link | Link | Specifies the map provider terms-of-service link shown in the dialog. |
| Custom CSS class name | Text | Specifies a custom CSS class that a theme can use to style the module. |
| Render module client side | **True** or **False** | Controls whether the module is rendered on the client. |

## Add the module to a header

Add the module to a header to let B2B buyers browse configured stores and warehouses without selecting a product.

1. In Commerce site builder, go to **Fragments**, and open the header fragment for the site.
1. Select the header module.
1. In the **Warehouse locator** slot, select the ellipsis (**...**), and then select **Add module**.
1. In the **Select modules** dialog box, select **Warehouse and store locator**, and then select **OK**.
1. In the module properties pane, set **Entry point** to **Top ribbon**.
1. Configure the heading, trigger text, search radius, filters, and other properties as required.
1. To display a map, add an Azure Maps module or Map module to the locator's **Map** slot.
1. Select **Save**, select **Finish editing** to check in the fragment, and then select **Publish**.

## Add the module to a PDP

Add the module to the buy box fragment used by PDP templates to show product availability across legal entities.

1. In Commerce site builder, go to **Fragments**, and open the buy box fragment used by the site's PDP template.
1. Select the buy box module.
1. In the **Warehouse locator** slot, select the ellipsis (**...**), and then select **Add module**.
1. In the **Select modules** dialog box, select **Warehouse and store locator**, and then select **OK**.
1. In the module properties pane, set **Entry point** to **Product detail page**.
1. Configure the heading, trigger text, search radius, filters, and other properties as required.
1. To display a map, add an Azure Maps module or Map module to the locator's **Map** slot.
1. Select **Save**, select **Finish editing** to check in the fragment, and then select **Publish**.

> [!NOTE]
> Add the warehouse and store locator module directly to the buy box module's **Warehouse locator** slot. You don't need to create a separate locator fragment.

## Configure a map

The map is optional. If you don't add a map module, the locator displays the location results as a list.

You can add one of the following modules to the locator's **Map** slot:

- **Azure Maps** – Uses the channel's Azure Maps configuration.
- **Map** – Uses the channel's Bing Maps configuration.

The map plots the locations currently shown in the result list. A location that doesn't have valid latitude and longitude values remains in the list but isn't plotted on the map.

For Azure Maps, configure the API key in Commerce headquarters and allow the required Azure Maps URLs in the site's content security policy (CSP). Learn more in [Azure Maps integration](store-selector.md#azure-maps-integration) and [Content security policy](dev-itpro/manage-csp.md).

## Phase 1 behavior and limitations

In Commerce version 10.0.50, the warehouse and store locator module has the following behavior and limitations:

- It supports B2B online channels only.
- The header entry point displays locations without product inventory.
- The PDP entry point displays inventory for the selected product or variant.
- It can display stores and warehouses from multiple legal entities that are included in the configured fulfillment group.
- It doesn't let buyers set a warehouse or store as the order fulfillment source.
- It doesn't reserve inventory or route orders across legal entities.
- It doesn't change tax, financial, intercompany, or order orchestration processes.

## Related information

- [Apply inventory settings](inventory-settings.md)
- [Buy box module](add-buy-box.md)
- [Header module](author-header-module.md)
- [Store selector module](store-selector.md)
- [Azure Maps module](azure-maps-module.md)
- [Set up fulfillment groups](customer-orders-overview.md#set-up-fulfillment-groups)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
