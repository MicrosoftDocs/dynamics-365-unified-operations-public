---
# required metadata

title: Add custom static resources
description: This topic describes how to add custom static resources such as font, image, and CSS files to your SDK customization code so that they can be accessed from within your theme.
author: samjarawan
manager: annbe
ms.date: 09/28/2020
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
# Add custom resources

[!include [banner](../includes/banner.md)]

This topic describes how to add custom static resources such as font, image, and Cascading Style Sheet (CSS) files to your software development kit (SDK) customization code so that they can be accessed from within your theme.

## Overview

Some scenarios require adding custom static resources such as font, image, or CSS files that can be accessed from within a module or a theme. These static files can be added to a ```/public``` folder within your SDK customization code so that they will be included in the configuration package generated with the [CLI **yarn msdyn365 pack** command](cli-command-reference.md#pack). Relative paths can then be used to access the resources.

## Example

Resources can be added to the ```/public``` directory or any subdirectory under this directory. For example, adding a font called "NewFont-Regular" may entail adding multiple font files such as "NewFont-Regular.eot", "NewFont-Regular.woff", "NewFont-Regular.ttv", and "NewFont-Regular.svg" to the ```/public``` directory.

After adding files to the ```/public``` directory, relative paths in the Sassy CSS (SCSS) file can then be used to point to them. The following SCSS example is taken from a theme that is located in the ```/src/themes/spring``` folder. When the command-line interface (CLI) command **pack** is used, the SCSS code is compiled into a zip file created in the ```/build/public/static/css/spring``` directory. A relative path is then used to access the font.

```
@import "bootstrap/scss/bootstrap";

@font-face {
    font-family: 'NewRocker-Regular';
    src: url('../../../NewFont-Regular.eot');
    src: url('../../../NewFont-Regular.eot?#iefix') format('embedded-opentype'),
         url('../../../NewFont-Regular.woff') format('woff'),
         url('../../../NewFont-Regular.ttf') format('truetype'),
         url('../../../NewFont-Regular.svg#NewFont-Regular') format('svg');
}

body {
    font-family: 'NewFont-Regular', Fallback, sans-serif;
}
```

## Dynamic access to the public path

When deploying your e-Commerce customizations via Microsoft LifeCycle Services (LCS), the physical paths to any files stored in the ```/public``` directory will change. This means that you cannot provide a static physical path to these files from within your code. However, there is a helper API named **getAsset** which is available to help you obtain the path.

The following example shows how to use the **getAsset** API to generate a URL to a font file stored in the ```/public/webfonts``` directory.

```typescript
import { getAsset } from '@msdyn365-commerce/core';

const url = `${getAsset('webfonts/fa-solid-900.woff', this.props.context.request)}`;
```

## Additional resources

[Theming overview](theming.md)

[Create a new theme](create-theme.md)

[Configure theme settings](configure-theme-settings.md)

[Configure theme style presets](theme-style-presets.md)

[Extend a theme to add module extensions](theme-module-extensions.md)

[Extend a theme from a base theme](extend-theme.md)
