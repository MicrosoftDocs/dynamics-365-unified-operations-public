---
title: Platform settings file
description: Learn about various properties you can configure in the Microsoft Dynamics 365 Commerce platform settings file.
author: samjarawan
ms.date: 02/05/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: samjar
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template 
---

# Platform settings file

[!include [banner](../includes/banner.md)]

This article describes the properties you can configure in the Microsoft Dynamics 365 Commerce platform settings file.

The Commerce e-commerce runtime uses the **platform.settings.json** file under the **\\src\\settings\\** directory to hold various platform property settings. This file might not exist by default. If it doesn't exist, you can add it under the **\\src\\settings\\** directory. The following example of a **platform.settings.json** file shows various supported property settings.

```json
{
    "serverSideDataActionTimeoutInMs": 4000,
    "clientSideDataActionTimeoutInMs": 4000,
    "minClientChunkSize": 30000,
    "excludeModules": [ ],
    "namespaceExtensions" : [ ],
    "secretsManagerOUN" : 128
}
```

## Properties

### serverSideDataActionTimeoutInMs

The **serverSideDataActionTimeoutInMs** property sets the maximum amount of time, in milliseconds, that the server side data actions wait for a response before they time out. The timeout value represents a lower bound for page response because the action framework waits as long as the defined timeout value before it times out and returns the page. The default value is 4,000 milliseconds (4 seconds). If you set this value too high, it can overload the Commerce Scale Unit (CSU).

### clientSideDataActionTimeoutInMs

The **clientSideDataActionTimeoutInMs** property sets the maximum amount of time, in milliseconds, that the client side data actions wait for a response before they time out. The timeout value represents a lower bound for page response because the action framework waits as long as the defined timeout value before it times out and returns the page. The default value is 4,000 milliseconds (4 seconds). If you set this value too high, it can overload the CSU.

### minClientChunkSize

The **minClientChunkSize** property sets the minimum size, in bytes, of webpack JavaScript chunks that you send to the browser. JavaScript chunks that are smaller than the minimum size are grouped together to form chunks that are larger than the minimum size. The smaller the minimum size is, the more chunks are generated. In this case, more code splitting occurs, and less unused JavaScript code is included. However, you must download many smaller chunks. By contrast, the larger the minimum size is, the fewer overall chunks are generated. In this case, you must download fewer JavaScript files, but some unused JavaScript code might be included. The default value is 30,000 bytes (30 KB).

### excludedModules

The **excludedModules** property sets a set of modules that are excluded from webpack JavaScript chunks. The client side bundles Commerce modules into JavaScript chunks and sends them to the browser. However, if you don't require modules on a site, exclude them to help reduce the size of JavaScript chunks and help increase the speed of page loads.

### namespaceExtensions

The **namespaceExtensions** property defines the supported namespaces that the framework uses for module registration. By default, the only supported namespace is **@msdyn365-commerce-modules**. This namespace contains all the module library modules and the core set of modules. The module package name follows this format: **\<namespace\>\/\<module_name\>**. If you publish modules that use a new namespace, add that namespace to the settings.

### secretsManagerOUN

The **secretsManagerOUN** property specifies the operating unit number to use when retrieving secret values by using the secret manager class. This operating unit number should match the store that you used in Commerce headquarters to configure key vault parameters for Retail Server. For more information, see [Set up Azure Key Vault for secure key management](set-up-key-vault.md).

## JavaScript bundling options

The Dynamics 365 Commerce framework generates JavaScript bundles by using a webpack-optimized configuration. Although the default configuration offers better "tree shaking" (removal of unused or dead code) and JavaScript chunking, you can tune the generation logic further to help improve bundle generation. For better control of JavaScript bundling, the framework offers the following options. 

### enableModuleEntryPoints

The Commerce framework supports generating JavaScript bundles per module and loading only the bundles that a page needs. The **enableModuleEntryPoints** platform setting enables the generation of JavaScript bundles per module.

Less JavaScript means better page performance and less unused JavaScript on a site page. However, this bundling can cause an increase in the number of JavaScript requests, depending on the number of modules that the page uses. Therefore, carefully analyze the results in your development environment before you enable this platform setting in production.

To generate JavaScript bundles per module, add the following platform setting in the **platform.settings.json** file.

`"enableModuleEntryPoints": true`

### build

For complex applications that have more modules or more customization, the **build** platform setting can cause webpack to use more memory. In these cases, the default node heap memory size isn't sufficient and can cause heap "out of memory" errors. To increase the heap memory, update the build target in the **package.json** file by setting **NODE_OPTIONS** to increase the heap memory limit, as shown in the following example.

`"build": "SET NODE_OPTIONS=--max_old_space_size=4096 && ..."`

### maxClientChunkSize

Smaller JavaScript bundles put less pressure on the main thread because the browser processes and runs the script faster. Therefore, there's a direct correlation between the size of bundles and the total blocking time performance. The **maxClientChunkSize** platform setting helps you control the bundle size by splitting larger JavaScript bundles into multiple parts, as shown in the following example.  

`"maxClientChunkSize": 500000 // 500KB unzipped size`

### secondaryInstrumentationKey

This setting specifies the instrumentation key from your Azure Application Insights subscription that's used to connect and log telemetry events to your own Application Insights subscription, as shown in the following example.

`"secondaryInstrumentationKey": "00000000-0000-0000-0000-000000000000" // Instrumentation Key GUID from your Azure Application Insights subscription`

For more information, see [Telemetry logger](telemetry-logger.md).

## Additional resources

[Request properties object](request-properties-object.md)

[App settings](app-settings.md)

[Extend a module definition file](extend-module-definition.md)

[Cookie API overview](cookie-api-overview.md)

[Interactive components overview](interactive-components.md)

[Mock the signed-in state during local development](mock-sign-in.md)

[Globalize modules by using the CultureInfoFormatter class](globalize-modules.md)

[Set up Azure Key Vault for secure key management](set-up-key-vault.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
