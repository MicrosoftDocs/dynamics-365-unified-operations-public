---
# required metadata

title: Extend a theme from a base theme
description: This topic describes how to extend a theme from a base theme for a Microsoft Dynamics 365 Commerce online site. 
author: samjarawan
manager: annbe
ms.date: 06/29/2020
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
# Extend a theme from a base theme

[!include [banner](../includes/banner.md)]

This topic describes how to extend a theme from a base theme for a Microsoft Dynamics 365 Commerce online site.

## Overview

By using the Dynamics 365 Commerce online store extensibility software development kit (SDK), you can create either themes that are standalone themes or themes that are extended from a base theme. For example, you can have a base theme that defines Cascading Style Sheets (CSS) styles for modules, module view extensions, and module definition extensions. You can then have a different theme, or even a set of themes, that adds changes on top of the base theme. This capability is helpful when a single Dynamics 365 environment has multiple online sites that use different theme branding.

## Specify a base theme

To specify the base theme for a theme, edit the theme definition file, and add a **$ref** section that points to the base theme.

In the following example, the **$ref** section references the **fabrikam** sample theme that is included as part of the store starter kit.

```json
{
    "$ref": "@msdyn365-commerce-modules/fabrikam-design-kit/dist/lib/modules/fabrikam/fabrikam.definition.json",
    "$type": "themeModule",
    "description": "This is SDK template theme module",
    "friendlyName": "adventureworks",
    "name": "adventureworks"
}
```

## Examples

In the following example, the **add-theme** command-line interface (CLI) command is used to create a base theme.

```console
yarn msdyn365 add-theme base
```

Here is the definition file for the base theme that is created.

**basetheme.definition.json**

```json
{
    "$type": "themeModule",
    "description": "This is SDK template theme module",
    "friendlyName": "base",
    "name": "base"
}
```

Next, the CLI command is used to create a theme that is named **extended**.

```console
yarn msdyn365 add-theme extended
```

The definition file for the extended theme can now reference the base theme by using a relative path, as shown here.

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

### Include base theme styles

By default, base theme styles aren't included in the extended theme. To include the base theme styles, you can add a reference in the **extended.theme.scss** file, as shown here. This example also shows how to add other styles.

**extended.theme.scss**

```scss
@import "../../base/styles/base.theme.scss";

body {
    background-color: red;
}
```

The following example resembles the previous example. It shows that you can also add a reference to the base theme in the **extended.definition.scss.json** file, if you want.

**extended.definition.scss.json**

```json
{
    "$ref": "../../base/styles/base.definition.scss.json",
    "name": "extended"
}
```

## Additional resources

[Theming overview](theming.md)

[Create a theme](create-theme.md)

[Configure theme settings](configure-theme-settings.md)

[Configure theme style presets](theme-style-presets.md)

[Extend a theme to add module extensions](theme-module-extensions.md)
