---
# required metadata

title: Create a new module
description: This topic explains how to create a new module.
author: samjarawan
manager: annbe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-retail
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

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic explains how to create a new module.

## Overview

The Dynamics 365 Commerce Online software development kit (SDK) provides a **yarn msdyn365 add-module MODULE\_NAME** command-line interface (CLI) command. When you run this command, you replace **MODULE\_NAME** with the name that you want to give to the new module. 

## Example

The following example shows how to create a module that is named **productFeature**.

```
yarn msdyn365 add-module productFeature
```

Creation of a module might take 20 to 30 seconds to generate all of the new module template files. After the command has finished running, you can find the new module in the \\src\\modules\\ directory.

## Preview a module

To preview the new module in a local web browser, do the following.

1. At a command prompt, go to your root SDK folder, and run the **yarn start** command. Here is an example.

    ```
    c:\repos\MyEcommerceSite\yarn start
    ```

2. Open the following URL in a web browser to view the module: `https://localhost:4000/modules?type=productFeature`. Note the module name in the **"type=MODULE\_NAME"** query string parameter.

![Module preview](media/create-new-module.png)

## Module naming conventions

You should use camel case (camelCase) for module names. You should also use whole words whenever you can.
