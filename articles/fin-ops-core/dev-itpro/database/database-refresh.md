---
title: Refresh database
description: Learn how to perform a refresh of a database for Microsoft Dynamics 365 Finance, including an overview of known issues.
author: LaneSwenka
ms.author: laswenka
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 04/03/2026
ms.reviewer: johnmichalak
audience: IT Pro, Developer
ms.assetid: 558598db-937e-4bfe-80c7-a861be021db1
ms.search.region: Global
ms.search.validFrom: 2016-09-30
ms.search.form:
ms.dyn365.ops.version: AX 7.0.0
---

# Refresh database

[!include [banner](../includes/banner.md)]

Use Microsoft Dynamics Lifecycle Services to refresh the database in a sandbox user acceptance testing (UAT) environment. A database refresh copies the transactional and financial reporting databases from your production environment to the target sandbox UAT environment. If you have another sandbox environment, you can also copy the databases from that environment to your target sandbox UAT environment.

> [!IMPORTANT]
> Copying production data during business hours or peak hours can affect the production system. Schedule the refresh database operation during off-peak hours and limit the operation to one refresh at a time.
>
> Copying production data to your sandbox environment for the purpose of production reporting isn't supported.

## Self-service database refresh

To provide Data Application Lifecycle Management (also referred to as *DataALM*) capabilities without relying on human or manual processes, the Lifecycle Services team introduced an automated **Refresh database** action. The following process outlines the action:

1. Visit your target sandbox on the **Environment Details** page, and select **Maintain** > **Move database**.
1. Select the **Refresh database** option and choose your source environment.
1. Review the warnings and the list of data elements that aren't copied from the source environment.
1. The refresh operation starts immediately.

### Refresh operation failed

If the operation fails, the refresh process automatically rolls back. The target sandbox environment is restored to the state it was before the refresh began. This restoration is possible because of the Azure SQL point-in-time restore capability. Restoration is often required if a customization present in the target sandbox can't complete a database synchronization with the newly refreshed data.

To determine the root cause of the failure, use the **Environment change history** page to download the logs for the failed operation.  

### Data elements that aren't copied during refresh

The information in this section lists certain elements of the database that aren't copied to the target environment during a database refresh operation.

#### When refreshing a production environment to a sandbox environment or a sandbox to another sandbox environment

- Email addresses in the LogisticsElectronicAddress table.
- SMTP Relay server in the SysEmailParameters table.
- Print Management settings in the PrintMgmtSettings and PrintMgmtDocInstance tables.
- All users except the admin are set to **Disabled** status.
- Dimension log and cache status tables including DIMENSIONHASHMESSAGELOG, DIMENSIONDATAINTEGRITYLOG, DIMENSIONVALUERENAMEAUDIT, DIMENSIONVALUEDELETEAUDIT, DIMENSIONATTRIBUTEVALUECOMBINATIONSTATUS, DIMENSIONATTRIBUTEVALUEGROUPSTATUS, DIMENSIONDATAENTITYSFKCACHE, DIMENSIONREFERENCES.

#### When refreshing from sandbox environment to production environment

This operation is also referred to as [Golden configuration promotion](dbmovement-scenario-goldenconfig.md).

- Batch job history is stored in the BatchJobHistory, BatchHistory, and BatchConstraintHistory tables.

#### These elements are removed for all database refresh operations

- Environment-specific records in the SysServerConfig, SysServerSessions, SysCorpNetPrinters, SysClientSessions, BatchServerConfig, and BatchServerGroup tables.
- All files stored in Azure blob storage. This removal includes document attachments (from the DocuValue and DocuDeletedValue tables) and custom Microsoft Office templates (from the DocuTemplate table).
- All batch jobs are set to **Withhold** status.
- All users have their partition value reset to the "initial" partition record ID.
- All Microsoft-encrypted fields are cleared, because they can't be decrypted on a different database server. An example is the **Password** field in the SysEmailSMTPPassword table.
- [Maintenance mode](../sysadmin/maintenance-mode.md) settings are disabled even if the source enabled them.
- Dual-write configuration.  To set up a new link on the target environment after this operation is successful, see [Enable Power Platform Integration](../../dev-itpro/power-platform/enable-power-platform-integration.md).
- Any [change-tracking on entities](../data-entities/entity-change-track.md) are disabled.
- [Service endpoints](../business-events/managing-business-event-endpoints.md) for business events and data events are removed.

Some of these elements aren't copied because they're environment-specific. Examples include BatchServerConfig and SysCorpNetPrinters records. Other elements aren't copied because of the volume of support tickets. For example, duplicate emails might be sent because Simple Mail Transfer Protocol (SMTP) is still enabled in the UAT environment, invalid integration messages might be sent because batch jobs are still enabled, and users might be enabled before admins can perform post-refresh cleanup activities.

### Environment administrator

The System Administrator account in the target environment (UserId of 'Admin') is reset to the value found in the web.config file on the target. This value should match the Administrator value from Lifecycle Services. To preview which account this is, visit your target sandbox **Environment Details** page in Lifecycle Services. The value of the **Environment Administrator** field that you select when you first deploy the environment becomes the System Administrator in the transactional database. This change also means that the tenant of the environment is that of the Environment Administrator.

If you use the Admin User Provisioning Tool on your environment to change the web.config file to a different value, it might not match what is in Lifecycle Services. If you need a different account, deallocate and delete the target sandbox, and redeploy selecting another account. After this step, you can perform another refresh database action to restore the data.

You can't refresh an environment from one tenant to another. This restriction applies even to .onmicrosoft.com tenants. Make sure that the admin accounts in the source and target environments are from the same tenant domain.

### Conditions of a database refresh

The following list describes the requirements and conditions for a database refresh operation:

- A refresh operation deletes the original target database.
- The target environment is available until the database copy reaches the target server. After that point, the environment is offline until the refresh process completes.
- The refresh affects only the application and Financial Reporting databases.
- No **file stored in Azure blob storage is copied** from one environment to another. This restriction includes **document attachments and custom Microsoft Office templates**. These documents stay unchanged and remain in their current state.
- All users except the Admin user and other internal service user accounts are unavailable. This process allows the Admin user to delete or obfuscate data before allowing other users back into the system.
- The Admin user must make required configuration changes, such as reconnecting integration endpoints to specific services or URLs.
- All data management framework recurring import and export jobs must be fully processed and stopped in the target system before initiating the restore. In addition, select the database from the source after all recurring import and export jobs are fully processed. This step ensures there are no orphaned files in Azure storage from either system. This condition is important because orphaned files can't be processed after the database is restored in the target environment. After the restore, the integration jobs can resume.
- Any user with a role of Project owner or Environment manager in Lifecycle Services has access to the SQL and machine credentials for all nonproduction environments.
- The databases must be hosted in the same Azure geographic region, unless the databases are Spartan-managed.  Databases are Spartan-managed when you see 'spartan' as part of the fully qualified SQL server address.
- The allocated database capacity of the source environment must be less than the maximum database capacity of the target environment.

## Steps to complete after a database refresh for environments that use Commerce functionality

[!include [environment-reprovision](../includes/environment-reprovision.md)]

## Known issues

### The Restore operation fails if the sandbox customizations are incompatible with production data

Even if you successfully add a customization to the sandbox environment (that is, the customer's AOT deployable package is successfully installed via Lifecycle Services), it might not succeed for production data. For example, a customer adds a unique index on **Vendor Name** to the VendTable table. You can successfully install this customization if there are no duplicate vendor names in the sandbox environment. However, when the production database is brought in as part of the Restore operation, installation might fail if there are duplicates in the dataset that is inbound to the sandbox environment. Duplicates in this dataset aren't supported. Therefore, you must remove the customization before you can have a successful Restore operation.

### Refresh is denied for environments that run Platform update 20 or earlier

The database refresh process can't currently be completed if the environment is running Platform update 20 or earlier. For more information, see the [list of currently supported platform updates](../migration-upgrade/versions-update-policy.md).

### Incompatible version of Financial Reporting between source and target environments

The database refresh process (self-service or via a service request) can't be completed successfully if the version of Financial Reporting in the target environment is earlier than the version in the source environment. To resolve this issue, update both environments so that they have the latest version of Financial Reporting.

To determine the version you have installed in your source and target environments, visit the **View detailed version information** link on the **Environment Details** page.

Search for **MRApplicationService** and ensure that the target environment is greater than or equal to the source environment.

:::image type="content" source="media/FinancialReporting_Binaries2.png" alt-text="Screenshot of MRApplicationService version information.":::

For customers that use version 8.1 or later:

1. Go to the **Update** tiles for your UAT environment. Save the updates to your Project asset library.
1. Apply this package to your UAT environment.
1. Verify that the error is resolved.

For customers that use version 8.0 or earlier:

1. Review the Environment history of your source environment. Specifically, look for any "Platform and application binary package" that might have been deployed to the source environment and not the target environment.
1. Apply this binary package to your target environment.
1. Verify that the error is resolved.

### Incompatible application versions between source and target environments

If your production environment is newer than your target sandbox, you need to either upgrade the target sandbox before the refresh or deallocate, delete, and redeploy the sandbox before performing the refresh.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
