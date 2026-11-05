---
title: Optimize images
description: Learn how you can improve website performance by optimizing image use in Microsoft Dynamics 365 Commerce during the upgrade or go-live process.
author: mssle
ms.date: 11/05/2026
ms.topic: how-to
ms.author: asharchw
ms.reviewer: mirao
ms.search.region: Global
ai-usage: ai-assisted
ms.search.validFrom: 2021-09-20
ms.custom: 
  - bap-template
---

# Optimize images

[!INCLUDE [banner](../includes/banner.md)]

This article explains how you can help improve website performance by optimizing image use in Microsoft Dynamics 365 Commerce during the upgrade or go-live process.

## Applies to

This article applies to the following configurations:

- **Version:** Commerce 10.0.16 or later
- **Component:** Business to consumer (B2C) or business to business (B2B)
- **Feature area:** Commerce website performance

## Prerequisites

Install the Dynamics 365 Commerce online software development kit (SDK). For more information, see [Install the online SDK](../dev-itpro/ecommerce-platform-sdk.md).

## Steps to optimize images

Downloading images can significantly affect the performance of a webpage. To reduce the size of your images and help improve the actual and perceived performance of your website, follow these steps:

1. Use Cascading Style Sheets (CSS) to generate images for items such as buttons whenever you can.
1. Upload high-quality, high-resolution marketing or product images to the Commerce site builder [Media Library](../dam-overview.md). The image resizer then automatically resizes images during rendering.
1. Include width and height properties for each image:

    1. For each module that uses images, open the **theme.settings.json** file in the **/src/settings** directory in the SDK installation location.
    1. Find the module that you want to update.
    1. Ensure that the image properties include width and height parameters. For more information, see [Configure theme settings](../e-commerce-extensibility/configure-theme-settings.md).

1. Disable lazy loading for images:

    1. Open Commerce site builder.
    1. Go to the module that includes an image that shouldn't be lazy loaded.
    1. For product collection modules, clear the **Enable module lazy load** checkbox. For other modules, select the **Disable Lazy Load** checkbox.
    1. Save, preview, and publish your content.

## Choose an image output format

Image dimensions, output format, and compression quality affect download size in different ways. Resizing reduces pixel dimensions. Selecting an output format can reduce the bytes required to represent those pixels. The quality setting controls lossy compression. It doesn't reduce file size when the output is lossless PNG.

> [!NOTE]
> The **Image format** setting requires image-format support to be enabled in your environment and a compatible online SDK. The setting applies to images processed by the Commerce image resizer, not an external image provider.

Where **Image format** is available in a module's image settings, use the following guidance:

- **WebP (smallest file size)**: Consider this option for opaque product photographs and marketing images. Compare the downloaded size and visual quality with the existing output.
- **JPEG (no transparency)**: Use this option for photographs when JPEG output is required.
- **PNG**: Use this option for images that require transparency. Converting a JPEG photograph to PNG can increase download size without improving its detail.
- **Original (no conversion)**: Leave the output format unspecified and retain existing image-resizer behavior. Other settings can still affect the output.

> [!IMPORTANT]
> JPEG doesn't support transparency. Don't assume that WebP output from the Commerce image resizer preserves transparency either. Use PNG for transparent images, and verify their appearance before publishing.

For a media gallery, configure thumbnails, main gallery images, and zoomed images separately. For instructions, see [Configure image output format](../media-gallery-module.md#configure-image-output-format). A format selection affects the served image, not the source file in the Media library.

Smaller images can download sooner and reduce data transfer, especially on slower connections. They don't guarantee an equivalent improvement in overall page load time or Largest Contentful Paint (LCP). Measure those metrics separately.

## Validate

Use the following method to validate that your image use is optimized:

- **Description or purpose:** Verify page performance.
- **Steps to run:** Run performance tests before and after you optimize your images.
- **Passing result:** Performance is improved after you optimize your images.

When you change the image output format, also perform these checks:

1. Open your browser's developer tools, disable the cache, and reload the page under the same network conditions for each comparison.
1. Inspect image requests. Confirm the response `Content-Type` and transferred size rather than relying on the source file extension. Where the format setting is applied, the image-resizer URL includes `f=webp`, `f=jpg`, or `f=png`.
1. Check thumbnails, main images, product variants, zoom, and full-screen views separately. Don't assume that one request represents every image path.
1. Compare visual quality, transparency, and image download duration before and after the change.
1. Measure page load time and LCP separately from image download duration. Publish the change only after you confirm acceptable appearance and performance.

## More resources

[Best practices for Dynamics 365 Commerce development](../e-commerce-extensibility/best-practices-dev.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
