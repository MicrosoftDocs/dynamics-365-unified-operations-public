---
# required metadata

title: Create a new module
description: This topic will cover the steps needed to create a new module.  The Dynamics 365 e-Commerce SDK provides a CLI command `yarn msdyn365 add-module MODULE_NAME`, where `MODULE_NAME` is the name to provide your module.
author: SamJarawan
manager: JeffBl
ms.date: 08/30/2019
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: SamJar
ms.search.validFrom: 2019-08-30
ms.dyn365.ops.version: 

---
# Create a new module

This topic will cover the steps needed to create a new module.  The Dynamics 365 e-Commerce SDK provides a CLI command `yarn msdyn365 add-module MODULE_NAME`, where `MODULE_NAME` is the name to provide your module.

Below is an example to create a module called `productFeature`:
```
yarn msdyn365 add-module productFeature
```

Creating the module could take 20-30 seconds as it pulls down all the dependencies.  When complete you will find the new module in the `\src\modules\` directory.

## Previewing a Module
To view the module rendering locally in a browser:
1. Start the app from a command prompt, navigate to your root SDK folder and run `yarn start`
    Example:
    ```
    c:\repos\MyEcommerceSite\yarn start
    ```
1. Launch the following url in a browser to see the module render in a development environment.  Notice the module name in the query string parameter "type=MODULE_NAME":
    * http://localhost:4000/modules?type=productFeature

![Module Preview](media/create-new-module.png)

## Module Naming conventions
You should camelCase module names using whole words where possible.
