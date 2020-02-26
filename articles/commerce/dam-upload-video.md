---

# required metadata

title: Upload videos
description: This topic describes how to upload videos in Microsoft Dynamics 365 Commerce site builder.
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

# Upload videos

[!include [banner](../includes/banner.md)]

This topic describes how to upload videos in Microsoft Dynamics 365 Commerce site builder.

## Upload a video

If single video is being uploaded, you will be able to specify the following information in the **Upload Media Item** dialog box.

- **Title, Description, Keywords** - Metadata
- **Automatically generate closed captions** - Specifies whether closed captions should be automatically generated for the video
- **Closed Caption** - Specifies the closed captions to be used
- **Regular Audio** - Specifies the regular audio track
- **Thumbnail** - Specifies the thumbnail for the video. If not specified, it will be generated automatically
- **Descriptive Audio** -Specifies the descriptive audio track

To upload a video in site builder, follow these steps.

1. In the left navigation pane, select **Media Library**.
1. On the command bar, select **Upload \> Upload Media Items**.
1. In the File Explorer window, navigate to and select one or more video files to upload, and then select **Open**.
1. In the **Upload Media Item** dialog box, enter the required title and alt text.
1. Enter optional description and keywords and select a category if desired. 
1. If you want to publish the image(s) after immediately upload, select the **Publish media items after upload** check box
1. Select **OK**.

If you are uploading multiple types of assets simultaneously (for example, images and videos), in the **Upload Media Item** dialog box you will only be able to specify the keywords, whether the files should be published immediately after upload, and whether closed captions should be automatically generated for video files. All the assets will share the same keywords.

<!--
![Video](./media/dam-screenshot4.png)
-->

> [NOTE]
> You should always upload the version of the video with highest bitrate and resolution. The video will be converted automatically to be suitable for different viewports and their breakpoints.

## Additional resources

[Digital asset management overview](dam-overview.md)

[Upload images](dam-upload-images.md)

[Upload files](dam-upload-files.md)

[Crop images](dam-crop-images.md)

[Customize image focal points](dam-custom-focal-point.md)
