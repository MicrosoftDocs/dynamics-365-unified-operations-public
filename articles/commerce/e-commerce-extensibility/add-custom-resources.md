---
# required metadata

title: Add custom static resources
description: This topic presents an overview of how to add custom resources such as font files, images, css files that you can be accessed within your theme.
author: samjarawan
manager: annbe
ms.date: 09/15/2020
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

This topic presents an overview of how to add custom resources such as font files, images, css files that you can be accessed within your theme.

## Overview
Some scenarios require adding custom static files such as font or CSS files that can be accessed from within a module or a theme.  These static files can be added to a **public** folder within your SDK customization code which will be included in the configuration package generated with the [CLI **yarn msdyn365 pack** command](cli-command-reference.md).  A relative path can then be used to access the resource.

## Example
Resources can be added to the ```/public``` directory or any subdirectory under this directory.  For example adding a font called "NewFont-Regular" may have multiple font files added to the ```/public``` directory including "NewFont-Regular.eot", "NewFont-Regular.woff", "NewFont-Regular.ttv", and "NewFont-Regular.svg".

A relative path should then be used from the SCSS file pointing to the static files.  The below example SCSS is taken from a theme which is located in a ```/src/themes/spring``` folder.  When the CLI **pack** is used, the SCSS code is compiled into a zip file into the ```/build/public/static/css/spring``` directory.  You can see a relative path is then used to access the font.

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
When deploying your e-Commerce customizations via LCS, the physical paths will change, thus any files stored in the ```/public``` directory will change.  This means you cannot provide a static physical path from within your code.  However there is a helper API **getAsset** which is available to get the path.  

The below example shows how to use the **getAsset** api to generate a URL to a font file stored in the ```/public/webfonts``` directory.

```typescript
import { getAsset } from '@msdyn365-commerce/core';

const url = `${getAsset('webfonts/fa-solid-900.woff', this.props.context.request)}`;
```





