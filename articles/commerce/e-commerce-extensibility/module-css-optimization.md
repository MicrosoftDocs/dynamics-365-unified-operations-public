---
# required metadata

title: Module CSS optimization
description: This topic presents an ....
author: samjarawan
ms.date: 11/20/2020
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 

ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: samjar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---
# Module CSS optimization

[!include [banner](../includes/banner.md)]

This topic presents an overview and instructions on leveraging the module CSS optimization feature to help reduce the overall CSS bundle size leading to improved page performance.  

By default, a theme bundles all module CSS in a single file within the theme styles directory named THEME_NAME.theme.scss file, where THEME_NAME is the name of your theme. The online SDK injects the theme CSS static file from CDN on every rendered e-commerce page, since the single THEME_NAME.theme.scss file contains CSS from all modules, there can be a good amount of unused CSS on a page that only uses a subset of available modules. The module CSS optimization feature adds support to split CSS per module and only dynamically inject the module CSS relevant to the rendered e-commerce.
 
## Requirements
To enable module CSS optimization feature ensure the following pre requisites are met:

* Using Online SDK version 1.35.13 or newer.
* Webpack5 is required for this feature to work, upgrade your SDK code to webpack5 using the **upgrade-webpack** CLI: ```yarn msdyn365 upgrade-webpack```.
* If you are using the Fabrikam reference theme (Fabrikam-design-kit), module CSS support will be added release 9.36 (10.0.26) or newer.
 
## Enable module CSS optimization
Module CSS optimization is an opt in feature and can be enabled by adding **ModuleCssOptimization** to the **src/settings/platform.setings.json** file as shown below

```json
{
    "enableModuleCssOptimization": true
}
```

### Configure theme styles to enable module CSS optimization for individual modules
 
The below steps will help you guide on how to configure CSS for individual modules.
 
Steps:

1.	Each theme contains `styles` folder where we configure all the CSS
![styles](media/css-optimization-1.png)

2.	Inside styles, you can define all module specific styles in styles/modules directory. 


Note : For configuring `rtl` specific styles, you can add all rtl specific module styles in styles/modules-rtl directory
 
3.	Modules folder will contain individual module CSS  <moduleName>.scss files, 
Note: The <module name> should match the name property in module.definition.json 
 
 
 
4.	Each <moduleName>.scss  should have its corresponding <moduleName>.js  file.
 
 
 
5.	<moduleName>.scss  file should contains all styles for related of that module
 
 
 
 
 
6.	In <moduleName>.js file, you can import <moduleName>.scss
 
 
 
<moduleName>.js files are the entry files for creation of the module css chunks. So each <moduleName>.scss file should always have a <moduleName>.js files.
 
	Configuring assets in CSS:
 
Old structure: 
 
Currently, all the assets are stored in root level public directory:
 
 
 
 
New structure:
 
All the needs to be stored in public/msdyn365-assets
 
 
 
•	Assets should be imported from msdyn365-assets folder your styles
 
Example:
 
 
 
Note: 
 
We use webpack to compile and build the module css chunks and only show the css compilation error when building the project in production mode. 
 
	How check for CSS compliation errors:
The customer can build the project in production mode using yarn build:prod command to see any css compliation error. Any CSS compliation errors are generated in stats-client-build-errors.json file at the root level

	Best practices for configuring module css styles:
 
•	Avoid Importing module-A styles into module-B styles as its an anti-pattern and it defeats the purpose of creating smaller css chunks. Rather, moduleA should only have styles related to moduleA and same for moduleB
 
•	Any component styles that is used by one or more module, can be imported in <moduleName>.js 
 
Example: 
 
If header and footer module uses a common button component styles,
 
header.js
 
 
Footer.js
 
 
 
With this approach, SDK will create common css chunks which will be help in keep individual module css chunks small.
 
•	Avoid importing index.scss file in the <moduleName>.scss, only import if all the styles imports from index.scss are used by your module.

