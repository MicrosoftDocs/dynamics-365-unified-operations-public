---
# required metadata

title: Creating a new theme
description: This topic will show how to create a new theme. 
author: SamJarawan
manager: annbe
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
ms.author: SamJar
ms.search.validFrom: 2019-08-30
ms.dyn365.ops.version: 

---
# Create a new theme
This topic will cover the process to create a new theme for a Dynamics 365 Commerce online site.  

To create a new theme add a directory under the **/src/themes** directory and a new **.scss** file.

For example, to create a new theme called **spring**:
* Create a new directory **spring** under the  **/src/themes/** directory
* Create a new file **spring.theme.scss** file under **/src/themes/spring/** directory.  

Below is an example theme file that has pulled in Bootstrap and FontAwesome dependencies.

```
$fa-font-path: 'https://use.fontawesome.com/releases/v5.2.0/webfonts' !default;
@import "bootstrap/scss/bootstrap";
body {
    background: purple;
    color: yellow;
}
```

## Testing a theme
It is easy to test your theme on your development environment using the following query string parameter: **?theme=THEME_NAME**.

To get started testing your theme,

* Run **yarn start** in a command prompt under the directory of your local code repository
* Load up your module test page in a web browser and add the additional query string parameter. 

Example: `https://localhost:4000/modules?type=campaignBanner&theme=spring`

## Exposing themes to authoring tools
For themes to show up in the tooling theme selector there needs to be an entry in the **\src\settings\app.settings.json** file.  Below shows an example entry for a spring theme.

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
## Naming convention

Note that themes are registered as **THEMENAME**.theme.scss where **THEMENAME** is the name of your theme.  Via the **app.settings.json** file, you provide the friendly name for your theme which will show up in the authoring tools
