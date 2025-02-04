---
title: Map module
description: This article covers map modules and describes how to configure them in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
ms.date: 08/01/2024
ms.topic: how-to
audience: Application User
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2020-02-10
ms.custom: 
  - bap-template
---

# Map module

[!include [banner](includes/banner.md)]


This article covers map modules and describes how to configure them in Microsoft Dynamics 365 Commerce.

A map module shows the locations of stores on an interactive map that is rendered by using the [Bing Maps V8 Web Control](/bingmaps/v8-web-control/). A Bing Maps API key is required and must be added to the shared parameters page in Commerce headquarters. Map modules provide different views, such as Road, Aerial, and Streetside, that users can select to view map locations. They also allow for interactions such as zooming and using the user's location.

A map module works in conjunction with the store selector module to determine the geographic locations of stores that must be rendered on a map. Store selector and map modules interact when a user selects a store in one of those modules on a site page. Map modules can be extended for other scenarios, beyond interaction with store selector modules. However, module customization is required.

> [!NOTE]
> The map module is available in the Dynamics 365 Commerce 10.0.13 release.

The following image shows an example of a map module that is used on a store locations page.

![Example of a store selector module.](./media/ecommerce-Storelocator.PNG)

## Module properties

| Property name             | Value                 | Description |
|---------------------------|-----------------------|-------------|
| Heading | Text | The heading for the module. |
| Pushpin options: Default icon | Image | The pushpin symbol image to use for stores that are shown on a map. |
| Pushpin options: Active icon | Image | The pushpin symbol image to use for a store that is selected on a map. |
| Pushpin options: Default icon color | Character string | The text or hexadecimal value for the color of pushpin symbols on a map. |
| Pushpin options: Active icon color | Character string | The text or hexadecimal value for the color of selected pushpin symbols on a map. |
| Show index | **True** or **False** | If this property is set to **True**, every pushpin symbol that indicates a store will show an index. This index will match the index in the list view that the store selector module shows. |

## Add allowed mapping URLs to a site's content security policy directives

For the maps module to interact with Bing Maps, you must ensure that the following mapping URLs are allowed per your site's content security policy (CSP). This setup is done in Commerce site builder, by adding allowed URLs to various site CSP directives (for example, **img-src**). For more information, see [Content security policy](dev-itpro/manage-csp.md). 

- To the **connect-src** directive, add **&#42;.bing.com**.
- To the **img-src** directive, add **&#42;.virtualearth.net**.
- To the **script-src** directive, add **&#42;.bing.com, &#42;.virtualearth.net**.
- To the **script style-src** directive, add **&#42;.bing.com**.

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
