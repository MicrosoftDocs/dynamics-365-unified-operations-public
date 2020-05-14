---
# required metadata
title: Work with style presets
description: This topic describes how to work with site style presets in Dynamics 365 Commerce site builder. 
author: phinneyridge
manager: annbe
ms.date: 05/14/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
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
ms.author: niholman
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5
---

# Work with style presets

[!include [banner](includes/banner.md)]

This topic describes how to work with site style presets in Dynamics 365 Commerce site builder.

## Overview

Style presets enable Commerce site builder authors to change, preview, and activate a set of style values accross their site quickly without need for cascading style sheets (CSS) or theme deployment. For example, font styles, button styles, and site colors are all common style variables that can be managed through style presets. The available set of style variables within a site is determined by the theme and module library deployed to a site's tenant. The Dynamics 365 Commerce online software development kit (SDK) enables developers to implement as many, or as few, authorable style variables as they need for a given theme. By enabling more style variables, a theme developer can put final site style choices into the hands of site builder authors. This makes previewing and updating site styles within the toolset possible for non-developers, or for any scenario where direct theme or CSS changes would cause unnecessary overhead.  

A style preset is a stored set of all authorable style values accross a site's theme, and can be used to immediately alter the look of a site from within site builder. Themes that have enabled authorable style variables will require a default style preset, and can optionally include additional preset options as part of a deployed theme package. For example, a theme could deploy with a single default "modern light" style preset, or it could include additional style preset options such as the default preset plus "modern dark," "vintage light," or "vintage dark." Such built-in theme presets are created by developers, and can be used as starting points for new site design. Within site builder, authors can choose from a theme's built-in presets, or they can create their own style presets and customizations using enabled style variables. A style preset can be previewed in site builder prior to activating it on the live site.  Once an author's style changes are reviewed, the style preset can then be set to "'active"' for the live site.

## Preview a style preset

To preview a style preset on your site in site builder, follow these steps.

1. In the left navigation pane for your site, select **Design**. In some environments you may first need to expand **Site Settings** in the lower left of the navigation pane.
1. Select the **Style presets** tab at the top of the design editor.
1. From the **Available presets** list, select one preset and then select **View** to navigate to the preset editor. If there are no options under **Available presets**, see [Create a custom style preset](#create-a-custom-style-preset) below for instructions on how to create a custom style preset.

    >[!NOTE]
    >Presets that came with the theme are indicated with a **Built-in** badge. These built-in presets are read-only, so use the **Save as** option on the ellipsis menu ("**...**") to copy any built-in preset as a new customizable preset.

1. On the command bar, select **Preview**.
1. Choose a URL from your site to use for previewing the style preset, and then select **OK**.
1. Choose the channel and locale-specific URL variant you with to preview by selecting the variant's name. This will launch a new browser window with your selected style preset applied to the chosen page where you can preview it.

    >[!NOTE]
    >The preview URL is persistent and authenticated, which means you can copy, paste, and send it to other authenticated co-workers for review prior to setting it active on your live site. The preview URL is also useful for checking styles on different devices, browsers, and screens. 

    >[!TIP]
    >While editing a style preset, it can be helpful to leave its full preview window open in a separate browser window for quickly validating changes. After saving changes to a preset, refresh the open preview browser window to validate the user experience.

## Create a custom style preset

To create a custom style preset in site builder, follow these steps.

1. In the left navigation pane for your site, go to **Site Settings \> **Design**.
1. Validate that you are in the **Style presets** tab at the top of the design editor.

1. Click on the **New preset** button in the action bar.

1. Enter a name and description for the new preset, and click **Save**.

1. This will create a new customizable preset with the theme's default values as its starting point. 

   >[!Note]
   >A new custom style preset can also be created from any existing preset by using the **Save as** option within an existing preset's elipse button menu ("**...**"), or the action bar within the preset editor. 

## Modify global and module-type style values

Some of a theme's style variables are shared between mutiple module types.  These style variables are refered to as **global**.  Examples of common global variables include primary site colors, default font styles, or button styles.  Setting global variables may change the look accross many different module types.  

Other style values can be unique to a module type, or may need to optionally over-ride a default global value.  If the site's theme has implemented module type style variables, then site builder authors can customize the style of a module type, independent from the global settings.  Module type variables can either augment or over-ride the global style variables within a theme.

   >[!Note]
   >The hierarchy of style values within a site will behave as follows:
   >**Theme default values**  < **Global style values** < **Module type style values**  < .**CSS override**, where the style values on the right, override the values to the left.

To change a style preset's global or module level values in site builder, follow these steps.

1. In site builder, click on **Design** from the left navigation pane.

   >[!Note]
   >In some environments you will need to first exapand **Site Settings**  in the lower left of the navigation pane to see the **Design** tab.

1. Validate that you are in the **Style presets** tab at the top of the design editor. 

1. Click the **View** button on any style preset to navigate to the editor.

1. Click the **Preview** button  and follow the URL selection steps to open a full browser window preview for your preset.   

1. Leave this preview browser window open, and return to the style editor browser window.

1. Click the **Edit** button in the upper right of the editor.

1. Change some global style values using the the style variable controls in the editor.

1. Now click the **Modules** tab to the right of the **Global** tab at the top of the editor.

1. Select a module type that needs to be styled.

1. Change some values for the module type using the style controls.

1. When ready to preview, click **Save** in the action bar.  

1. Return to the open preview window from *step 5* above and refresh the URL.  

    >[!Note]
    >Full browser window preview is usefull for checking style changes at different view breakpoints, browsers, and even different device platforms, just as your end-users will see it.

1. Repeat *steps 7-9* until changes are complete and validated, then click **Finish editing** in the upper right of the editor.

   >[!Note]
   >If you are editing the currently active preset on your site, you will see a blue **Active** badge in the editor to indicate that it is already live on your website.  If you make changes to the active preset, clicking the **Publish** button will push these changes to your live site.

## Set a new style preset active on your live site

To set a style preset as the new active one on your site, follow these steps.

* Click the **Set as active button** in either:

  * The action bar in style preset editor 

    or,

  * The elipse button menu ("**...**") on any available preset card within the main **Design > Style presets** view.

This will make a preset's style values active accross your public facing website.

## Additional resources

[Add a logo](add-logo.md)

[Select a site theme](select-site-theme.md)

[Work with CSS override files](css-override-files.md)

[Add a favicon](add-favicon.md)

[Add a welcome message](add-welcome-message.md)

[Add a copyright notice](add-copyright-notice.md)

[Add languages to your site](add-languages-to-site.md)

[Add script code to site pages to support telemetry](add-telemetry.md)




