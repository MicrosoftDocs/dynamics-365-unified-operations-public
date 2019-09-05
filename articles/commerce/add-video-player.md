---
# required metadata

title: Add a video player module to a page
description: This topic covers video player modules and how to add them to site pages in Dynamics 365 Commerce.
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

This topic covers video player modules and how to add them to site pages in Dynamics 365 Commerce.

## Overview

Video player modules are used to support video playback. There are two video player modules that are provided in the store starter kit, the ambient video player module and the video player module. They both support the .mp4 media type.

## Ambient video player module

The ambient video player module supports short informational videos. It should be used for videos less than 5 seconds long, and supports limited video playback controls such as play and pause.  

### Examples of ambient video player module uses in e-Commerce

- Short informational videos highlighting new products on home page  
- Short informational videos highlighting product features on a product details page 

### Ambient video player module properties

| Property name     | Values        | Property Description                                         |
| ----------------- | ------------- | ------------------------------------------------------------ |
| Autoplay         | True or False | Autoplays the video when this property is set to True          |
| Mute              | True or False | Mutes the audio. The default value is True for this player. In the Chrome browser, autoplay videos will be muted by default, and audio will be played only if the user plays the video.  |
| Loop              | True or False | Repeats the video in a loop when this property is set to True   |
| Media             |               | The video file to be played by the video player |
| Playback controls | True or False | When this property is set to True, a play/pause button will be shown on the video. If this property is set to False, the play/pause button will not be shown but the video can still be paused or resumed using the keyboard |

## Video player module

The video player module can be used to showcase videos on an the ecommerce site. It supports all playback capabilities such as play, pause, full size, closed captions, etc. In addition to supporting closed captions, the video player module also supports customization of closed captions such as font size and background color to meet Microsoft accessibility standards. 

### Examples of video player module uses in e-Commerce 

- Instructional videos on product details or marketing pages 
- Promotions and policies videos on any marketing page 
- Marketing videos that highlight product features on product details or marketing pages 


### Video player module properties

| Property name          | Values        | Property Description                                         |
| ---------------------- | ------------- | ------------------------------------------------------------ |
| Auto play              | True or False | Autoplays the video when this property is set to True          |
| Mute                   | True or False | Mutes the audio. The default value is False for this player. In the Chrome browser, autoplay videos will be muted by default, and audio will be played only if the user chooses to play the video.  |
| Loop                   | True or False | Repeats the video in a loop when this property is set to True   |
| Media                  |               | The video file to be played in the video player|
| Playback controls      | True or False | When this property is set to True, a lay/pause button will be shown on the video. If this property is set to False, the play/pause button will not be shown but the video can still be paused or resumed using the keyboard |
| Play fullscreen       | True or False | The video can be played in full screen if this property is set to True |
| Controls               | True or False | All controls will be shown when this property is set to True. This includes play, pause, progress, closed captions, etc. |
| Hide poster frame      | True or False   | A video can have a poster frame, and if this property is set to True, the poster frame will be hidden |
| Mask level             | 0-100         | A mask that can be applied to the video for styling             |
| Fullscreen icon style | Square or Arrow  | This property defines the style of the fullscreen icon shown on the video player |

## Add a video player module to a page 

To add a video player module to a new page and set the required properties, do the following.

1. Create a new page template named "video player template." 
1. In the **Main** slot of the default page, add a container module. 
1. In the container module, add video player and ambient video player modules. 
1. Check in the template and publish.  
1. Create a new page using the video player template you created named "video player page." 
1. In the **Main** slot of the new page, add an ambient video player module. 
1. In the settings for the ambient video player module, go to **Media** and upload a video file. You can change the autoplay, loop, and other properties as needed.
1. Save and preview the page. 
1. In the **Main** slot of the new page, add a video player module. 
1. In the settings for the video player module, go to **Media** and upload a video file.  
1. Save and preview the page. You should see both video modules on the page. Additional settings can be changed to customize the behavior of each module.
1. Check in and publish the page.
