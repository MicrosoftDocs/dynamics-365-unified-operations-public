---
# required metadata

title: Overview of upgrade and N-1 support for Dynamics 365 for Retail 
description: Upgrade and N-1 support have been enabled in the July release of Dynamics 365 for Retail. N-1 support enables customers to have stores that are running AX 2012 R3 CU10 to be able to work with a Dynamics 365 for Retail headquarters after an upgrade. 
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

Upgrade and N-1 support have been enabled in the July release of Dynamics 365 for Retail. N-1 support enables customers to have stores that are running AX 2012 R3 CU10 to be able to work with a Dynamics 365 for Retail headquarters after an upgrade. 

The key goal of upgrade and N-1 is to enable Dynamics AX 2012 R3 customers to leverage the benefits of the cloud by moving to Dynamics 365 for Retail. These features enable customers to upgrade in a seamless way. 
- Customers can now perform database upgrade from AX 2012 R3 to Dynamics 365 for Retail headquarters through the upgrade process 
- Customers can operate their stores with the components of AX 2012 R3 CU10 version 
- Pre and post upgrade checklist validations are built-in to the upgrade process
- The upgrade process has enhanced error handling and messaging for debugging failures quickly
- Customer canuse tools to bring forward custom code in X++ for Retail headquarters.

The upgrade procedure is largely the same as upgrading Dynamics 365 for Retail to the latest version. For details about upgrade in general, see [Upgrade overview: AX 2012 to Dynamics 365 for Finance and Operations](dynamics635/operations/dev-itpro/migration-upgrade/upgrade-ax-2012).

Planned downtime is required. The key difference is in the data upgrade step, first the upgrade analysis is done. The upgrade analysis runs against the AX 2012 database and is based on the LCS Diagnostic Service. This step identifies tasks to help make upgrade faster and cheaper. It also identified the required SQL configuration, data cleanup, and deprecated features.
  
The actual data upgrade process then happens, to move the AX 2012 database to SQL Azure and then execute data upgrade package as normal through the run book process. After this the upgrade validation is done. A validation tool is run against upgraded environment before using it. This tool performs an automated smoke test to check things like whether service is running and accessible, row counts match, financial and inventory reconcile etc.
 
Most of the post upgrade configuration for retail channels requires few manual steps. Customers can then use the pre and post upgrade checklists to learn about the tasks that must be completed. 

Some of the post upgrade tasks include validating channels, registers and devices against the upgraded database, validating transaction sync, and validating that N-1 support is in place.
 
For N-1 support, the customer will have to install the N-1 package in the Retail headquarters; there is no setup required in the stores. This must be done during the upgrade window, after the N-1 related configurations have been completed. After the Retail headquarters upgrade and N-1 setup is complete, the N-1 store components can communicate with the Dynamics 365 for Retail headquarters. There are no channel-side components that need to be installed for N-1 support. The system will require a cashier password change during the first login for the N-1 store to communicate with  Dynamics 365 for Retail headquarters.  
 
Instructions for N-1 installation are in the topic [Installing N-1 components for use with Microsoft Dynamics 365 for Retail](n-1-installation-configuration.md).
