---
title: Azure Maps module
description: Learn how to configure the Azure Maps module in Microsoft Dynamics 365 Commerce.
author: giripriya-v
ms.date: 09/02/2025
ms.topic: how-to
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: giripriyav
ms.search.validFrom: 2025-04-25
ms.custom:
  - bap-template
---

# Azure Maps Module

[!include [banner](includes/banner.md)]

This article explains how to configure the Azure Maps module in Microsoft Dynamics 365 Commerce.

The Azure Maps module shows the locations of stores on an interactive map that's rendered by using the [Azure Maps map control](/azure/azure-maps/how-to-use-map-control). An Azure Maps API key is required and must be added to the shared parameters page in Commerce headquarters. The Azure Maps module provides different views such as Road, Aerial, and Streetside that users can select to view map locations. The Azure Maps module also allows for interactions such as zooming in and out and using the user's location.

The Azure Maps module works with the store selector module to determine the geographic locations of stores that must be rendered on a map. The store selector and Azure Maps modules interact when a user selects a store in one of those modules on a site page. The Azure Maps module can be customized and extended for scenarios other than interaction with store selector modules.

> [!NOTE]
> The Azure Maps module is available as of the Dynamics 365 Commerce version 10.0.45 release.

The following image shows an example of an Azure Maps module used on a store locations page.

![Example of a store selector module.](./media/store-locator-azure.PNG)

## Module properties

| Property name             | Value                 | Description |
|---------------------------|-----------------------|-------------|
| Heading | Text | The heading for the module. |
| Pushpin options: Size | Number | Specifies the size of pushpin. |
| Pushpin options: Default icon color | Character string | The text or hexadecimal value for the color of pushpin symbols on a map. |
| Pushpin options: Selection icon color | Character string | The text or hexadecimal value for the color of selected pushpin symbols on a map. |
| Show index | **True** or **False** | If this property is set to **True**, every pushpin symbol that indicates a store shows an index. This index matches the index in the list view that the store selector module displays. |

## Add allowed mapping URLs to a site's content security policy (CSP) directives

For the Azure Maps module to interact with Azure Maps, you must ensure that the following mapping URLs are allowed per your site's content security policy (CSP). This setup is done in Commerce site builder, by adding allowed URLs to various site CSP directives (for example, **img-src**). Learn more in [Content security policy](dev-itpro/manage-csp.md).
- To the **child-src** directive, add "blob:".  
- To the **connect-src** directive, add `https://atlas.microsoft.com/` and `https://js.monitor.azure.com/`.
- To the **font-src** directive, add `https://atlas.microsoft.com/`.
- To the **script-src** directive, add `https://atlas.microsoft.com/`.
- To the **style-src** directive, add `https://atlas.microsoft.com/`.

## Add a map module to a page

For detailed information about how to configure The Azure Maps module on a page, see [Store selector module](store-selector.md).
 
## Additional resources

[Module library overview](starter-kit-overview.md)

[Buy box module](add-buy-box.md)

[Cart module](add-cart-module.md)

[Store selector module](store-selector.md)

[Manage Azure Maps for your organization](./dev-itpro/manage-azure-maps.md)

[Azure Maps map control](/azure/azure-maps/how-to-use-map-control)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
