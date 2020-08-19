---
# required metadata

title: SDK and store starter kit updates
description: This topic covers regular updates that will be released as part of the Microsoft Dynamics 365 Commerce online software development kit (SDK).
author: samjarawan
manager: annbe
ms.date: 08/18/2020
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
# SDK and store starter kit updates

[!include [banner](../includes/banner.md)]

This topic covers regular updates that will be released as part of the Microsoft Dynamics 365 Commerce online software development kit (SDK).

## Overview

Regular updates will be released as part of the Dynamics 365 Commerce online SDK and store starter kit (SSK). These updates might include new features or product fixes. Product release notes will be provided for all changes.

## Dependency versions in the packages.json file

The SDK packages.json file that is included in the SDK root directory controls which versions of the SDK, SSK, Fabrikam design kit, and Retail Server proxy are downloaded. The specific entries can be found in the **"dependencies"** section, as shown in the following example. Note that the version numbers might differ, depending on when the SDK was acquired.

```json
...
"dependencies": {
    "@msdyn365-commerce-modules/starter-pack": "9.20.8",
    "@msdyn365-commerce-modules/fabrikam-design-kit": "9.20.8",
    "@msdyn365-commerce/retail-proxy": "9.20.2",
    "@msdyn365-commerce/bootloader": "^1.0.0",
}
...
```

- **@msdyn365-commerce-modules/starter-pack** – This entry represents the SSK, which includes the set of starter modules and data actions. The preceding example is configured to pull down only the specified version.
- **@msdyn365-commerce-modules/fabrikam-design-kit** – This entry represents the Fabrikam design kit, which includes the Fabrikam theme. The Fabrikam theme defines specific Cascading Style Sheets (CSS) and module view overrides for the set of modules in the SSK. The preceding example is configured to pull down only the specified version.
- **@msdyn365-commerce/retail-proxy** – This entry represents the Retail Server proxy, which is used to access the set of APIs for the Commerce Scale Unit. The preceding example is configured to pull down only the specified version.
- **@msdyn365-commerce/bootloader** – This entry represents the SDK. The caret (\^) symbol ensures that the **yarn** command always pulls down the latest released version.

The version numbers that are used in the preceding example are in the format *X.Y.Z*, where *X* is the major version, *Y* is the minor version, and *Z* is the patch version.

SDK dependencies are backward-compatible and can be pulled down at any time. The SSK minor versions are dependent on the Commerce Scale Unit. Therefore, they can't be higher than the versions that are shown in the table that follows.

Patch versions won't change dependencies on the Commerce Scale Unit. Therefore, they can be updated at any time. The tilde (\~) symbol can be used with version numbers to ensure that any patch versions that might include software updates are always pulled down. The following example shows how the tilde is used to pull down the latest patch version.

```json
...
"dependencies": {
    "@msdyn365-commerce-modules/starter-pack": "~9.21.0",
    "@msdyn365-commerce-modules/fabrikam-design-kit": "~9.21.0",
    "@msdyn365-commerce/retail-proxy": "~9.21.0",
    "@msdyn365-commerce/bootloader": "^1.0.0",
}
...
```

The following table maps SSK versions to Commerce Scale Unit versions. The same SSK versions that are mapped to the Commerce Scale Unit should be used for the Retail Server proxy and Fabrikam design kit.

| Commerce Scale Unit version | Maximum SSK version |
| --------------- | --------------- |
| 10.0.10 | 9.20.x |
| 10.0.11 | 9.21.x |
| 10.0.12 | 9.22.x |
| 10.0.13 (not live yet) | 9.23.x |

## Pull updates

The SDK, SSK, and other dependency updates are optional and can be pulled down to a local development environment by using the **yarn** command in the SDK source code. When this command is run, the latest dependencies are pulled down, based on the versions that are specified in the packages.json file. Before you run the **yarn** command, you should delete the yarn.lock file from the root directory. Optionally, you can also delete the /node\_modules folder to get a clean set of dependency files.

After the latest dependencies are pulled down, you can run **yarn start** to run the Node server on your development environment and test the new SDK and SSK components.

When a configuration package is created by using the **yarn msdyn365 pack** command-line interface (CLI) tool, all dependencies are updated to their local versions during the packaging process. The package that is created can then be uploaded to an online site by using Microsoft Dynamics Lifecycle Services (LCS).

## Determine the latest released versions of the dependency packages

To determine the latest released versions of the dependency packages, follow these feed links:

- [SSK feed](https://dev.azure.com/commerce-partner/Registry/_packaging?_a=package&feed=dynamics365-commerce&view=versions&package=%40msdyn365-commerce-modules%2Fstarter-pack&protocolType=Npm)
- [SDK feed](https://dev.azure.com/commerce-partner/Registry/_packaging?_a=package&feed=dynamics365-commerce&view=versions&package=%40msdyn365-commerce%2Fbootloader&protocolType=Npm)
- [Retail Server proxy feed](https://dev.azure.com/commerce-partner/Registry/_packaging?_a=package&feed=dynamics365-commerce&view=versions&package=%40msdyn365-commerce%2Fretail-proxy&protocolType=Npm)

## Determine the versions deployed on an e-Commerce site

To determine the deployed versions of the SDK, SSK, and Retail Server proxy that are used on an e-Commerce site, right-click a site page, select **View page source**, and then search for the following strings to find the version number:

- **commerceSDKVersion** – The SDK version.
- **commerceSSKVersion** – The SSK version.
- **retailServerProxyVersion** – The Retail Server proxy version.

## Updating the app.settings.json file
Within the SDK **/src/settings** directory is a file called **app.settings.json** file which surfaces global settings to the site builder tool which are used by the store starter kit set of modules.  These settings can be found in the site builder tool under the **Site Settings** -> **Extensions** section. This file can also be with customized settings that custom modules can use.  

When upgrading the store starter, there may be new settings that are applicable to them that need to be manually added.  The latest app.settings.json file can be found in the [online SDK GitHub settings directory](https://github.com/microsoft/Msdyn365.Commerce.Online/tree/master/src/settings).  This file contains the latest settings for the latest available store starter kit.  If you've not made any additions to the app.settings.json file, you can copy the contents to your version or do a diff and merge the new settings in manually.  If you are updating to an older store starter kit than the latest you can find the specific app.settings.json file under the [online SDK GitHub settings version directory](https://github.com/microsoft/Msdyn365.Commerce.Online/tree/master/src/settings/versions).  You'll need to manually merge the contents to your app.settings.json file. 

When a configuration package is created by using the **yarn msdyn365 pack** command-line interface (CLI) tool, the app.settings.json file updates will be included. The package that is created can then be uploaded to an online site by using Microsoft Dynamics Lifecycle Services (LCS) and you should now see the new settings in the site builder tool.

## Additional resources

[Package configurations and deploy them to an online environment](package-deploy.md)
