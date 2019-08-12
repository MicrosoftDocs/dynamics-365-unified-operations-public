---
# required metadata

title: CLI command reference
description: This topic covers the [CLI](https://en.wikipedia.org/wiki/Command-line_interface) commands made available as part of the Dynamics Commerce Online SDK. 
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
# CLI command reference

This topic covers the [CLI](https://en.wikipedia.org/wiki/Command-line_interface) commands made available as part of the Dynamics Commerce Online SDK. 

All these commands will need to be run with yarn. They will have the following structure:

```bash
yarn msdyn365 {command} {command-arguments}
```
For more information on each command refer to this document or use the command `yarn  --help` or `yarn msdyn365 {command} --help`


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
This command will create a package of the local site configurations (modules, data actions, themes, ...) which will be used to upload via LCS to the Node server.  This command should be run from the root directory of your local SDK files.  

The output will be a zip file in directory it was ran with a file name build using the name and version found in your SDK package.json file in the format Name-Version.zip example: `@msdyn365-commerce-partners-fabrikam-1.2.73.zip`.

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
The packageVersions.json file includes information on Dynamics 365 Commerce and Dynamics 365 Commerce Module packages, their versions and how the versions in use were determined.

Example:

```bash
yarn msdyn365 packages
```

## update-versions

Usage:

```bash
yarn msdyn365 update-versions <tag>
```

Updates the SDK versions to latest alpha/rc/release based on tag.  Default is `latest`.
Example:

```bash
yarn msdyn365 update-versions latest
```

## validate

Usage:

```bash
yarn msdyn365 validate <path/to/directory>
```

Runs a series of validation checks on your package and any modules in the package. Specifically, validate ensures that each module has a default export, contains the necessary files and ensures that your package-level initalization.json is properly registering each of the modules in the package.

The path will be the complete path to the package folder containing the package.json file

Example:

```bash
yarn msdyn365 validate ./

