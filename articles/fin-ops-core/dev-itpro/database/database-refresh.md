---
# required metadata

title: Refresh database
description: This topic explains how to perform a refresh of a database for Microsoft Dynamics 365 Finance.
author: LaneSwenka
manager: AnnBe
ms.date: 02/02/2020
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
ms.custom: 257614
ms.assetid: 558598db-937e-4bfe-80c7-a861be021db1
ms.search.region: Global
# ms.search.industry:
ms.author: laneswenka
ms.search.validFrom: 2016-09-30
ms.dyn365.ops.version: AX 7.0.0

---

# Refresh database

[!include [banner](../includes/banner.md)]

You can use Microsoft Dynamics Lifecycle Services (LCS) to perform a refresh of the database to a sandbox user acceptance testing (UAT) environment. A database refresh lets you copy the transactional and financial reporting databases of your production environment into the target, sandbox UAT environment. If you have another sandbox environment, you can also copy the databases from that environment to your target, sandbox UAT environment.

> [!IMPORTANT]
> Copying production data to your sandbox environment for the purpose of production reporting is not supported.

## Self-service database refresh
With the goal of providing Data Application Lifecycle Management (also referred to as *DataALM*) capabilities to our customers without relying on human or manual processes, the Lifecycle Services team has introduced an automated **Refresh database** action. This process is outlined below:

1. Visit your target sandbox on the **Environment Details** page, and click the **Maintain** \> **Move database** menu option.
2. Select the **Refresh database** option and choose your source environment.
3. Note the warnings and review the list of data elements that are not copied from the source environment.
4. The refresh operation will begin immediately.

### Refresh operation failed
In case of failure, the option to perform a rollback is available.  By clicking the **Rollback** option after the operation has initially failed, your target sandbox environment will be restored to the state it was before the refresh began. This is made possible by the Azure SQL point-in-time restore capability to restore the database. This is often required if a customization, that is present in the target sandbox, cannot complete a database synchronization with the newly refreshed data.

To determine the root cause of the failure, use the available buttons to download the runbook logs before you start the rollback operation.  

### Data elements that aren't copied during refresh
When refreshing a production environment to a sandbox environment, or a sandbox environment to another sandbox environment, there are certain elements of the database that are not copied over to the target environment. These elements include:

* Email addresses in the LogisticsElectronicAddress table.
* Batch job history in the BatchJobHistory, BatchHistory, and BatchConstraintHistory tables.
* SMTP Relay server in the SysEmailParameters table.
* Print Management settings in the PrintMgmtSettings and PrintMgmtDocInstance tables.
* Environment-specific records in the SysServerConfig, SysServerSessions, SysCorpNetPrinters, SysClientSessions, BatchServerConfig, and BatchServerGroup tables.
* Document attachments in the DocuValue table. These attachments include any Microsoft Office templates that were overwritten in the source environment.
* All users except the admin will be set to **Disabled** status.
* All batch jobs are set to **Withhold** status.
* All users will have their partition value reset to the "initial" partition record ID.
* All Microsoft-encrypted fields will be cleared, because they can't be decrypted on a different database server. An example is the **Password** field in the SysEmailSMTPPassword table.

Some of these elements aren't copied because they are environment-specific. Examples include BatchServerConfig and SysCorpNetPrinters records. Other elements aren't copied because of the volume of support tickets. For example, duplicate emails might be sent because Simple Mail Transfer Protocol (SMTP) is still enabled in the UAT environment, invalid integration messages might be sent because batch jobs are still enabled, and users might be enabled before admins can perform post-refresh cleanup activities.

### Environment administrator
The System Administrator account in the target environment (UserId of 'Admin') is reset to the value found in the web.config file on the target.  This should be the same value as that of the Administrator from Lifecycle Services.  To preview which account this will be, visit your target sandbox **Environment Details** page in LCS.  The value of the **Environment Administrator** field that was selected when the environment was first deployed is updated to be the System Administrator in the transactional database. This also means that the tenant of the environment will be that of the Environment Administrator.

If you have used the Admin User Provisioning Tool on your environment to change the web.config file to a different value, it may not match what is in Lifecycle Services.  If you require a different account to be used, you will need to deallocate and delete the target sandbox, and redeploy selecting another account. After this, you can perform another refresh database action to restore the data.

An environment can't be refreshed from one tenant to another. This restriction applies even to .onmicrosoft.com tenants. You should make sure that the admin accounts in the source and target environments are from the same tenant domain.

### Conditions of a database refresh
Here is the list of requirements and conditions of operation for a database refresh:

- A refresh performs a delete operation on the original target database.
- The target environment will be available until the database copy has reached the target server. After that point, the environment will be offline until the refresh process is completed.
- The refresh will affect only the application and Financial Reporting databases.
- Documents in Azure blob storage are not copied from one environment to another. This means that attached document handling documents and templates won't be changed and will remain in their current state.
- All users except the Admin user and other internal service user accounts will be unavailable. This process allows the Admin user to delete or obfuscate data before allowing other users back into the system.
- The Admin user must make required configuration changes, such as reconnecting integration endpoints to specific services or URLs.
- All data management framework with recurring import and export jobs must be fully processed and stopped in the target system prior to initiating the restore. In addition, we recommend that you select the database from the source after all recurring import and export jobs have been fully processed. This will ensure there are no orphaned files in Azure storage from either system. This is important because orphaned files cannot be processed after the database is restored in the target environment. After the restore, the integration jobs can be resumed.
- Any user with a role of Project owner or Environment manager in LCS will have access to the SQL and machine credentials for all non-production environments.
- The databases must be hosted in the same Azure geographic region.
- The allocated database capacity of the source environment must be less than the maximum database capacity of the target environment.

## Steps to complete after a database refresh for environments that use Commerce functionality
[!include [environment-reprovision](../includes/environment-reprovision.md)]

## Known issues

### Refresh is denied for environments that run Platform update 20 or earlier
The database refresh process can't currently be completed if the environment is running Platform update 20 or earlier. For more information, see the [list of currently supported platform updates](../migration-upgrade/versions-update-policy.md).

### Incompatible version of Financial Reporting between source and target environments
The database refresh process (self-service or via a service request) can't be completed successfully if the version of Financial Reporting in the target environment is earlier than the version in the source environment. To resolve this issue, update both environments so that they have the latest version of Financial Reporting.

To determine the version you have installed in your source and target environments, visit the **View detailed version information** link on the **Environment Details** page.

Search for **MRApplicationService** and ensure that the target environment is greater than or equal to the source environment.

<img src="media/FinancialReporting_Binaries2.png" width="500px" alt="MRApplicationService">

For customers that are using version 8.1 or later:
1. Go to the **Update** tiles for your UAT environment. Save the updates to your Project asset library.
2. Apply this package to your UAT environment.
3. Verify that the error has been resolved.

For customers that are using version 8.0 or earlier:
1. Review the Environment history of your source environment. Specifically, look for any "Platform and application binary package" that might have been deployed to the source environment and not the target environment.
2. Apply this binary package to your target environment.
3. Verify that the error has been resolved.

### Incompatible application versions between source and target environments
The database refresh process (self-service or via service request) cannot be completed if the Application release of your source and target environment are not the same. This is because the data upgrade process is not executed by database movement operations such as refresh, and data loss can occur.

If upgrading your sandbox UAT environment to a newer Application version (for example, 7.3 to 8.1), be sure to perform the database refresh action prior to starting the upgrade. After your sandbox is upgraded to the newer version, you cannot restore an older production environment database in to the sandbox UAT environment.

Conversely, if your production environment is newer than your target sandbox, you will need to either upgrade the target sandbox prior to the refresh or simply deallocate, delete, and redeploy prior to performing the refresh.
