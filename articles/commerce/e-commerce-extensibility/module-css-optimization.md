---
# required metadata

title: Module CSS optimization
description: This topic presents an
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

This topic presents an overview and instructions on leveraging module CSS optimization to get better performance on page load.

## Web storefront component-based architecture

Module CSS optimization helps in reducing the overall CSS bundle size on the page which helps in improving the page performance. Current structure is all CSS is bundled up in a single *.theme.scss file inside a theme. SDK injects the theme css static file from cdn in every page, since the single *theme.scss file contains css from all modules, there is a lot of unused css on a page for modules that does not exists on the page.
 
To help improve the CSS performance and reduces the unused css on the page, customers can leverage this new feature which will help improve the page load performance.
 
With module CSS Optimization feature, we have added support for splitting CSS per module and dynamically inject the module CSS on the page. This will help in on reducing unused CSS on a page that browser has to download and help improve performance.
 
  Requirements: 
•	Webpack5 : This feature is only supported on Webpack5. To use this feature please, upgrade the partner app to use webpack5 using this CLI       
 
                        yarn msdyn365 upgrade-webpack
 
•	SDK 1.35.13 or later 
•	Fabrikam-design-kit theme styles for module css with supported from 9.36 or later
 
	How to turn on moduleCssOptimization feature:
 
ModuleCssOptimization is an opt in feature and can be enabled through paltform.settings.json located in src/settings/platform.setings.json
 
{
    "enableModuleCssOptimization": true
}
 
 
	How to configure styles to enable moduleCssOptimization:
 
With this feature, we will support splitting individual module styles inside themes. Below steps will help you guide on how to configure styles for individual modules.
 
Steps:

1.	Each theme contains `styles` folder where we configure all the CSS
 
 
 
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

