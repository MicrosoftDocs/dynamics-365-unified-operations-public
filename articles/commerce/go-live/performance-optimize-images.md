---
# required metadata

title: Optimize images
description: This topic explains how you can help improve website performance by optimizing image use in Microsoft Dynamics 365 Commerce.
author: mssle
ms.date: 01/28/2022
ms.topic: article
audience: Developer, IT Pro
ms.reviewer: josaw
ms.search.region: Global
ms.author: sheaton
ms.search.validFrom: 2021-09-20
---

# Optimize images

[!include[banner](../includes/banner.md)]

This topic explains how you can help improve website performance by optimizing image use in Microsoft Dynamics 365 Commerce during the upgrade or go-live process.

## Applies to

This topic applies to the following configurations:

- **Version:** Commerce 10.0.16 or later
- **Component:** Business to consumer (B2C) or business to business (B2B)
- **Feature area:** Commerce website performance

## Prerequisites

Install the Dynamics 365 Commerce online software development kit (SDK). For more information, see [Install the online SDK](../dev-itpro/ecommerce-platform-sdk.md).

## Steps to optimize images

One of the biggest performance hits for a webpage can occur when images are downloaded. To reduce the size of your images and help improve the actual and perceived performance of your website, follow these steps.

1. Use Cascading Style Sheets (CSS) to generate images for items such as buttons whenever you can.
1. Upload high-quality/high-resolution marketing or product images to the Commerce site builder [Media Library](../dam-overview.md). The image resizer will then automatically be used during rendering.
1. Include width and height properties for each image:

    1. For each module that uses images, open the **theme.settings.json** file in the **/src/settings** directory in the SDK installation location.
    1. Find the module that you want to update.
    1. Ensure that the image properties include width and height parameters. For more information, see [Configure theme settings](../e-commerce-extensibility/configure-theme-settings.md).

1. Disable lazy loading for images:

    1. Open Commerce site builder.
    1. Go to the module that includes an image that should not be lazy loaded.
    1. For product collection modules, clear the **Enable module lazy load** checkbox. For other modules, select the **Disable Lazy Load** checkbox.
    1. Save, preview, and publish your content.

## Validate

Use the following method to validate that image use has been optimized.

- **Description or purpose:** Verify page performance.
- **Steps to run:** Run performance tests before and after you optimize your images.
- **Passing result:** Performance is improved after you optimize your images.

## Additional resources

[Best practices for Dynamics 365 Commerce development](../e-commerce-extensibility/best-practices-dev.md)
