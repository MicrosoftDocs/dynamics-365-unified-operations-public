---
# required metadata

title: CLI command reference
description: This topic covers the command line interface (CLI) commands that are available in the Dynamics 365 Commerce online SDK
author: samjarawan
manager: annbe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-retail
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application user
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

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic covers the command line interface ([CLI](https://en.wikipedia.org/wiki/Command-line_interface)) commands that are available in the Dynamics 365 Commerce online SDK. 

## Overview

All these commands must be run with Yarn. They will have the following structure:

```bash
yarn msdyn365 {command} {command-arguments}
```
For more information on each command, refer to the entries in this topic or use the command `yarn  --help` or `yarn msdyn365 {command} --help`.

## add-data-action

Usage:

``` bash
yarn msdyn365 add-data-action <action-name>
```

This will add a template data action to the root/src/actions folder.

Example:

``` bash
yarn msdyn365 add-data-action getMyData
```

## add-module

Usage:

``` bash
yarn msdyn365 add-module <module-name>
```
This will add a module to the root/src/modules folder. 

Example:

``` bash
yarn msdyb365 add-module campaignBanner
```

## clone

Usage:

``` bash
yarn d365 clone <starter-kit-module-name> <new-module-name>
```
This will create a renamed copy of a Starter Kit module and add the source code to the local root/src/modules folder.

Example:

``` bash
yarn msdyn365 clone hero myHero
```

## pack

Usage:

``` bash
yarn msdyn365 pack
```

This command will create a package of the local site configurations (modules, data actions, themes, etc.) that will be uploaded to the node server using Lifecycle Services (LCS). This command should be run from the root directory of your local SDK files.  

The output will be a zip file located in the directory the command was run from, with a file name built using the name and version found in your SDK package.json file, for example `@msdyn365-commerce-partners-fabrikam-1.2.73.zip`.

Example:

``` bash
yarn msdyn365 pack
```

## packages
Usage:

```bash
yarn msdyn365 packages
```

Prints the packageVersions.json file generated at build time to the console.

The packageVersions.json file includes information on Dynamics 365 Commerce and Dynamics 365 Commerce module packages, their versions, and how the versions in use were determined.

Example:

```bash
yarn msdyn365 packages
```

## update-versions

Usage:

```bash
yarn msdyn365 update-versions <tag>
```

Updates the SDK versions to the latest alpha/rc/release based on tag. The default tag is `latest`.

Example:

```bash
yarn msdyn365 update-versions latest
```

## validate

Usage:

```bash
yarn msdyn365 validate <path/to/directory>
```

Runs a series of validation checks on your package and any modules in the package. Specifically, it ensures that each module has a valid definition json file.

The path will be the complete path to the package folder containing the package.json file.

Example:

```bash
yarn msdyn365 validate ./

