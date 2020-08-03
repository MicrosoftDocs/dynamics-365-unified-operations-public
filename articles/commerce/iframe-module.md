---
# required metadata

title: Iframe module
description: This topic covers the iframe module and describes how to add it to site pages in Microsoft Dynamics 365 Commerce.
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
ms.dyn365.ops.version: Release 10.0.13

---

# Iframe module

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This topic covers the iframe module and describes how to add it to site pages in Microsoft Dynamics 365 Commerce.

## Overview

An iframe module provides an iframe (inline frame) that hosts external content on a site. For example, it can be used to host a YouTube video or a PDF file viewer on any site page. 

An iframe module requires a target URL. It then hosts the content of the target page inside an HTML **iframe** element. External URLs must be on the allow list (also known as a "whitelist") per the site's content security policy (CSP) directives. For iframe content, URLs should be allowed by using the **frame-ancestor** directive. For more information, see [Manage Content Security Policy (CSP)](manage-csp.md).

The following image shows examples of iframe modules that showcase external videos on site pages.

![Example of iframe modules that showcase external videos](./media/ecommerce-iframe.PNG)

## Iframe module properties

| Property name             | Value                 | Description |
|---------------------------|-----------------------|-------------|
| Heading | Text | The heading for the module. |
| Target URL | URL | The URL that is hosted in the module. |
| Height | Number or percentage | The height of the module, in pixels or as a percentage. For example, the value **100** will be treated as a number of pixels, and the value **100%** will be treated as a percentage. |
| Aria label | Text | An Accessible Rich Internet Applications (ARIA) label can be defined for accessibility purposes. |

## Add an iframe module to a page

To add an iframe module to a page to show an external video, follow these steps.

1. Go to **Templates**, and select **New** to create a new template.
1. In the **New Template** dialog box, under **Template name**, enter **Marketing template**, and then select **OK**.
1. Select **Save**, select **Finish editing** to check in the template, and then select **Publish** to publish it.
1. Go to **Pages**, and select **New** to create a new page.
1. In the **Choose a template** dialog box, select the **Marketing template** template. Under **Page name**, enter **Marketing page**, and then select **OK**.
1. In the **Main** slot of the new page, select the ellipsis (**...**), and then select **Add Module**.
1. In the **Add Module** dialog box, select the **Container** module, and then select **OK**.
1. In the module's properties pane, set the **Width** value to **Fill Container**.
1. In the **Container** slot, select the ellipsis (**...**), and then select **Add Module**.
1. In the **Add Module** dialog box, select the **iframe** module, and then select **OK**.
1. In the module's properties pane, set the **Target URL** value to an external URL for a video.
1. Set other properties, such as **Heading** and **Height**, as you require.
1. Select **Save**, select **Finish editing** to check in the page, and then select **Publish** to publish it.
1. Go to the marketing page on your site. You should see that the video is rendered in the iframe module.
 
## Additional resources

[Starter kit overview](starter-kit-overview.md)

[Manage Content Security Policy (CSP)](manage-csp.md)
