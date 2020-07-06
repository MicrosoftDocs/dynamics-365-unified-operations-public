---

# required metadata

title: IFrame module
description: This topic covers the IFrame module and describes how to add it to site pages in Microsoft Dynamics 365 Commerce.
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

# IFrame module

[!include [banner](includes/banner.md)]

This topic covers the IFrame module and describes how to add it to site pages in Microsoft Dynamics 365 Commerce.

## Overview

A IFrame module provies an iframe to host external content on a site. For instance, it can be used to host a youtube video or a pdf viewer on any site page. 

It requires the destination URL to be provided and hosts whatever content in the URL within an iframe. Its required that the external URLs are whitelisted per the [Content security policy](manage-csp.md). For IFrame content, the URLs should be whitelisted under **frame-ancestor**.

This is an example of an IFrame module on a page showcasing some external videos
![Example of IFrame module](./media/ecommerce-iframe.PNG)

## IFrame module properties

| Property name             | Value                 | Description |
|---------------------------|-----------------------|-------------|
| Heading| Text| Heading for the module|
| Target Url| Url to be hosted within the module|
| Height| Number or percentage| Height of the module can  defined in pixels or percentage. A number "100" will be treated as pixels and 100% will be treated as percentage |
| Aria label| Text| An aria label can be defined for accessibilty purposes |

## Add an IFrame module to a page

To use the module to display available stores for a Store locations page, follow the below steps
 1. Go to **Templates**, and create a page template that is named **Marketing template**.
1. In the **Main** slot of the default page, dont add any modules.
1. Select **Save**, select **Finish editing** to check in the template, and then select **Publish** to publish it.
1. Create a new page **Marketing page** using the Marketing template.
1. Add a Container and set Width=Fill Container
1. Add an IFrame module to the container. 
1. 1. Select **Save**, select **Finish editing** to check in the template, and then select **Publish** to publish it.
1. Go to the Marketing page and you should see the YouTube video rendered in the IFrame. 
 
## Additional resources

[Starter kit overview](starter-kit-overview.md)

[Content security policy](manage-csp.md)




