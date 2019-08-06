---
# required metadata

title: CLI command reference
description: This topic describes the command-line interface (CLI) commands that are available as part of the e-Commerce software development kit (SDK).
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

This topic describes the [command-line interface (CLI)](https://wikipedia.org/wiki/Command-line_interface) commands that are available as part of the Microsoft Dynamics 365 for Commerce e-Commerce software development kit (SDK). 

All the commands must be run by using Yarn, and they have the following structure.

```bash
yarn msdyn365 {command} {command-arguments}
```

For more information about each command, see the relevant section of this topic, or use the **yarn --help** or **yarn msdyn365 {command} --help** command.

## add-data-action

**Usage**

``` bash
yarn msdyn365 add-data-action <action-name>
```

This command adds an action to the root/src/actions folder.

**Example**

``` bash
yarn msdyn365 add-data-action getMyData
```

## add-module

**Usage**

``` bash
yarn msdyn365 add-module <module-name>
```

This command adds a module to the root/src/modules folder.

**Example**

``` bash
yarn msdyb365 add-module campaignBanner
```

## clone

**Usage**

``` bash
yarn d365 clone <core-module-name> <new-module-name>
```

This command creates a copy of a starter kit module and adds the source code to the root/src/modules folder.

**Example**

``` bash
yarn msdyn365 clone hero myHero
```

## pack

**Usage**

``` bash
yarn msdyn365 pack
```

This command creates a package of the local site configurations (modules, data actions, themes, and so on). These configurations will be used to upload to the Node server via Microsoft Dynamics Lifecycle Services (LCS). This command should be run from the root directory of your local SDK files.

The output will be a zip file in the directory where the command was run. The file name is built from the name and version that are found in your SDK package.json file, in the following format: **Name-Version.zip**. Here is an example: **@msdyn365-commerce-partners-fabrikam-1.2.73.zip**.

**Example**

``` bash
yarn msdyn365 pack
```

## print-package-versions

**Usage**

```bash
yarn msdyn365 print-package-versions
```

This command prints the packageVersions.json file that was generated at build time to the console. The packageVersions.json file includes information about Dynamics 365 for Commerce and Dynamics 365 for Commerce module packages, their versions, and how the versions that are used were determined.

**Example**

```bash
yarn msdyn365 print-package-versions
```

## validate

**Usage**

```bash
yarn msdyn365 validate <path/of/directory>
```

This command runs a series of validations on your package and any modules that are in it. Specifically, this command makes sure that each module has a default export and contains the required files. It also makes sure that your package-level initalization.json file correctly registers each module in the package.

The path is the complete path of the package folder that contains the package.json file.

**Example**

```bash
yarn msdyn365 validate ./
```
