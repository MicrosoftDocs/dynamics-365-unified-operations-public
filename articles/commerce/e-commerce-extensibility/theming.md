---
# required metadata

title: Theming overview
description: This topic presents an overview of online site theming in Microsoft Dynamics 365 Commerce.
author: samjarawan
manager: annbe
ms.date: 10/08/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: samjar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---
# Theming overview

[!include [banner](../includes/banner.md)]

This topic presents an overview of online site theming in Microsoft Dynamics 365 Commerce.

## Overview

Dynamics 365 Commerce lets you apply a theme to your whole online site, individual templates, or individual pages. For example, you might have a default theme that is set for the whole online site and a campaign theme that is applied to just a subset of the pages on the site. 

Themes include Sassy Cascading Style Sheets (SCSS) files that you can use to format your site pages and modules. They can optionally also contain module view and definition extensions, so that modules can render different views, depending on the theme that is selected. 

After a theme is created and uploaded to your production site, you can use the Commerce site builder tool to set the theme for the site. You can set the site's theme in a template, in a layout, or on a single page. When an online page is rendered, the appropriate theme is applied, so that all the modules on that page have a consistent look and feel. The site builder tool also lets you upload additional Cascading Style Sheets (CSS) overrides. In that way, you can make changes on top of the selected theme.

The following illustration shows how a theme is selected for a page in Dynamics 365 Commerce. Notice that the page container (**Default page**) is selected, and the **Theme** field for the page appears in the properties pane on the right.

![Theme selection](media/theming-1.png)

A theme can be set on the master page in a similar manner. In this case, the theme is applied to all pages that are derived from the master page. Note that if the **locked** property is turned off, individual pages can override the theme.

## General guidelines for creating a custom theme

- Create a new theme by using the **yarn msdyn365 add-theme NEW_THEME_NAME** command-line interface (CLI) command. This command will create a theme in the /src/themes/ folder.
- Under the styles directory, you will find the SCSS entry point file for the theme. This file uses the naming pattern **THEME_NAME.theme.scss**. 
- Themes are created as special modules. They contain definition files that include the theme's friendly name and description, and also a template React component.
- There is no limit to the number of .scss files that your theme can contain.
- Your theme entry point can import other .scss files by using relative paths.

## Best practices

- Module library modules are built by using Bootstrap 4 classes. Therefore, we recommend that every theme include either Bootstrap 4 or Bootstrap 4 RTL as the  SCSS framework.
- If you want to take advantage of module library modules that are built by using Font Awesome glyph icons, you should include **font-awesome** in the SCSS file. The following example shows how to include **Bootstrap** and **font-awesome** in a SCSS file.

    ```css
    $fa-font-path: 'https://use.fontawesome.com/releases/v5.2.0/webfonts' !default;
    @import "bootstrap/scss/bootstrap";
    ...
    ```

## Recommended structure for a custom theme

This section shows the recommended structure for any custom theme. 

Import or define the following items:

- Fonts and glyph icons
- Mix-ins and functions:

    - **Bootstrap:** Dependencies, excluding components and utilities
    - **Shared components:** Dependencies, excluding components and utilities
    - Custom theme mix-ins and functions

- Theme variables:

    - Custom theme variables
    - **Bootstrap:** Default theme variables (fallbacks)

- SCSS for components and modules:

    - **Shared components:** Components
    - Custom components and modules

- Utilities:

    - Bootstrap, shared component, and custom utilities

## Hooks for module theming

For every module, a class name is defined that matches the module name. In this way, any theme can target the module. This class name should be the first class name that is applied to the outermost element that is rendered by the React component. To allow for more granular theme options, developers can provide additional class names on elements or features of a module. In that way, custom themes can target those elements or features.

## Custom themes

Custom themes can be created by using the Dynamics 365 Commerce online SDK. They can then be stored in the **/src/themes/** folder. For more information, see [Create a theme](create-theme.md).

## RTL and LTR support within a theme

You may have requirements to support both right-to-left (RTL) and left-to-right (LTR) languages on your e-Commerce site. Themes support the ability to specify different RTL and LTR SCSS files. 

> [!NOTE]
> RTL and LTR support within a theme is available in Dynamics 365 Commerce release 10.0.15.

Each theme has a **styles\THEME_NAME.theme.scss** file that is created using the **yarn msdyn365 add-theme** command-line interface (CLI) command. For example, using the command **yarn msdyn365 add-theme spring** to create a new theme called "spring" will create the file "\src\themes\spring\styles\spring.theme.scss", which contains the SCSS code for the theme. SCSS files are compiled into CSS files when using the **yarn start** or **yarn pack** commands, and are then used to render site pages. 

To support specific RTL or LTR versions of a SCSS file, you can provide additional files using the following file naming convention: **THEME_NAME.rtl.theme.scss** for RTL support and **THEME_NAME.ltr.theme.scss** for LTR support. When a page renders, the appropriate CSS file will be referenced according to the browser language setting. If you only need support for a single language, use the default **THEME_NAME.theme.scss** file.

## RTL and LTR best practices

Because the CSS code used in RTL and LTR layouts is generally the same except for a few properties, those differing properties can be specified in their respective "theme" files and a "base-style" file can be created to be shared (and imported) by both the RTL and LTR SCSS files.

- **THEME_NAME-rtl.theme.scss** - Contains specific properties for the RTL layout.
- **THEME_NAME-ltr.theme.scss** - Contains specific properties for the LTR layout.
- **base-style.scss** - Contains shared styles and is imported in the two THEME_NAME files.

## Additional resources

[Create a new theme](create-theme.md)

[Configure theme settings](configure-theme-settings.md)

[Configure theme style presets](theme-style-presets.md)

[Extend a theme to add module extensions](theme-module-extensions.md)

[Override a module library component in a theme](override-theme-component.md)

[Extend a theme from a base theme](extend-theme.md)

[Add custom resources to your customization code](add-custom-resources.md)

[CLI command reference](cli-command-reference.md)
