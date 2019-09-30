---
# required metadata

title: Export a database
description: This topic explains how to export a database for Finance and Operations.
author: LaneSwenka
manager: AnnBe
ms.date: 08/15/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro, Developer
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.search.region: Global
# ms.search.industry: 
ms.author: laneswenka
ms.search.validFrom: 2019-01-31
ms.dyn365.ops.version: 8.1.3

---

# Export a database

[!include [banner](../includes/banner.md)]

You can use Microsoft Dynamics Lifecycle Services (LCS) to export a database from a sandbox user acceptance testing (UAT) environment to the Asset library.

## Self-service export database

[!include [dbmovement-export](../includes/dbmovement-export.md)]

### Export operation failure

Export fails most often when the process in LCS times out awaiting a response from Azure SQL.  You can use the **Resume** button to reconnect LCS to the ongoing export process to see it through to completion.  If more than 24 hours is passed since you began the export, the pending asset in the LCS Project Asset Library has expired and your export must be rolled back and started over.

To cancel an export operation which has failed, you may use the *Rollback* button.

### Data elements that aren't exported

When you export a database backup from an environment, some elements of the database aren't exported in the backup file. Here are some examples:

* Email addresses in the LogisticsElectronicAddress table.
* Batch job history in the BatchJobHistory, BatchHistory, and BatchConstraintHistory tables.
* SMTP password in the SysEmailSMTPPassword table.
* SMTP Relay server in the SysEmailParameters table.
* Print Management settings in the PrintMgmtSettings and PrintMgmtDocInstance tables.
* Environment-specific records in the SysServerConfig, SysServerSessions, SysCorpNetPrinters, SysClientSessions, BatchServerConfig, and BatchServerGroup tables.
* **Document attachments** in the DocuValue table. This includes any Office Templates that were overriden in the source environment.
* Connection string in the PersonnellIntegrationConfiguration table
* All users except the admin will be set to **Disabled** status.
* All batch jobs are set to **Withhold** status.

### Known issues

#### Export ran for some time and then reached a "Preparation failed" state

The export process can time out on Azure SQL Database when large databases are involved. In some cases, the export process can be recovered by using the **Resume** action from LCS. The Lifecycle Services team is working to identify known error codes, so these can be added to the logs for the export database operation to help guide users toward a resolution. These known error codes will be added in a future release of LCS. If you encounter an issue, you can manually export by following the “Manual export” section below.

#### Export doesn't show any progress in LCS

The export process differs from other database movement operations and the general package deployment doesn't use a runbook. Therefore, the progress indicator in LCS doesn't show any output, as it would typically show in other scenarios. The LCS team is working to identify known error codes, so these can be added to the logs for the export database operation to help guide users toward a resolution. These known error codes will be added in a future release of LCS.