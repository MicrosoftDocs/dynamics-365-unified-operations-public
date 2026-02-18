---
title: Upgrade and N-1 support for Commerce
description: This article provides an overview of upgrade support and N-1 support enabled in Microsoft Dynamics 365 Commerce.
author: josaw1
ms.date: 02/18/2026
ms.topic: overview
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2017-07-31
ms.collection: get-started
ms.custom: 
  - bap-template
---

# Upgrade and N-1 support for Commerce

[!include [banner](../../includes/banner.md)]

> [!WARNING]
> - Support for Microsoft Dynamics AX 2012 R3 has ended. For more information, see [End of mainstream support for Microsoft Dynamics AX 2012 R3](../../fin-ops-core/fin-ops/get-started/mainstream-support-ax-2009-2012.md).
> - Upgrade and N-1 support for Dynamics 365 Commerce end with the Commerce version 10.0.40 release.

Upgrade and N-1 support are available starting with the July 2017 release of Microsoft Dynamics 365 Retail. N-1 support lets customers who have stores that run Microsoft Dynamics AX 2012 R3 Cumulative Update 10 (CU10) work with Commerce headquarters after an upgrade. The main purpose of upgrade and N-1 support is to let AX 2012 R3 customers take advantage of the benefits of the cloud.

The following features help customers upgrade seamlessly:

- Users can now perform database upgrade from AX 2012 R3 to headquarters through the upgrade process.
- Users can operate their stores by using the components of AX 2012 R3 CU10.
- Preupgrade and post-upgrade checklist validations are built into the upgrade process.
- The upgrade process enhances error handling and messaging, so that customers can quickly debug problems.
- Users can use tools to bring forward custom X++ code in their existing headquarters to the upgraded version of the headquarters.

The upgrade procedure is largely the same as the procedure for upgrading Retail to the latest version. For details about upgrade in general, see [Upgrade overview: AX 2012 to Dynamics 365 Retail](../../fin-ops-core/dev-itpro/migration-upgrade/upgrade-overview-2012.md).

Planned downtime is required. Upgrade analysis is done first. The upgrade analysis runs against the Microsoft Dynamics AX 2012 database and is based on the Microsoft Dynamics Lifecycle Services Diagnostic service. This step identifies tasks that can help make upgrade faster and less expensive. It also identifies the required SQL configuration, data headquarters cleanup, and deprecated features.
  
The actual data upgrade process then occurs. The AX 2012 database is moved to Microsoft Azure SQL Database, and then the data upgrade package is run as usual, through the runbook process. Upgrade validation is then done. A validation tool is run against the upgraded environment before it's used. This tool does an automated smoke test to verify that the service is running and accessible, row counts match, financials and inventory reconcile, and so on.

Most of the post-upgrade configuration for channels requires few manual steps. Customers can then use the preupgrade and postupgrade checklists to learn about the tasks that must be completed. The post-upgrade tasks include initiating a full sync to the stores from the upgraded database, validating channels, registers, and devices against the upgraded database, validating transaction synchronization, and validating that N-1 support is in place.

For N-1 support, the customer must install the N-1 package in Commerce headquarters. No setup is required in the stores. This installation must be done during the upgrade window, after the N-1-related configuration is complete.

After the Commerce headquarters upgrade and N-1 setup are completed, the N-1 store components can communicate with Commerce headquarters. No channel-side components must be installed for N-1 support. However, to enable the N-1 store to communicate with Commerce headquarters, cashiers must change their password the first time that they sign in.

For instructions for N-1 installation, see [Phased Rollout (N-1) installation, configuration, and cutover guide](n-1-installation-configuration.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
