---
# required metadata

title: Add custom resources to your customization code
description: This topic describes how to add custom static resources to your SDK customization code so that they can be accessed from within your theme.
author: samjarawan
ms.date: 05/27/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: samjar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---
# Add custom resources to your customization code

[!include [banner](../includes/banner.md)]

This topic describes how to add custom static resources such as font, image, and Cascading Style Sheet (CSS) files to your software development kit (SDK) customization code so that they can be accessed from within your theme.

Some scenarios require adding custom static resources such as font, image, or CSS files that can be accessed from within a module or a theme. These static files can be added to a ```/public``` folder within your SDK customization code so that they will be included in the configuration package generated with the [CLI **yarn msdyn365 pack** command](cli-command-reference.md#pack). Relative paths can then be used to access the resources.

During the build step, style Sassy CSS (SCSS) files are compiled into CSS files and stored inside of the same ```/public``` folder, which should be taken into account when referencing other static resources inside of the ```/public``` folder.

## Example

Resources can be added to the ```/public``` directory or any subdirectory under this directory. For example, adding a font called "NewFont-Regular" could include adding multiple font files such as "NewFont-Regular.eot", "NewFont-Regular.woff", "NewFont-Regular.ttv", and "NewFont-Regular.svg" to the ```/public``` directory.

After adding files to the ```/public``` directory, relative paths in the Sassy CSS (SCSS) file can then be used to point to them. The following SCSS example is taken from a theme that is located in the ```/src/themes/spring``` folder. When the command-line interface (CLI) command **pack** is used, the SCSS code is compiled into a zip file created in the ```/build/public/static/css/spring``` directory. A relative path is then used to access the font within the ```/public``` folder.

```SCSS
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

When you deploy your e-Commerce customizations using Microsoft Lifecycle Services (LCS), the physical paths to any files stored in the ```/public``` directory will change, so you cannot provide static physical paths to these files from within your code. However, there is a helper API named **getAsset** that is available to help you obtain the path.

The following example from a custom module .tsx file shows how to use the **getAsset** API to generate a URL to a font file stored in the ```/public/webfonts``` directory.

```typescript
import { getAsset } from '@msdyn365-commerce/core';

const url = `${getAsset('webfonts/fa-solid-900.woff', this.props.context.request)}`;
```

## Additional resources

[CLI command reference](cli-command-reference.md)

[Theming overview](theming.md)

[Create a new theme](create-theme.md)

[Configure theme settings](configure-theme-settings.md)

[Configure theme style presets](theme-style-presets.md)

[Extend a theme to add module extensions](theme-module-extensions.md)

[Override a module library component in a theme](override-theme-component.md)

[Extend a theme from a base theme](extend-theme.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
