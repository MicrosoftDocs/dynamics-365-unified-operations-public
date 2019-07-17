---
# required metadata

title: Modify a Starter Kit module
description: The Dynamics 365 for Commerce e-Commerce SDK includes a set of starter kit modules for use on an e-Commerce site.
author: SamJarawan
manager: annbe
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
# Modify a Starter Kit module

The Dynamics 365 for Commerce e-Commerce SDK includes a set of starter kit modules for use on an e-Commerce site. These modules can't be modified, but they can be cloned into a new module and then changed.

To clone a module and change it, use the CLI command `yarn msdyn365 clone SDK_MODULE_NAME NEW_MODULE_NAME`, where `SDK_MODULE_NAME` is the name of the module to modify and `NEW_MODULE_NAME` is the name of the new module. This will add the modules source code to the `/src/modules/` directory and pull in any required dependencies for the module.

Below is an example to modify the **hero** SDK module:
```
yarn msdyn365 clone hero heroV2
```

Modifying the module could take a minute or two, as it pulls down all the dependencies. When complete, you can find the new module in the `\src\modules\` directory.

## Previewing a module
To view the module rendered locally in a browser:

1. Start the app from a command prompt, navigate to your root SDK folder, and run `yarn start`:
    ```
    c:\repos\MyEcommerceSite\yarn start
    ```
1. Launch the following pages in a browser. Notice the module name in the query string parameter "type=MODULE_NAME":
    * https://localhost:4000/modules?type=heroV2

You can now modify the module code as required.
