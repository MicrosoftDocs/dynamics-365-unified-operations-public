---
# required metadata

title: CLI command reference
description: 
author: SamJarawan
manager: annbe
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
# CLI command reference

This topic covers the [CLI](https://en.wikipedia.org/wiki/Command-line_interface) commands made available as part of the Dynamics 365 for Commerce e-Commerce SDK. 

All of the commands must be run with Yarn, and will have the following structure:

```bash
yarn msdyn365 {command} {command-arguments}
```
For more information on each command, refer to this document or use the command `yarn  --help` or `yarn msdyn365 {command} --help`.


## add-data-action

Usage:

``` bash
yarn msdyn365 add-data-action <action-name>
```
This adds an action to the root/src/actions folder. 

Example:

``` bash
yarn msdyn365 add-data-action getMyData
```

## add-module

Usage:

``` bash
yarn msdyn365 add-module <module-name>
```
This adds a module to the root/src/modules folder. 

Example:

``` bash
yarn msdyb365 add-module campaignBanner
```

## clone

Usage:

``` bash
yarn d365 clone <core-module-name> <new-module-name>
```
This creates a copy of a starter kit module and add the source code to the root/src/modules folder. 

Example:

``` bash
yarn msdyn365 clone hero myHero
```

## pack

Usage:

``` bash
yarn msdyn365 pack
```
This command creates a package of the local site configurations (modules, data actions, themes, etc.) which will be used to upload via Lifecycle Services (LCS) to the Node server. This command should be run from the root directory of your local SDK files.  

The output will be a zip file in the directory it was run, with a file name build using the name and version found in your SDK package.json file in the format Name-Version.zip. For example: `@msdyn365-commerce-partners-fabrikam-1.2.73.zip`.

Example:

``` bash
yarn msdyn365 pack
```

## print-package-versions
Usage:

```bash
yarn msdyn365 print-package-versions 
```

This command prints the packageVersions.json file generated at build time to the console. The packageVersions.json file includes information on Dynamics 365 for Commerce and Dynamics 365 for Commerce Module packages, their versions, and how the versions in use were determined.

Example:

```bash
yarn msdyn365 print-package-versions 
```

## validate

Usage:

```bash
yarn msdyn365 validate <path/to/directory>
```

This runs a series of validation checks on your package and any modules in the package. Specifically, the validate command ensures that each module has a default export, contains the necessary files, and ensures that your package-level initalization.json is properly registering each of the modules in the package.

The path will be the complete path to the package folder containing the package.json file.

Example:

```bash
yarn msdyn365 validate ./

