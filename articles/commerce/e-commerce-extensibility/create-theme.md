---
# required metadata

title: Create a new theme
description: This topic describes how to create a new theme for a Dynamics 365 Commerce online site. 
author: samjarawan
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
ms.author: samjar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---
# Create a new theme

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic describes how to create a new theme for a Dynamics 365 Commerce online site.  

## Overview

Dynamics 365 Commerce enables you to apply a theme to your entire online site, and also to individual templates or pages. For example, you may have a default theme set up site-wide, and also have a campaign theme which is only applied to some pages of the site.

Once a theme is created and uploaded to your production site, authoring tools can be used to set the theme on your site. Themes can be set in a template, layout, or single page. When an online page is rendered, the appropriate theme will be applied, giving all the modules on that page a consistent look and feel.

## Create the theme directory and theme file

To create a new theme, do the following.

1. Create a new directory under the **/src/themes** directory, using the local name of the theme.
1. In the new directory, create a new **&#42;.theme.scss** file, using the local name of the theme.

For example, to create a new theme called **spring**, the steps would be as follows.

1. Create a new directory **spring** under the  **/src/themes/** directory.
1. In the **/src/themes/spring** directory, create a new file named **spring.theme.scss**.  

The following example shows a theme file that has pulled in Bootstrap and FontAwesome dependencies.

```
$fa-font-path: 'https://use.fontawesome.com/releases/v5.2.0/webfonts' !default;
@import "bootstrap/scss/bootstrap";
body {
    background: purple;
    color: yellow;
}
```

### Naming convention

Note that themes are registered as **THEMENAME**.theme.scss where **THEMENAME** is the local name of your theme.  Using the **app.settings.json** file, you provide the friendly name for your theme which will show up in the authoring tools.

## Test a theme
It is easy to test a theme in your development environment using the following query string parameter: **?theme=THEME_NAME**.

To test your theme, do the following.

1. In a command prompt under the directory of your local code repository, run **yarn start**. 
1. Load a module test page in a web browser and add the query string parameter **?theme=THEME_NAME**. 

Example: `https://localhost:4000/modules?type=campaignBanner&theme=spring`

## Expose themes to authoring tools

For themes to appear in the tooling theme selector, there must be a "themes" entry in the **\src\settings\app.settings.json** file that specifies the friendly name of the theme. Below shows an example entry for a spring theme.

```json
{
    "config":{
        "logoUrl":{
            "type": "image",
            "friendlyName": "Logo Image",
            "description": "Logo Image"
        }
    },
    "routes": {
        "cart": {
            "friendlyName": "Cart Page Route",
            "description": "Cart Page Route",
            "default": "/cart2"
        },
        "checkout": {
            "friendlyName": "Checkout Page Route",
            "description": "Checkout Page Route",
            "default": "/checkout"
        }
    },
    "themes": {
        "spring":{
            "friendlyName": "Spring Theme"
        }
    }
}
```

