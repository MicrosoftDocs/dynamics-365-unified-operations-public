---

# required metadata

title: Map module
description: This topic covers the Map module and describes how to add it to site pages in Microsoft Dynamics 365 Commerce.
author:  anupamar-ms
manager: annbe
ms.date: 03/19/2020
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
ms.dyn365.ops.version:

---

# Map module

[!include [banner](includes/banner.md)]

This topic covers the Map module and describes how to add it to site pages in Microsoft Dynamics 365 Commerce.

## Overview

A Map module visually displays the location of the stores in an interactive map.  This module uses the Bing Maps V8 Web Control to render a map.  A Bing Maps API key is required and must be added to the Commerce shared parameters page in Dynamics 365 Commerce. THe map module provides different views such as Road, Aerial, Streetside etc which the user can choose to view the locations. The map allows interactions such as zoom in and out, locate me in the map etc. These are capabilities provided by the Bing Maps V8 web control.

It works in conjunction with the Store selector module to determine the location where stores need to be rendered. Store selector and Map module interact with each other when a user selects a store on either of them.

The module can be extended for other scenarios outside Store selector but will require a customization.

Below is an example of the module used in a Store locations page.
()


## Module properties

| Property name             | Value                 | Description |
|---------------------------|-----------------------|-------------|
| Heading| Text| Heading for the module|



## Add a map module to a page

See [Store selector module](store-selector.md) for details on how to configure Maps module on a page
 
## Additional resources

[Starter kit overview](starter-kit-overview.md)

[Buy box module](add-buy-box.md)

[Cart module](add-cart-module.md)

[Store selector module](store-selector.md)

[Manage Bing Maps for your organization](dev-itpro/manage-bing-maps.md)



