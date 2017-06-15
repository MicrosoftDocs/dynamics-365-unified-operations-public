---
# required metadata

title: Overview of upgrade and N-1 support for Dynamics 365 for Retail 
description: Upgrade support and N-1 support have been enabled in the release of Dynamics 365 for Retail. N-1 support lets customers who have stores that run AX 2012 R3 CU10 work with Dynamics 365 for Retail headquarters after an upgrade. 
author: athinesh99
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
# ms.reviewer: margoc
ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 44351
ms.search.region: Global
# ms.search.industry: 
ms.author: athinesh
ms.search.validFrom: 2017-07-31
ms.dyn365.ops.version: Retail July 2017 update

---

# Overview of upgrade and N-1 support for Dynamics 365 for Retail

Upgrade and N-1 support have been enabled in the July release of Microsoft Dynamics 365 for Retail. N-1 support lets customers who have stores that run Microsoft Dynamics AX 2012 R3 Cumulative Update 10 (CU10) work with Microsoft Dynamics 365 for Retail headquarters after an upgrade. The main purpose of upgrade and N-1 support is to let AX 2012 R3 customers take advantage of the benefits of the cloud by moving to Retail.

The following features let customers upgrade in a seamless manner:

- Customers can now perform database upgrade from AX 2012 R3 to Retail headquarters through the upgrade process.
- Customers can operate their stores by using the components of AX 2012 R3 CU10.
- Pre-upgrade and post-upgrade checklist validations are built into the upgrade process.
- The upgrade process has enhanced error handling and messaging, so that customers can quickly debug issues.
- Customers can use tools to bring forward custom X++ code in their existing Retail headquarters to the upgraded version of the headquarters.

The upgrade procedure is largely the same as the procedure for upgrading Retail to the latest version. For details about upgrade in general, see [Upgrade overview: AX 2012 to Dynamics 365 for Finance and Operations](dynamics635/operations/dev-itpro/migration-upgrade/upgrade-overview-2012).

Planned downtime is required. Upgrade analysis is done first. The upgrade analysis runs against the Microsoft Dynamics AX 2012 database and is based on the Microsoft Dynamics Lifecycle Services (LCS) Diagnostic service. This step identifies tasks that can help make upgrade faster and less expensive. It also identifies the required SQL configuration, data head quarterscleanup, and deprecated features.
  
The actual data upgrade process then occurs. The AX 2012 database is moved to Microsoft Azure SQL Database, and then the data upgrade package is run as usual, through the runbook process. Upgrade validation is then done. A validation tool is run against the upgraded environment before it's used. This tool does an automated smoke test to verify that the service is running and accessible, row counts match, financials and inventory reconcile, and so on.
 
Most of the post-upgrade configuration for retail channels requires few manual steps. Customers can then use the pre-upgrade and post-upgrade checklists to learn about the tasks that must be completed. The post-upgrade tasks include validating channels, registers, and devices against the upgraded database, validating transaction synchronization, and validating that N-1 support is in place.
 
For N-1 support, the customer must install the N-1 package in Retail headquarters. No setup is required in the stores. This installation must be done during the upgrade window, after the N-1-related configuration has been completed.

After the Retail headquarters upgrade and N-1 setup are completed, the N-1 store components can communicate with Retail headquarters. No channel-side components must be installed for N-1 support. However, to enable the N-1 store to communicate with Retail headquarters, cashiers must change their password the first time that they sign in.
 
For instructions for N-1 installation, see [Installing N-1 components for use with Microsoft Dynamics 365 for Retail](n-1-installation-configuration.md).
