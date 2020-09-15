---
# required metadata

title: Extend a theme to add component overrides
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
# Extend a theme to add component overrides

[!include [banner](../includes/banner.md)]

This topic provides an overview of ..

## Overview
The Dynamics 365 Commerce e-Commerce starter kit contains a set of typescript components that are used by the starter kit modules.  These components contain helper APIs called by the starter kit modules that contain business and other logic to help in rendering the appropriate module HTML markup.  If you need to change any logic in a comonent, they can be overwritten for a selected theme using the CLI [add-component-override](cli.md) command.

Components can be found under the "\node_modules\@msdyn365-commerce\components\src\add-to-cart" inside the installed Online SDK directory.

## Component list
The following is a list of components includes as part of the store starter kit.  The below list may differ based on the version of the store starter kit being used.


| Component                 | Description                                                           |
|---------------------------|-----------------------------------------------------------------------|
| add-to-cart.component.tsx | temp description |
| add-to-cart.test.tsx      | temp description |

## Override a component in a theme
To override a component in a theme, you can use CLI command ```yarn msdyn365 add-component-override [themeName] [componentName] [--list-components]```.

### Example
```yarn msdyn365 add-component-override spring add-to-cart```





