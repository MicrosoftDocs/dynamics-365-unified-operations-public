---
# required metadata

title: Platform settings file
description: This topic covers the platform settings file options in Microsoft Dynamics 365 Commerce.
author: samjarawan
manager: annbe
ms.date: 01/28/2021
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
[!include [banner](../includes/preview-banner.md)]

This topic covers the platform settings file options in Microsoft Dynamics 365 Commerce.

The **\src\settings\platform.settings.json** file holds various platform settings used by the Commerce e-commerce runtime. This file may not exist by default, but can be added under the **\src\settings\\** directory. The following example JSON file shows various supported feature settings.

```json
{
    "dataActionTimeoutInMs": 4000,
    "minClientChunkSize": 30000,
    "excludeModules": [ ],
    "namespaceExtensions" : [ ],
    "enableChunkByModulePackage": false,
    "chunkingGroupPreference": [ ] 
}
```

## dataActionTimeoutInMs

The **dataActionTimeoutInMs** property defines the maximum amount of time in milliseconds that data actions will wait for a response before timing out. The timeout represents a lower bound for page response since the action framework will wait as long as the timeout is defined before timing out and returning the page. The default value is 4000 milliseconds (4 seconds).

## minClientChunkSize

The **minClientChunkSize** property defines the minimum webpack JavaScript chunk size in bytes to be delivered to the browser. JavaScript chunks smaller than the minimum size will be grouped together to form chunks over the minimum size. A smaller minimum size will mean more chunks will be generated, which will offer greater code splitting and less unused JavaScript at the cost of downloading many smaller chunks. A larger minimum size will mean fewer overall chunks will be generated, which will reduce the amount of JavaScript files that need to be downloaded at the cost of potentially including some unused JavaScript code. The default value is 30000 bytes (30 KB).

## excludedModules

The **excludedModules** property defines a set of modules that will be excluded from webpack JavaScript chunks. Commerce modules get bundled into JavaScript chunks and shipped to the browser client side, but if modules are not needed on a site they can be excluded to reduce the JavaScript chunk size and help increase the page load speed.

## namespaceExtensions

The **namespaceExtensions** property defines the supported namespaces used for module registration. By default, the only supported namespace is the **@msdyn365-commerce-modules** namespace which contains all of the module library and core set of modules. The module package name is defined in following format: **\<namespace\>\/\<module_name\>**. If modules are published with a new namespace, the namespace can be added to the settings.

## enableChunkByModulePackage

The **enableChunkByModulePackage** property is used to enable module webpack JavaScript to be chunked in an ordered way. By default, modules from the same module package will be bundled together into the same webpack JavaScript chunk. By setting this property to **true**, the **chunkingGroupPreference** property setting can then be used to specify groups of modules to be packed together in a chunk. The default value is **false**.

When the Commerce e-commerce runtime loads a page, all JavaScript chunks containing the required modules for the page will be sent to the client. The JavaScript sent to a client browser for a page can be reduced by grouping together modules that interact with each other within a page. This grouping can reduce the page load time.

## chunkingGroupPreference

The **chunkingGroupPreference** property is used to specify sets of modules that will be grouped together into a webpack chunk when the **enableChunkByModulePackage** property is set to **true**. The default chunking logic is to group modules from the same package into the same chunk. In the case where the same module name exists in different namespaces, the module namespace can be used to specify the module name (for example, **[\<namespace\>\/<module_name1\>, \<module_name2\>]**). The namespace used for local modules is **\_\_local\_\_**. 
    
For example, if module1 and module2 will always be used at the same time on the same page, module1 and module2 can be added to one chunk group to avoid being split between two different chunks. In this example module1 and module2 will be sent to a browser client in a single JavaScript chunk, instead of potentially multiple JavaScript chunks containing other unused modules.  

> [!NOTE]
> Depending on the **minClientChunkSize** setting, other modules may be automatically merged into a defined chunking group.

## Additional resources

[Request properties object](request-properties-object.md)

[App settings](app-settings.md)

[Extend a module definition file](extend-module-definition.md)

[Cookie API overview](cookie-api-overview.md)

[Interactive components overview](interactive-components.md)

[Mock the signed-in state during local development](mock-sign-in.md)

[Globalize modules by using the CultureInfoFormatter class](globalize-modules.md)

[Set up Azure Key Vault for secure key management](set-up-key-vault.md)

