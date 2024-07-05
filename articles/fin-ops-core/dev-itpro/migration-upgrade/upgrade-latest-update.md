---
title: Process for moving to the latest update of finance and operations
description: Learn about the process for moving to the latest update of finance and operations, including definitions and an overview on paths to one version.
author: laneswenka
ms.author: laswenka
ms.topic: article
ms.date: 11/01/2021
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2016-05-31
ms.search.form: 
ms.dyn365.ops.version: Platform update 1
ms.assetid: e48d7424-371a-49ee-882c-07b7ceb00183
---

# Process for moving to the latest update of finance and operations

[!include [banner](../includes/banner.md)]

This article explains the process of updating or upgrading to the latest release of finance and operations. It describes the overall process and supported scenarios, but it doesn't provide detailed instructions for every step of the process.

For information about the contents of each release of finance and operations, see [What's new or changed in finance and operations home page](../../fin-ops/get-started/whats-new-changed.md).

For information about One Version service updates, see the [One Version service updates overview](../lifecycle-services/oneversion-overview.md).

> [!Note]
> For those looking to upgrade to finance and operations from Microsoft Dynamics AX 2012, please see [Upgrade from AX 2012 to finance and operations](upgrade-overview-2012.md).

## Definitions

- **Upgrade** – The process of moving from one official release of finance and operations to the next release, for source environments prior to version 8.0. Some examples are the move from 7.1 to 7.3, or from 7.3 to 10.0.1. The process involves setup of a free sandbox environment, code upgrade, and data upgrade.
- **Update** – The process of applying a binary package to an environment to move it from one official release of finance and operations to the next release, for source environments starting with version 8.0. This process has lower downtime requirements and doesn't involve data upgrade. For more information, see the [Rebuild and update](upgrade-latest-update.md#rebuild-and-update) section later in this article.

## Paths to One Version
<img src="../migration-upgrade/media/OneVersion_Paths.png" width="600px" alt="Paths to One Version" />
There are three primary paths to get to the latest version of finance and operations.  Each path is referenced below with a link to detailed steps.

### Self-service upgrade
*Applicable starting version: Microsoft Dynamics 365 Finance and Operations 7.0 (RTW), 7.1 (1611), 7.2 (July 2017), 7.3.*<br/>
*Scope: Complex*<br/>
This path involves code refactoring to Extensions, and Data Upgrade in a DevTest, Sandbox, and eventually a Production environment. 

> [!NOTE]
> This process is now deprecated.

[Self-service upgrade to the latest version](../migration-upgrade/self-service-upgrade.md).

### Rebuild and update
*Applicable starting version: Microsoft Dynamics 365 Finance and Operations 8.0*<br/>
*Scope: Moderate*<br/>
This path involves removing Microsoft X++ hotfixes and creating a merged update package.

[Update environments from version 8.0 to 10.0.X](../migration-upgrade/appupdate-80-81.md).

### Automatic update
*Applicable starting version: Finance and Operations 8.1.0+*<br/>
*Scope: Simple*<br/>
This path involves configuring your project for continuous updates.

[Configure service updates through Lifecycle Services (LCS)](../lifecycle-services/configure-service-updates.md).



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

