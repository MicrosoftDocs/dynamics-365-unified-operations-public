---
# required metadata

title: SDK and core library updates
description: This topic covers regular updates that will be released as part of the Microsoft Dynamics 365 Commerce online software development kit (SDK).
author: samjarawan
manager: annbe
ms.date: 10/24/2019
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
# SDK and core library updates

[!include [banner](../includes/banner.md)]

This topic covers regular updates that will be released as part of the Microsoft Dynamics 365 Commerce online software development kit (SDK).

## Overview

Regular updates will be released as part of the Dynamics 365 Commerce online SDK and store starter kit. These updates might include new features or product fixes. Product release notes will be provided for all changes.

## Dependency versions in package.json file

The SDK packages.json file included in the SDK root directory controls which versions of the SDK, store starter kit (SSK), Fabrikam theme kit and retail proxy to download.
The specific entries can be found in the “dependencies” section as shown below (note the versions numbers may be different depending on when the SDK was acquired).

```json
…
  "dependencies": {
    "@msdyn365-commerce-modules/starter-pack": "9.20.8",
    "@msdyn365-commerce-modules/fabrikam-design-kit": "9.20.8",
    "@msdyn365-commerce/retail-proxy": "9.20.2",
    "@msdyn365-commerce/bootloader": "^1.0.0",
…
```
* @msdyn365-commerce-modules/starter-pack - this entery represents the store starter kit, which includes the set of starter modules and data actions.  The above example is set to only pull down the specific version.
* @msdyn365-commerce-modules/fabrikam-design-kit - this entry represents the Fabrikam design kit, which includes the Fabrikam theme.  The Fabrikam theme defines specific CSS and module view overrides for the store starter kit set of modules. The above example is set to only pull down the specific version.
* @msdyn365-commerce/retail-proxy - this entry represents the retail proxy which is used to access the Commerce scale unit set of APIs. The above example is set to only pull down the specific version.
* @msdyn365-commerce/bootloader - this entry represents the SDK, note the "^" symbol used, which will ensure the **yarn** command always pulls down the latest released version.

The version numbers used above are X.y.z, where X is the major version, y is the minor version and z is patch version.  

SDK Dependencies are backward-compatible and can be pulled down at any time. The store starter kit minor versions take a dependency on the Commerce scale unit, so cannot be higher than shown in the table below.  Patch versions will not change dependencies on the Commerce scale unit, so can be updated at any time.  The "~" can be used with version numbers to always pull down any patch versions which may include bug fixes.  The below example shows the use of "~" to pull down the latest patch version.

```json
…
  "dependencies": {
    "@msdyn365-commerce-modules/starter-pack": "~9.21.0",
    "@msdyn365-commerce-modules/fabrikam-design-kit": "~9.21.0",
    "@msdyn365-commerce/retail-proxy": "~9.21.0",
    "@msdyn365-commerce/bootloader": "^1.0.0",
    …
```

The below table shows the Store Starter Kit version mapping to the Commerce scale unit.  The same version number below for SSK should be used for the retail proxy and Fabrikam design kit.

| Commerce Scale Unit Version | Max Store Starter Kit Version |
| --------------- | --------------- |
| 10.0.10 | 9.20.x |
| 10.0.11 | 9.21.x |
| 10.0.12 (not live yet) | 9.22.x |

## Pull updates

SDK, the store starter kit and other dependency updates are optional and can be pulled down to a local development environment by using the **yarn** command in the SDK source code. This command causes the latest dependencies to be pulled down based on the versions specified in the packages.json file. Before running the **yarn** command you should delete the **yarn.lock** file found in the root directory and can optionally delete the **/node_modules** folder to get a clean set of dependency files.

Once the latest dependencies are pulled down, you can now do a **yarn start** to run the Node server on your development environment and test the new SDK/SSK components.

When a configuration package is created by using the **yarn msdyn365 pack** command-line interface (CLI) tool, all dependencies are updated to their local versions during the packaging process. The package that is created can then be uploaded to an online site by using Microsoft Dynamics Lifecycle Services (LCS).

## Determine the latest dependency released versions

To determine the latest released versions of the dependency packages follow the feed links below.

* [Starter Kit Feed (SSK)](https://dev.azure.com/commerce-partner/Registry/_packaging?_a=package&feed=dynamics365-commerce&view=versions&package=%40msdyn365-commerce-modules%2Fstarter-pack&protocolType=Npm)
* [Software Developer Kit (SDK)](https://dev.azure.com/commerce-partner/Registry/_packaging?_a=package&feed=dynamics365-commerce&view=versions&package=%40msdyn365-commerce%2Fbootloader&protocolType=Npm)
* [Retail Proxy](https://dev.azure.com/commerce-partner/Registry/_packaging?_a=package&feed=dynamics365-commerce&view=versions&package=%40msdyn365-commerce%2Fretail-proxy&protocolType=Npm)

## Determine the versions deployed on an e-Commerce site.
To determine the deployed version of the SDK and the store starter kit, navigate to the deployed e-Commerce site, right click on the browser and select "View page source", and search for the below strings and you'll see the version number embedded in the page source: 

* commerceSDKVersion - SDK version
* commerceSSKVersion - SSK version 
* retailServerProxyVersion - Retail proxy version


## Additional resources

[Package configurations and deploy them to an online environment](package-deploy.md)
