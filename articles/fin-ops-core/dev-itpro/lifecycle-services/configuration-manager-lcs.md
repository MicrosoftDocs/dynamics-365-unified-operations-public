---
# required metadata

title: Configuration in Lifecycle Services overview
description: The Configuration manager (beta) functionality in Microsoft Dynamics Lifecycle Services lets you copy a configuration from one instance of Microsoft Dynamics AX 2012 R3 to another. 
author: RobinARH
manager: AnnBe
ms.date: 07/23/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: AX 2012, Operations
# ms.tgt_pltfrm: 
ms.custom: 62753
ms.assetid: fab3f6cf-03db-47c7-90fb-f8bc03dacf49
ms.search.region: Global
# ms.search.industry: 
ms.author: jorisde
ms.search.validFrom: 
ms.dyn365.ops.version: 2012

---

# Configuration in Lifecycle Services overview

[!include [banner](../includes/banner.md)]

You can use the Configuration manager to copy from and to Dynamics AX 2012 R3 environments that meet the following criteria:
-   Managed as part of a Lifecycle Services project
-   Running System diagnostics
-   Running the Data Import/Export Framework

> [!IMPORTANT]
> This feature is **not** supported for production use. Configuration manager (beta) relies on entities from the Data Import/Export Framework in your environment. Because these entities do not currently include all the functionality in AX 2012 R3, some configuration data is not copied between environments.

For more information, see:
-   [Set up Configuration manager](set-up-configuration-manager-lcs.md)
-   [Copy configurations by using Configuration manager](copy-configuration-lcs.md)





