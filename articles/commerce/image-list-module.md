---
# required metadata

title: Image list module
description: This topic covers image list modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
ms.date: 07/08/2021
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

This topic covers image list modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.

The image list module can be used to easily add a collection (array) of images to site pages. Each image in the array can be configured with paragraph text and link URLs. The image list module is best suited to displaying brand logos or a list that includes logos.

> [!IMPORTANT]
> - The image list module is available in the Commerce module library as of the Dynamics 365 Commerce version 10.0.20 release.
> - The image list module is showcased in the Adventure Works theme.

The following illustration shows an example where an image list module displays a list of text that includes logos on an Adventure Works business-to-consumer (B2C) site page.

![Example of an image list module that displays a list of text that includes logos](./media/Image_list.PNG)

The following illustration shows an example where an image list module displays brand logos on an Adventure Works business-to-business (B2B) site page.

![Example of an image list module that displays brand logos](./media/Image_list_B2B.PNG)

## Image list module properties

| Property name | Values | Description |
|---------------|--------|-------------|
| Heading       | Heading text and heading tag (**H1**, **H2**, **H3**, **H4**, **H5**, or **H6**) | A text heading for the image list module. |
| Image list    | Images, text, and URLs | Each item in the array is an image that is accompanied by paragraph text and a URL. |

## Add an image list module to a new page

To add an image list module to a new page and set the required properties in Commerce site builder, follow these steps.

1. Go to **Templates**, and open the marketing template for your site's home page (or create a new marketing template).
1. In the **Main** slot of the default page, select the ellipsis (**...**), and then select **Add Module**.
1. In the **Add Module** dialog box, select the **Image list** module, and then select **OK**.
1. Select **Save**, select **Finish editing** to check in the template, and then select **Publish** to publish it.
1. Go to **Pages**, and open the site's home page (or create a new home page by using the marketing template).
1. In the **Main** slot of the default page, select the ellipsis button (**...**), and then select **Add Module**.
1. In the **Add Module** dialog box, select the **Image list**, and then select **OK**.
1. In the property pane for the image list module, add a heading (for example, **Our brands**).
1. Add an image list item, and specify an image, some paragraph text, and a redirection URL.
1. Add and configure additional image list item modules as you require.
1. Select **Save**, and then select **Preview** to preview the page.
1. Select **Finish editing** to check in the template, and then select **Publish** to publish it.

## Additional resources

[Module library overview](starter-kit-overview.md)

[Adventure Works theme](adventure-works-theme.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
