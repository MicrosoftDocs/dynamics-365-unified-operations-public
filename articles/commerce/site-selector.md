---
# required metadata

title: Site selector module
description: This topic covers the Site selector module and describes how to add it to site pages in Microsoft Dynamics 365 Commerce.
author:  anupamar-ms
manager: annbe
ms.date: 09/15/2020
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

This topic covers the Site selector module and describes how to add it to site pages in Microsoft Dynamics 365 Commerce.

## Overview
When a business has different sites across markets, regions, locales etc a shopper needs an easy way to switch between these sites and choose the site of their preference to shop. For this scenario, a Site selector module allows a site user to browse across multiple sites

> [!NOTE]
> The Site selector module is available in the Dynamics 365 Commerce 10.0.14 release.

The following image shows examples of Site selector module featured on the header of the page.
![Example of Site selector module](./media/tbd.PNG)

## Site selector module properties

| Property name             | Value                 | Description |
|---------------------------|-----------------------|-------------|
| Heading | Text | The heading for the module. |
| Site options | Name, Image, Url | For each site that you want to include provide a name, a link to the site home page and an optional image (icon) to be displayed. Icon can be a flag or some represention of the market, region, locale etc|

## Add a Site selector module to a page
Site selector module can be added to the [Header module](author-header-module.md) under the site selector slot. Once added, define a heading and the Site options. 


## Additional resources

[Module library overview](starter-kit-overview.md)

[Header module](author-header-module.md)
