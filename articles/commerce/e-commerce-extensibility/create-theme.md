---
# required metadata

title: Create a new theme
description: This topic describes how to create a new theme for a Microsoft Dynamics 365 Commerce online site. 
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

[!include [banner](../../includes/preview-banner.md)]
[!include [banner](../../includes/banner.md)]

This topic describes how to create a new theme for a Microsoft Dynamics 365 Commerce online site.

## Overview

Dynamics 365 Commerce lets you apply a theme to your whole online site, and also to individual templates or pages. For example, you can have a default, site-wide theme, and you can also have a campaign theme that is applied only to some pages of the site.

After a theme is created and uploaded to your production site, you can use authoring tools to set the theme on the site. Themes can be set in a template, in a layout, or on a single page. When an online page is rendered, the appropriate theme is applied. In this way, all the modules on the page have a consistent look and feel.

## Create the theme directory and theme file

To create a new theme, follow these steps.

1. Under the **/src/themes** directory, create a directory. Use the local name of the theme as the name.
1. In the new directory, create a **\*.theme.scss** file. Use the local name of the theme as the name.

For example, to create a new theme that is named **spring**, follow these steps.

1. Under the **/src/themes/** directory, create a directory that is named **spring**.
1. In the **/src/themes/spring** directory, create a file that is named **spring.theme.scss**.

The following example shows a theme file that pulls in Bootstrap and FontAwesome dependencies.

```
$fa-font-path: 'https://use.fontawesome.com/releases/v5.2.0/webfonts' !default;
@import "bootstrap/scss/bootstrap";
body {
    background: purple;
    color: yellow;
}
```

### Naming convention

Themes are registered as **THEMENAME.theme.scss**, where **THEMENAME** is the local name of your theme. In the app.settings.json file, you provide the friendly name for your theme. This friendly name will appear in the authoring tools.

## Test a theme

You can easily test a theme in your development environment by using the **?theme=THEME\_NAME** query string parameter.

To test your theme, follow these steps.

1. At a command prompt, under the directory of your local code repository, run **yarn start**. 
1. In a web browser, load a module test page, and add the **?theme=THEME\_NAME** query string parameter. Here is an example.

    `https://localhost:4000/modules?type=campaignBanner&theme=spring`

## Surface a theme in the authoring tools

For a theme to appear in the theme selector in the authoring tools, the \\src\\settings\\app.settings.json file must include a **themes** entry that specifies the friendly name of the theme. The following example shows an entry for a theme that is named **spring**.

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
