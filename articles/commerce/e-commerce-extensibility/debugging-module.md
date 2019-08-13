---
# required metadata

title: Debug modules
description: Various options are available to help you debug your modules during development.
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
# Debug modules

Various options are available to help you debug your modules during development. The e-Commerce functionality in Microsoft Dynamics 365 Commerce uses React and Node, which support client-side debugging. Although you can also use standard React and Node debugging patterns, they aren't covered in this topic.

## Debug query string parameter

When you test your modules in a local developer environment, you can add the **&debug=true** query parameter to the query string. This parameter provides extended trace output in the **Command Prompt** window that is running Yarn.

## Browser debugging

During the development of modules, you can take advantage of the standard debugging tools that are available in your web browser. For more information, see the documentation for your web browser.
