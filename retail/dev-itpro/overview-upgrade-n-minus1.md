 
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

# Overview of upgrade and support for previous versions in (N-1 support) Dynamics 365 for Operations or Retail

Upgrade support and support for previous versions are now enabled in Microsoft Dynamics 365 for Retail and Dynamics 365 for Operations.  The main purpose of upgrade and support for previous versions is to let AX 2012 R3 customers take advantage of the benefits of the cloud by moving to the new Dynamics 365. Support for previous versions aka N-1 support, is the capability for enabling the Stores running 2012 R3 CU version, to be able to work against a Dynamics 365 for Operations or Retail head quarters, after the upgrade. We are initially supporting 2012 R3 CU10 for N-1 capability. The following are some capabilities that enable existing customers to move to Dynamics 365 in a seamless manner:

- Users can now perform database upgrade from AX 2012 R3 to Retail headquarters through the upgrade process.
- Users can operate their stores by using the components of AX 2012 R3 CU10.
- Pre-upgrade and post-upgrade checklist validations are built into the upgrade process.
- The upgrade process has enhanced error handling and messaging, so that customers can quickly debug issues.
- Users can use tools to bring forward custom X++ code in their existing Retail headquarters to the upgraded version of the headquarters.

The upgrade procedure is largely the same as the procedure for upgrading Retail to the latest version. For details about upgrade in general, see [Upgrade overview: AX 2012 to Dynamics 365 for Finance and Operations](dynamics635/operations/dev-itpro/migration-upgrade/upgrade-overview-2012).

As part of the upgrade process, a planned downtime is required. While beginning an upgrade, the upgrade analysis is done first. The upgrade analysis runs against the Microsoft Dynamics AX 2012 database and is based on the Microsoft Dynamics Lifecycle Services (LCS) Diagnostic service. This step identifies tasks that can help make upgrade faster and less expensive. It also identifies the required SQL configuration, data cleanup, and deprecated features.The actual data upgrade process then occurs. The AX 2012 database is moved to Microsoft Azure SQL Database, and then the data upgrade package is run as usual, through the runbook process. Upgrade validation is then done. A validation tool is run against the upgraded environment before it's used. This tool does an automated smoke test to verify that the service is running and accessible, row counts match, financials and inventory reconcile, and so on. Most of the post-upgrade configuration for retail channels requires few manual steps. Customers can then use the pre-upgrade and post-upgrade checklists to learn about the tasks that must be completed. The post-upgrade tasks include intiating a full sync to the stores from the upgraded database, validating channels, registers, and devices against the upgraded database, validating transaction synchronization, and validating that N-1 support is in place.
 
The Connector for Microsoft Dynamics AX enables the N-1 support, where existing Dynamics AX 2012 R3 CU 10 customers will be able to leverage the benefits of cloud in their business using Dynamics 365 for Retail or Operations, in a hybrid model where the stores maintain the current Dynamics AX 2012 R3 installations. For N-1 support, the customer must install the "Connector for Microsoft Dynamics AX package" in Retail headquarters. No setup is required in the stores. This installation must be done during the upgrade window, after the N-1-related configuration has been completed. After the Retail headquarters upgrade and N-1 setup are completed, the N-1 store components can communicate with Retail headquarters. No channel-side components must be installed for N-1 support. However, to enable the N-1 store to communicate with Retail headquarters, cashiers must change their password the first time that they sign in.
 
For instructions for N-1 installation, see [Installing N-1 components for use with Microsoft Dynamics 365 for Retail](n-1-installation-configuration.md).
