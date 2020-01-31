---
# required metadata

title: CLI command reference
description: This topic covers the command-line interface (CLI) commands that are available in the Microsoft Dynamics 365 Commerce online software development kit (SDK).
author: samjarawan
manager: annbe
ms.date: 01/31/2020
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
# CLI command reference

[!include [banner](../includes/banner.md)]

This topic covers the command-line interface ([CLI](https://en.wikipedia.org/wiki/Command-line_interface)) commands that are available in the Microsoft Dynamics 365 Commerce online software development kit (SDK).

## Overview

All the following commands must be run by using Yarn. They all have the following structure.

```bash
yarn msdyn365 {command} {command-arguments}
```

For information about each command, see the entries in this topic, or use the **yarn --help** or **yarn msdyn365 {command} --help** command.

## add-data-action

**Usage**

``` bash
yarn msdyn365 add-data-action <action-name>
```

This command adds a template data action to the root/src/actions folder.

**Example**

``` bash
yarn msdyn365 add-data-action getMyData
```

## add-module

**Usage**

``` bash
yarn msdyn365 add-module <module-name>
```

This command adds a module to the root/src/modules folder. Note that module names are case-insensitive. 

**Example**

``` bash
yarn msdyn365 add-module product-feature
```

## add-theme

**Usage**

``` bash
yarn msdyn365 add-theme <theme-name>
```

This command adds a theme to the root/src/themes folder.

**Example**

``` bash
yarn msdyn365 add-theme spring-theme
```

## add-view-extension

**Usage**

``` bash
yarn msdyn365 add-view-extension <theme-name> <Module-name>
```

This command adds a module view extension to the root/src/themes/\<theme-name\>/views folder. The theme can then add more module definition items, such as configurations, resources, and slots.

**Example**

``` bash
yarn msdyn365 add-view-extension spring-theme product-feature
```

## clone

**Usage**

``` bash
yarn msdyn365 clone <starter-kit-module-name> <new-module-name>
```

This command creates a renamed copy of a starter kit module and adds the source code to the local root/src/modules folder.

**Example**

``` bash
yarn msdyn365 clone content-block super-content-block
```

## pack

**Usage**

``` bash
yarn msdyn365 pack
```

This command creates a package of the local site configurations (modules, data actions, themes, and so on). This package will then be uploaded to the node server by using Microsoft Dynamics Lifecycle Services (LCS). This command should be run from the root directory of your local SDK files.

The output is a zip file in the directory that the command was run from. The file name is built by using the name and version that are found in your SDK package.json file. For example, a zip file might be named **\@msdyn365-commerce-partners-fabrikam-1.2.73.zip**.

**Example**

``` bash
yarn msdyn365 pack
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

## update-versions

**Usage**

```bash
yarn msdyn365 update-versions <tag>
```

This command updates the SDK versions to the latest alpha/rc/release, based on the tag. The default tag is **latest**.

**Example**

```bash
yarn msdyn365 update-versions latest
```

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

[Architectural overview](architectural-overview.md)

[e-Commerce components](ecommerce-components.md)
