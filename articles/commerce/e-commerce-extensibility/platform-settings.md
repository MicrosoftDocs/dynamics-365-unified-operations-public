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
    "namespaceExtentions" : [ ],
    "enableChunkByModulePackage": false,
    "chunkingGroupPreference": [ ] 
}
```

### dataActionTimeoutInMs
The **dataActionTimeoutInMs** setting defines the maximum amount of time in milliseconds that data actions will wait for a response before timing out. The timeout represents a lower bound for your page response as the action framework will wait as long as the timeout is defined before timing out and returning the page. The default value is 4000 milliseconds (4 seconds).

### minClientChunkSize
The **minClientChunkSize** setting defines the minimum webpack JavaScript chunk size in bytes to be delivered to the browser. JavaScript chunks smaller than the min size will be grouped together to form chunks over the minimum size. A smaller minimum size will mean more chunks will be generated which will offer greater code splitting and less unused JavaScript at the cost of downloading many smaller chunks. A larger minimum size will mean less overall chunks will be generated which will reduce the amount of JavaScript files that need to be downloaded at the cost of potentially including some unused JavaScript code. The default value is 30000 bytes (30KB).

### excludedModules
The **excludedModules** setting defines a set of modules that will be excluded from webpack JavaScript chunks. E-Commerce modules get bundled into JavaScript chunks and shipped to the browser client side, if modules are not needed on a site, they can be excluded to reduce the JavaScript chunk size and help increase the page load speed.

### namespaceExtentions
The **namespaceExtensions** setting defines the supported namespaces used for module registration. By default, the only supported namespace is the **@msdyn365-commerce-modules** namespace which contains all of the module library and core set of modules. The module package name is defined in following format: <namespace>/<module_name>. If modules are published with a new namespace, the namespace can be added to the this settings.

### enableChunkByModulePackage
The **enableChunkByModulePackage** setting is used to enable module webpack JavaScript to be chunked in an ordered way. By default, modules from the same module package will be bundled together into the same webpack JavaScript chunk.  By setting this to **true**, the **chunkingGroupPreference** setting can be used to specify groups of modules to be packed together in a chunk. The default value is **false**.

When the e-Commerce runtime load a page, all JavaScript chunks containing the required modules for the page will be sent to the client.  The JavaScript sent to a client browser for a page can be reduced by grouping modules that interact with each other within a page which can reduce the page load time.

### chunkingGroupPreference
The **chunkingGroupPreference** settings is used to specify sets of modules that will be grouped together into a webpack chunk when the **enableChunkByModulePackage** setting is set to **true**. The default chunking logic is to group modules from the same package into the same chunk.  In a case where same module name exist in different namespace's, the module namespace can be used to specify the module name ([<namespace>/<module_name1>, module_name2]). The namespace used for local modules is **__local__**. 
    
For example, if module1 and module2 will always be used at the same time on the same page, module1 and module2 can be added to one chunk group to avoid those be split into two different chunks.  In this example module1 and module2 will be sent to a browser client in a single JavaScript chunk, instead of potentially multiple JavaScript chunks containing other not used modules.  

Note: Due to **minCLientChunkSize** setting, other modules may be automatically merged into a defined chunking group.


