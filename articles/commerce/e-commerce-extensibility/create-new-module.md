---
# required metadata

title: Create a new module
description: This topic describes how to create a new module in Dynamics 365 Commerce.
author: samjarawan
manager: annbe
ms.date: 09/15/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: samjar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---
# Create a new module

[!include [banner](../includes/banner.md)]

This topic describes how to create a new module in Dynamics 365 Commerce.

## Overview

To create a new module in Commerce, the online Software Development Kit (SDK) provides the **add-module** command-line interface (CLI) command. When you run the command as in the following example, you replace **MODULE\_NAME** with the name that you want to give to the new module. 

**yarn msdyn365 add-module MODULE\_NAME**

## Example

The following example shows how to create a module that is named **product-feature**.

```Console
yarn msdyn365 add-module product-feature
```

It can take 20 to 30 seconds to create a module and generate all the template files for it. After the command has finished running, you can find the new module in the \\src\\modules\\ directory.

## Preview a module

To preview the new module in a local web browser, follow these steps.

1. At a command prompt, go to your root SDK folder, and run the **yarn start** command. Here is an example.

    ```Console
    c:\repos\Msdyn365.Commerce.Online\yarn start
    ```

2. In a web browser, open the following URL to view the module: `https://localhost:4000/modules?type=product-feature`. Notice the module name in the **type=MODULE\_NAME** query string parameter.

![Module preview](media/create-new-module.png)

## Module naming conventions

Module names are case-insensitive. We recommended that you use whole words for module names whenever you can.

## Deferred module rendering
By default all modules are rendered server side, however deferred loading of some modules may be needed to improve page load performance. See the client side rendering section inside the [page load actions](page-load-data-action) for more information.

Any references to the window or document objects which are available only in the context of a browser should be handled appropriately during server side rendering. This will avoid unexpected rendering behavior such as page flicker and DOM mismatch issues. The below SDK utility function can be used for this purpose:

```
import MsDyn365 from '@msdyn365-commerce/core';

if (MsDyn365.isBrowser) {
    return new URL(window.location.href);
}
```

## Module Error handling 
If a module encounters an error while sever side rendering the failed module will get wrapped into an **ErrorModule** component to prevent any module level render error from breaking the page. For example, a module using document/window objects during a server side render would fail since these objects are non-existent on server side and in that case, the module is wrapped in an error component. The module would then attempt to render again on client. In development mode, to see if a module failed on server side, you can provide a ?debug=true query string parameter.


## Additional resources
[CLI command reference](cli-command-reference.md)

[Clone a module library module](clone-starter-module.md)

[Add module configuration fields](add-module-config-fields.md)

[Preview and debug a module](test-module.md)

[Test modules by using module mocks](test-module-mock.md)

[Test modules by using page mocks](test-page-mock.md)

[Container modules](container-modules.md)

[Create a layout container module](create-layout-container.md)

[Create a page container module](create-page-containers.md)

[Localize a module](localize-module.md)
