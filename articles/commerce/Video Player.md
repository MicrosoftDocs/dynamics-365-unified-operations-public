---
# required metadata

title: Video Player
description: This topic reviews setting up an e-Commerce page with the Video Player module.
author: anupamar-ms
manager: BrendanSullivanMSFT
ms.date: 08/30/2019
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anupamar
ms.search.validFrom: 2019-08-30
ms.dyn365.ops.version: 

---

# Video Player 

Video player is used to support video playback. There are two video players that are supported in starter kit– Ambient Video Player and Video Player. They both support mp4 media type.

## Ambient video player 

Ambient video player supports short informational videos. It should be used for videos less than 5 seconds. It supports limited video playback controls such as play and pause.  

### Usage examples for ecommerce: 

- Short informational video highlighting new products on home page.  
- Short informational video highlighting product features on a product details page 



Properties for Ambient video player :

| Property name     | Values        | Property Description                                         |
| ----------------- | ------------- | ------------------------------------------------------------ |
| Auto play         | True or False | Auto plays the video when this setting is turned on          |
| Mute              | True or False | Mutes the audio. The default value is True for this player. In Chrome browser, autoplay videos will be muted by default, audio will be played only if the user plays the video.  |
| Loop              | True or False | Repeats the video in a loop when this setting is turned on   |
| Media             |               | This is video file that should be played in the video player. |
| Playback controls | True or False | When this setting is true, a Play/Pause button will be shown on the video. If this setting is false, the play/pause button will not be shown but the video can still be paused or resumed using keyboard action |

 

## Video Player 

Video player can be used for videos that we want to showcase in the ecommerce site. It supports all play back capabilities such as play, pause, full size, closed captions etc. The video player supports closed captions and also supports customization of closed captions – font size, background color etc to meet Microsoft Accessibility Standards. 

Usage examples for ecommerce: 

- It can be used for instructional video in product details page or marketing page 
- It can be used to market promotions and policies on any marketing page 
- It can be used to market products by highlighting its features on a product details page or marketing page 

 

Properties for Video player:

| Property name          | Values        | Property Description                                         |
| ---------------------- | ------------- | ------------------------------------------------------------ |
| Auto play              | True or False | Auto plays the video when this setting is turned on          |
| Mute                   | True or False | Mutes the audio. The default value is false for this player. In Chrome browser, autoplay videos will be muted by default, audio will be played only if the user chooses to play the video.  |
| Loop                   | True or False | Repeats the video in a loop when this setting is turned on   |
| Media                  |               | This is the video file that should be played in the video player|
| Playback controls      | True or False | When this setting is true, a Play/Pause button will be shown on the video. If this setting is false, the play/pause button will not be shown but the video can still be paused or resumed using keyboard action |
| Play full screen       | True or False | The video can be played in full screen if this option is true |
| Controls               | True or False | All controls will be shown when this option is shown. This includes Play, Pause, Progress, Closed captions etc |
| Hide poster frame      | True, False   | A video can have a poster frame. If this setting is true, the poster frame will be hidden |
| Mask level             | 0-100         | A mask can be applied to the video for styling.              |
| Full screen icon style | Square Arrow  | This defines the style of the full screen icon shown on the video player. |


## Creating a page with a Video player module  

This section explains how to add a video player module to a new page and set the required properties. Refer to Templates and Pages for more details. 

1. We need to first create a template. In tooling, create a new page template “Video player template”. 

2. In the Main slot of the Default Page, add a Container module. See Container topic for more details. 

3. To the Container, add a Video player module and Ambient Video player module. 

4. Check-in and Publish.  

5. Now create a new page with the “Video player template” and call it “Video player page” 

6. In the page outline, add Ambient Video player module to the Main slot 

7. In the settings for Ambient Video player module, go to Media and upload a video file. You can change the Auto play, Loop and other properties as needed.

8. Save and Preview 

9. Go back to the page outline, add Video player module to the Main slot 

10. In the settings for Video player module, go to Media and upload a video file.  

11. Save and Preview. On Preview, you should see both video modules on the page. Additional settings can be changed to customize the behavior of each module 

12. Check-in and Publish
