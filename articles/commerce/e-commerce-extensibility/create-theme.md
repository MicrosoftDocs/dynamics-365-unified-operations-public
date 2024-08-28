---
title: Create a new theme
description: This article describes how to create a new theme for a Microsoft Dynamics 365 Commerce online site.
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
# Create a new theme

[!include [banner](../includes/banner.md)]

This article describes how to create a new theme for a Microsoft Dynamics 365 Commerce online site.

The Dynamics 365 Commerce online software development kit (SDK) lets you create custom themes that can be applied to your online site. They can also be shared across the sites in a single tenant if desired.

After a theme is created and uploaded to your sandbox or production environment, you can use Commerce site builder to set the theme on your site (or sites). Then, when an online page is rendered, the appropriate theme is applied. In this way, modules will have a consistent look and feel across site pages.

Themes contain Sassy Cascading Style Sheet (SCSS) files that you can use to style your online site and individual modules. They can also optionally contain the following extensions:

- Module view extensions that provide new layout views on a module
- Definition extensions to change a module's configurations

## Create a new theme

The online software development kit (SDK) provides the **add-theme** command-line interface (CLI) command. To create a new theme in Commerce, you run the command as shown in the following example, replacing **THEME\_NAME** with the name that you want to give to the new module. 

**yarn msdyn365 add-theme THEME\_NAME**

The following example shows how to create a theme that is named **spring**.

```Console
yarn msdyn365 add-theme spring
```

The new theme will be created in a new directory under the **...\\src\\themes** directory. For example, the spring-time theme is created under the **...\\src\\themes\\spring** directory.

### Theme naming conventions

Theme names are case-insensitive. The theme's friendly name and description can be added to the theme definition file in the new theme directory.

## Theme definition file

A theme is created as a special module. Each theme has a theme definition file in JavaScript Object Notation (JSON) format that contains the theme's friendly name and description. The **$type** property will be set to **"themeModule"**.

The following example shows a theme definition file.

```json
{
    "$type": "themeModule",
    "friendlyName": "Spring theme",
    "name": "spring",
    "description": "This is default theme."
}
```

## Theme styles

SCSS files are stored under the **...\\src\\themes\\THEME\_NAME\\styles** directory. By default, this directory includes a **THEME\_NAME.theme.scss** file. This file is the entry point SCSS file. You can add other SCSS files and directories to the directory as you require.

For example, the file name and path of the **spring** theme might be **...\\src\\themes\\spring\\styles\\spring.theme.scss**.


## Test a theme

You can easily test a theme in your development environment by using the **?theme=THEME\_NAME** query string parameter.

To test your theme, follow these steps.

1. At a command prompt, under the directory of your local code repository, run **yarn start**. 
1. In a web browser, load a module test page, and add the **?theme=THEME\_NAME** query string parameter, as shown in the following example.

    `https://localhost:4000/modules?type=product-feature&theme=spring`

If your .env file's **MSDyn365\_HOST** entry points to your production site, you can also use the following URL to preview what your site looks like when a custom theme is applied.

`https://localhost:4000?theme=spring`

### Mock new configuration values in a theme

If new configuration fields are added to a module in a theme, mock data can be added to the module's mock file. For example, if you modify a module library module's view and definition files, you can add new configuration mocks to the module library mock files that are under the **...\node_modules\\@msdyn365-commerce-modules** directory in the module library module.

In a similar way, if you're mocking data for a custom module, you can add new mock data in the module's mock JSON file. Alternatively, you can create new mock files under the same module mock directory.

## Additional resources

[Theming overview](theming.md)

[Configure theme settings](configure-theme-settings.md)

[Configure theme style presets](theme-style-presets.md)

[Extend a theme to add module extensions](theme-module-extensions.md)

[Override a module library component in a theme](override-theme-component.md)

[Extend a theme from a base theme](extend-theme.md)

[Add custom resources to your customization code](add-custom-resources.md)

[Configure a development .env file](configure-env-file.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
