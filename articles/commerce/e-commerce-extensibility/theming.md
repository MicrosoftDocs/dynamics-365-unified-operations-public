---
# required metadata

title: Theming
description: Dynamics 365 Commerce E-Commerce allows you to apply a SCSS theme to your whole e-Commerce site, templates or individual pages.  For example, you may have a default theme and have seasonal themes which are only applied to some pages or the whole site for a set period of time like a holiday.
author: SamJarawan
manager: JeffBl
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
# Theming
Dynamics 365 Commerce allows you to apply a SCSS theme to your whole online site to individual templates or individual pages.  For example, you may have a default theme set the whole online site and have campaign theme which is only applied to some pages on the site.

Once a theme is created and uploaded to your production site, authoring tools can be used to set the theme on your site, within a template, layout or on a single page.  When an online page is rendered, the appropriate theme will be applied, giving all the modules on that page a consistent look and feel.

Below images shows how a theme is selected for a page, notice the "Page Container" is selected (titled "default-page 1" below) which has the **Page theme** setting in the right-hand pane.

![Theme Selection](media/theming-1.png)

Similarly, the theme can be set on the master page, so that all pages that inherit from the master will leverage the theme.  Note if the "locked" property is disabled individual pages can override the theme.

## General Instructions to create a custom theme
* Create a new theme directory in your SDK **/src/themes/** folder.
  * Example `/src/themes/spring/`
* From within the new directory, create a new SCSS entry point file for the theme using the following name pattern **THEME_NAME.theme.scs**.  The theme will be registered and show up in the authoring tools with the THEME_NAME provided in the file name.
  * Example `/src/themes/spring/spring.theme.scss`
* Once the theme is complete, your configurations can be packaged up and uploaded to your site.  New themes will then automatically appear within the authoring tools.

## Best Practices
* There is no limit to the number of **.scss** files your theme may contain.
* Your theme entry point may import other **.scss** files using relative paths.
* Starter kit modules are built using Bootstrap 4 classes, so the recommended scss framework to include in any theme is either Bootstrap 4 or Bootstrap 4 RTL.
* To leverage Starter Kit modules built with Font Awesome glyphicons, font-awesome should be included in the scss.
* You can optionally import the **react-ts-strap-default-them** which addresses accessibility issues with Bootstrap 4. See details below.

## To consume SCSS files distributed via NPM
Some dependencies such as Bootstrap and FontAwesome are distributed via NPM packages and if used in your SCSS file must be referenced in your SDK packages.json file.
* Edit package.json in the root folder of the SDK and add the dependencies

Example adding bootstrap
```
"dependencies": {
     …
     "bootstrap": "^4.3.1",
     …
}
```

## Recommended structure for a custom theme
The below list is recommended to cover inside of any custom theme.  Import or define the following:
*	Fonts and glyph icons
*	Mixins and functions
  *	Bootstrap: dependencies, excluding components and utilities
  * Shared components: dependencies, excluding components and utilities
  *	Custom theme mixins and functions
*	Theme variables
  *	Custom theme variables
  * Bootstrap: theme variable defaults (fallbacks)
*	Components and modules scss
  * Shared components: components
  *	Custom components and modules
*	Utilities
  *	Bootstrap, shared component, and custom utilities

## Hooks for theming modules
Modules allow targeting by any theme by defining a class name matching the module name. This class name should be the first class name applied to the outermost element rendered by the React component. Developers may allow for more granular themability options by providing additional class names on elements or features of a module that may be targetable by custom themes.
