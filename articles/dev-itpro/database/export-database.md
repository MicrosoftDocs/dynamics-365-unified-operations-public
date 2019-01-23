---
# required metadata

title: Database Movement Operations - Export Database Quickstart
description: This topic explains how to perform an export of a database for Microsoft Dynamics 365 for Finance and Operations.
author: LaneSwenka
manager: AnnBe
ms.date: 1/22/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro, Developer
# ms.devlang: 
ms.reviewer: margoc
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.search.region: Global
# ms.search.industry: 
ms.author: laneswenka
ms.search.validFrom: 2019-01-22
ms.dyn365.ops.version: AX 7.0.0

---

# Export database quickstart

[!include [banner](../includes/banner.md)]

You can use Microsoft Dynamics Lifecycle Services (LCS) to perform the export of a database for Microsoft Dynamics 365 for Finance and Operations sandbox user acceptance testing (UAT) environment to the Asset Library. 

## Self-service export database
[!include [dbmovement-export](../includes/dbmovement-export.md)]

### Export operation failed
In case of failure, the option to perform a **Rollback** is available.  By clicking the rollback option after the operation has initially failed, your source sandbox environment will be restored to the state it was before the export began.  

To determine the root cause of the failure, download the runbook logs using the available buttons before starting the rollback operation.

### Data elements that are not exported
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

## Known issues

### Export ran for some time and then reached 'Preparation failed' state
The export process can potentially timeout on Azure SQL when large databases are involved.  In some cases this can be recovered by using the **Resume** action from LCS.  The Lifecycle Services team is working to identify Known Error Codes to add to the logs for Export database operation that can help guide towards a resolution.  This will be added in a future release of LCS.

### Export doesn't show any progress in Lifecycle Services
The export process is different than the other database movement operations as well as general package deployment in that it doesn't use a Runbook.  Because of this the progress indicator in LCS shows no output like you would normally see in other scenarios.  The Lifecycle Services team is looking to improve this in a future release of LCS.
