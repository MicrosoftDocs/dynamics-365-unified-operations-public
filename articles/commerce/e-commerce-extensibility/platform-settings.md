---
title: Platform settings file
description: This article covers various properties that can be configured in the Microsoft Dynamics 365 Commerce platform settings file.
author: samjarawan
ms.date: 07/02/2024
ms.topic: how-to
audience: Developer
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: samjar
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template 
---

# Platform settings file

[!include [banner](../includes/banner.md)]

This article covers various properties that can be configured in the Microsoft Dynamics 365 Commerce platform settings file.

The **platform.settings.json** file under the **\\src\\settings\\** directory holds various platform property settings that are used by the Commerce e-commerce runtime. This file might not exist by default. If it doesn't exist, you can add it under the **\\src\\settings\\** directory. The following example of a **platform.settings.json** file shows various supported property settings.

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

The **serverSideDataActionTimeoutInMs** property defines the maximum amount of time, in milliseconds, that the server side data actions wait for a response before they time out. The timeout value represents a lower bound for page response because the action framework waits as long as the defined timeout value before it times out and returns the page. The default value is 4000 milliseconds (4 seconds). If this value is set too high, it could potentially overload the Commerce Scale Unit (CSU).

### clientSideDataActionTimeoutInMs

The **clientSideDataActionTimeoutInMs** property defines the maximum amount of time, in milliseconds, that the client side data actions wait for a response before they time out. The timeout value represents a lower bound for page response because the action framework waits as long as the defined timeout value before it times out and returns the page. The default value is 4000 milliseconds (4 seconds). If this value is set too high, it could potentially overload the CSU.

### minClientChunkSize

The **minClientChunkSize** property defines the minimum size, in bytes, of webpack JavaScript chunks that are sent to the browser. JavaScript chunks that are smaller than the minimum size are grouped together to form chunks that are larger than the minimum size. The smaller the minimum size is, the more chunks are generated. In this case, more code splitting occurs, and less unused JavaScript code is included. However, many smaller chunks must be downloaded. By contrast, the larger the minimum size is, the fewer overall chunks are generated. In this case, fewer JavaScript files must be downloaded, but some unused JavaScript code might be included. The default value is 30,000 bytes (30 KB).

### excludedModules

The **excludedModules** property defines a set of modules that are excluded from webpack JavaScript chunks. Commerce modules are bundled into JavaScript chunks and sent to the browser on the client side. However, if modules aren't required on a site, they can be excluded to help reduce the size of JavaScript chunks and help increase the speed of page loads.

### namespaceExtensions

The **namespaceExtensions** property defines the supported namespaces that are used for module registration. By default, the only supported namespace is **@msdyn365-commerce-modules**. This namespace contains all the module library modules and the core set of modules. The module package name is defined in the following format: **\<namespace\>\/\<module_name\>**. If modules are published that use a new namespace, the namespace can be added to the settings.

### secretsManagerOUN

The **secretsManagerOUN** property specifies the operating unit number to use when retrieving secret values using the secret manager class. This operating unit number should match that of the store that was used in Commerce headquarters to configure key vault parameters for Retail Server. For more information, see [Set up Azure Key Vault for secure key management](set-up-key-vault.md).

## JavaScript bundling options

The Dynamics 365 Commerce framework generates JavaScript bundles by using a webpack-optimized configuration. Although the default configuration offers better "tree shaking" (removal of unused or dead code) and JavaScript chunking, the generation logic can be tuned further to help improve bundle generation. For better control of JavaScript bundling, the framework offers the following options. 

### enableModuleEntryPoints

The Commerce framework supports generating JavaScript bundles per module and loading only the bundles that are needed on a page. The **enableModuleEntryPoints** platform setting enables the generation of JavaScript bundles per module.

Less JavaScript means better page performance and less unused JavaScript on a site page. However, this bundling can cause an increase in the number of JavaScript requests, depending on the number of modules that are used on the page. Therefore, we recommend that you carefully analyze the results in your development environment before you enable this platform setting in production.

To generate JavaScript bundles per module, add the following platform setting in the **platform.settings.json** file.

`"enableModuleEntryPoints": true`

### build

For complex applications that have more modules and/or more customization, the **build** platform setting can cause the webpack to use more memory. In these cases, the default node heap memory size isn't sufficient and can cause heap "out of memory" errors. To increase the heap memory, update the build target in the **package.json** file by setting **NODE_OPTIONS** to increase the heap memory limit, as shown in the following example.

`"build": "SET NODE_OPTIONS=--max_old_space_size=4096 && ..."`

### maxClientChunkSize

Smaller JavaScript bundles put less pressure on the main thread by causing the browser to process and run the script faster. Therefore, there's a direct correlation between the size of bundles and the total blocking time performance. The **maxClientChunkSize** platform setting helps control the bundle size by splitting the larger JavaScript bundles into multiple parts, as shown in the following example.  

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
