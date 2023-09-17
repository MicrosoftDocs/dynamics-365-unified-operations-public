---
title: Configuration in Lifecycle Services overview
description: The Configuration manager (beta) functionality lets you copy a configuration from one instance of Microsoft Dynamics AX 2012 R3 to another.
author: gianugo
ms.date: 07/23/2019
ms.topic: overview
ms.prod: 
ms.technology: 
audience: Developer, IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: gianura
ms.search.validFrom: 
ms.dyn365.ops.version: 2012
ms.collection: get-started
ms.assetid: fab3f6cf-03db-47c7-90fb-f8bc03dacf49
---

# Configuration in Lifecycle Services overview

[!include [banner](../includes/banner.md)]
[!include [LCS deprecation](../includes/lcs-deprecation.md)]

You can use the Configuration manager to copy from and to Dynamics AX 2012 R3 environments that meet the following criteria:
-   Managed as part of a Lifecycle Services project
-   Running System diagnostics
-   Running the Data Import/Export Framework

> [!IMPORTANT]
> This feature is **not** supported for production use. Configuration manager (beta) relies on entities from the Data Import/Export Framework in your environment. Because these entities do not currently include all the functionality in AX 2012 R3, some configuration data is not copied between environments.

For more information, see:
-   [Set up Configuration manager](set-up-configuration-manager-lcs.md)
-   [Copy configurations by using Configuration manager](copy-configuration-lcs.md)







[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
