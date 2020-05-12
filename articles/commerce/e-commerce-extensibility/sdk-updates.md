---
# required metadata

title: SDK and core library updates
description: This topic covers regular updates that will be released as part of the Microsoft Dynamics 365 Commerce online software development kit (SDK).
author: samjarawan
manager: annbe
ms.date: 10/24/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
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
# SDK and core library updates

[!include [banner](../includes/banner.md)]

This topic covers regular updates that will be released as part of the Microsoft Dynamics 365 Commerce online software development kit (SDK).

## Overview

Regular updates will be released as part of the Dynamics 365 Commerce online SDK. These updates might include new features or product fixes. Product release notes will be provided for all changes.

## Pull SDK updates

SDK updates are optional and can be pulled down to a local development environment by using the **yarn** command in the SDK source code. This command causes the latest dependencies to be pulled down. Dependencies are backward-compatible and can be pulled down at any time.

When a configuration package is created by using the **yarn msdyn365 pack** command-line interface (CLI) tool, all dependencies are updated to their local versions during the packaging process. The package that is created can then be uploaded to an online site by using Microsoft Dynamics Lifecycle Services (LCS).

## Additional resources

[Package configurations and deploy them to an online environment](package-deploy.md)
