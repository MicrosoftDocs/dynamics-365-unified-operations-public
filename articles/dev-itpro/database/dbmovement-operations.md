---
# required metadata

title: Database Movement operations
description: This topic describes the operations available as part of the Database Movement features in Lifecycle Services. 
author: laneswenka
manager: AnnBe
ms.date: 10/09/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: 
ms.author: laswenka
ms.search.validFrom: 2018-10-31
ms.dyn365.ops.version: 8.1

---

# Database Movement Operations

[!include [banner](../includes/banner.md)]

>[!Note]This document describes functionality that may not have been released yet.  Projected >functionality may change or may not ship (see Microsoft policy).

This topic describes the operations available as part of the Database Movement features in Lifecycle Services.  

## Sandbox Refresh
When refreshing a Production Environment to a Sandbox Environment, or a Sandbox Environment to another Sandbox Environment, there are certain elements of the database that are not copied over to the target environment.  These elements include:
* Email addresses in the LogisticsElectronicAddress table
* Batch Job History in the BatchJobHistory, BatchHistory, and BatchConstraintHistory Tables
* SMTP Password in the SysEmailSMTPPassword table
* SMTP Relay Server in the SysEmailParameters table
* Print Management Settings in the PrintMgmtSettings, and PrintMgmtDocInstance tables
* Environment-specific records in the SysServerConfig, SysServerSessions, SysCorpNetPrinters, SysClientSessions, BatchServerConfig, BatchServerGroup tables
* Document attachments in the DocuValue table
* All users except for the Admin are disabled
* All Batch Jobs are set to Withhold status

## Import
When importing a database backup in to a Sandbox environment, there are certain activities which must be performed.  These include:
* Ensure Email capabilities are properly reconfigured or disabled, per your requirements
* AOS servers are added back to required batch groups
* System Help and Task Guides are reconnected
* Batch jobs are set to Waiting status
* Users are re-enabled

## Export
When exporting a database backup from an environment, there are certain elements of the database that are not exported in the backup file.  These elements include:
* Email addresses in the LogisticsElectronicAddress table
* Batch Job History in the BatchJobHistory, BatchHistory, and BatchConstraintHistory Tables
* SMTP Password in the SysEmailSMTPPassword table
* SMTP Relay Server in the SysEmailParameters table
* Print Management Settings in the PrintMgmtSettings, and PrintMgmtDocInstance tables
* Environment-specific records in the SysServerConfig, SysServerSessions, SysCorpNetPrinters, SysClientSessions, BatchServerConfig, BatchServerGroup tables
* Document attachments in the DocuValue table
* All users except for the Admin are disabled
* All Batch Jobs are set to Withhold status
