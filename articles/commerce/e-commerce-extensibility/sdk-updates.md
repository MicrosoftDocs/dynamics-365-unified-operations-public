---
# required metadata

title: SDK and core library updates
description: This topic covers regular updates that will be released as part of the Dynamics 365 Commerce online software development kit (SDK).
author: samjarawan
manager: annbe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-retail
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application user
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
# SDK and core library updates

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic covers regular updates that will be released as part of the Dynamics 365 Commerce online software development kit (SDK).

## Overview

Regular updates will be released as part of the Dynamics 365 Commerce online SDK, which may include new features or product fixes.  Product release notes will be provided with all changes.  

## Pull SDK updates
SDK updates are optional and can be pulled down to a local development environment using the **yarn** command in the SDK source code, which will cause the latest dependencies to be pulled down. Dependencies are backwards compatible and can be pulled down at any time.

When creating a configuration package using the **yarn msdyn265 pack** command line interface (CLI) tool, all dependencies will be updated to their local versions during the pack process. The package created can then be uploaded to an online site using Lifecycle Services (LCS).
