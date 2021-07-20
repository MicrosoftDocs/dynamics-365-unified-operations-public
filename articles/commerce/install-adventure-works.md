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

### Step 1: Install the Adventure Works theme in your application

The Adventure Works theme package is available in the dynamics365-commerce feed as **@msdyn365-commerce-theme/adventureworks-theme-kit**. The Adventure Works theme package is part of the same feed, but under a different namespace, so you will need to add a registry entry for this namespace as shown below:

Update.npmrc file to include the below registry entry (if not already included)
**@msdyn365-commerce-theme:registry=https://pkgs.dev.azure.com/commerce-partner/Registry/_packaging/dynamics365-commerce/npm/registry/**

Update .yarnrc to include the below registry entry (if not already included)
**"@msdyn365-commerce-theme:registry" "https://pkgs.dev.azure.com/commerce-partner/Registry/_packaging/dynamics365-commerce/npm/registry/"**  	
	
In your command prompt, execute the below command to install the package on your local environment.  This will auto-update the package.json file to include the dependency.

`yarn add @msdyn365-commerce-theme/adventureworks-theme-kit`

You should update theme version in package.json to a specific version. 

> [!IMPORTANT]
> The version of the theme should match the Module library (SSK package) version to ensure all the features work as expected. 
> The minimum version for Module Library and SDK should be 10.0.20 (9.31). 


### Step 2: Set up the fonts for the Adventure Works theme

Now that the adventure works theme is installed on your app, you need to add the font files required for this theme. For this, copy all the font files from **\node_modules@msdyn365-commerce-theme\adventureworks-theme-kit\src\modules\adventureworks\public\webfonts** to partner application public folder font path **\public\webfonts**.

### Step 3: Set up the resources for the Adventure Works theme

Next step, is to update the required default resource for the theme. For this, copy the content of global.json file from **\node_modules@msdyn365-commerce-theme\adventureworks-theme-kit\src\modules\adventureworks\resources\modules** to partner application global.json file under **\src\resources\modules**.  If resource folder does not exists, it can be just copied from this path entirely **"\node_modules@msdyn365-commerce-theme\adventureworks-theme-kit\src\modules\adventureworks\** under **\src\**

### Step 4: Pull updates and validate the theme

To pull SDK, module library, and other dependency updates, see the "Pull updates" section of [SDK and module library updates](e-commerce-extensibility/sdk-updates#pull-updates).

Delete the **yarn.lock** file from the root directory and then . Optionally, you can also delete the **/node_modules** folder to get a clean set of dependency files. Run the yarn command to pull all the dependencies as mentioned in package.json 

After the latest dependencies are pulled down, you can run yarn start to run the Node server on your development environment and test the new adventure works theme. Browse application locally and with query string parameter ``?theme=adventureworks`` (for example, ``https://localhost:4000/?theme=adventureworks``).


## Additional resources

[Adventure works theme](adventureworks-theme.md)

[Module library overview](starter-kit-overview.md)

[Module Library and SDK updates](sdk-updates.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
