---
# required metadata

title: Install the Adventure Works theme
description: This topic describes how to install the Adventure Works theme in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
ms.date: 12/10/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
ms.search.industry: 
ms.author: anupamar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.8

---

# Install the Adventure Works theme

[!include [banner](includes/banner.md)]

This topic describes how to install the Adventure Works theme in Microsoft Dynamics 365 Commerce. 

> [!IMPORTANT]
> The Adventure Works theme and modules are available as of the Dynamics 365 Commerce version 10.0.20 release. They are available from Microsoft AppSource.

## Prerequisites

Before you install the Adventure Works theme, you must have a Dynamics 365 Commerce environment (Commerce version 10.0.20 or later) that includes Retail Cloud Scale Unit (RCSU), the Commerce online software development kit (SDK), and the Commerce module library. For information about how to install the Commerce SDK and module library, see [Set up a development environment](e-commerce-extensibility/setup-dev-environment.md) . 

## Installation steps

### Install the Adventure Works theme in your application

The Adventure Works theme package is available in the **dynamics365-commerce** feed, as **@msdyn365-commerce-theme/adventureworks-theme-kit**. However, although the Adventure Works theme package is part of that feed, it's under a different namespace. Therefore, you must follow these steps to add registry entries for the namespace.

1. Update the **.npmrc** file so that it includes the following registry entry (if the entry isn't already included):

    `@msdyn365-commerce-theme:registry=https://pkgs.dev.azure.com/commerce-partner/Registry/_packaging/dynamics365-commerce/npm/registry/`

1. Update the **.yarnrc** file so that it includes the following registry entry (if the entry isn't already included):

    `"@msdyn365-commerce-theme:registry" "https://pkgs.dev.azure.com/commerce-partner/Registry/_packaging/dynamics365-commerce/npm/registry/"`	
	
To install the package in your local environment, run the `yarn add THEME_PACKAGE@VERSION` command from the command prompt, where **THEME_PACKAGE** is the theme package (@msdyn365-commerce-theme/adventureworks-theme-kit) and **VERSION** is the version number of the module library being used. It is important that the versions of the theme package and the module library match. To find the correct module library version number to use, open the package.json file and locate the **starter-pack** value under the **dependencies** section. In the following example, the package.json file uses version 9.32 of the module library which maps to the Dynamics 365 Commerce version 10.0.22 release.  

```json
"dependencies": {
    "@msdyn365-commerce-modules/starter-pack": "9.32",
}
```

The following example shows how to run the `yarn add` command to add version 9.32 of the Adventure Works theme. The command automatically updates the package.json file so that it includes the dependency.

`yarn add @msdyn365-commerce-theme/adventureworks-theme-kit@9.32`

For more information about updating the module library version, see [SDK and module library updates](e-commerce-extensibility/sdk-updates.md). 

> [!IMPORTANT]
> - The theme version should match the module library version to ensure that all features work as expected. 
> - The minimum version for the Commerce module library and SDK should be 10.0.20 (9.31). 

### Add the font files for the Adventure Works theme

After the Adventure Works theme is installed in your app, you must add the font files that are required for it. To complete this step, copy all the font files from **\node_modules@msdyn365-commerce-theme\adventureworks-theme-kit\src\modules\adventureworks\public\webfonts** to the partner application public directory path **\public\webfonts**.

### Set up the resources for the Adventure Works theme

The next step is to update the required default resource for the theme. To complete this step, copy the content from the global.json file under **\node_modules@msdyn365-commerce-theme\adventureworks-theme-kit\src\modules\adventureworks\resources\modules** to the partner application global.json file under **\src\resources\modules**. If the **\src\resources** target directory doesn't exist, it can be copied in its entirety from the **\node_modules@msdyn365-commerce-theme\adventureworks-theme-kit\src\modules\adventureworks** source directory to the **\src** target directory.

### Pull updates and validate the theme

For information about how to pull the latest SDK, module library, and other dependency updates, see the "Pull updates" section of [SDK and module library updates](e-commerce-extensibility/sdk-updates.md#pull-updates).

After the latest dependencies are pulled down, you can run the **yarn start** command to start the Node server in your development environment and test the new Adventure Works theme. Browse the application locally by using the query string parameter `?theme=adventureworks` (for example, `https://localhost:4000/?theme=adventureworks`).

## Additional resources

[Adventure works theme](adventure-works-theme.md)

[Module library overview](starter-kit-overview.md)

[SDK and module library updates](e-commerce-extensibility/sdk-updates.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
