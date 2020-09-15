---
# required metadata

title: This topic provides an overview of how to override a starter kit components to allow customizations within a theme.
description: This topic provides an overview of 
author: samjarawan
manager: annbe
ms.date: 10/01/2019
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
# Override a starter kit component in a theme

[!include [banner](../includes/banner.md)]

This topic provides an overview of how to override a starter kit components to allow customizations within a theme.

## Overview
The Dynamics 365 Commerce e-Commerce starter kit contains a set of overridable typescript components that are used by various starter kit modules.  These components contain helper APIs called by some starter kit modules that contain business and other logic to help in rendering the appropriate module HTML markup or making server side calls.  If you need to change any logic in a component, the component can be overwritten for a selected theme using the CLI [add-component-override](cli-command-reference.md) command. 

For example if you want to change the logic for strike-through pricing, you can look at overriding the **Price** component and make changes.  Other changes such as [module view overrides](theme-module-extensions.md) can also be used for visual changes.  In rare cases, you may need to [clone a module]() to make all the changes you need.  Cloning a module will make a copy of the module.

## Component list
To get a list of components you can use the following CLI command. 

```bash
yarn msdyn365 add-component-override --list-components
```

Component source code can be found under the "\node_modules\@msdyn365-commerce\components\src\" inside the installed Online SDK directory.  You may want to browse the source code to see what options are available within each component.

The following is a list of components includes as part of the store starter kit.  The list may differ based on the version of the store starter kit being used.

| Component                 | Description                                                           |
|---------------------------|-----------------------------------------------------------------------|
| AddToCart     | temp description |
| AddToWishlist | temp description |
| CartIcon      | temp description |
| CartLineItem  | temp description |
| Price         | temp description |
| Product       | temp description |
| PromoCode     | temp description |
| Rating        | temp description |
| WishListIcon  | temp description |

## Override a component in a theme
To override a component in a theme, you can use CLI command ```yarn msdyn365 add-component-override [themeName] [componentName] [--list-components]```.  Once complete you will find a new typescript file under the theme's ```\view\components``` directory.  This file can now be modified as required. 

### Example
```yarn msdyn365 add-component-override spring add-to-cart```





