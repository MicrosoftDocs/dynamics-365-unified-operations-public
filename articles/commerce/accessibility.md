---
title: Accessibility features and capabilities
description: This article provides information about the accessibility features and capabilities in Microsoft Dynamics 365 Commerce.
author: BrianShook
ms.date: 04/14/2020
ms.topic: how-to
audience: Application user
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---

# Accessibility features and capabilities

[!include [banner](includes/banner.md)]

This article provides information about the accessibility features and capabilities in Microsoft Dynamics 365 Commerce.

Accessibility features and capabilities provide the functional means for all users to access and perform actions so that they can accomplish their goals. This broad range of users might require assistive tools for hearing, vision, mobility, or neurodiversity.

Various features in Dynamics 365 Commerce let you build your site so that it includes assistive functionality. When you design your site, you should consider the areas of accessibility functionality that are mentioned in the [Microsoft Accessibility Center](https://www.microsoft.com/accessibility). 

This article describes some additional areas of accessibility functionality that you should consider when you use Dynamics 365 Commerce.

## Image alt text

Dynamics 365 Commerce has a built-in digital asset management system to track image and video assets that are used on your site. Image captions, descriptions, and alt text can be added in the properties pane for an image when it's selected or uploaded.

## Video accessibility

The Dynamics 365 Commerce digital asset management system supports several accessibility features for video content. The following table lists some examples.

| Video feature               | Description |
|-----------------------------|-------------|
| Closed captioning (CC)      | Text that can be shown for the audio and audio descriptive elements of a video, to help users who are deaf or hard of hearing |
| Subtitles                   | Caption files that show the text of context clues or dialog on-screen |
| Audio transcripts           | A textual transcript of spoken words that is generated from the audio of a video asset |
| Descriptive audio           | A non-primary audio channel that describes the content or context that is occurring on-screen |
| Minimum age gate            | An attribute that can store the minimum age that a viewer must be to view a video (metadata only) |

### Configure video accessibility elements

In the Commerce **Media Library** section for your site, you can upload video assets that have separate files for closed captions, regular audio, and descriptive audio. Closed captions can also be generated automatically when a video asset is uploaded.

#### Generate or upload closed caption files during video asset upload

To have a closed caption file automatically generated when you upload a video, follow this step.

- In the **Asset Upload** dialog box, select **Automatically generate closed captions**. If you're generating a closed caption file, the file selector for closed caption files will be unavailable in the dialog box.

To manually upload a closed caption file when you upload a video, follow this step.

- In the **Asset Upload** dialog box, clear **Automatically generate closed captions**.

To upload regular audio or descriptive audio files for the video, use the file selector in the **Asset Upload** dialog box.

> [!NOTE]
> Closed caption, regular audio, and descriptive audio assets can also be added after a video asset is uploaded. Go to **Media Library**, select the video asset, and select **Edit** to check it out. Then, in the properties pane for the video asset, upload the additional assets.

#### Edit CC and audio transcript files

CC and audio transcript files can be edited directly in the authoring tool. Video playback is available during editing.

To edit CC and audio transcript files, follow these steps.

1. Go to **Media Library**, and select the file name of the video asset. The closed caption and transcript content editor appears.
1. Select **Edit**.
1. Edit the closed caption or transcript text.
1. When you've finished, select **Save**, and then select **Finish editing**.
1. When you're ready to publish, select **Publish**.

#### Set the Minimum Age attribute

A **Minimum Age** metadata attribute can be associated with video assets.

To set the **Minimum Age** attribute for a video asset, follow these steps.

1. Go to **Media Library**, and select the video asset.
1. Select **Edit**.
1. In the properties pane for the video asset, set the **Minimum Age** attribute.

> [!NOTE]
> The properties pane is used only to set and store the metadata attribute value. Customized modules must be created to use this attribute for playback gating.

## Additional resources

[Accessibility in forms, products, and controls](/dynamics365/unified-operations/dev-itpro/user-interface/enable-accessibility)

[Microsoft Accessibility Center](https://www.microsoft.com/accessibility)

[Dynamics 365 Accessibility Center](/dynamics365/get-started/accessibility/index)

[Compliance overview](compliance-overview.md)

[Cookie compliance](cookie-compliance.md)

[Add a privacy policy page](add-privacy-page.md)

[Replace user IDs associated with tracked content changes](dev-itpro/replace-IDs-tracked-changes.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
