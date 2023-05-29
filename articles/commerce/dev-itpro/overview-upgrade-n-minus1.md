---
title: Upgrade and N-1 support for Commerce
description: Upgrade support and N-1 support have been enabled in the release of Dynamics 365 Commerce.
author: josaw1
ms.date: 01/12/2023
ms.topic: overview
ms.prod: 
ms.technology: 
audience: IT Pro
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2017-07-31
ms.dyn365.ops.version: Retail July 2017 update
ms.collection: get-started
---

# Upgrade and N-1 support for Commerce

[!include [banner](../../includes/banner.md)]

> [!WARNING]
> Support for Microsoft Dynamics AX 2012 R3 is ending. Although upgrade and migration are still supported, make a note of the dates that are relevant to this end of support. For more information, see [End of mainstream support for Microsoft Dynamics AX 2012 R3](../../fin-ops-core/fin-ops/get-started/mainstream-support-ax-2009-2012.md).

Upgrade and N-1 support have been enabled in the July 2017 release of Microsoft Dynamics 365 Retail. N-1 support lets customers who have stores that run Microsoft Dynamics AX 2012 R3 Cumulative Update 10 (CU10) work with Headquarters after an upgrade. The main purpose of upgrade and N-1 support is to let AX 2012 R3 customers take advantage of the benefits of the cloud.

The following features let customers upgrade in a seamless manner:

- Users can now perform database upgrade from AX 2012 R3 to Headquarters through the upgrade process.
- Users can operate their stores by using the components of AX 2012 R3 CU10.
- Pre-upgrade and post-upgrade checklist validations are built into the upgrade process.
- The upgrade process has enhanced error handling and messaging, so that customers can quickly debug issues.
- Users can use tools to bring forward custom X++ code in their existing Headquarters to the upgraded version of the headquarters.

The upgrade procedure is largely the same as the procedure for upgrading Retail to the latest version. For details about upgrade in general, see [Upgrade overview: AX 2012 to Dynamics 365 Retail](../../fin-ops-core/dev-itpro/migration-upgrade/upgrade-overview-2012.md).

Planned downtime is required. Upgrade analysis is done first. The upgrade analysis runs against the Microsoft Dynamics AX 2012 database and is based on the Microsoft Dynamics Lifecycle Services Diagnostic service. This step identifies tasks that can help make upgrade faster and less expensive. It also identifies the required SQL configuration, data headquarters cleanup, and deprecated features.
  
The actual data upgrade process then occurs. The AX 2012 database is moved to Microsoft Azure SQL Database, and then the data upgrade package is run as usual, through the runbook process. Upgrade validation is then done. A validation tool is run against the upgraded environment before it's used. This tool does an automated smoke test to verify that the service is running and accessible, row counts match, financials and inventory reconcile, and so on.

Most of the post-upgrade configuration for channels requires few manual steps. Customers can then use the pre-upgrade and post-upgrade checklists to learn about the tasks that must be completed. The post-upgrade tasks include initiating a full sync to the stores from the upgraded database, validating channels, registers, and devices against the upgraded database, validating transaction synchronization, and validating that N-1 support is in place.

For N-1 support, the customer must install the N-1 package in Commerce headquarters. No setup is required in the stores. This installation must be done during the upgrade window, after the N-1-related configuration has been completed.

After the Commerce headquarters upgrade and N-1 setup are completed, the N-1 store components can communicate with Commerce headquarters. No channel-side components must be installed for N-1 support. However, to enable the N-1 store to communicate with Commerce headquarters, cashiers must change their password the first time that they sign in.

For instructions for N-1 installation, see [Phased Rollout (N-1) installation, configuration, and cutover guide](n-1-installation-configuration.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
