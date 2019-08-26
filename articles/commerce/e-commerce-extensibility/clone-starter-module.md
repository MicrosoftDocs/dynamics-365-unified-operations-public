---
# required metadata

title: Clone a starter kit module
description: This topic describes how to clone a starter kit module.
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
# Clone a starter kit module

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic describes how to clone a starter kit module.

## Overview

The Dynamics 365 Commerce Online SDK includes a set of starter kit modules that can be used on an e-Commerce site. Although these modules can't be modified directly, they can be cloned into new modules and then changed.

## Clone a module and change it

To clone a module and change it, use the **yarn msdyn365 clone SDK\_MODULE\_NAME NEW\_MODULE\_NAME** command-line interface (CLI) command. In this command, **SDK\_MODULE\_NAME** is the name of the module that you want to modify, and **NEW\_MODULE\_NAME** is the name of the new module. This command adds the source code for the module to the /src/modules/ directory and pulls in any required dependencies for the module.

## Example

The following example shows the command that is used to clone the hero SDK module so that you can change it.

```
yarn msdyn365 clone hero heroExtended
```

It can take one to two minutes to clone the module. After the command has finished running, you can find the new module in the \\src\\modules\\ directory.

[!NOTE]
Cloning a module does not pull down the module dependencies automatically. You will need to run Yarn and fix any missing dependencies before building the module.

## Preview a module

To preview the new module in a local web browser, do the following.

1. At a command prompt, go to your root SDK folder and run the **yarn start** command. Here is an example:

    ```
    c:\repos\MyEcommerceSite\yarn start
    ```

1. Open the following URL in a web browser: `https://localhost:4000/modules?type=heroV2`. Notice the module name in the **"type=MODULE\_NAME"** query string parameter.

You can now change the module code as needed.
