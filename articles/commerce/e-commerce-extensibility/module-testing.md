---
# required metadata

title: Testing a module
description: During development of a module, the module can be previewed and debugged in your local web browser.
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
# Testing a module
During development of a module, the module can be previewed and debugged in your local web browser.

To preview the new module in a local web browser, follow these steps.

1. At a command prompt, go to your root SDK folder, and run the **yarn start** command. Here is an example.

    ```
    c:\repos\MyEcommerceSite\yarn start
    ```

2. Open the following URL in a web browser to view the module: `https://localhost:4000/modules?type=productFeature`. Notice the module name in the **"type=MODULE\_NAME"** query string parameter.
    
* Adding &debug=true will provide more verbose debug information in the yarn output window.
    * https://localhost:4000/modules?type=productFeature&debug=true
