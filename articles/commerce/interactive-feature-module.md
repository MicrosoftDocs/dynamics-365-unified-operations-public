---
# required metadata

title: Interactive feature module 
description: This topic covers interactive feature modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.
author:  anupamar-ms
ms.date: 06/24/2021
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

# Interactive Feature

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This topic covers interactive feature modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.

Interactive feature modules are mosaic-like modules that can be used to market multiple product categories or product brands using a combination of images and text. For example, a retailer can add an interactive feature module to the home page of an e-Commerce site to promote all the top-selling categories. Its similar to Tile List module but has different layout and interaction model.

Interactive feature module is a collection of interactive feature item modules. Each feature item module is driven by data from the content management system (CMS) and doesn't depend on any other modules or data from the backoffice. It can be added to put on any site page where a retailer wants to market or promote something (for example, products, categories, brands etc).

>[!IMPORTANT]
> - The interactive feature module is available as of the Dynamics 365 Commerce version 10.0.20 release.
> - The interactive feature module is included in the Adventure Works theme.

The following example image shows an interactive feature module on the Adventure Works home page.

![Example showing an interactive feature module on the Adventure Works home page](./media/Feature.PNG)

## Interactive feature module and themes

Interactive Feature module can support various layouts and styles based on a theme. For example, the Adventure works theme, the Interactive feature has a 2-column layout with an animation effect when user hovers on each item.  The module is optimized for an even number of images that are shown on a 2-column layout. 

## Interactive feature module properties

| Property name  | Values | Description |
|----------------|--------|-------------|
|Heading| Heading text, Heading tag| This property is used to set a heading for the Interactive Feature |

## Interactive feature item module properties

| Property name  | Values | Description |
|----------------|--------|-------------|
| Image          | Image file | An image can be used to showcase a product or a category. The image can be uploaded to the image gallery, or an existing image can be used. |
| Heading        | Heading text and heading tag (**H1**, **H2**, **H3**, **H4**, **H5**, or **H6**) | By default, the **H2** heading tag is used for the heading, but the tag can be changed to meet accessibility requirements. |
| Paragraph      | Paragraph text | The module supports paragraph text in rich text format. Some basic rich text capabilities such as hyperlinks and bolded, underlined, and italicized text are supported. Some of these capabilities can be overridden by the page theme that is applied to the module. |
| Link           | Link text, link URL, Accessible Rich Internet Applications (ARIA) label, and **Open link in new tab** selector. | Supports one or more "call to action" links. If a link is added, link text, a URL, and an ARIA label are required. ARIA labels should be descriptive to meet accessibility requirements. Links can be configured to open in a new tab. |

## Add an interactive feature module to a new page

To add a interactive feature module to a new page and set the required properties in Commerce site builder, follow these steps.

1. Go to **Templates**, and open **Marketing template** which is used for the home page (or create a new one)
1. In the **Main** slot of the default page, add Interactive Feature module.
1. Select **Save**, select **Finish editing** to check in the template, and then select **Publish** to publish it.
1. Open the site Home page (or create a new one)
1. In the **Main** slot of the default page, select the ellipsis button (**...**), and then select **Add Module**.
1. In the **Add Module** dialog box, under **Select Modules**, select the Interactive Feature, and then select **OK**.
1. In the module property panel of Interactive Feature module, set a Heading
1. To the Interactive Feature module, add Interactive Feature Item module from the module outline
1. In the property panel for Interactive Feature Item module, add an Image, Heading, Paragraph and Link.
1. Repeat the above steps and continue adding more Interactive Feature Item modules to Interactive Feature
1. Select **Save**, and then select **Preview** to preview the page.
1. Select **Finish editing** to check in the template, and then select **Publish** to publish it. 

## Additional resources

[Module library overview](starter-kit-overview.md)

[Adventure Works theme](adventure-works-theme.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
