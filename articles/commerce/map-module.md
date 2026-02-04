---
title: Map module
description: Learn about map modules and how to configure them in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
ms.date: 01/23/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2020-02-10
ms.custom: 
  - bap-template
---

# Map module

[!include [banner](includes/banner.md)]

This article describes map modules and how to configure them in Microsoft Dynamics 365 Commerce.

> [!IMPORTANT]
> - Bing Maps for Enterprise is deprecated and will be retired. If you have an enterprise license for Bing Maps for Enterprise, you can use it until June 30, 2028. If you have a free or basic license for Bing Maps for Enterprise, you can use it until June 30, 2025.
> - Until Azure Maps becomes available as a module in E-Commerce version 10.0.45, you can manually enable Azure Maps by following the steps provided in the [Dynamics365Commerce.Solutions GitHub repository](https://github.com/microsoft/Dynamics365Commerce.Solutions/tree/release/9.54/src/OnlineSDK/Extensibility%20Samples/AzureMaps).

A map module shows the locations of stores on an interactive map that uses the [Bing Maps V8 Web Control](/bingmaps/v8-web-control/). You need a Bing Maps API key, which you add to the shared parameters page in Commerce headquarters. Map modules provide different views, such as Road, Aerial, and Streetside, that users can select to view map locations. They also allow for interactions such as zooming and using the user's location.

A map module works with the store selector module to determine the geographic locations of stores that appear on the map. Store selector and map modules interact when a user selects a store in one of those modules on a site page. You can extend map modules for other scenarios beyond interaction with store selector modules. However, module customization is required.

> [!NOTE]
> The map module is available in the Dynamics 365 Commerce 10.0.13 release.

The following image shows an example of a map module that is used on a store locations page.

:::image type="content" source="./media/ecommerce-Storelocator.PNG" alt-text="Screenshot of a store selector module on a store locations page.":::

## Module properties

| Property name             | Value                 | Description |
|---------------------------|-----------------------|-------------|
| Heading | Text | The heading for the module. |
| Pushpin options: Default icon | Image | The pushpin symbol image to use for stores that are shown on a map. |
| Pushpin options: Active icon | Image | The pushpin symbol image to use for a store that is selected on a map. |
| Pushpin options: Default icon color | Character string | The text or hexadecimal value for the color of pushpin symbols on a map. |
| Pushpin options: Active icon color | Character string | The text or hexadecimal value for the color of selected pushpin symbols on a map. |
| Show index | **True** or **False** | If you set this property to **True**, every pushpin symbol that indicates a store shows an index. This index matches the index in the list view that the store selector module shows. |

## Add allowed mapping URLs to a site's content security policy directives

For the maps module to interact with Bing Maps, you must ensure that the following mapping URLs are allowed per your site's content security policy (CSP). Commerce site builder is where you set up this configuration. Add allowed URLs to various site CSP directives (for example, **img-src**). For more information, see [Content security policy](dev-itpro/manage-csp.md).

- Add **&#42;.bing.com** to the **connect-src** directive.
- Add **&#42;.virtualearth.net** to the **img-src** directive.
- Add **&#42;.bing.com, &#42;.virtualearth.net** to the **script-src** directive.
- Add **&#42;.bing.com** to the **script style-src** directive.

## Add a map module to a page

For detailed information about how to configure a map module on a page, see [Store selector module](store-selector.md).

## Additional resources

[Module library overview](starter-kit-overview.md)

[Buy box module](add-buy-box.md)

[Cart module](add-cart-module.md)

[Store selector module](store-selector.md)

[Manage Bing Maps for your organization](./dev-itpro/manage-bing-maps.md)

[Bing Maps V8 Web Control](/bingmaps/v8-web-control/)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
