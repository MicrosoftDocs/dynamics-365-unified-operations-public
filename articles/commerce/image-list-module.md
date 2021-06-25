---
# required metadata

title: Image list module
description: This topic covers image list modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
ms.date: 06/25/2021
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

# Image list module

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This topic covers image list modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.

The image list module can be used to easily add a collection of images to site pages. Each image in the array can be configured with paragraph text and link URLs. The image list module is best suited for displaying brand logos or a list with logos.

> [!IMPORTANT]
> - The image list module is available in the Commerce module library as of the Dynamics 365 Commerce version 10.0.20 release.
> - The image list module is included in the Adventure Works theme.

The following example image shows an image list module displaying a list of text with logos on an Adventure Works B2C site page.

![Example showing an image list module displaying a list of text with logos](./media/Image_list.PNG)

The following example image shows an image list module displaying brand logos on an Adventure Works B2B site page.

![Example showing an image list module displaying brand logos](./media/Image_list_B2B.PNG)

## Image list module properties

| Property name  | Values | Description |
|----------------|--------|-------------|
| Heading        | Heading text and heading tag (**H1**, **H2**, **H3**, **H4**, **H5**, or **H6**) | A heading can be defined for the image list. |
| Image list      | Array of images, text paragraphs, URLs | Each item in the array is an image accompanied by a text paragraph and URL. |

## Add an image list module to a new page

To add an image list module to a new page and set the required properties in Commerce site builder, follow these steps.

1. Go to **Templates**, and open **Marketing template** which is used for the home page (or create a new one)
1. In the **Main** slot of the default page, add Image List module.
1. Select **Save**, select **Finish editing** to check in the template, and then select **Publish** to publish it.
1. Open the site Home page or create a new one using Marketing template.
1. In the **Main** slot of the default page, select the ellipsis button (**...**), and then select **Add Module**.
1. In the **Add Module** dialog box, under **Select Modules**, select the Image List, and then select **OK**.
1. In the property panel for Image List module, add a Heading say “Our brands”
1. In the property panel for Image List module, add an Image List – add an image, some paragraph, redirection link.
1. Repeat with more Image list items
1. Select **Save**, and then select **Preview** to preview the page.
1. Select **Finish editing** to check in the template, and then select **Publish** to publish it. 

## Additional resources

[Module library overview](starter-kit-overview.md)

[Adventure Works theme](adventure-works-theme.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
