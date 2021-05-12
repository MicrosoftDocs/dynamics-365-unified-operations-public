---
# required metadata

title: Image List module
description: This topic covers Image List modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
ms.date: 01/28/2021
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


# Image List

[!include [banner](includes/banner.md)]
This topic covers Image List module and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.
The Image List module can be used on a page to add an array of images, each with a paragraph, text, link etc. The Image List module has an easy authoring experience for adding a collection of images. Its best used when showcasing brand logos or showcasing a list with logos.

Below is an example of Image List on Adventure works B2C showcasing list of text with logos.

Below is an example of Image List on Adventure works B2B showcasing brand logos.

> [!IMPORTANT]
> Image List module is available in Dynamics 365 Commerce 10.0.20 release.
> Image List module is showcased in Adventure works theme.


## Image List module properties
| Property name  | Values | Description |
|----------------|--------|-------------|
| Heading        | Heading text and heading tag (**H1**, **H2**, **H3**, **H4**, **H5**, or **H6**) | A heading can be defined for the Image List |
| Image List      | Array of image, paragraph, link | Each item is an image, along with paragraph and a redirection link. |

## Add Image List module to a new page
To add Image List module to a new page and set the required properties, follow these steps.
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

[Adventure works]()

[!INCLUDE[footer-include](../includes/footer-banner.md)]
