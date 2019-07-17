---
# required metadata

title: Debug modules
description: There are various options available to aid in debugging modules during development in Dynamics 365 for Commerce.
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
There are various options available to aid in debugging your modules during development. Dynamics 365 for Commerce e-Commerce functionality leverages React and Node which support client-side debugging. Standard React and Node debugging patterns can be used but are not covered in this topic.

## Debug query string paramater
The `&debug=true` query parameter can be added to your query string as you test your modules on a local developer environment. Using this parameter will provide extended trace output in the Command Prompt window running Yarn.

## Browser debugging
Standard browser debugging tools can be leveraged during the development of modules. Reference the documentation for the specific browser for further details.
