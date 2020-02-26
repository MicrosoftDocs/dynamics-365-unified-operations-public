---
# required metadata

title: Upload images
description: This topic describes how to upload images in Microsoft Dynamics 365 Commerce site builder.
author: psimolin
manager: annbe
ms.date: 02/26/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: 
ms.author: psimolin
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: 
---

# Upload images

[!include [banner](../includes/banner.md)]

This topic describes how to upload images in Microsoft Dynamics 365 Commerce product site builder.

## Overview

Commerce site builder allows you to upload images, either singly or in bulk using folders.

You should always upload the version of the image with highest resolution and quality. The image resizer component will automatically optimize the image for different viewports/breakpoints.

### Image information specified during upload

When uploading an image or folder of images, the following information can be specified.

- **Title, Alt Text, Description, Keywords**: Metadata of the image or images. Title and alt text are required values.
- **Select category**:
    - **None**: Used for an e-Commerce storytelling image or images
    - **Product, Category, Customer, Employee, Catalog**: Used for Dynamics 365 Commerce omni-channel image or images.
- **Publish assets after upload**: When this check box is selected, the image or images are published immediately after upload.

> [!NOTE]
> Image assets with a category assigned are also automatically tagged with the category as a keyword to allow searching for assets of specific category.

### Naming conventions for omni-channel images 

If you have configured the Media Library as the omni-channel image backend, you can use image categories to indicate which category the uploaded image belongs to. There is also a naming convention that needs to be followed to make sure that images are retrieved correctly by other channels, such as point of sale (POS).

The default naming convention varies based on the category:
- Catalog images should be named "**/Catalogs/\{LanguageId\}/\{CatalogName\}.jpg**"
- Category images should be named "**/Categories/\{CategoryName\}.png**"
- Customer images should be named "**/Customers/\{CustomerNumber\}.jpg**"
- Employee images should be named "**/Workers/\{WorkerNumber\}.jpg**"
- Product images should be named "**/Products/\{ProductNumber\}_000_001.png**"
    - 001 is the sequence of the image and it can be 001, 002, 003, 004 or 005
- Product variant images should be named "**/Products/\{ProductNumber\}\_\{Size\}\_\{Color\}\_\{Style\}\_000_001.png**"

## Upload an image

To upload an image in site builder, follow these steps.

1. In the left navigation pane, select **Media Library**.
1. On the command bar, select **Upload \> Upload Media Items**.
1. In the File Explorer window, navigate to and select one or more image files to upload, and then select **Open**.
1. In the **Upload Media Item** dialog box, enter the required title and alt text.
1. Enter optional description and keywords and select a category if desired. 
1. If you want to publish the image(s) immediately after upload, select the **Publish media items after upload** check box
1. Select **OK**.

## Upload a folder of images

To bulk upload a folder of images in site builder, follow these steps.

1. In the left navigation pane, select **Media Library**.
1. On the command bar, select **Upload \> Upload Folder**.
1. In the File Explorer window, navigate to and select a folder to upload, and then select **Open**.
1. In the **Upload Media Items** dialog box, enter optional keywords and select a category if desired. 
1. If you want to publish the images in the folder immediately after upload, select the **Publish media items after upload** check box
1. Select **OK**.

## Additional resources

[Digital asset management overview](dam-overview.md)

[Upload video](dam-upload-video.md)

[Upload files](dam-upload-files.md)

[Crop images](dam-crop-images.md)

[Customize image focal points](dam-custom-focal-point.md)
