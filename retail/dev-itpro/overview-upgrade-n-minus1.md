---
# required metadata

title: Overview of upgrade and N-1 support for Dynamics 365 for Retail 
description: By customizing the properties of sales orders, you can send additional data from your online store to meet the requirements of your business processes. This article explains how to add properties to a sales order.
author: kfend
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
# ms.reviewer: robinr
ms.search.scope: AX 7.0.0, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 44351
ms.assetid: dd9b86cb-630a-4429-9aea-8ba4c4723baa
ms.search.region: Global
# ms.search.industry: 
ms.author: meeram
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

Overview of the Upgrade and N-1 Support

Upgrade and N-1 support has been enabled in the July release of Dynamics 365 for Retail. N-1 support enables customers to have stores that are running AX 2012 R3 CU10 to be able to work with a Dynamics 365 for Retail headquarters after an upgrade. 

The key goal of upgrade and N-1 is to enable Dynamics AX 2012 R3 customers to leverage the benefits of the cloud by moving to Dynamics 365 for Retail. These features enable customers to upgrade in a seamless way. 
- Customers can now perform database upgrade from AX 2012 R3 to Dynamics 365 for Retail headquarters through the upgrade process 
- Customers can operate their stores with the components of AX 2012 R3 CU10 version 
- Pre and post upgrade checklist validations are built-in to the upgrade process
- The upgrade process has enhanced error handling and messaging for debugging failures quickly
- Customer canuse tools to bring forward custom code in X++ for Retail headquarters.

The upgrade procedure is largely the same as upgrading Dynamics 365 for Retail to the latest version. Planned downtime is required. The key difference is in the data upgrade step, first the upgrade analysis is done. The upgrade analysis runs against the AX 2012 database and is based on the LCS Diagnostic Service. This step identifies tasks to help make upgrade faster and cheaper. It also identified the required SQL configuration, data cleanup, and deprecated features.
  
The actual data upgrade process then happens, to move the AX 2012 database to SQL Azure and then execute data upgrade package as normal through the run book process. After this the upgrade validation is done. A validation tool is run against upgraded environment before using it. This tool performs an automated smoke test to check things like whether service is running and accessible, row counts match, financial and inventory reconcile etc.
 
Most of the post upgrade configuration for retail channels require few manual steps. The customers can then use the pre and post upgrade task check lists to learn about the required tasks to be completed. 

Some of the post upgrade tasks include validating channels, registers and devices against the upgraded database, validating transaction sync, and validating that N-1 support is in place.
 
For N-1 support, the customer will have to install the N-1 package in the Retail headquarters; there is no setup required in the stores. This must be done during the upgrade window, after the N-1 related configurations have been completed. After the Retail headquarters upgrade and N-1 setup is complete, the N-1 store components can communicate with the Dynamics 365 for Retail headquarters. There are no channel-side components that need to be installed for N-1 support. The system will require a cashier password change during the first login for the N-1 store to communicate with  Dynamics 365 for Retail headquarters.  
 
The instructions for the N-1 setup can be found here: 
