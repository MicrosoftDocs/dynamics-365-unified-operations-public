---
title: Iframe module
description: This article covers the iframe module and describes how to add it to site pages in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
ms.date: 08/02/2024
ms.topic: how-to
audience: Application User
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2020-02-10
ms.custom: 
  - bap-template
---

# Iframe module

[!include [banner](includes/banner.md)]

This article covers the iframe module and describes how to add it to site pages in Microsoft Dynamics 365 Commerce.

An iframe module provides an iframe (inline frame) that hosts external content on a site. For example, it can be used to host a YouTube video or a PDF file viewer on any site page. 

An iframe module requires a target URL. It then hosts the content of the target page inside an HTML **iframe** element. External URLs must be on the allow list per the site's content security policy (CSP) directives. For iframe content, URLs should be allowed by using the **frame-ancestor** directive. For more information, see [Manage Content Security Policy (CSP)](dev-itpro/manage-csp.md).

> [!NOTE]
> The iframe module is available in the Dynamics 365 Commerce 10.0.13 release.

The following image shows examples of iframe modules that showcase external videos on site pages.

![Example of iframe modules that showcase external videos.](./media/ecommerce-iframe.PNG)

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
1. In the **New template** dialog box, under **Template name**, enter **Marketing template**, and then select **OK**.
1. Select **Save**, select **Finish editing** to check in the template, and then select **Publish** to publish it.
1. Go to **Pages**, and select **New** to create a new page.
1. In the **Create a new page** dialog box, under **Page name**, enter **Marketing page**, and then select **Next**.
1. Under **Choose a template**, select the **Marketing template** you created, and then select **Next**.
1. Under **Choose a layout**, select a page layout (for example, **Flexible layout**), and then select **Next**.
1. Under **Review and finish**, review the page configuration. If you need to edit the page information, select **Back**. If the page information is correct, select **Create page**. 
1. In the **Main** slot of the new page, select the ellipsis (**...**), and then select **Add module**.
1. In the **Select modules** dialog box, select the **Container** module, and then select **OK**.
1. In the module's properties pane, set the **Width** value to **Fill Container**.
1. In the **Container** slot, select the ellipsis (**...**), and then select **Add module**.
1. In the **Select modules** dialog box, select the **iframe** module, and then select **OK**.
1. In the module's properties pane, set the **Target URL** value to an external URL for a video.
1. Set other properties, such as **Heading** and **Height**, as you require.
1. Select **Save**, select **Finish editing** to check in the page, and then select **Publish** to publish it.
1. Go to the marketing page on your site. You should see that the video is rendered in the iframe module.

> [!NOTE]
> Because the iframe module hosts external content, site authors must ensure that content hosted within an iframe module does not violate content restriction policies in the respective market. If there is a content violation on a page that uses the iframe module, the site author can remove the iframe module by opening the page in site builder, selecting **Remove module** in the iframe module slot, and then saving and republishing the page.

## Additional resources

[Module library overview](starter-kit-overview.md)

[Manage Content Security Policy (CSP)](dev-itpro/manage-csp.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
