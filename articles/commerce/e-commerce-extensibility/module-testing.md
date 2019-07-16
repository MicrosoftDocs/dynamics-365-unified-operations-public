---
# required metadata

title: Testing a module
description: During development of a module, the module can be previewed and debugged in your local web browser.
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
# Testing a module
During development of a module, the module can be previewed and debugged in your local web browser.

To view the module rendering locally in a browser:
1. Start the app from a command prompt, navigate to your root SDK folder and run `yarn start`:
    ```
    c:\repos\MyEcommerceSite\yarn start
    ```
1. Launch the following pages in a browser.  Notice the module name in the query string parameter `type=MODULE_NAME`:
    * https://localhost:4000/modules?type=productFeature
    
* Adding &debug=true will provide more verbose debug information in the yarn output window.
    * https://localhost:4000/modules?type=productFeature&debug=true
