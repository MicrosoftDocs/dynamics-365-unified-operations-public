---
# required metadata

title: Media gallery module
description: This topic covers Media gallery module and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
manager: annbe
ms.date: 05/28/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anupamar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---

# Media gallery module

[!include [banner](includes/preview-banner.md)]
[!include [banner](includes/banner.md)]

This topic covers Media gallery module and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.

## Overview

The Media gallery module is to display media (images) in a gallery view. It provides additional capabilties that allow images to be zoomed, viewed in full screen etc.

Usage examples of Media gallery
- Media gallery can be used on the Product details page to render the product images
- Media gallery can be used on a marketing page for a product to render theproduct images
- Media gallery can be used on a marketing page to showcase a curated set of images

The following image shows an example of a buy box on a product details page that hosts the images using the Media gallery module

![Example of a Media gallery module](./media/ecommerce-pdp-buybox.PNG)

## Media gallery properties
| Property name  | Values | Description |
|----------------|--------|-------------|
| Image Source          | Image file | An image can be used to showcase a product or a promotion. An image can be uploaded to the image gallery, or an existing image can be used. |
| Heading        | Heading text and heading tag (**H1**, **H2**, **H3**, **H4**, **H5**, or **H6**) | Every hero module can have a heading. By default, the **H2** heading tag is used for the heading. However, the tag can be changed to meet accessibility requirements. |
| Paragraph      | Paragraph text | Hero modules support paragraph text in rich text format. Some basic rich text capabilities are supported, such as bold, underlined, and italic text, and hyperlinks. Some of these capabilities can be overridden by the page theme that is applied to the module. |
| Link           | Link text, link URL, Accessible Rich Internet Applications (ARIA) label, and **Open link in new tab** | Hero modules support one or more "call to action" links. If a link is added, link text, a URL, and an ARIA label are required. ARIA labels should be descriptive to meet accessibility requirements. Links can be configured so that they are opened on a new tab. |


## Commerce Scale Unit interaction

The media gallery module retrieves product information by using Commerce Scale Unit application programming interfaces (APIs). When the Image source is page context, the product ID from the product details page is used to retrieve the images.

## Add an Image gallery to a page

To add a Image gallery module to a Buy Box, see [Buy Box module](add-buy-box.md)

1. Go to **Page Fragments**, and select **New** to create a new fragment.
1. In the **New Page Fragment** dialog box, select the **Buybox** module.
1. Under **Page Fragment Name**, enter the name **Buy box fragment**, and then select **OK**.
1. In the **Media Gallery** slot of the buy box module, select the ellipsis (**...**), and then select **Add Module**.
1. In the **Add Module** dialog box, select the **Media gallery** module, and then select **OK**.
1. In the **Store selector** slot of the buy box module, select the ellipsis (**...**), and then select **Add Module**.
1. In the **Add Module** dialog box, select the **Store selector** module, and then select **OK**.
1. Select **Save**, select **Finish editing** to check in the fragment, and then select **Publish** to publish it.
1. Go to **Templates**, and select **New** to create a new template.
1. In the **New Template** dialog box, under **Template name**, enter **PDP template**, and then select **OK**.
1. In the **Body** slot, select the ellipsis (**...**), and then select **Add Module**.
1. In the **Add Module** dialog box, select the **Default Page** module, and then select **OK**.
1. In the **Main** slot of the default page, select the ellipsis (**...**), and then select **Add Page Fragment**.
1. In the **Select Page Fragment** dialog box, select the **Buy box fragment** fragment that you created earlier, and then select **OK**.
1. Select **Save**, select **Finish editing** to check in the template, and then select **Publish** to publish it.
1. Go to **Pages**, and select **New** to create a new page.
1. In the **Choose a template** dialog box, select the **PDP template** template. Under **Page name**, enter **PDP page**, and then select **OK**.
1. In the **Main** slot of the new page, select the ellipsis (**...**), and then select **Add Page Fragment**.
1. In the **Select Page Fragment** dialog box, select the **Buy box fragment** fragment that you created earlier, and then select **OK**.
1. Save and preview the page. Add the **?productid=&lt;product id&gt;** query string parameter to the URL of the preview page. In that way, the product context is used to load and render the preview page.
1. Select **Save**, select **Finish editing** to check in the page, and then select **Publish** to publish it. A buy box should appear on the product details page.

## Additional resources

[Starter kit overview](starter-kit-overview.md)

[Buy box module](add-buy-box.md)

[Container module](add-container-module.md)

