---
# required metadata

title: Install the Adventure Works theme
description: This topic describes how to install the Adventure Works theme in Microsoft Dynamics 365 Commerce.
author: anupamar-ms
ms.date: 07/20/2021
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
> The Adventure Works theme and modules are available as of the Dynamics 365 Commerce version 10.0.20 release and is available from Microsoft AppSource.

## Prerequisites

Before installing the Adventure Works theme, it is required to have a Dynamics 365 Commerce environment installed (Commerce version 10.0.20 or later), including Retail Cloud Scale Unit (RCSU), the Commerce online software development kit (SDK), and the Commerce module library. For information on installing the Commerce SDK and module library, see [SDK and module library updates](e-commerce-extensibility/sdk-updates.md). 

## Installation steps

### Install the Adventure Works theme in your application

The Adventure Works theme package is available in the dynamics365-commerce feed as **@msdyn365-commerce-theme/adventureworks-theme-kit**. The Adventure Works theme package is part of the same feed, but under a different namespace, so you will need to add registry entries for this namespace as shown below:

Update the **.npmrc** file to include the following registry entry (if not already included):

`@msdyn365-commerce-theme:registry=https://pkgs.dev.azure.com/commerce-partner/Registry/_packaging/dynamics365-commerce/npm/registry/`

Update the **.yarnrc** file to include the following registry entry (if not already included):

`"@msdyn365-commerce-theme:registry" "https://pkgs.dev.azure.com/commerce-partner/Registry/_packaging/dynamics365-commerce/npm/registry/"`	
	
In your command prompt, execute the following command to install the package on your local environment. This will automatically update the package.json file to include the dependency.

`yarn add @msdyn365-commerce-theme/adventureworks-theme-kit`

You should update the theme version in package.json to a specific version. 

> [!IMPORTANT]
> - The version of the theme should match the module library version to ensure that all features work as expected. 
> - The minimum version for the Commerce module library and SDK should be 10.0.20 (9.31). 

### Set up the fonts for the Adventure Works theme

After the Adventure Works theme is installed on your app, you must add the font files required for the theme. To do this, copy all of the font files from **\node_modules@msdyn365-commerce-theme\adventureworks-theme-kit\src\modules\adventureworks\public\webfonts** to the partner application public directory font path **\public\webfonts**.

### Set up the resources for the Adventure Works theme

The next step is to update the required default resource for the theme. To do this, copy the content from the global.json file under **\node_modules@msdyn365-commerce-theme\adventureworks-theme-kit\src\modules\adventureworks\resources\modules** to the partner application global.json file under **\src\resources\modules**. If the target **\src\resources** directory does not exist, it can be copied in its entirety from **\node_modules@msdyn365-commerce-theme\adventureworks-theme-kit\src\modules\adventureworks** to **\src**.

### Pull updates and validate the theme

To pull SDK, module library, and other dependency updates, see the "Pull updates" section of [SDK and module library updates](e-commerce-extensibility/sdk-updates.md#pull-updates).

After the latest dependencies are pulled down, you can run **yarn start** to run the Node server on your development environment and test the new Adventure Works theme. Browse the application locally using the query string parameter ``?theme=adventureworks`` (for example, ``https://localhost:4000/?theme=adventureworks``).

## Additional resources

[Adventure works theme](adventure-works-theme.md)

[Module library overview](starter-kit-overview.md)

[SDK and module library updates](e-commerce-extensibility/sdk-updates.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
