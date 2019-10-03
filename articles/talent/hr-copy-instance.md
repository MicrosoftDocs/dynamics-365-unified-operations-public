---
# required metadata

title: Copy a Core HR instance
description: Copy the database for Dynamics 365 Talent - Core HR to a sandbox environment.
author: andreabichsel
manager: AnnBe
ms.date: 10/03/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

# ms.search.form: HcmACACoverageGroup
# ROBOTS: 
audience: Admin
# ms.devlang: 
ms.reviewer: anbichse
ms.search.scope: Core, Talent
# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 3b953d5f-6325-4c9e-8b9b-6ab0458a73f8
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2019-10-03
ms.dyn365.ops.version: AX 7.0.0, Talent July 2017 update

---
# Copy a Core HR instance

[!include [banner](../includes/banner.md)]

You can use Microsoft Dynamics Lifecycle Services (LCS) to copy a Dynamics 365 Talent: Core HR database to a sandbox environment. If you have another sandbox environment, you can also copy the database from that environment to a targeted sandbox environment.

> [!IMPORTANT]
> Copying the Core HR database does not copy apps or data contained in a PowerApps environment. To copy elements in a PowerApps environment, see [Copy an environment](https://docs.microsoft.com/en-us/power-platform/admin/copy-environment).

## Effects of a copying a Core HR database

The following happens when you copy a core HR database:

- Copying erases the existing database in the target environment. You can't recover the existing database recovered after the copy completes.

- The target environment will be unavailable until the copy process completes.

- Documents in Azure blob storage are not copied from one environment to another. This means that attached document handling documents and templates won't be changed and will remain in their current state.

- All users except the Admin user and other internal service user accounts will be unavailable. This process allows the Admin user to delete or obfuscate data before allowing other users back into the system.

- The Admin user must make required configuration changes, such as reconnecting integration endpoints to specific services or URLs.

- All data management framework with recurring import and export jobs must be fully processed and stopped in the target system prior to initiating the restore. In addition, we recommend that you select the database from the source after all recurring import and export jobs have been fully processed. This will ensure there are no orphaned files in Azure storage from either system. This is important because orphaned files can't be processed after the database is restored in the target environment. After the restore, the integration jobs can resume.

## Copy the Core HR database

To complete this task, you will first copy an instance and then sign into the Power Platform Admin Center and copy your PowerApps environment.

> [!WARNING]
> Copying an instance erases the database in the target instance. The target instance is unavailable during this process.

1. Sign into LCS and select the LCS project that contains the instance you want to copy.

2. In your LCS project, select the **Talent App Management** tile.

3. Select the instance you want to copy and select **Copy**.

4. In the **Copy an instance** task pane, select the instance to overwrite and select **Copy**. Wait for **Copy status** to display **Completed**.

5. Select **Power Platform** and sign into the Power Platform Admin Center.

6. Select the PowerApps environment you want to copy and select **Copy**.

7. When the copy completes, sign into your instance and turn on Common Data Service integration. For more information and instructions, see [Integrate data into Common Data Service](https://docs.microsoft.com/en-us/power-platform/admin/data-integrator).

## Data elements and statuses

The following data elements aren't copied when you copy a Core HR instance:

- Email addresses in the LogisticsElectronicAddress table

- Batch job history in the BatchJobHistory, BatchHistory, and BatchConstraintHistory tables

- SMTP password in the SysEmailSMTPPassword table

- SMTP Relay server in the SysEmailParameters table

- Print Management settings in the PrintMgmtSettings and PrintMgmtDocInstance tables

- Environment-specific records in the SysServerConfig, SysServerSessions, SysCorpNetPrinters, SysClientSessions, BatchServerConfig, and BatchServerGroup tables

- Document attachments in the DocuValue table, including any Office Templates that were overriden in the source environment

- Connection string in the PersonnellIntegrationConfiguration table

Some of these elements aren't copied because they are environment-specific. Examples include BatchServerConfig and SysCorpNetPrinters records. Other elements aren't copied because of the volume of support tickets. For example, duplicate emails might be sent because Simple Mail Transfer Protocol (SMTP) is still enabled in the UAT environment, invalid integration messages might be sent because batch jobs are still enabled, and users might be enabled before admins can perform post-refresh cleanup activities.

In addition, the following statuses change when you copy an instance:

- All users except the admin are set to **Disabled** status.

- All batch jobs are set to **Withhold** status.

## Environment administrator

The System Administrator account (the **Admin** userid) in the target environment is reset to the value found in the web.config file on the target. This should be the same value as that of the Administrator from Lifecycle Services. To see which account this is, view the **Environment Details** page of your target sandbox in LCS. The value of the **Environment Administrator** field that was selected when the environment was first deployed is updated to the System Administrator in the transactional database. This also means that the tenant of the environment will be that of the Environment Administrator.

If you used the admin user provisioning tool on your environment to change the web.config file to a different value, it might not match the value in Lifecycle Services. If you need to use a different account, you need to deallocate and delete the target sandbox, and the redeploy with another account. After this, you can refresh the database to restore the data. For instructions on how to refresh the database, see [Refresh database](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/database/database-refresh).



