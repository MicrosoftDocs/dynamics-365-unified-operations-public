---
# required metadata

title: Debugging modules
description: There are various options available to aid in debugging your modules during development.  Dynamics 365 e-Commerce leverages React and Node which supports client side debugging. 
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
# Debugging modules
There are various options available to aid in debugging your modules during development.  Dynamics 365 e-Commerce leverages React and Node which supports client side debugging.  Standard React / Node debugging patterns can be used but are not covered here.

## Debug query string paramater
The `&debug=true` query parameter can be added to your query string as you test out your modules on a local developer environment.  This will provided extended trace output in the Command Prompt window running Yarn.

## Browser debugging
Standard browser debugging tools can be leveraged during development of modules.  See browser documentation for further details.
