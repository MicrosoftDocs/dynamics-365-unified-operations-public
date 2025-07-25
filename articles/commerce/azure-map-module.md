---
title: Azure Maps module
description: This article covers azure-map module and describes how to configure them in Microsoft Dynamics 365 Commerce.
author: giripriya-v
ms.date: 04/08/2025
ms.topic: how-to
audience: Application User
ms.reviewer:
ms.search.region: Global
ms.author: giripriyav
ms.search.validFrom: 2025-04-25
ms.custom:
  - bap-template
---

# Azure Maps module (Preview)

[!include [banner](includes/banner.md)]


This article covers azure maps module and describes how to configure them in Microsoft Dynamics 365 Commerce.

Azure maps module shows the locations of stores on an interactive map that is rendered by using the [Azure Maps map control](/azure/azure-maps/how-to-use-map-control). An Azure Maps API key is required and must be added to the shared parameters page in Commerce headquarters. Azure Maps module provide different views, such as Road, Aerial, and Streetside, that users can select to view map locations. They also allow for interactions such as zooming and using the user's location.

Azure maps module works in conjunction with the store selector module to determine the geographic locations of stores that must be rendered on a map. Store selector and azure maps modules interact when a user selects a store in one of those modules on a site page. Azure maps module can be extended for other scenarios, beyond interaction with store selector modules. However, module customization is required.

> [!NOTE]
> Azure maps module is available in the Dynamics 365 Commerce 10.0.44 release.

The following image shows an example of a map module that is used on a store locations page.

![Example of a store selector module.](./media/ecommerce-Storelocator-azure.PNG)

## Module properties

| Property name             | Value                 | Description |
|---------------------------|-----------------------|-------------|
| Heading | Text | The heading for the module. |
| Pushpin options: Size | Number | Specifies the size of pushpin. |
| Pushpin options: Default icon color | Character string | The text or hexadecimal value for the color of pushpin symbols on a map. |
| Pushpin options: Selection icon color | Character string | The text or hexadecimal value for the color of selected pushpin symbols on a map. |
| Show index | **True** or **False** | If this property is set to **True**, every pushpin symbol that indicates a store will show an index. This index will match the index in the list view that the store selector module shows. |

## Add allowed mapping URLs to a site's content security policy directives

For the Azure maps module to interact with Azure Maps, you must ensure that the following mapping URLs are allowed per your site's content security policy (CSP). This setup is done in Commerce site builder, by adding allowed URLs to various site CSP directives (for example, **img-src**). For more information, see [Content security policy](dev-itpro/manage-csp.md).
- To the **child-src** directive, add **blob:**.  
- To the **connect-src** directive, add **https://atlas.microsoft.com/** and **https://js.monitor.azure.com/**.
- To the **font-src** directive, add **https://atlas.microsoft.com/**.
- To the **script-src** directive, add **https://atlas.microsoft.com/**.
- To the **style-src** directive, add **https://atlas.microsoft.com/**.

## Add a map module to a page

For detailed information about how to configure azure maps module on a page, see [Store selector module](store-selector.md).
 
## Additional resources

[Module library overview](starter-kit-overview.md)

[Buy box module](add-buy-box.md)

[Cart module](add-cart-module.md)

[Store selector module](store-selector.md)

[Manage Azure Maps for your organization](./dev-itpro/manage-azure-maps.md)

[Azure Maps map control](/azure/azure-maps/how-to-use-map-control)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
