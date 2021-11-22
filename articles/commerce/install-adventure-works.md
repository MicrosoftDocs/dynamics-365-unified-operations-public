---
# required metadata

title: Install the Adventure Works theme
description: This topic describes how to install the Adventure Works theme in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
ms.date: 07/21/2021
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

Before you install the Adventure Works theme, you must have a Dynamics 365 Commerce environment (Commerce version 10.0.20 or later) that includes Retail Cloud Scale Unit (RCSU), the Commerce online software development kit (SDK), and the Commerce module library. For information about how to install the Commerce SDK and module library, see [SDK and module library updates](e-commerce-extensibility/sdk-updates.md). 

## Installation steps

### Install the Adventure Works theme in your application

The Adventure Works theme package is available in the **dynamics365-commerce** feed, as **@msdyn365-commerce-theme/adventureworks-theme-kit**. However, although the Adventure Works theme package is part of that feed, it's under a different namespace. Therefore, you must follow these steps to add registry entries for the namespace.

1. Update the **.npmrc** file so that it includes the following registry entry (if the entry isn't already included):

    `@msdyn365-commerce-theme:registry=https://pkgs.dev.azure.com/commerce-partner/Registry/_packaging/dynamics365-commerce/npm/registry/`

1. Update the **.yarnrc** file so that it includes the following registry entry (if the entry isn't already included):

    `"@msdyn365-commerce-theme:registry" "https://pkgs.dev.azure.com/commerce-partner/Registry/_packaging/dynamics365-commerce/npm/registry/"`	
	
To install the package in your local environment, run the following command from the command prompt. This command automatically updates the package.json file so that it includes the dependency.

`yarn add @msdyn365-commerce-theme/adventureworks-theme-kit`

In the **package.json** file, you should update the theme version to a specific version.

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
