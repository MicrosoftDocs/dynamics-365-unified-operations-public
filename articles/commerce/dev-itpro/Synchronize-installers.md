---
# required metadata

title: Synchronize self-service installers in Dynamics 365 Commerce
description: This topic explains how to use Asset and Shared asset libraries in Microsoft Dynamics Lifecycle Services (LCS), and Dynamics 365 Headquarters, to upload and synchronize self-service installers so that they can be used with the standard self-service download mechanism.
author: jashanno
manager: AnnBe
ms.date: 04/15/2020
ms.topic: article
ms.prod: 
ms.service: Dynamics-365-retail
ms.technology:  

# optional metadata

ms.search.form: SysAADClientTable, RetailTransactionServiceProfile
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations, Retail, Core
# ms.tgt_pltfrm: 
ms.custom: 44351
ms.search.region: Global
# ms.search.industry: 
ms.author: jashanno
ms.search.validFrom: 2020-04-30
ms.dyn365.ops.version: 10.0.10

---

# Synchronize self-service installers in Dynamics 365 Commerce

[!include [banner](../../includes/banner.md)]

This topic explains how to use the Asset library and Shared asset library in Microsoft Dynamics Lifecycle Services (LCS), and Dynamics 365 Headquarters, to upload and synchronize self-service installers so that they can be used with the standard self-service download mechanism.

> [!IMPORTANT]
> The earlier method of uploading self-service packages is currently still supported. However, it's obsolete and will be removed in the future.

## Key terms

| Term | Description |
|---|---|
| Shared asset library | In LCS, two types of asset libraries are available: the Shared asset library and the project-level Asset library. For more information about these libraries, see [Asset library in Lifecycle Services (LCS)](../../fin-ops-core/dev-itpro/lifecycle-services/asset-library.md). |
| Asset library | For more information, see [Asset library in Lifecycle Services (LCS)](../../fin-ops-core/dev-itpro/lifecycle-services/asset-library.md). |
| Self-service installers | Self-service installers are the Dynamics 365 Commerce components. For more information about the installers, see the links at the end of this topic. |

## Overview

The **Retail Self-service package** subsection in the Shared asset library stores all monthly releases for self-service installers. These installers include Modern POS (which includes the offline version), Commerce Scale Unit (which was formerly known as Retail Store Scale Unit \[RSSU\]), and hardware station. You can also upload customized installers into both this library and the project-level Asset library. By using these locations, you can then synchronize the available installers in Dynamics 365 Headquarters. After synchronization is completed, all the installers that are available between these two libraries (and whatever previously existed in the environment) will be accessible for the standard self-service download processes that are described in detail in separate topics (see the links in the table of terms earlier in this topic).

The following illustration shows a generic example of the **Retail Self-service package** subsection in the Shared asset library (or Asset library).

![Retail Self-service package subsection in the Shared asset library](media/SharedAssets.jpg)

## Synchronize installers in Dynamics 365 Headquarters

1. Go to **Retail and Commerce** &gt; **Headquarters setup** &gt; **Parameters** &gt; **Commerce parameters**.
2. On the **Channel deployment** tab, select **Check for package updates** to perform synchronization. The installers that are available for download (through standard self-service processes) are synchronized and updated, depending on which of the installers that are currently available in LCS apply to environment.

    > [!IMPORTANT]
    > Previously, the RetailSelfService table was used as the source that all installer information was pulled from. Information was entered in this table, based on the installers that had been uploaded into headquarters through the earlier package application method. The new self-service population methodology combines all values in the RetailSelfService table (the earlier self-service package upload method) with all available installers in the LCS Shared asset library. The self-service drop-down package selectors will show the options from this newly synchronized, combined source.
    >
    > As was stated at the beginning of this topic, the earlier self-service package upload method is obsolete, but it will continue to be supported until it's removed in the future.

4. On the same page, you can select default packages that will be used throughout headquarters in their relevant locations (**Devices**, **All stores**, and **Channel database**).
5. Perform standard configuration and installation flows for Modern POS, hardware station, or Commerce Scale Unit by using the links in the following table.

    | Component | Link |
    |---|---|
    | Modern POS | [Configure, install, and activate Modern POS (MPOS)](../retail-modern-pos-device-activation.md) |
    | Hardware station | [Configure and install Retail hardware station](../retail-hardware-station-configuration-installation.md) |
    | Commerce Scale Unit (formerly known as Retail Store Scale Unit) | [Configure and install Commerce Scale Unit](retail-store-scale-unit-configuration-installation.md) |
