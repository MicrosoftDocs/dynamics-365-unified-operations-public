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
ROBOTS: NOINDEX, NOFOLLOW
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

# Database Movement operations

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/private-preview-banner.md)]

This topic describes the operations that are available as part of the Database Movement features in Lifecycle Services (LCS).  

## Sandbox refresh
When refreshing a production environment to a sandbox environment, or a sandbox environment to another sandbox environment, there are certain elements of the database that are not copied over to the target environment.  These elements include:
* Email addresses in the LogisticsElectronicAddress table.
* Batch job history in the BatchJobHistory, BatchHistory, and BatchConstraintHistory tables.
* SMTP password in the SysEmailSMTPPassword table.
* SMTP Relay server in the SysEmailParameters table.
* Print Management settings in the PrintMgmtSettings and PrintMgmtDocInstance tables.
* Environment-specific records in the SysServerConfig, SysServerSessions, SysCorpNetPrinters, SysClientSessions, BatchServerConfig, and BatchServerGroup tables.
* Document attachments in the DocuValue table.
* All users except for the administrator are disabled.
* All batch jobs are set to Withhold status.

## Import
When importing a database backup in to a sandbox environment, there are certain activities which must be performed.  These include:
* Ensure email capabilities are properly reconfigured or disabled, per your requirements.
* AOS servers are added back to required batch groups.
* System Help and Task guides are reconnected.
* Batch jobs are set to Waiting status.
* Users are re-enabled.

## Export
When exporting a database backup from an environment, there are certain elements of the database that are not exported in the backup file.  These elements include:
* Email addresses in the LogisticsElectronicAddress table.
* Batch job history in the BatchJobHistory, BatchHistory, and BatchConstraintHistory tables.
* SMTP password in the SysEmailSMTPPassword table.
* SMTP Relay server in the SysEmailParameters table.
* Print Management settings in the PrintMgmtSettings and PrintMgmtDocInstance tables.
* Environment-specific records in the SysServerConfig, SysServerSessions, SysCorpNetPrinters, SysClientSessions, BatchServerConfig, and BatchServerGroup tables.
* Document attachments in the DocuValue table.
* All users except for the administrator are disabled.
* All batch jobs are set to Withhold status.
