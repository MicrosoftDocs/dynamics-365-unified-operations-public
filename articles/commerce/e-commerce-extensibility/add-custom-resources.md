---
title: Add custom resources to your customization code
description: This article describes how to add custom static resources to your SDK customization code so that they're accessible from within your theme in Microsoft Dynamics 365 Commerce.
author: samjarawan
ms.date: 07/30/2024
ms.topic: how-to
audience: Developer
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---
# Add custom resources to your customization code

[!include [banner](../includes/banner.md)]

This article describes how to add custom static resources such as font, image, and Cascading Style Sheet (CSS) files to your software development kit (SDK) customization code so that they're accessible from within your theme in Microsoft Dynamics 365 Commerce.

Some scenarios require adding custom static resources such as font, image, or CSS files that are accessible from within a module or a theme. These static files can be added to a `/public` folder within your SDK customization code so that they're included in the configuration package generated with the [CLI **yarn msdyn365 pack** command](cli-command-reference.md#pack). Relative paths can then be used to access the resources.

During the build step, style Sassy CSS (SCSS) files are compiled into CSS files and stored inside of the same `/public` folder, which should be taken into account when referencing other static resources inside of the `/public` folder.

## Example

Resources can be added to the `/public` directory or any subdirectory under this directory. For example, adding a font called "NewFont-Regular" could include adding multiple font files such as "NewFont-Regular.eot", "NewFont-Regular.woff", "NewFont-Regular.ttv", and "NewFont-Regular.svg" to the `/public` directory.

After you add files to the `/public` directory, relative paths in the Sassy CSS (SCSS) file can then be used to point to them. The following SCSS example is taken from a theme that is located in the `/src/themes/spring` folder. When the command-line interface (CLI) command **pack** is used, the SCSS code is compiled into a zip file created in the `/build/public/static/css/spring` directory. A relative path is then used to access the font within the `/public` folder.

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

When you deploy your e-commerce customizations using Microsoft Lifecycle Services (LCS), the physical paths to any files stored in the `/public` directory change, so you can't provide static physical paths to these files from within your code. However, there's a helper API named **getAsset** that's available to help you obtain the path.

The following example from a custom module .tsx file shows how to use the **getAsset** API to generate a URL to a font file stored in the `/public/webfonts` directory.

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
