---
title: Upload images
description: This article describes how to upload images in Microsoft Dynamics 365 Commerce site builder.
author: josaw1
ms.date: 12/03/2021
ms.topic: article
audience: Application User
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: 
ms.custom: 
ms.assetid: 
ms.search.industry: 
---

# Upload images

[!include [banner](includes/banner.md)]

This article describes how to upload images in Microsoft Dynamics 365 Commerce site builder.

The Commerce site builder Media Library allows you to upload images, either singly or in bulk using folders. You should always upload the version of the image with highest resolution and quality, because the image resizer component will automatically optimize the image for different viewports and their breakpoints.

### Image information specified during upload

When uploading an image, the following information can be specified.

- **Title, Alt Text, Description, Keywords**: Metadata of the image or images. Title and alt text are required values.
- **Select category**:
    - **None**: Used for an e-Commerce storytelling image or images.
    - **Product, Category, Customer, Employee, Catalog**: Used for Dynamics 365 Commerce omni-channel image or images.
- **Publish assets after upload**: When this check box is selected, the image or images are published immediately after upload.

> [!NOTE]
> - Image assets with a category assigned are also automatically tagged with the category as a keyword to aid searching for assets of a specific category.
> - Product detail pages dynamically generate the **Alt Text** using the product name, so changing the **Alt Text** for a product image will have no impact on the rendered image.

### Naming conventions for omni-channel images 

If you have configured the Media Library as the omni-channel image backend, you can use image categories to indicate which category the uploaded image belongs to. There is also a naming convention that should be followed to ensure that images are retrieved correctly by other channels, such as point of sale (POS).

The default naming convention varies based on the category:
- Catalog images should be named "**/Catalogs/\{LanguageId\}/\{CatalogName\}.jpg**"
- Category images should be named "**/Categories/\{CategoryName\}.png**"
- Customer images should be named "**/Customers/\{CustomerNumber\}.jpg**"
- Employee images should be named "**/Workers/\{WorkerNumber\}.jpg**"
- Product images should be named "**/Products/\{ProductNumber\}\_000_001.png**"
    - 001 is the sequence of the image and it can be 001, 002, 003, 004 or 005
- Product variant images should be named "**/Products/\{ProductNumber\} \^ \{Style\} \^ \{Size\} \^ \{Color\} \^\_000_001.png**"
    - For example: 93039 \^ &nbsp;\^ 2 \^ Black \^\_000_001.png
- Product variant images with configuration dimension should be named "**/Products/\{ProductNumber\} \^ \{Configuration\}\_000_001.png**"
    - For example: 93039 \^ LB8017_000_001.png

> [!NOTE]
> For product variant images, if the dimension value is empty there must be two whitespaces between the carets in the file name.

The examples above use the default configuration. The separator character and dimensions are configurable and the exact naming required may vary between deployments. One method of identifying the exact naming convention required is to use the developer console of the browser to inspect the product variant image requests while changing the product dimensions on the storefront product details page (PDP).

## Upload an image

To upload an image in site builder, follow these steps.

1. In the left navigation pane, select **Media Library**.
1. On the command bar, select **Upload \> Upload Media Items**.
1. In the File Explorer window, navigate to and select one or more image files to upload, and then select **Open**.
1. In the **Upload Media Item** dialog box, enter the required title and alt text.
1. Enter optional description and keywords and select a category if desired. 
1. If you want to publish the image(s) immediately after upload, select the **Publish media items after upload** check box.
1. Select **OK**.

## Upload a folder of images

To bulk upload a folder of images in site builder, follow these steps.

1. In the left navigation pane, select **Media Library**.
1. On the command bar, select **Upload \> Upload Folder**.
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
