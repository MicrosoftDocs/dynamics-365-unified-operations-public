---
# required metadata

title: Clone a starter kit module
description: This topic describes how to clone a starter kit module.
author: samjarawan
manager: annbe
ms.date: 02/07/2020
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
# Clone a starter kit module

[!include [banner](../includes/banner.md)]

This topic describes how to clone a starter kit module.

## Overview

The Microsoft Dynamics 365 Commerce online software development kit (SDK) includes a set of starter kit modules that can be used on an e-Commerce site. Although these modules can't be modified directly, they can be cloned into new modules and then updated. 

You can also create module extension views. In this way, you can provide alternative layout views without having to clone a module. We recommend that you avoid cloning if you can, because clones will be copies of starter kit modules and won't receive any automatic service updates that the starter kit modules get. For more information, see [Theming overview](theming.md). 

## Clone and update a module

To clone a module and then update it, use the **clone** command-line interface (CLI) command. When you run the below command, you replace **SDK\_MODULE\_NAME** with the name of the module that you want to modify and **NEW\_MODULE\_NAME** with the name of the new module.

**yarn msdyn365 clone SDK\_MODULE\_NAME NEW\_MODULE\_NAME**

This command adds the source code for the module to the /src/modules/ directory and pulls in any required dependencies for the module.

## Example

The following example shows how to clone the hero SDK module so that you can update it.

```
yarn msdyn365 clone content-block super-content-block
```

It can take up to a minute to clone a module. After the command has finished running, you can find the new module in the \\src\\modules\\ directory.

> [!NOTE]
> Module dependencies aren't automatically pulled down when you clone a module. Before you build the module, you must run Yarn and fix any missing dependencies.

## Preview a module

To preview the new module in a local web browser, follow these steps.

1. At a command prompt, go to your root SDK folder, and run the **yarn start** command. Here is an example.

    ```
    c:\repos\Msdyn365.Commerce.Online\yarn start
    ```

2. In a web browser, open the following URL to view the module: `https://localhost:4000/modules?type=super-content-block`. Notice the module name in the **type=MODULE\_NAME** query string parameter.

You can now update the module code as needed.

## Additional resources

[Create a new module](create-new-module.md)

[Add module configuration fields](add-module-config-fields.md)

[Preview and debug a module](test-module.md)

[Test modules by using module mocks](test-module-mock.md)

[Test modules by using page mocks](test-page-mock.md)

[Container modules](container-modules.md)

[Create a layout container module](create-layout-container.md)

[Create a page container module](create-page-containers.md)

[Localize a module](localize-module.md)
