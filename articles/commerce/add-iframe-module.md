---

# required metadata

title: Iframe module
description: This topic covers the Iframe module and describes how to add it to site pages in Microsoft Dynamics 365 Commerce.
author:  anupamar-ms
manager: annbe
ms.date: 07/31/2020
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
[!include [banner](includes/preview-banner.md)]

This topic covers the Iframe module and describes how to add it to site pages in Microsoft Dynamics 365 Commerce.

## Overview

An Iframe module provides an iframe (inline frame) to host external content on a site. For example, it can be used to host a YouTube video or a PDF file viewer on any site page. 

An Iframe module requires a destination URL and then hosts whatever content in on the destination page within an HTML Iframe. The external URLs must be on the allow list (otherwise known as a whitelist) per the site's content security policy (CSP) allowed source URLs. For Iframe content, URLs should be allowed using the "frame-ancestor" directive. For more information, see [Manage Content Security Policy (CSP)](manage-csp.md).

The following image shows an example of an Iframe module on a page showcasing some external videos.

![Example of IFrame module](./media/ecommerce-iframe.PNG)

## Iframe module properties

| Property name             | Value                 | Description |
|---------------------------|-----------------------|-------------|
| Heading| Text| Heading for the module|
| Target Url| Url to be hosted within the module|
| Height| Number or percentage| Height of the module can  defined in pixels or percentage. A number "100" will be treated as pixels and 100% will be treated as percentage |
| Aria label| Text| An aria label can be defined for accessibilty purposes |

## Add an Iframe module to a page

To use an Iframe module to display available stores for a store locations page, follow these steps.

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




