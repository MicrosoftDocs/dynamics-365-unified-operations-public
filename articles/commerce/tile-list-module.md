---
title: Tile list module
description: This article covers tile list modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
ms.date: 07/31/2024
ms.topic: how-to
audience: Application User
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---

# Tile list module

[!include [banner](includes/banner.md)]

This article covers tile list modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.

A tile list module is a collection of tiles in a carousel. It's used to market product categories or product brands through images and text. For example, a retailer can add a tile list module to the home page of an e-commerce site to promote all the top-selling categories.

The tile list module is driven by data from the content management system (CMS). It doesn't depend on any other modules or data from Commerce headquarters. The tile list module can be added to any site page where a retailer wants to market or promote something (for example products, categories, or brands).

The following illustration shows an example of a tile list module and tile modules on the Adventure Works home page.

![Example of a tile list module and tile modules on the Adventure Works home page](./media/Tile_list.PNG)

> [!IMPORTANT]
> The tile list module is available as of the Dynamics 365 Commerce version 10.0.20 release.
> The tile list module is showcased in the Adventure Works theme.

## Tile list modules and themes

The tile list module can support various layouts and styles, based on a theme. For example, in the Adventure Works theme, tiles show an animation effect when site users hover over them. Each theme can contain additional properties for the tile list and tile modules. Theme developers can also build additional layouts for the tile list and tile modules.

## Tile list module properties

| Property name | Values | Description |
|---------------|--------|-------------|
| Heading       | Heading text and heading tag | A text heading for the tile list module. |

## Tile module properties

| Property name | Values | Description |
|---------------|--------|-------------|
| Image         | Image file | An image can be used to showcase a product or a category. The image can be uploaded to the Media Library in Commerce site builder, or an existing image can be used. |
| Heading       | Heading text and heading tag (**H1**, **H2**, **H3**, **H4**, **H5**, or **H6**) | By default, the **H2** heading tag is used for the heading, but the tag can be changed to meet accessibility requirements. |
| Paragraph     | Paragraph text | The module supports paragraph text in rich text format. Some basic rich text capabilities are supported, such as hyperlinks, and bold, underlined, and italic text. Some of these capabilities can be overridden by the page theme that is applied to the module. |
| Link          | Link text, link URL, Accessible Rich Internet Applications (ARIA) label, and **Open link in new tab** | Modules support one or more "call to action" links. If a link is added, link text, a URL, and an ARIA label are required. ARIA labels should be descriptive, to meet accessibility requirements. Links can be configured so that they are opened on a new tab. |
| Tile link     | Link text, link URL, ARIA label, and **Open link in new tab** selector | This property is used to define a "call to action" link. If a link is added, link text, a URL, and an ARIA label are required. ARIA labels should be descriptive, to meet accessibility requirements. Links can be configured so that they are opened on a new tab.|
| Icon          | Image | In addition to a product or category image, an icon symbol can be added. The icon symbol image will appear above the product or category image. |

## Add a tile list module to a new page

To add a tile list module to a new page and set the required properties, follow these steps.

1. Go to **Templates**, and open the marketing template for your site's home page (or create a new marketing template).
1. In the **Main** slot of the default page, select the ellipsis (**...**), and then select **Add module**.
1. In the **Select modules** dialog box, select the **Tile list** module, and then select **OK**.
1. Select **Save**, select **Finish editing** to check in the template, and then select **Publish** to publish it.
1. Go to **Pages**, and open the site's home page (or create a new home page by using the marketing template).
1. In the **Main** slot of the default page, select the ellipsis button (**...**), and then select **Add module**.
1. In the **Select modules** dialog box, select the **Tile list** module, and then select **OK**.
1. In the property pane of the tile list module, add a heading.
1. In the **Tile list** slot, select the ellipsis button (**...**), and then select **Add module**.
1. In the **Select modules** dialog box, select the **Tile module** module, and then select **OK**.
1. In the property pane of the tile module, add an image, a heading, and an icon symbol image.
1. Add and configure additional tile modules as you require.
1. Select **Save**, and then select **Preview** to preview the page.
1. Select **Finish editing** to check in the template, and then select **Publish** to publish it.

## Additional resources

[Module library overview](starter-kit-overview.md)

[Adventure Works theme](adventure-works-theme.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
