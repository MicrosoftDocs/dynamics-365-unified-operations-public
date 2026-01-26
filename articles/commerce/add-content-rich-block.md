---
title: Text block module
description: Learn about text block modules and how to add them to site pages in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
ms.date: 01/14/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---

# Text block module

[!include [banner](includes/banner.md)]

This article covers text block modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.

Use a text block module to add textual content. This content can be informational or promotional.

Text block modules use data from the content management system (CMS) and can be added to any page. They're stand-alone modules that don't depend on page context or any other modules.

## Examples of text block modules in e-commerce

Use text block modules in the following ways:

* Showcase product features on a product details page.
* Provide informational content on any page. For example, they can explain the benefits of loyalty programs, describe shipping and return policies, answer frequently asked questions, or provide "about us" content.
* Add custom messages on a product details page. For example, "Free shipping for orders over $50."
* Provide disclaimers and contact details on product details pages, cart pages, checkout pages, and other pages. For example, "Shipping and returns are subject to store policies."

The following image shows an example of a text block module that's used on a home page.

:::image type="content" source="./media/ecommerce-textblock.PNG" alt-text="Screenshot of a text block module.":::

## Text block module properties

| Property name     | Value                                            | Description |
|-------------------|--------------------------------------------------|-------------|
| Rich text         | Rich text                                        | Paragraph text. Some basic rich text capabilities are supported, such as bold, underlined, and italic text. |
| Custom class name | A Cascading Style Sheets (CSS) class name        | The name of a custom CSS class that a developer provides to format this module. Define the class name in the theme pack. |
| Font size         | **Small**, **Medium**, **Large**, or **X-Large** | The font size of the content. |

## Add a text block module to a page

To add a text block module to a new page and set the required properties, follow these steps:

1. Go to **Templates**, and select **New** to create a new template.
1. In the **New template** dialog box, under **Template name**, enter **Content template**.
1. In the **Body** slot, select the ellipsis (**...**), and then select **Add module**.
1. In the **Select modules** dialog box, select the **Default page** module, and then select **OK**.
1. Select **Save**, select **Finish editing** to check in the template, and then select **Publish** to publish it.
1. Go to **Pages**, and select **New** to create a new page.
1. In the **Create a new page** dialog box, under **Page name**, enter **Content page**, and then select **Next**.
1. Under **Choose a template**, select **Content template**, and then select **Next**.
1. Under **Choose a layout**, select a page layout (for example, **Flexible layout**), and then select **Next**.
1. Under **Review and finish**, review the page configuration. If you need to edit the page information, select **Back**. If the page information is correct, select **Create page**.
1. In the **Main** slot of the new page, select the ellipsis (**...**), and then select **Add module**.
1. In the **Select modules** dialog box, select the **Container** module, and then select **OK**.
1. In the property pane for the container module, set the **Width** property to **Fill container**.
1. In the **Container** slot, select the ellipsis (**...**), and then select **Add module**.
1. In the **Select modules** dialog box, select the **Text block** module, and then select **OK**.
1. In the property pane of the text block module, add text to the **Rich text** field.
1. Select **Save**, and then select **Preview** to preview the page.
1. Select **Finish editing** to check in the page, and then select **Publish** to publish it.

## Additional resources

[Module library overview](starter-kit-overview.md)

[Promo banner module](add-alert.md)

[Carousel module](add-carousel.md)

[Content block module](add-hero-module.md)

[Video player module](add-video-player.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
