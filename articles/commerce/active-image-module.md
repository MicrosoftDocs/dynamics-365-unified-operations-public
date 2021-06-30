---
# required metadata

title: Active image module
description: This topic covers active image modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
ms.date: 06/30/2021
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
ms.dyn365.ops.version: Release 10.0.8

---
# Active image module

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This topic covers active image modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.

An active image module can be used to embed an image with product tags that e-commerce site users can hover over to preview products shown in the image. When users select a preview popup, they can directly navigate to the product details page (PDP) of that product. 

The tags are defined using X and Y coordinates on the image. Each tagged point should be configured with the product ID of the respective product that is shown on the image.

The following example image shows an active image preview popup on an Adventure Works home page hero image.

![Example of a active image module preview popup](./media/Active_image.PNG)

>[!IMPORTANT]
> - The active image module is available as of the Dynamics 365 Commerce version 10.0.20 release.
> - The active image module is showcased in the Adventure Works theme.

## Active image module properties

| Property name  | Values | Description |
|----------------|--------|-------------|
| Image          | Image file | An image can be used to showcase one or more products. The image can be uploaded to the Commerce site builder Media Library, or an existing image can be used. |
|Width| Pixels| This property defines the width of the image. The active coordinates are calculated based on the width of the image.|
|Active coordinates| X and Y coordinates, product ID number.| Each active image array consists of X and Y coordinates and the product ID number.|
| Heading        | Heading text and heading tag (**H1**, **H2**, **H3**, **H4**, **H5**, or **H6**) | By default, the **H2** heading tag is used for the heading, but the tag can be changed to meet accessibility requirements. |
| Paragraph      | Paragraph text | The module supports paragraph text in rich text format. Some basic rich text capabilities such as hyperlinks and bolded, underlined, and italicized text are supported. Some of these capabilities can be overridden by the page theme that is applied to the module. |
| Link           | Link text, link URL, Accessible Rich Internet Applications (ARIA) label, and **Open link in new tab** selector. | Supports one or more "call to action" links. If a link is added, link text, a URL, and an ARIA label are required. ARIA labels should be descriptive to meet accessibility requirements. Links can be configured to open in a new tab. |
| Sub text|  Heading, text, links| Additional context for the image can be added, for example an author or designer name, or links to personal blogs.|
|Text theme| **Light** or **Dark**| This property allows a user to set the text to light or dark based on the background image, and is available as a theme extension in the Adventure Works theme. |

## Add an active image module to a new page

To add an active image module to a new page and set the required properties, follow these steps.

1. Go to **Templates** and open your site's home page marketing template (or create a new one).
1. In the **Main** slot of the default page, select the ellipsis (...), and then select **Add Module**.
1. In the **Add Module** dialog box, select the **Active image** module, and then select **OK**.
1. Select **Save**, select **Finish editing** to check in the template, and then select **Publish** to publish it.
1. Go to **Pages** and open the site home page (or create a new one using the marketing template).
1. In the **Main** slot of the default page, select the ellipsis button (**...**), and then select **Add Module**.
1. In the **Add Module** dialog box, select the **Active image** module, and then select **OK**.
1. In the property pane of the active image module, add an image and set the canvas width to the size of the image.
1. In the property panel of the active image module, set the X and Y coordinates and add the respective product ID number.
1. Add and configure additional active image modules as needed.
1. Select **Save**, and then select **Preview** to preview the page.
1. Select **Finish editing** to check in the template, and then select **Publish** to publish it. 

## Additional resources

[Module library overview](starter-kit-overview.md)

[Adventure Works theme](adventure-works-theme.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]

