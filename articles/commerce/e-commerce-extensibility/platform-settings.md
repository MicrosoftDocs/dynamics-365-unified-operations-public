---
# required metadata

title: Platform settings file
description: This topic covers the platform settings file options in Microsoft Dynamics 365 Commerce.
author: samjarawan
manager: annbe
ms.date: 09/28/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: samjar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.13

---

# Platform settings file

[!include [banner](../includes/banner.md)]

This topic covers the platform settings file options in Microsoft Dynamics 365 Commerce.

## Overview

The \src\settings\platform.settings.json file holds various platform settings used by the e-Commerce runtime. This file may not exist by default, by can be added under the **\src\settings\\** directory.  The following example JSON (JavaScript Object Notation) file includes various supported feature settings.

```json
{
    "dataActionTimeoutInMs": 4000,
    "minClientChunkSize": 30000,
    "excludeModules": [ ],
    "namespaceExtentions" :  [ ],
    "enableChunkByModulePackage": false,
    "chunkingGroupPreference": [ ] 
}
```

### dataActionTimeoutInMs
Defines the maximum amount of time in milliseconds that data actions will wait for a response before timing out. Keep in mind that timeout represents a lower bound for your page response as the action framework will wait as long as the timeout is defined before timing out and returning the page. The default value is 4000 milliseconds or 4 seconds.

### minClientChunkSize
Defines the minimum webpack JavaScript chunk size in bytes to be delivered to the browser. JavaScript chunks smaller than the min size will be grouped together to form chunks over the minimum size. 

A smaller minimum size will mean more chunks will be generated which will offer greater code splitting and less unused JavaScript at the cost of downloading many smaller chunks.
A larger minimum size will mean less overall chunks will be generates will reduce the amount of JavaScript files that need to be downloaded at the cost of potentially including some unused JavaScript code.

The default value is 30KB or 30000

### excludedModules
E-Commerce Modules will be bundled into JavaScript chunks and shipped to client side.  However, if customer find that there are modules that they wont use for their site, they can define list of unused module       names to exclude those modules from being bundled into webpack JavaScript chunks for the site. Doing this will reduce the chunk size shipped to client, and will increase the page load speed

### namespaceExtentions
 The module package name is defined in following format: <namespace> / <module_name>. SDK will only register modules from supported namespace (By default, we only support namespace         @msdyn365-  commerce-modules). If customer publishes their own modules under new namespaces, the can extended supported package namespace by adding their namespace to the list and all modules from namespaceExtensions will be registered as well.

### enableChunkByModulePackage
              eCommerce modules will be created with the directory path in format - <package_name>/src/modules/<module_name>.
enable this will automatically bundle eCommerce modules into webpack JavaScript chunks in ordered way. Modules from the same module package will be bundled together into the same Webpack JavaScript chunk. When SDK load a page, SDK will ship all JavaScript chunks containing the required modules of the page.  Doing this will weed out non-required modules from the JavaScript chunks shipping to client side as much as possible. Therefore, it will increase the page load speed.

For example:
PDP page need modules : checkout, buybox
HOME page need modules: navigation-menu.

Random chunking logic will potentially group checkout module and navigation-menu module together. Therefore, whenever we load PDP page or HOME page, we have to ship both checkout and navigation-menu module to the client side, even though navigation-menu is not needed for PDP and checkout is not needed for HOME page.  With the new logic, we will only ship checkout , buybox to PDP page and navigation-menu to HOME page. 

default value is : false. 

### chunkingGroupPreference
When enableChunkByModulePackage  is enabled,  the default chunking logic is to group modules from the same package into the same chunk. However, the default chunking logic might not fit customer’s situation. Customer can customize Webpack chunking groups by defining module names into the same chunking-group. Modules from  the same group will be bundled into the same webpack JavaScript chunk. In case of same module name exist in different namespace, customer can use module namespace - [<namespace>/<module_name1>, module_name2] to specify the specific module. Namespace for local modules is __local__.   Bundle required modules into the same JavaScript chunk will help reduce the chunk size shipped to client side for a certain page and increase the page load speed.

For example, if customer find module1 and module2 will always be used at the same time, customer can put module 1 and module2 to one group in              chunkingGroupPreference to avoid those be split into two different chunks. Therefore, when we ship module1 and modul2 to client side, we only need to ship one JavaScript chunk containing module1 and module2 , instead of shipping two JavaScript chunks containing other not used modules.

FYI: some tiny modules might still be automatically merged into customer defined chunking group by webpack due to minClientChunkSize setting.


## JavaScript chunking
By default, when modules are compiled the JavaScript code is grouped into different chunks randomly.  This may not be the optimal since the JavaScript chunks served to a client browser may contain JavaScript for modules that are not used a particular page.  By cusomizing the JavaScript chunking, the over chunk size sent to a client can be reduces thus improving load time on a page.

As an example, the product details page (PDP) may render the checkout and buybox modules and the homepage a carousel and content block module.  Random chunking logic could group the checkout and carousel together into a chunk and the buybox and content block module in another chunk.  When rendering the PDP, the client would need both JavaScript  chunks to render the page, and get extra JavaScript not needed for the particular page.

To enable non random chunking
* Set the **enableChunkByModulePackage** property to true in the platform.settings.json file
* Group modules into chunks by defining the **chunkingGroupPreference** groups as shown below:

```"chunkingPreference": [[<group1>], [<group2>]]```
  
Modules that fall into the same group will be bundled together into the same chunk as shown below:
```"chunkingPreference": [["module1", "module2"], ["module", "module4"]]```

If the chunkingPreference is not set, modules from the same module package (under the supported namespace) will be bundled together. 
