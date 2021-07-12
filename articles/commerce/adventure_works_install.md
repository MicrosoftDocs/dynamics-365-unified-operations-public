---
# required metadata

title: Adventure Works theme installation
description: This topic gives an overview of how to install the Adventure Works theme.
author: anupamar-ms
ms.date: 07/08/2021
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

# Adventure Works theme installation

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This topic gives an overview of how to install the Adventure works theme. 

> [!IMPORTANT]
> The Adventure Works theme and the new modules are available as of the Dynamics 365 Commerce version 10.0.20 release. THis theme is available via Marketplace (Appsource) and will need to be installed  *new customer*  * old customers*

## Prerequisites

## Installation steps

### Step 1: Install Adventure works theme in your application

The adventure works theme package is available in the dynamics365-commerce feed as @msdyn365-commerce-theme/adventureworks-theme-kit. The package is part of the same feed, but under a different namespace, so you will need to add a registry entry for this namespace as shown below:

Update.npmrc file to include the below registry entry

  - @msdyn365-commerce-theme:registry=https://pkgs.dev.azure.com/commerce-partner/Registry/_packaging/dynamics365-commerce/npm/registry/
  - @msdyn365-commerce-modules:registry=https://pkgs.dev.azure.com/commerce-partner/Registry/_packaging/dynamics365-commerce/npm/registry/
  - @msdyn365-commerce:registry=https://pkgs.dev.azure.com/commerce-partner/Registry/_packaging/dynamics365-commerce/npm/registry/
  - @msdyn365-commerce-thirdpartyconnectors:registry=https://pkgs.dev.azure.com/commerce-partner/Registry/_packaging/dynamics365-commerce/npm/registry/
  	- registry=https://registry.npmjs.org/
	always-auth=true
	

Update .yarnrc to include the below registry entry
   - registry "https://registry.npmjs.org/"
   -   "@msdyn365-commerce-modules:registry" "https://pkgs.dev.azure.com/commerce-partner/Registry/_packaging/dynamics365-commerce/npm/registry/"
   -  "@msdyn365-commerce-theme:registry" "https://pkgs.dev.azure.com/commerce-partner/Registry/_packaging/dynamics365-commerce/npm/registry/"
   -  "@msdyn365-commerce:registry" "https://pkgs.dev.azure.com/commerce-partner/Registry/_packaging/dynamics365-commerce/npm/registry/"
   -  "@msdyn365-commerce-thirdpartyconnectors:registry" 
   -  "https://pkgs.dev.azure.com/commerce-partner/Registry/_packaging/dynamics365-commerce/npm/registry/"
	network-timeout 120000
	
	
In your command prompt, execute the below command to install the package on your local environment.  This will auto-update the package.json file to include the dependency.

`yarn add @msdyn365-commerce-theme/adventureworks-theme-kit`

You can should update theme version in package.json to a specific version by updating the version number manually.

> [!IMPORTANT]
> The version of the theme should match the Module library (SSK package) version to ensure the features work as expected. 


### Step 2: Setup the fonts for adventure works theme
Now that the adventure works theme is installed on your app, you need to add the font files required for this theme. For this, copy all the font files from **\node_modules@msdyn365-commerce-theme\adventureworks-theme-kit\src\modules\adventureworks\public\webfonts** to partner application public folder font path **\public\webfonts**.

### Step 3: Setup the resources for adventure works theme
Next step, is to update the required default resource for the theme. For this, copy the content of global.json file from **\node_modules@msdyn365-commerce-theme\adventureworks-theme-kit\src\modules\adventureworks\resources\modules** to partner application global.json file under **\src\resources\modules**. If this does not exists create the one as **\src\resources\modules\global.json** and update the content.

### Step 4: Validate the theme
Run yarn on command prompt to make sure all the dependecies are downloaded. You might need to delete the yarn.lock file under partner application root. Run yarn build followed by yarn start. Browse application locally and with query string parameter **?theme=adventureworks**. Your page shoudl render with adventure works theme styles.


## Additional resources

[Adventure works theme](adventureworks-theme.md)

[Module library overview](starter-kit-overview.md)

[Tile list module](tile-list-module.md)

[Interactive feature module](interactive-feature-module.md)

[Active image module](active-image-module.md)

[Subscribe module](subscribe-module.md)

[Image list module](image-list-module.md)

[Theme extensions](e-commerce-extensibility/theme-module-extensions.md)

[Cart icon module](cart-icon-module.md)

[Set up a B2B e-commerce site](./b2b/set-up-b2b-site.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
