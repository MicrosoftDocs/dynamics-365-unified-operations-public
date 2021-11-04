---
# required metadata

title: Content block module 
description: This topic covers content block modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.
author:  anupamar-ms
ms.date: 09/15/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: 
ms.author: anupamar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: 
---

# Content block module

[!include [banner](includes/banner.md)]

This topic covers content block modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.

A content block module is used to market products or promotions through a combination of images and text. For example, a retailer can add a content block module to the home page of an e-Commerce site to promote a new product and attract the attention of customers.

A content block module is driven by data from the content management system (CMS). It's a stand-alone module that doesn't depend on any other modules on the page. A content block module can be put on any site page where a retailer wants to market or promote something (for example, products, sales, or features).

## Examples of content block module in e-Commerce

- A content block module can be used on the home page of an e-Commerce site to highlight promotions and new products.
- A content block module can be used on a product details page to showcase product information.
- Multiple content block modules can be put inside a carousel module to highlight multiple products or promotions.

## Content block modules and themes

Content block modules can support various layouts and styles based on a theme. For example, the Fabrikam theme supports three layout variations of a content block module: hero, feature, and tile. The hero layout shows an image on the background with text overlay. The feature layout shows an image and text side by side. The tile layout allows multiple content blocks in a tile format.

In addition, the theme can expose different properties for each layout. A theme developer can build more layouts with more styles using the content block module.

The following image shows an example of a content block module with a hero layout.

![Example of a hero module.](./media/Hero.PNG)

The following image shows an example of a content block module with a feature layout.

![Examples of feature modules.](./media/Feature.PNG)

## Content block module properties

| Property name  | Values | Description |
|----------------|--------|-------------|
| Image          | Image file | An image can be used to showcase a product or a promotion. An image can be uploaded to the image gallery, or an existing image can be used. |
| Heading        | Heading text and heading tag (**H1**, **H2**, **H3**, **H4**, **H5**, or **H6**) | Every hero module can have a heading. By default, the **H2** heading tag is used for the heading. However, the tag can be changed to meet accessibility requirements. |
| Paragraph      | Paragraph text | Hero modules support paragraph text in rich text format. Some basic rich text capabilities are supported, such as bold, underlined, and italic text, and hyperlinks. Some of these capabilities can be overridden by the page theme that is applied to the module. |
| Link           | Link text, link URL, Accessible Rich Internet Applications (ARIA) label, and **Open link in new tab** | Hero modules support one or more "call to action" links. If a link is added, link text, a URL, and an ARIA label are required. ARIA labels should be descriptive to meet accessibility requirements. Links can be configured so that they are opened on a new tab. |

## Content block module properties exposed by the Fabrikam theme 

| Property name  | Values | Description |
|----------------|--------|-------------|
| Text placement | **Left**, **Right**, **Center** | This property defines the position of the text on the image. It only applies to the hero layout. |
| Text theme     | **Light** or **Dark** | A color scheme can be defined for the text, based on the background image. For example, if the image has a dark background, a light theme can be applied to make the text more visible and to meet color contrast ratios for accessibility purposes. It only applies to the hero layout.|
| Image placement       | **Left**,  **Right** | This property specifies if the image should be to the left or right of the text. It only applies to the feature layout.  |

## Add a content block module to a new page

To add a hero module to a new page and set the required properties, follow these steps.

1. Go to **Templates**, and create a page template that is named **Content block template**.
1. In the **Main** slot of the default page, add a hero module.
1. Select **Save**, select **Finish editing** to check in the template, and then select **Publish** to publish it.
1. Use the hero template that you just created to create a page that is named **Content block page**.
1. In the **Main** slot of the default page, select the ellipsis button (**...**), and then select **Add Module**.
1. In the **Add Module** dialog box, under **Select Modules**, select the hero module, and then select **OK**.
1. In the outline tree on the left, select the content block module.
1. In the properties pane on the right, select **Add an image**. Then either select an existing image or upload a new image.
1. Select **Heading**.
1. In the **Heading** dialog box, add the heading text, select the heading level, and then select **OK**.
1. Under **Rich Text**, add text as you require.
1. Select **Add Link**.
1. In the **Link** dialog box, add link text, a link URL, and an ARIA label for the link, and then select **OK**.
1. Select the **Hero** layout.
1. Select **Save**, and then select **Preview** to preview the page.
1. Select **Finish editing** to check in the template, and then select **Publish** to publish it. 

## Additional resources

[Module library overview](starter-kit-overview.md)

[Promo banner module](add-alert.md)

[Carousel module](add-carousel.md)

[Text block module](add-content-rich-block.md)

[Video player module](add-video-player.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]