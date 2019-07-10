---
# required metadata

title: Export a database
description: This topic explains how to export a database for Microsoft Dynamics 365 for Finance and Operations.
author: LaneSwenka
manager: AnnBe
ms.date: 07/08/2019
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

You can use Microsoft Dynamics Lifecycle Services (LCS) to export a database for Microsoft Dynamics 365 for Finance and Operations from a sandbox user acceptance testing (UAT) environment to the Asset library.

## Self-service export database

[!include [dbmovement-export](../includes/dbmovement-export.md)]

### Export operation failure

If the export operation isn't successful, you can do a *rollback*. If you select the **Rollback** option after the initial failure of the operation, your source sandbox environment is restored to the state that it was in before the export began.

To determine the root cause of the failure, download the runbook logs by using the available buttons before you start the rollback operation.

### Data elements that aren't exported

When you export a database backup from an environment, some elements of the database aren't exported in the backup file. Here are some examples:

* Email addresses in the LogisticsElectronicAddress table
* Batch job history in the BatchJobHistory, BatchHistory, and BatchConstraintHistory tables
* SMTP password in the SysEmailSMTPPassword table
* SMTP Relay server in the SysEmailParameters table
* Print Management settings in the PrintMgmtSettings and PrintMgmtDocInstance tables
* Environment-specific records in the SysServerConfig, SysServerSessions, SysCorpNetPrinters, SysClientSessions, BatchServerConfig, and BatchServerGroup tables
* Document attachments in the DocuValue table

Additionally, all users except the admin are disabled, and all batch jobs are set to a status of **Withhold**.

## Known issues

### Export ran for some time and then reached a "Preparation failed" state

The export process can time out on Azure SQL Database when large databases are involved. In some cases, the export process can be recovered by using the **Resume** action from LCS. The Lifecycle Services team is working to identify known error codes, so these can be added to the logs for the export database operation to help guide users toward a resolution. These known error codes will be added in a future release of LCS. If you encounter an issue, you can export manually by exporting the [legacy documentation](https://github.com/MicrosoftDocs/dynamics-365-unified-operations-public/blob/8bf1db9f2d994fc585caf380af85bb0a50eaf02b/articles/dev-itpro/database/copy-database-from-azure-sql-to-sql-server.md).

### Export doesn't show any progress in LCS

The export process differs from other database movement operations and the general package deployment in that it doesn't use a runbook. Therefore, the progress indicator in LCS doesn't show any output, as it would typically show in other scenarios. The Lifecycle Services team is working to improve this behavior in a future release of LCS. If you encounter an issue, you can export manually by exporting the [legacy documentation](https://github.com/MicrosoftDocs/dynamics-365-unified-operations-public/blob/8bf1db9f2d994fc585caf380af85bb0a50eaf02b/articles/dev-itpro/database/copy-database-from-azure-sql-to-sql-server.md).
