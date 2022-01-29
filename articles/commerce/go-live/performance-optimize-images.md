---
# required metadata

title: Optimize images
description: This topic explains how to improve website performance by optimizing image use in Microsoft Dynamics 365 Commerce.
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

This topic explains how to improve website performance by optimizing image use in Microsoft Dynamics 365 Commerce during the upgrade or go-live process. 

## Applies to

This topic applies to the following configurations: 

- **Version**: Commerce 10.0.16 or later.
- **Component**: Business to consumer (B2C) or business to business (B2B). 
- **Feature area**: Commerce website performance.

## Prerequisites

Install the Dynamics 365 Commerce online software development kit (SDK). For more information, see [Install the online SDK](../dev-itpro/ecommerce-platform-sdk.md).

## Steps to optimize images

One of the biggest performance hits to a web page can be the downloading of images. To reduce the size of your images and improve the actual and perceived performance of your website, follow these steps.

1. Use Cascading Style Sheets (CSS) to generate images for items such as buttons whenever possible.
1. Upload high quality/resolution marketing or product images to the Commerce site builder [Media Library](../dam-overview.md), where the image resizer will be used automatically during rendering.
1. Include width and height properties for each image as follows:
    1. For each module that uses images, open the **theme.settings.json** file in the **/src/settings** directory in the SDK install location
    1. Locate the module you wish to update. 
    1. Ensure the image properties include width and height parameters. Learn more: [Configure theme settings](../e-commerce-extensibility/configure-theme-settings.md)
1. Disable lazy loading for images as follows:
    1. Open Commerce site builder
    1. Navigate to the module with an image that should not be lazy loaded.
    1. Select the **Disable Lazy Load** checkbox.
    1. Save, preview, and publish your content.

> [!NOTE]
> For product collection modules, lazy loading is disabled by clearing the **Enable module lazy load** checkbox.

## Validate 

Use the following method to validate that image use has been optimized.

- **Description or Purpose**: Verify page performance.
- **Steps to Run**:  Run performance tests before and after optimizing your images.
- **Passing Result**: Performance is improved after optimizing your images.
  
 ## Additional resources
 
 [Best practices for Dynamics 365 Commerce development](../e-commerce-extensibility/best-practices-dev.md)
