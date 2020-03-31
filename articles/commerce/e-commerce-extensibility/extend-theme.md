---
# required metadata

title: Extend a theme
description: This topic describes how to create a theme based off of another theme for a Microsoft Dynamics 365 Commerce online site. 
author: samjarawan
manager: annbe
ms.date: 03/31/2020
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
ms.dyn365.ops.version: Release 10.0.11

---
# Extend a theme

[!include [banner](../includes/banner.md)]

This topic describes how to create a theme based off of another theme for a Microsoft Dynamics 365 Commerce online site.

## Overview

Using the Dynamics 365 Commerce online store extensibility SDK, themes can be created to be stand alone themes or extended from a base theme. For example, you can have a base theme that defines module CSS styles, module view extensions and module definition extensions then have a different theme (or set of themes) that add additional changes on top of the base theme. This is helpful when a single Dynamics 365 environments has multiple online sites with different theme branding.

## Setting a base theme

To specify a base theme on a theme, edit the theme definition file and add a '$ref' section pointing to the base theme.

In the below example, notice the "$ref" that's been addded to reference the fabrikam sample theme which is included as part of the store starter kit.

```json
{
    "$ref": "@msdyn365-commerce-modules/fabrikam-design-kit/dist/lib/modules/fabrikam/fabrikam.definition.json",
    "$type": "themeModule",
    "description": "This is SDK template theme module",
    "friendlyName": "adventureworks",
    "name": "adventureworks"
}
```

## Example
The below example has a base theme created with the **add-theme** CLI command:
```Console
yarn msdyn365 add-theme base
```
The base theme has a definition file as shown below.

**basetheme.definition.json**
```json
{
    "$type": "themeModule",
    "description": "This is SDK template theme module",
    "friendlyName": "base",
    "name": "base"
}
```

The below example CLI command creates a new theme called "extended".
```Console
yarn msdyn365 add-theme extended
```

The extended theme definition file can now reference the base theme using a relative path as shown below.

**extended.definition.json**
```json
{
    "$ref": "../base/base.definition.json",
    "$type": "themeModule",
    "description": "This is SDK template theme module",
    "friendlyName": "extended",
    "name": "extended"
}

```

### Including base theme styles
By default the styles are not included in the extended theme.  To include the base theme styles you can include the reference in the extended.theme.scss as shown in the below example, which also shows how to add additional scss to the file.

**extended.theme.scss"
```
@import "../../base/styles/base.definition.scss.json";

body {
    background-color: red;
}
```

Similar to above the **extended.definition.scss.json** file can also reference the base theme if desired as shown in the below example.

**extended.definition.scss.json**
```
{
    "$ref": "../../base/styles/base.definition.scss.json",
    "name": "extended"
}
```

## Additional resources

[Theming overview](theming.md)

[Create a theme](create-theme.md)

[Configure theme settings](configure-theme-settings.md)

