---
# required metadata

title: Add a video player module to a page
description: This topic covers video player modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
manager: annbe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-retail
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application user
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anupamar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---

# Add a video player module to a page

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic covers video player modules and describes how to add them to site pages in Microsoft Dynamics 365 Commerce.

## Overview

Video player modules are used to support video playback. Two video player modules are provided in the store starter kit: the ambient video player module and the video player module. Both players support the .mp4 media type.

## Ambient video player module

The ambient video player module supports short informational videos. It should be used for videos that are less than five seconds long. This player supports limited video playback capabilities, such as play and pause.

### Examples of ambient video player modules in e-Commerce

- Short informational videos that highlight new products on the home page
- Short informational videos that highlight product features on a product details page

### Ambient video player module properties

| Property name     | Value                 | Description |
|-------------------|-----------------------|-------------|
| Autoplay          | **True** or **False** | When the value is set to **True**, the video is automatically played. |
| Mute              | **True** or **False** | When the value is set to **True**, the audio is muted. For this player, the default value is **True**. In the Google Chrome browser, autoplay videos are muted by default, and the audio is played only if the user manually plays the video. |
| Loop              | **True** or **False** | When the value is set to **True**, the video is repeated in a loop. |
| Media             |                       | The video file that is played by the video player. |
| Playback controls | **True** or **False** | When the value is set to **True**, a play/pause button is shown on the video. If the value is set to **False**, the play/pause button isn't shown, but users can still pause and resume the video by using the keyboard. |

## Video player module

The video player module can be used to showcase videos on an e-Commerce site. It supports all playback capabilities, such as play, pause, full-size mode, and closed captions. The video player module also supports customization of closed captions to meet Microsoft accessibility standards. For example, you can customize the font size and background color.

### Examples of video player modules in e-Commerce

- Instructional videos on product details pages or marketing pages
- Promotional videos or videos about policies on any marketing page
- Marketing videos that highlight product features on product details pages or marketing pages

### Video player module properties

| Property name         | Value                               | Description |
|-----------------------|-------------------------------------|-------------|
| Auto play             | **True** or **False**               | When the value is set to **True**, the video is automatically played. |
| Mute                  | **True** or **False**               | When the value is set to **True**, the audio is muted. For this player, the default value is **False**. In the Chrome browser, autoplay videos are muted by default, and the audio is played only if the user manually plays the video. |
| Loop                  | **True** or **False**               | When the value is set to **True**, the video is repeated in a loop. |
| Media                 |                                     | The video file that is played in the video player. |
| Playback controls     | **True** or **False**               | When the value is set to **True**, a play/pause button is shown on the video. If the value is set to **False**, the play/pause button isn't shown, but users can still pause and resume the video by using the keyboard. |
| Play fullscreen       | **True** or **False**               | When the value is set to **True**, the video is played in full-screen mode. |
| Controls              | **True** or **False**               | When the value is set to **True**, all controls are shown. These controls include play and pause buttons, a progress indicator, and closed captions. |
| Hide poster frame     | **True** or **False**               | A video can have a poster frame. When the value of this property is set to **True**, the poster frame is hidden. |
| Mask level            | A number from **0** through **100** | The mask that is applied to the video for styling. |
| Fullscreen icon style | **Square** or **Arrow**             | The style of the full-screen icon that is shown in the video player. |

## Add a video player module to a page

To add a video player module to a new page and set the required properties, follow these steps.

1. Create a page template that is named **video player template**.
1. In the **Main** slot of the default page, add a container module.
1. In the container module, add video player and ambient video player modules.
1. Check in the template, and publish it.
1. Use the video player template that you just created to create a page that is named **video player page**.
1. In the **Main** slot of the new page, add an ambient video player module.
1. In the settings for the ambient video player module, go to **Media**, and upload a video file. You can change the **Autoplay**, **Loop**, and other properties as you require.
1. Save and preview the page.
1. In the **Main** slot of the new page, add a video player module.
1. In the settings for the video player module, go to **Media**, and upload a video file.
1. Save and preview the page. You should see both video modules on the page. You can change additional settings to customize the behavior of each module.
1. Check in the page, and publish it.
