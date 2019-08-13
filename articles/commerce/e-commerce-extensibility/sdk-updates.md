---
# required metadata

title: SDK and core library updates
description: Regular updates will be released as part of the Dynamics 365 Commerce e-Commerce SDK, which may include new features and/or product fixes.  Product release notes will be provided with all changes.  
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
# SDK and core library updates
Regular updates will be released as part of the Dynamics 365 Commerce online SDK, which may include new features and/or product fixes.  Product release notes will be provided with all changes.  

## Pulling SDK updates
SDK updates are optional and can be pulled down to a local development environment using the **yarn** command in the SDK source code, which will cause the latest dependencies to be pulled down.  Dependencies are backwards compatible and can be pulled down at any time.

## Creating a configuration package
When creating a configuration package using the **yarn msdyn265 pack** CLI tool, all dependencies will be updated to their local versions during the pack process.  The package created can then be uploaded via LCS to an online site.
