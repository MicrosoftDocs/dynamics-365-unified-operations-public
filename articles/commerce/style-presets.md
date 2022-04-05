---
# required metadata
title: Work with style presets
description: This topic describes how to work with site style presets in Microsoft Dynamics 365 Commerce site builder. 
author: phinneyridge
ms.date: 05/28/2020
ms.topic: article
ms.prod: 
ms.technology: 
# optional metadata
# ms.search.form: 
audience: Application user
# ms.devlang: 
ms.reviewer: v-chgri
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

This topic describes how to work with site style presets in Microsoft Dynamics 365 Commerce site builder.

A style preset is a stored set of all authorable style values across a site's theme. It can be used to immediately change the look of a site from site builder. Style presets let Commerce site builder authors quickly change, preview, and activate a set of style values across their site, without having to use Cascading Style Sheets (CSS) or deploy themes. Font styles, button styles, and site colors are typical examples of style variables that can be managed through style presets.

The set of style variables that is available in a site is determined by the theme and module library that is deployed to a site's tenant. The Dynamics 365 Commerce online software development kit (SDK) lets developers implement as many (or as few) authorable style variables as they require for a given theme. By enabling more style variables, a theme developer can put final choices about site styles into the hands of site builder authors. Therefore, non-developers can update and preview site styles by using the toolset. The capability is also useful for any scenario where direct changes to themes or CSS will cause unnecessary overhead.

Themes where authorable style variables are enabled require a default style preset. They can optionally include additional preset options as part of a deployed theme package. For example, a theme can be deployed that has a single default "modern light" style preset. Alternatively, it might include additional style preset options besides the default preset, such as "modern dark," "vintage light," or "vintage dark." These built-in theme presets are created by developers and can be used as starting points for new site designs.

In site builder, authors can select among a theme's built-in presets, or they can create their own style presets and customizations by using the enabled style variables. A style preset can be previewed in site builder before it's activated on the live site. After an author's style changes are reviewed, the style preset can then be set to "active" for the live site.

## Preview a style preset

To preview a style preset on your site in site builder, follow these steps.

1. In the left navigation pane for your site, go to **Site Settings \> Design**.
1. On the **Style presets** tab at the top of the design editor, in the **Available presets** list, select a preset, and then select **View** to go to the preset editor.

    If there are currently no presets in the **Available presets** list, see [Create a custom style preset](#create-a-custom-style-preset) for information about how to create a custom style preset.

    > [!NOTE]
    > Presets that were included with the theme are indicated by a **Built-in** badge. These built-in presets are read-only. To copy a built-in preset as a new customizable preset, select the ellipsis button (**...**) for the preset, and then select **Save as**.

1. On the command bar, select **Preview**.
1. Select a URL from your site to use to preview the style preset, and then select **OK**.
1. Select the channel-specific and locale-specific URL variant to preview by selecting the variant's name. A new preview browser window is opened, where the selected style preset is applied to the specified page.

> [!NOTE]
> The preview URL is persistent and authenticated. Therefore, you can copy, paste, and send it to other authenticated co-workers for review before you set it to "active" on your live site. The preview URL is also useful for checking styles on different devices, in different browsers, and on different screens.

> [!TIP]
> While you edit a style preset, you might find it helpful to leave the preview browser window for it open in a separate browser window, so that you can quickly validate your changes. After you save your changes to a preset, refresh the open preview browser window to validate the user experience.

## Create a custom style preset

To create a custom style preset in site builder, follow these steps.

1. In the left navigation pane for your site, go to **Site Settings \> Design**.
1. On the **Style presets** tab at the top of the design editor, on the command bar, select **New preset**.
1. Enter a name and description for the new preset, and then select **Save**. A new customizable preset is created that uses the theme's default values as a starting point.

> [!NOTE]
> You can also create a new custom style preset from any existing preset by selecting the ellipsis button (**...**) for that preset and then selecting **Save as**. Alternatively, select **Save as** on the command bar in the preset editor.

## Modify global and module type style values

Some of a theme's style variables are shared among multiple module types. These style variables are referred to as *global* style variables. Examples include primary site colors, default font styles, and button styles. By setting global variables, you might change the look across many different module types.

Some style values can be unique to a module type, or they might have to optionally override a default global value. If a site's theme has implemented module type style variables, site builder authors can customize the style of a module type independently of the global settings. Module type variables can either augment or override the global style variables in a theme.

> [!NOTE]
> The hierarchy of style values in a site behaves in the following manner. Style values that appear farther to the right override the style values to the left of them.
>
> Theme default values \< Global style values \< Module type style values \< CSS override

To change a style preset's global or module type values in site builder, follow these steps.

1. In the left navigation pane for your site, go to **Site Settings \> Design**.
1. On the **Style presets** tab at the top of the design editor, select **View** for any style preset to go to the preset editor.
1. Select **Preview**, and then follow the URL selection steps to open a full-browser-window preview for your preset. Leave this preview browser window open.
1. In the preset editor, select **Edit** in the upper right.
1. Use the style variable controls in the editor to change some global style values.
1. At the top of the editor, on the **Modules** tab to the right of the **Global** tab, select a module type that must be styled.
1. Use the style controls to change some values for the module type.
1. When you're ready to preview your changes, select **Save** on the command bar.
1. Return to the open preview browser window, and refresh it. The full-browser-window preview is useful for checking style changes at different view breakpoints, in different browsers, and on different device platforms.
1. When all changes have been completed and validated, select **Finish editing** in the upper right of the editor.

> [!NOTE]
> If you're editing the style preset that is currently active on your site, you will see a blue **Active** badge in the editor. This badge indicates that the preset is currently live on your website. If you change the active preset, select **Publish** to push those changes to your live site.

## Make a new style preset active on your live site

To set a style preset as the new active preset on your site, follow these steps.

- Select the **Set as active button** in one of these places:

    - The command bar in the style preset editor
    - The ellipsis menu (**...**) for any available preset in the main view on the **Style presets** tab at **Site Settings \> Design**

The preset's style values are made active across your public-facing website.

## Additional resources

[Add a logo](add-logo.md)

[Select a site theme](select-site-theme.md)

[Work with CSS override files](css-override-files.md)

[Add a favicon](add-favicon.md)

[Add a copyright notice](add-copyright-notice.md)

[Add languages to your site](add-languages-to-site.md)

[Add script code to site pages to support telemetry](add-telemetry.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
