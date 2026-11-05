---
title: Media gallery module
description: Learn about media gallery modules and how to add them to site pages in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
ms.date: 11/05/2026
ms.topic: how-to
ms.author: asharchw
ms.reviewer: mirao
ms.search.region: Global
ai-usage: ai-assisted
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---

# Media gallery module

[!INCLUDE [banner](includes/banner.md)]

This article describes media gallery modules and explains how to add them to site pages in Microsoft Dynamics 365 Commerce.

Media gallery modules show one or more images in a gallery view. Media gallery modules support thumbnail images, which you can arrange either horizontally (as a row below the image) or vertically (as a column next to the image). Media gallery modules also provide capabilities that enable images to be zoomed (magnified) or viewed in full-screen mode. To render an image in a media gallery module, you must add the image to the Commerce site builder Media Library. Currently, media gallery modules support only images.

In the default mode, a media gallery module uses the product ID that's available from the page context of a product details page (PDP) to render the corresponding product images. In Commerce headquarters, you must define a media file path for all products. Then, upload images to the site builder Media Library according to the file path that you defined for the products in Commerce headquarters. These images include images for products and any product variants. For more information about how to upload images to site builder Media Library, see [Upload images](dam-upload-images.md).

Alternatively, a media gallery module can host a fully curated set of images on an image gallery page, where there are no dependencies on the product ID or page context. In this case, you must upload images to site builder Media Library and specify them in site builder.

Here are some usage examples for media gallery modules:

- Rendering product images on a PDP
- Rendering product images on a product marketing page
- Showcasing a curated set of images on a marketing page, such as a gallery page

In the following illustration, a buy box on a PDP hosts product images by using a media gallery module.

:::image type="content" source="./media/ecommerce-pdp-buybox.PNG" alt-text="Screenshot of a buy box on a product details page that hosts product images by using a media gallery module." lightbox="./media/ecommerce-pdp-buybox.PNG":::

## Media gallery properties

| Property name | Values | Description |
| ------------- | ------ | ----------- |
| Image source | **Page context** or **Product ID** | The default value is **Page context**. If you select **Page context**, the module expects the page to provide the product ID information. If you select **Product ID**, you must provide the product ID for an image as the value of the **Product ID** property. This capability is available in Commerce version 10.0.12. |
| Product ID | A product ID | This property is applicable only if the value of the **Image source** property is **Product ID**. |
| Image zoom | **Inline** or **Container** | This property lets the user zoom images in the media gallery module. You can zoom an image either inline or in a separate container next to the image. This capability is available in 10.0.12. |
| Zoom factor | A decimal number | This property specifies the scale factor for zooming images. For example, if you set the value to **2.5**, images are magnified 2.5 times. |
| Full screen | **True** or **False** | This property specifies whether users can view images in full-screen mode. In full-screen mode, users can also further magnify images if the zoom capability is turned on. This capability is available in the Commerce version 10.0.13 release. |
| Zoomed image quality | A number from 1 through 100 that represents a percentage and that is selected by using a trackbar control | This property controls compression quality for zoomed-in images, not their pixel dimensions. The quality control doesn't reduce file size when the output format is PNG, because PNG uses lossless compression. To compress a PNG photograph with a lossy format, select a different output format where **Image format** is available. The quality control is available as of Commerce release version 10.0.19. |
| Images | Images that are selected from site builder Media Library | In addition to being rendered from a product, you can curate images for a media gallery module. These images append to any product images that are available. This capability is available in Commerce version 10.0.12. |
| Thumbnail orientation | **Vertical** or **Horizontal** | This property specifies whether thumbnail images show in a vertical strip or a horizontal strip. |
| Hide product master images for variant | **True** or **False** | If you set this property to **True**, when a variant is selected, images of the product master are hidden unless the variant has no images. This property doesn't affect products that have no variants. |
| Update media on dimension selection | **True** or **False** | If you set this property to **True**, images in the media library update when any dimension (such as color, style, or size) is selected, and if an image is available. This property helps simplify the browsing experience, because not every product variant dimension must be selected for the corresponding image to be updated. This property is available on the **Advanced** tab. |

> [!IMPORTANT]
> The **Update media on dimension selection** property is available as of the Commerce version 10.0.21 release. It requires that Commerce module library package version 9.31 is installed.

The following illustration shows an example of a media gallery module where the full-screen and zoom options are available.

:::image type="content" source="./media/ecommerce-media-zoom.png" alt-text="Screenshot of a media gallery module where the full-screen and zoom options are available." lightbox="./media/ecommerce-media-zoom.png":::

The following illustration shows an example of a media gallery module that has curated images. The specified images aren't dependent on the product ID or page context.

:::image type="content" source="./media/ecommerce-media-curated.PNG" alt-text="Screenshot of a media gallery module that has curated images." lightbox="./media/ecommerce-media-curated.PNG":::

## Configure image output format

The **Image format** setting controls the format requested from the Commerce image resizer. Changing this setting doesn't replace the uploaded file in the Media library.

> [!NOTE]
> The **Image format** setting is available only when image-format support is enabled in your environment and your online SDK supports the setting. It doesn't apply to images served by an external image provider.

The media gallery has the following three independent image settings. A selection in one doesn't change the other two.

| Settings group | Property | Images affected |
| -------------- | -------- | --------------- |
| **Image settings** | **Thumbnail image quality** | The small images in the thumbnail strip. |
| **Image settings** | **Gallery image quality** | The main gallery images. |
| **Image zoom** | **Zoomed image quality** | Images used for magnified views. |

In each property's image settings, select an **Image format** option.

| Option | Guidance |
| ------ | -------- |
| **Original (no conversion)** | Leaves the output format unspecified. Existing image-resizer behavior, including other image settings, continues to apply. |
| **WebP (smallest file size)** | Consider this option for product photographs to reduce download size. Actual savings depend on the image and quality setting. |
| **JPEG (no transparency)** | Use this option for photographs when JPEG output is required. JPEG doesn't preserve transparency. |
| **PNG** | Use this option when you must retain transparency. Converting a JPEG photograph to PNG can increase file size without restoring lost detail. |

> [!IMPORTANT]
> Don't assume that WebP output from the Commerce image resizer preserves transparency. Use PNG for images that require transparent backgrounds, and preview the result before publishing.

To configure the format, follow these steps:

1. In Commerce site builder, open the page, template, or layout that owns the media gallery configuration.
1. Select the **Media gallery** module.
1. Open the image settings for **Thumbnail image quality**, **Gallery image quality**, or **Zoomed image quality**, and select the required **Image format**.
1. Repeat the selection for each image settings property that you want to change.
1. Select **Save**, and then select **Preview**. Check the main image, thumbnails, zoom, full-screen view, and product variants that your page supports.
1. Use your browser's network tools to verify the response content type and transferred image size. Check zoom and full-screen requests separately.
1. Select **Finish editing**, and then select **Publish** when the results meet your requirements.

When you update a shared template or layout, the setting applies to pages that inherit that configuration. Pages with their own overrides require separate updates.

For more information, see [Optimize images](go-live/performance-optimize-images.md#choose-an-image-output-format).

## Commerce Scale Unit interaction

When the image source comes from the page context, the product ID from the PDP retrieves the images. The media gallery module uses Commerce Scale Unit application programming interfaces (APIs) to retrieve the image file path for products. The images are then pulled from the Media Library so that the module can render them.

## Add a media gallery module to a page

To add a media gallery module to a marketing page, follow these steps:

1. Go to **Templates**, and select **New** to create a new template.
1. In the **New template** dialog box, under **Template name**, enter **Marketing template**, and then select **OK**.
1. In the **Body** slot, select the ellipsis (**...**), and then select **Add module**.
1. In the **Select modules** dialog box, select the **Default Page** module, and then select **OK**.
1. In the **Main** slot of the default page, select the ellipsis (**...**), and then select **Add module**.
1. In the **Select modules** dialog box, select the **Container** module, and then select **OK**.
1. Select **Save**, select **Finish editing** to check in the template, and then select **Publish** to publish it.
1. Go to **Pages**, and select **New** to create a new page.
1. In the **Create a new page** dialog box, under **Page name**, enter **Media gallery page**, and then select **Next**.
1. Under **Choose a template**, select the **Marketing template** you created, and then select **Next**.
1. Under **Choose a layout**, select a page layout (for example, **Flexible layout**), and then select **Next**.
1. Under **Review and finish**, review the page configuration. If you need to edit the page information, select **Back**. If the page information is correct, select **Create page**. 
1. In the **Main** slot of the new page, select the ellipsis (**...**), and then select **Add module**.
1. In the **Select modules** dialog box, select the **Container** module, and then select **OK**.
1. In the **Container** slot, select the ellipsis (**...**), and then select **Add module**.
1. In the **Select modules** dialog box, select the **Media gallery** module, and then select **OK**.
1. In the property pane for the media gallery module, under **Image source**, select **Productid**. Then, in the **Product id** field, enter a product ID.
1. Select **Save**, and then select **Preview** to preview the page. You should be able to see the images for the product in a gallery view.
1. To use only curated images, in the property pane, under **Image source**, select **Productid**. Then, under **Images**, select **Add an image** as many times as required to add images from the Media Library.
1. Set any other properties that you want to set, such as **Image zoom**, **Zoom factor**, and **Thumbnails orientation**.
1. When you're finished, select **Save**, select **Finish editing** to check in the page, and then select **Publish** to publish it.

## More resources

- [Module library overview](starter-kit-overview.md)
- [Buy box module](add-buy-box.md)
- [Container module](add-container-module.md)
- [Upload images](dam-upload-images.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
