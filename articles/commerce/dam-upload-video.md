---

# required metadata

title: Upload videos
description: This topic describes how to upload videos in Microsoft Dynamics 365 Commerce site builder.
author: psimolin
ms.date: 06/09/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
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

[!include [banner](includes/banner.md)]

This topic describes how to upload videos in Microsoft Dynamics 365 Commerce site builder.

The Commerce site builder Media Library allows you to upload videos. You should always upload the version of a video with the highest bitrate and resolution, because the video will be automatically converted to be suitable for different viewports and their breakpoints.

### Video information specified during upload

When uploading a video, the following information can be specified.

- **Title, Description, Keywords**: Metadata of the video.
- **Automatically generate closed captions**: Specifies whether closed captions should be automatically generated for the video (only English language is supported). 
- **Closed Caption**: Specifies the closed captions to be used.
- **Regular Audio**: Specifies the regular audio track to be used.
- **Thumbnail**: Specifies the thumbnail for the video. If not specified, it will be generated automatically.
- **Descriptive Audio**: Specifies the descriptive audio track to be used.

## Upload a video

To upload a video in site builder, follow these steps.

1. In the left navigation pane, select **Media Library**.
1. On the command bar, select **Upload \> Upload Media Items**.
1. In the File Explorer window, navigate to and select one or more video files to upload, and then select **Open**.
1. In the **Upload Media Item** dialog box, enter the required title and alt text.
1. Enter optional description and keywords and select a category if desired. 
1. If you want to publish the image(s) after immediately upload, select the **Publish media items after upload** check box
1. Select **OK**.

If you are uploading multiple types of assets simultaneously (for example, images and videos), in the **Upload Media Item** dialog box you will only be able to specify keywords, whether the files should be published immediately after upload, and whether closed captions should be automatically generated for video files. All the assets will share the same keywords.

## Additional resources

[Digital asset management overview](dam-overview.md)

[Upload images](dam-upload-images.md)

[Upload files](dam-upload-files.md)

[Crop images](dam-crop-images.md)

[Customize image focal points](dam-custom-focal-point.md)

[Upload and serve static files](upload-serve-static-files.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
