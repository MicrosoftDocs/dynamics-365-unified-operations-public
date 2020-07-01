---
# required metadata

title: SDK and core library updates
description: This topic covers regular updates that will be released as part of the Microsoft Dynamics 365 Commerce online software development kit (SDK).
author: samjarawan
manager: annbe
ms.date: 07/01/2020
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

Regular updates will be released as part of the Dynamics 365 Commerce online SDK and store starter kit (SSK). These updates might include new features or product fixes. Product release notes will be provided for all changes.

## Dependency versions in package.json file

The SDK packages.json file included in the SDK root directory controls which versions of the SDK, SSK, Fabrikam theme kit, and Retail Server proxy to download. The specific entries can be found in the "dependencies" section as shown in the example below. Note that the version numbers may differ depending on when the SDK was acquired.

```json
…
  "dependencies": {
    "@msdyn365-commerce-modules/starter-pack": "9.20.8",
    "@msdyn365-commerce-modules/fabrikam-design-kit": "9.20.8",
    "@msdyn365-commerce/retail-proxy": "9.20.2",
    "@msdyn365-commerce/bootloader": "^1.0.0",
…
```
- **@msdyn365-commerce-modules/starter-pack** - This entry represents the SSK, which includes the set of starter modules and data actions. The example above is configured to only pull down the specified version.
- **@msdyn365-commerce-modules/fabrikam-design-kit** - This entry represents the Fabrikam design kit, which includes the Fabrikam theme. The Fabrikam theme defines specific Cascading Style Sheets (CSS) and module view overrides for the store starter kit set of modules. The example above is configured to only pull down the specified version.
- **@msdyn365-commerce/retail-proxy** - This entry represents the retail proxy which is used to access the Commerce Scale Unit set of APIs. The example above is configured to only pull down the specified version.
- **@msdyn365-commerce/bootloader** - This entry represents the SDK. The "^" symbol ensures that the **yarn** command always pulls down the latest released version.

The version numbers used above are in the format *X.Y.Z*, where *X* is the major version, *Y* is the minor version and *Z* is patch version.  

SDK dependencies are backward-compatible and can be pulled down at any time. The store starter kit minor versions are dependent on the Commerce Scale Unit, and so cannot be higher than those shown in the table below. Patch versions will not change dependencies on the Commerce Scale Unit, and so can be updated at any time. The "&#126;" symbol can be used with version numbers to always pull down any patch versions that may include bug fixes. The following example shows the use of the "&#126;" symbol to pull down the latest patch version.

```json
…
  "dependencies": {
    "@msdyn365-commerce-modules/starter-pack": "~9.21.0",
    "@msdyn365-commerce-modules/fabrikam-design-kit": "~9.21.0",
    "@msdyn365-commerce/retail-proxy": "~9.21.0",
    "@msdyn365-commerce/bootloader": "^1.0.0",
    …
```

The following table maps SSK versions to Commerce Scale Unit versions. The same SSK versions mapped to the Commerce Scale Unit should be used for the retail proxy and Fabrikam design kit.

| Commerce Scale Unit version | Max SSK version |
| --------------- | --------------- |
| 10.0.10 | 9.20.x |
| 10.0.11 | 9.21.x |
| 10.0.12 (not live yet) | 9.22.x |

## Pull updates

The SDK, SSK, and other dependency updates are optional and can be pulled down to a local development environment by using the **yarn** command in the SDK source code. Running this command causes the latest dependencies to be pulled down based on the versions specified in the packages.json file. Before running the **yarn** command, you should delete the **yarn.lock** file found in the root directory. Optionally, you can also delete the **/node_modules** folder to get a clean set of dependency files.

Once the latest dependencies are pulled down, you can then do a **yarn start** to run the Node server on your development environment and test the new SDK and SSK components.

When a configuration package is created by using the **yarn msdyn365 pack** command-line interface (CLI) tool, all dependencies are updated to their local versions during the packaging process. The package that is created can then be uploaded to an online site by using Microsoft Dynamics Lifecycle Services (LCS).

## Determine the latest released versions of the dependency packages

To determine the latest released versions of the dependency packages, follow the feed links below.

- [SSK feed](https://dev.azure.com/commerce-partner/Registry/_packaging?_a=package&feed=dynamics365-commerce&view=versions&package=%40msdyn365-commerce-modules%2Fstarter-pack&protocolType=Npm)
- [SDK feed](https://dev.azure.com/commerce-partner/Registry/_packaging?_a=package&feed=dynamics365-commerce&view=versions&package=%40msdyn365-commerce%2Fbootloader&protocolType=Npm)
- [Retail Server proxy feed](https://dev.azure.com/commerce-partner/Registry/_packaging?_a=package&feed=dynamics365-commerce&view=versions&package=%40msdyn365-commerce%2Fretail-proxy&protocolType=Npm)

## Determine the versions deployed on an e-Commerce site

To determine the deployed versions of the SDK, SSK, and Retail Server proxy used on an e-Commerce site, right-click on a site page, select **View page source**, and then search for the strings below to find the version number.

- **commerceSDKVersion** - SDK version.
- **commerceSSKVersion** - SSK version.
- **retailServerProxyVersion** - Retail Server proxy version.

## Additional resources

[Package configurations and deploy them to an online environment](package-deploy.md)
