---
# required metadata

title: Improve performance by optimizing images
description: This topic describes how to improve website performance by optimizing your use of images in Microsoft Dynamics 365 Commerce.
author: mssle
ms.date: 09/17/2021
ms.topic: article
audience: Developer, IT Pro
ms.reviewer: josaw
ms.search.region: Global
ms.author: sheaton
ms.search.validFrom: 2021-09-20
---

# Improve performance by optimizing images

[!include[banner](../includes/banner.md)]


This topic describes how to improve website performance by optimizing your use of images in Microsoft Dynamics 365 Commerce. 

## When should I use this topic?

This topic applies to the following configurations:

<table>
<tr>
    <th>When your...</th>
    <th>is...</th>
<tr>
    <th>Process</th>
    <td>Upgrade or Go Live</td>
</tr>
<tr>
    <th>Component</th>
    <td>B2C eCommerce or B2B eCommerce</td>
</tr>
<tr>
    <th>Feature Area</th>
    <td>eCommerce Website Performance</td>
</tr>
<tr>
    <th>Version</th>
    <td>eCommerce version 10.0.16 or later</td>
</tr>
</table> 

## How do I perform this operation?

### Pre-conditions:

- You have installed the Dynamics 365 Commerce online software development kit (SDK). For more information, see [Install the online SDK](./dev-itpro/ecommerce-platform-sdk.md).

### Steps to complete:

One of the biggest performance hits to a web page can be the downloading of images. You can reduce the size of your images and improve actual and perceived performance using the instructions below.

1. Use CSS to generate images for items such as buttons whenever possible.
1. Upload high quality/resolution marketing or product images to the Commerce site builder [Media Library](https://docs.microsoft.com/en-us/dynamics365/commerce/dam-overview), where the image resizer will be used automatically during rendering.
1. Include width and height properties for each image
    1. For each module that uses images, open the **theme.settings.json** file in the **/src/settings** directory in the SDK install location
    1. Locate the module you wish to update. 
    1. Ensure the image properties include width and height parameters. Learn more: [Configure theme settings](https://docs.microsoft.com/en-us/dynamics365/commerce/e-commerce-extensibility/configure-theme-settings)
1. Disable lazy loading for images* 
    1. Open Commerce Site Builder
    1. Navigate to the module with an image that should not be lazy loaded
    1. Select the checkbox next to "Disable Lazy Load"
    1. Save, preview, and publish your content.
  
*Note: for a Product Collection Module, ensure lazy loading is enabled by selecting the "Enable module lazy load" checkbox

## Validation Steps

Use these options to validate that the module was successfully excluded.

- **Description or Purpose:** Verify page performance
- **Steps to Run:**  Run performance tests before and after optimizing your images
- **Passing Result:** Performance is improved after optimizing your images

## Additional resources

[Install the online SDK](./dev-itpro/ecommerce-platform-sdk.md)

[Digital asset management overview](./dam-overview.md)

[Configure theme settings](./e-commerce-extensibility/configure-theme-settings.md)

[Optimize images](./e-commerce-extensibility/best-practices-dev.md#optimize-images) 

[Enable lazy loading for product collection modules](./e-commerce-extensibility/best-practices-dev.md#enable-lazy-loading-for-a-product-collection-module) 


  
