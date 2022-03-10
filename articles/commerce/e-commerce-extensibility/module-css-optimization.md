---
# required metadata

title: Module CSS optimization
description: This topic describes how to use the module CSS optimization feature in Microsoft Dynamics 365 Commerce to help reduce the overall CSS bundle size of an e-commerce page to improve page performance.
author: samjarawan
ms.date: 03/10/2022
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: v-chgriffin
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

This topic describes how to use the module Cascading Style Sheets (CSS) optimization feature in Microsoft Dynamics 365 Commerce to help reduce the overall CSS bundle size of an e-commerce page to improve page performance.

By default, a theme bundles all module CSS code into a single file named **\<THEME_NAME\>.theme.scss file** within the theme styles directory, where **\<THEME_NAME\>** is the name of the theme. The online software development kit (SDK) then injects the single static theme CSS file from the content delivery network (CDN) on every rendered e-commerce page. Since the single **\<THEME_NAME\>.theme.scss** file contains CSS code from all modules, there can be a non-trivial amount of unused CSS code injected for pages that only use a subset of available modules. The module CSS optimization feature adds support to split CSS code per module and only dynamically inject the module CSS code relevant to a rendered e-commerce page.
 
## Prerequisites

To enable the module CSS optimization feature, the following prerequisites must be met.

- Online SDK version 1.35.17 or later.
- Webpack 5 is required for this feature to work. Upgrade your SDK code to Webpack 5 using the **upgrade-webpack** CLI command: ```yarn msdyn365 upgrade-webpack```.
- If you are using the Fabrikam reference theme (Fabrikam-design-kit), module CSS support will be added to release 9.36 (Commerce version 10.0.26 release) and later.
 
## Enable module CSS optimization

Module CSS optimization is an opt-in feature that can be enabled by adding the **enableModuleCssOptimization** property to the **src/settings/platform.setings.json** file, as shown in the following example:

```json
{
    "enableModuleCssOptimization": true
}
```

### Configure theme styles to enable module CSS optimization for individual modules
 
Each theme contains a **styles** folder where all of the theme CSS files reside. Module-specific styles must be included in a new **modules** directory within the styles folder.

> [!NOTE]
> When configuring right-to-left (RTL) styles, add all RTL-specific module styles to the **styles\/modules-rtl** directory.
 
Each module that you want to enable CSS optimization on will require two files added to the **modules** directory: **\<MODULE_NAME\>.scss** and **\<MODULE_NAME\>.js**, where **\<MODULE_NAME\>** matches the name property within the module definition file (**\<MODULE_NAME\>.definition.json**). For example, for the header module the two files would be named **header.js** and **header.scss**.
 
The **\<MODULE_NAME\>.scss** file contains all styles needed for the individual module, as shown in the following example for a header module.

![Example of a header.scss file](media/css-optimization-3.png)

The **\<MODULE_NAME\>**.js file is the entry file for creation of the module CSS chunks and contains a single line to import the CSS file, as shown in the following example.

```javascript
import "./header.scss"
```
 
## Configure assets in CSS for use with module CSS optimization
 
By default all the assets are stored in root level **public** directory, for example **public/images**. To use assets within the module CSS optimization files they must be stored in the **public/msdyn365-assets** directory, for example  **public/msdyn365-assets/images**. Assets should then be imported from the **msdyn365-assets** directory within SCSS files using the relative path **../../../../../msdyn365-assets/**, as shown in the following example.

```SCSS
$msv-font-path: ../../../../../msdyn365-assets/webfonts
```

## CSS compilation errors

Webpack 5 is used to compile and build the module CSS chunks and only shows CSS compilation errors when building the project in production mode using the **yarn build:prod** CLI command. CSS compilation errors can be found in a generated **stats-client-build-errors.json** file at the root SDK level.

## Best practices for configuring module CSS styles
 
The following are best practices for configuring module CSS styles, using "module-A" and "module-B" to represent two different modules.
 
- Avoid importing module-A styles into module-B styles because it defeats the purpose of creating smaller CSS chunks. Instead, module-A styles should only have styles related to module-A and module-B styles should only have styles for module-B.
- Avoid importing the **index.scss** file in the **\<MODULE_NAME\>.scss** file. Only import the **index.scss** file if all the styles imported from the file are used by the module.
- Component styles that are used by one or more modules can be imported in the **\<MODULE_NAME\>.js**. For example if module-A and module-B use common button component styles, they can both import the component as shown in the following examples:

**module-A.js**
```js
import "./module-A"
import "../common/03-components/button.scss"
```

**module-B.js**
```js
import "./module-B"
import "../common/03-components/button.scss"
``` 

With this approach, the SDK will create common CSS chunks that will help to keep individual module CSS chunks small.
 
