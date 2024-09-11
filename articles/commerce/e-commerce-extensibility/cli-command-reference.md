---
title: CLI command reference
description: This article covers the command-line interface (CLI) commands that are available in the Microsoft Dynamics 365 Commerce online software development kit (SDK).
author: samjarawan
ms.date: 05/28/2024
ms.topic: how-to
audience: Developer
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: anupamar
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---

# CLI command reference

[!include [banner](../includes/banner.md)]

This article covers the command-line interface ([CLI](https://en.wikipedia.org/wiki/Command-line_interface)) commands that are available in the Microsoft Dynamics 365 Commerce online software development kit (SDK).

All the following commands must be run by using Yarn. They all have the following structure.

```bash
yarn {msdyn365} {command} {command-arguments}
```

For information about each command, see the entries in this article, or use the **yarn --help** or **yarn msdyn365 {command} --help** command.

## start

**Usage**

``` bash
yarn start <--verbose>
```

This command builds and launches the Node server using the port defined in the .env file.

The `--verbose` option is used to provide more verbose debugging output in the command prompt window.

**Examples**

``` bash
yarn start
```

``` bash
yarn start --verbose
```

## build

**Usage**

``` bash
yarn build <--verbose>
```

This command performs a complete build on the customization code.

The `--verbose` option is used to provide more verbose debugging output in the command prompt window.

**Examples**

``` bash
yarn build
```

``` bash
yarn build --verbose
```

## add-component-override

**Usage**

``` bash
yarn msdyn365 add-component-override <themeName> <componentName> <--list-components> <--verbose>
```

This command adds a component to the specified theme component folder. The component can then be modified as desired from that folder.

- The `--list-components` option is used to show a list of components.
- The `--verbose` option is used to provide more verbose debugging output in the command prompt window.

**Examples**

``` bash
yarn msdyn365 add-component-override spring-theme add-to-cart.component
```

``` bash
yarn msdyn365 add-component-override --list-components
```

## add-data-action

**Usage**

``` bash
yarn msdyn365 add-data-action <action-name> <--verbose>
```

This command adds a template data action to the root/src/actions folder.

The `--verbose` option is used to provide more verbose debugging output in the command prompt window.

**Example**

``` bash
yarn msdyn365 add-data-action getMyData --verbose
```

## add-module

**Usage**

``` bash
yarn msdyn365 add-module <module-name> <--verbose>
```

This command adds a module to the root/src/modules folder. Module names are case-insensitive. 

The `--verbose` option is used to provide more verbose debugging output in the command prompt window.

**Example**

``` bash
yarn msdyn365 add-module product-feature --verbose
```

## add-theme

**Usage**

``` bash
yarn msdyn365 add-theme <theme-name> <--verbose>
```

This command adds a theme to the root/src/themes folder.

The `--verbose` option is used to provide more verbose debugging output in the command prompt window.

**Example**

``` bash
yarn msdyn365 add-theme spring-theme --verbose
```

## add-view-extension

**Usage**

``` bash
yarn msdyn365 add-view-extension <theme-name> <Module-name> <--verbose>
```

This command adds a module view extension to the root/src/themes/\<theme-name\>/views folder. The theme can then add more module definition items, such as configurations, resources, and slots.

The `--verbose` option is used to provide more verbose debugging output in the command prompt window.

**Example**

``` bash
yarn msdyn365 add-view-extension spring-theme product-feature --verbose
```

## clone

**Usage**

``` bash
yarn msdyn365 clone <module-library-module-name> <new-module-name> <--verbose>
```

This command creates a renamed copy of a module library module and adds the source code to the local root/src/modules folder.

The `--verbose` option is used to provide more verbose debugging output in the command prompt window.

**Example**

``` bash
yarn msdyn365 clone content-block super-content-block --verbose
```

## create-request-hook 

**Usage**

``` bash
yarn msdyn365 create-request-hook <--verbose>
```

This command creates a request pipeline plug-in hook file (**src/requestHooks/initialRequest.hook.ts**). The request pipeline plug-in hook file provides the ability to intercept the rendering request that is sent to the **root/src/modules** folder on the Node server.

The `--verbose` option is used to provide more verbose debugging output in the command prompt window.

**Example**

``` bash
yarn msdyn365 create-request-hook --verbose
```

## optimize-module-css

**Usage**

``` bash
yarn msdyn365 optimize-module-css <themeName> --requiredStyles=<requiredStylesFolder> --componentStyles=<componentStylesFolder> --assetFiles=<assetFiles> --assetVar=<assetVar>
```

This command optimizes styles for the [module CSS optimization](module-css-optimization.md) feature by creating the necessary file structure.  Styles still must be updated within the individual **\<MODULE_NAME\>.scss** files for specific modules.

- The `--requiredStyles` option is used to specify the folder names of required/abstract styles.
- The `--componentStyles` option is used to provide the folder names of component styles. 
- The `--assetFiles` option is used to provide the file names where style assets are being used. 
- The `--assetVar` option is used to provide variable names that describe the path to asset files without using the `$` character.

**Example**

``` bash
yarn msdyn365 optimize-module-css adventureWorks --requiredStyles=00-settings,01-tools,02-generic --componentStyles=03-components --assetFiles=icons.scss --assetVar=msv-font-path
```

## pack

**Usage**

``` bash
yarn msdyn365 pack <--verbose>
```

This command creates a package of the local site configurations (modules, data actions, themes, and so on). This package is then uploaded to the Node server using Microsoft Dynamics Lifecycle Services (LCS). This command should be run from the root directory of your local SDK files.

The output is a zip file in the directory that the command was run from. The file name is built by using the name and version that are found in your SDK package.json file. For example, a zip file might be named **\@msdyn365-commerce-partners-fabrikam-1.2.73.zip**.

The `--verbose` option is used to provide more verbose debugging output in the command prompt window.

**Example**

``` bash
yarn msdyn365 pack --verbose
```

## packages

**Usage**

```bash
yarn msdyn365 packages
```

This command prints the packageVersions.json file that was generated at build time to the console.

The packageVersions.json file includes information about Dynamics 365 Commerce packages and Dynamics 365 Commerce module packages, their versions, and how the versions that are used were determined.

**Example**

```bash
yarn msdyn365 packages
```

## preview

**Usage**

```bash
yarn msdyn365 pack --preview
```

This command creates a package with the latest SDK preview version, and is available with SDK version 1.41.10-preview.0 and later.

## update-versions

**Usage**

```bash
yarn msdyn365 update-versions <entity>
```

This command updates the entity (SDK, module library, or retail proxy) versions to the latest release.

**Examples**

```bash
yarn msdyn365 update-versions module-library
yarn msdyn365 update-versions retail-proxy
yarn msdyn365 update-versions sdk
```

The **--verbose** option is used to provide more verbose debugging output in the command prompt window.

## validate

**Usage**

```bash
yarn msdyn365 validate <path/to/directory>
```

This command runs a series of validation checks on your package and any modules in the package. Specifically, it makes sure that each module has a valid definition .json file.

The path is the full path of the package folder that contains the package.json file.

**Example**

```bash
yarn msdyn365 validate ./
```
## Additional resources

[E-commerce architectural overview](architectural-overview.md)

[E-commerce components](ecommerce-components.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
