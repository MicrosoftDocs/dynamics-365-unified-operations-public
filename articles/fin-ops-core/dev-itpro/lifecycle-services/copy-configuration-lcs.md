---
title: Copy configurations by using Configuration manager
description: You can use the Configuration manager (beta) to copy a configuration from one instance of Microsoft Dynamics AX 2012 R3 to another.
author: johnmichalak
ms.author: johnmichalak
ms.topic: how-to
ms.date: 11/11/2025
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 
ms.dyn365.ops.version: 2012
ms.assetid: 54283db7-6f1a-46e8-b74d-c67d54e6e5fb
---

# Copy configurations by using Configuration manager

[!include [banner](../includes/banner.md)]
[!include [LCS deprecation](../includes/lcs-deprecation.md)]

Before you begin, set up Configuration manager (beta). For more information, see [Set up Configuration manager](set-up-configuration-manager-lcs.md).

> [!IMPORTANT]
> This feature isn't supported for production use. Configuration manager (beta) relies on entities from the Data Import Export Framework in your environment. Because these entities don't currently include all the functionality in AX 2012 R3, some configuration data isn't copied between environments.


## Export a configuration
You can create a stored configuration by exporting it from a specified legal entity and entities.
1.  In the **Configurations to export** list, select the plus sign (+).
1.  Enter a name for the configuration, then select **Start**.
1.  Select a storage location, then select **Continue**. You can store your configuration locally, in the cloud, or in both locations.
1.  Select an environment to connect to, then select **Continue**.
1.  Review the legal entities that are available in the partitions in your environment. Select the legal entities to work with, then select **Continue**.
1.  Select the entities to copy to a stored configuration.
1.  Optional: Tables that contain configuration data but aren't in entities can't be copied to a stored configuration. To see these tables, select the **Missing tables** tab.
1.  Select **Continue** to create your stored configuration. After a configuration is created, you can review what it contains.

## Import a configuration
1.  In the **Configurations to import** list, select an existing configuration.
1.  Use the default name, or enter a new name. If the configuration is stored both locally and in the cloud, select the location to import the stored configuration from. Select **Continue**.
1.  Select the environment to import the configuration to, then select **Continue**.
1.  Review the companies that are available in the partitions in your environment. Select the companies to work with by selecting the location of the company that you're importing from (for example, initialDAT), then select **Continue**.
1.  Select the entities to copy to a stored configuration.
1.  Select **Continue** to import your stored configuration. After you create a configuration, you can review what it contains.




[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
