---
title: Upload images
description: Learn how to upload images in Microsoft Dynamics 365 Commerce site builder.
author: josaw1
ms.date: 01/21/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---

# Upload images

[!include [banner](includes/banner.md)]

This article describes how to upload images in Microsoft Dynamics 365 Commerce site builder.

The Commerce site builder Media Library lets you upload images one at a time or in bulk by using folders. Always upload the version of the image with the highest resolution and quality. The image resizer component automatically optimizes the image for different viewports and their breakpoints.

### Image information specified during upload

When you upload an image, specify the following information.

- **Title, Alt Text, Description, Keywords**: Metadata for the images. You must provide the title and alt text.
- **Select category**:
    - **None**: Use for an e-commerce storytelling images.
    - **Product, Category, Customer, Employee, Catalog**: Use for Dynamics 365 Commerce omni-channel images.
- **Publish assets after upload**: When you select this check box, the images are published immediately after upload.

> [!NOTE]
> - When you assign a category to image assets, the system automatically adds the category as a keyword to help you search for assets in a specific category.
> - Product detail pages dynamically generate the **Alt Text** by using the product name. So, changing the **Alt Text** for a product image doesn't affect the rendered image.

### Naming conventions for omnichannel images 

If you configure the Media Library as the omnichannel image backend, use image categories to indicate which category the uploaded image belongs to. Follow the naming convention to ensure that other channels, such as point of sale (POS), can retrieve images correctly.

The default naming convention varies based on the category:
- Catalog images use the name "**/Catalogs/\{LanguageId\}/\{CatalogName\}.jpg**"
- Category images use the name "**/Categories/\{CategoryName\}.png**"
- Customer images use the name "**/Customers/\{CustomerNumber\}.jpg**"
- Employee images use the name "**/Workers/\{WorkerNumber\}.jpg**"
- Product images use the name "**/Products/\{ProductNumber\}\_000_001.png**"
    - 001 is the sequence of the image and it can be 001, 002, 003, 004, or 005
- Product variant images use the name "**/Products/\{ProductNumber\} \^ \{Style\} \^ \{Size\} \^ \{Color\} \^\_000_001.png**"
    - For example: 93039 \^ &nbsp;\^ 2 \^ Black \^\_000_001.png
- Product variant images with configuration dimension use the name "**/Products/\{ProductNumber\} \^ \{Configuration\}\_000_001.png**"
    - For example: 93039 \^ LB8017_000_001.png

> [!NOTE]
> For product variant images, if the dimension value is empty, the file name must have two whitespaces between the carets.

The examples use the default configuration. The separator character and dimensions are configurable, and the exact naming required might vary between deployments. To identify the exact naming convention required, use the developer console of the browser to inspect the product variant image requests while changing the product dimensions on the storefront product details page (PDP).

## Upload an image

To upload an image in site builder, follow these steps:

1. In the left navigation pane, select **Media Library**.
1. On the command bar, select **Upload > Upload Media Items**.
1. In the File Explorer window, navigate to and select one or more image files to upload, and then select **Open**.
1. In the **Upload Media Item** dialog box, enter the required title and alt text.
1. Enter optional description and keywords and select a category if desired. 
1. If you want to publish the images immediately after upload, select the **Publish media items after upload** check box.
1. Select **OK**.

## Upload a folder of images

To bulk upload a folder of images in site builder, follow these steps:

1. In the left navigation pane, select **Media Library**.
1. On the command bar, select **Upload > Upload Folder**.
1. In the File Explorer window, navigate to and select a folder to upload, and then select **Open**.
1. In the **Upload Media Items** dialog box, enter optional keywords and select a category if desired. 
1. If you want to publish the images in the folder immediately after upload, select the **Publish media items after upload** check box.
1. Select **OK**.

## Additional resources

[Digital asset management overview](dam-overview.md)

[Upload video](dam-upload-video.md)

[Upload files](dam-upload-files.md)

[Crop images](dam-crop-images.md)

[Customize image focal points](dam-custom-focal-point.md)

[Upload and serve static files](upload-serve-static-files.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
