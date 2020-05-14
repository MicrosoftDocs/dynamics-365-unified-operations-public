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

A style preset is a stored set of all authorable style values across a site's theme, and can be used to immediately alter the look of a site from within site builder. Style presets enable Commerce site builder authors to change, preview, and activate a set of style values across their site quickly without the need for cascading style sheets (CSS) or theme deployment. For example, font styles, button styles, and site colors are all common style variables that can be managed through style presets. The available set of style variables within a site is determined by the theme and module library deployed to a site's tenant. The Dynamics 365 Commerce online software development kit (SDK) enables developers to implement as many (or as few) authorable style variables as they need for a given theme. By enabling more style variables, a theme developer can put final site style choices into the hands of site builder authors. This ability enables non-developers to update and preview site styles within the toolset, and is also useful for any scenario where direct theme or CSS changes would cause unnecessary overhead.  

Themes that have enabled authorable style variables will require a default style preset, and can optionally include additional preset options as part of a deployed theme package. For example, a theme could deploy with a single default "modern light" style preset, or it could include additional style preset options such as the default preset plus "modern dark," "vintage light," or "vintage dark." Such built-in theme presets are created by developers, and can be used as starting points for new site design. Within site builder, authors can choose from a theme's built-in presets, or they can create their own style presets and customizations using enabled style variables. A style preset can be previewed in site builder before activating it on the live site.  Once an author's style changes are reviewed, the style preset can then be set to "'active"' for the live site.

## Preview a style preset

To preview a style preset on your site in site builder, follow these steps.

1. In the left navigation pane for your site, go to **Site Settings \> Design**.
1. Select the **Style presets** tab at the top of the design editor.
1. From the **Available presets** list, choose one preset and then select **View** to navigate to the preset editor. If there are no presets currently under **Available presets**, see [Create a custom style preset](#create-a-custom-style-preset) for instructions on how to create a custom style preset.

    >[!NOTE]
    >Presets that came with the theme are indicated with a **Built-in** badge. These built-in presets are read-only. To copy any built-in preset as a new customizable preset, select **Save as** from the existing preset's ellipsis menu ("**...**").

1. On the command bar, select **Preview**.
1. Choose a URL from your site to use for previewing the style preset, and then select **OK**.
1. Choose the channel and locale-specific URL variant you with to preview by selecting the variant's name. A new preview browser window will then launch with your selected style preset applied to the chosen page.

>[!NOTE]
>The preview URL is persistent and authenticated, which means you can copy, paste, and send it to other authenticated co-workers for review prior to setting it active on your live site. The preview URL is also useful for checking styles on different devices, browsers, and screens. 

>[!TIP]
>While editing a style preset, it can be helpful to leave its full preview window open in a separate browser window for quickly validating changes. After saving changes to a preset, refresh the open preview browser window to validate the user experience.

## Create a custom style preset

To create a custom style preset in site builder, follow these steps.

1. In the left navigation pane for your site, go to **Site Settings \> Design**.
1. Select the **Style presets** tab at the top of the design editor.
1. On the command bar, select **New preset**.
1. Enter a name and description for the new preset, and then select **Save**. A new customizable preset is then created that uses the theme's default values as a starting point. 

>[!NOTE]
>A new custom style preset can also be created from any existing preset by selecting **Save as** from an existing preset's ellipsis menu ("**...**"), or from the command bar within the preset editor. 

## Modify global and module type style values

Some of a theme's style variables are shared between multiple module types. These style variables are referred to as **global**.  Examples of common global type style variables include primary site colors, default font styles, or button styles. Setting global variables may change the look across many different module types.  

Some style values can be unique to a module type, or may need to optionally override a default global value. If a site's theme has implemented module type style variables, site builder authors can customize the style of a module type independent from the global settings. Module type variables can either augment or override the global style variables within a theme.

>[!NOTE]
>The hierarchy of style values within a site will behave as follows, where the style values on the right override the values to the left:
>
>**Theme default values** \< **Global style values** \< **Module type style values**  \< **CSS override**.

To change a style preset's global or module type values in site builder, follow these steps.

1. In the left navigation pane for your site, go to **Site Settings \> Design**.
1. Select the **Style presets** tab at the top of the design editor.
1. Select **View** for any style preset to navigate to the preset editor.
1. Select **Preview** and then follow the URL selection steps to open a full browser window preview for your preset. Leave this preview browser window open.
1. In the preset editor, select **Edit** on the upper right.
1. Using the style variable controls in the editor, change some global style values.
1. At the top of the editor, Select the **Modules** tab to the right of the **Global** tab.
1. Select a module type that needs to be styled.
1. Using the style controls, change some values for the module type.
1. When ready to preview, select **Save** on the command bar.  
1. Return to the open preview window and refresh the URL. The full browser window preview is useful for checking style changes at different view breakpoints, browsers, and device platforms.
1. When all changes are complete and validated, select **Finish editing** on the upper right of the editor.

>[!NOTE]
>If you are editing the currently active preset on your site, you will see a blue **Active** badge in the editor to indicate that it is currently live on your website. If you make changes to the active preset, selecting **Publish** will push these changes to your live site.

## Set a new style preset active on your live site

To set a style preset as the new active one on your site, do the following.

- Select the **Set as active button** on either:
    - The command bar in style preset editor.
    - The ellipsis menu ("**...**") on any available preset from within the main **Design \> Style presets** view.

This will make a preset's style values active across your public facing website.

## Additional resources

[Add a logo](add-logo.md)

[Select a site theme](select-site-theme.md)

[Work with CSS override files](css-override-files.md)

[Add a favicon](add-favicon.md)

[Add a welcome message](add-welcome-message.md)

[Add a copyright notice](add-copyright-notice.md)

[Add languages to your site](add-languages-to-site.md)

[Add script code to site pages to support telemetry](add-telemetry.md)




