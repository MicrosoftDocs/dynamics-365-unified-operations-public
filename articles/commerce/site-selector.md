---
# required metadata

title: Site selector module
description: This topic covers the site selector module and describes how to add it to site pages in Microsoft Dynamics 365 Commerce.
author:  anupamar-ms
manager: annbe
ms.date: 10/20/2020
ms.topic: article
ms.prod:
ms.service: dynamics-365-commerce
ms.technology:

# optional metadata
# ms.search.form:
# ROBOTS:
audience: Application User
# ms.devlang:
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt\_pltfrm:
ms.custom:
ms.assetid:
ms.search.region: Global
ms.search.industry:
ms.author: anupamar
ms.search.validFrom: 2020-02-10
ms.dyn365.ops.version: Release 10.0.13

---

# Site selector module

[!include [banner](includes/banner.md)]

This topic covers the site selector module and describes how to add it to site pages in Microsoft Dynamics 365 Commerce.

## Overview

When a business has different sites across markets, regions, and locales, site users need an easy way to switch between sites and select their preferred shopping site. To accommodate this scenario, the site selector module lets users browse across multiple sites.

The site selector module must be configured with the list of sites (markets, regions, or locales) that site users can browse.

> [!NOTE]
> The site selector module is available in the Dynamics 365 Commerce 10.0.14 release.

The following illustration shows an example of a site selector module that is featured in the header of a site page.

![Example of a site selector module in the header of a site page](./media/ecommerce-sitepicker.PNG)

## Site selector module properties

| Property name | Value                 | Description |
|---------------|-----------------------|-------------|
| Heading       | Text                  | The heading for the module. |
| Site options  | Name, Image, URL      | This property specifies a name, a link to the site's home page, and an optional image to show for each site that is included in the module. The image can be a flag, or some representation of a market, region, or locale. |

## Add a site selector module to a page

The site selector module can be added to the [Header module](author-header-module.md) under the site selector slot. After it's added, you can define the module heading and site options.

## Additional resources

[Module library overview](starter-kit-overview.md)

[Header module](author-header-module.md)

[Breadcrumb module](add-breadcrumb.md)

[Navigation menu module](nav-menu-module.md)
