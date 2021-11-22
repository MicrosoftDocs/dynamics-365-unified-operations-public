---
# required metadata

title: Text block module
description: This topic covers text block modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
ms.date: 09/15/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
ms.search.industry: 
ms.author: anupamar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---
# Text block module

[!include [banner](includes/banner.md)]

This topic covers text block modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.

A text block module is a module that is used to add textual content. This content can be informational or promotional.

Text block modules are driven by data from the content management system (CMS) and can be put on any page. They are stand-alone modules that don't depend on page context or any other modules.

## Examples of text block modules in e-Commerce

Text block modules can be used in the following ways:

* To showcase product features on a product details page.
* For informational purposes on any page. For example, they can explain the benefits of loyalty programs, describe shipping and return policies, answer frequently asked questions, or provide "about us" content.
* To add custom messages on a product details page. (for example, "Free shipping for orders over $50").
* For disclaimers and contact details on product details pages, cart pages, checkout pages, and other pages (for example, "Shipping and returns are subject to store policies").

The following image shows an example of a text block module that is used on a home page.

![Example of a text block module.](./media/ecommerce-textblock.PNG)

## Text block module properties

| Property name     | Value                                            | Description |
|-------------------|--------------------------------------------------|-------------|
| Rich text         | Rich text                                        | Paragraph text. Some basic rich text capabilities are supported, such as bold, underlined, and italic text. |
| Custom class name | A Cascading Style Sheets (CSS) class name        | The name of a custom CSS class that a developer provides to format this module. The class name should be defined in the theme pack. |
| Font size         | **Small**, **Medium**, **Large**, or **X-Large** | The font size of the content. |

## Add a text block module to a page

To add a text block module to a new page and set the required properties, follow these steps.

1. Go to **Templates**, and select **New** to create a new template.
1. In the **New Template** dialog box, under **Template name**, enter **Content template**.
1. In the **Body** slot, select the ellipsis (**...**), and then select **Add Module**.
1. In the **Add Module** dialog box, select the **Default page** module, and then select **OK**.
1. Select **Save**, select **Finish editing** to check in the template, and then select **Publish** to publish it.
1. Go to **Pages**, and select **New** to create a new page.
1. In the **Choose a template** dialog box, select **Content template**. Under **Page name**, enter **Content page**, and then select **OK**.
1. In the **Main** slot of the new page, select the ellipsis (**...**), and then select **Add Module**.
1. In the **Add Module** dialog box, select the **Container** module, and then select **OK**.
1. In the property pane for the container module, set the **Width** property to **Fill container**.
1. In the **Container** slot, select the ellipsis (**...**), and then select **Add Module**.
1. In the **Add Module** dialog box, select the **Text block** module, and then select **OK**. 
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