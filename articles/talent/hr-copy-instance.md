---
# required metadata

title: Copy a Core HR instance
description: Copy the database for Dynamics 365 Talent - Core HR to a sandbox environment.
author: andreabichsel
manager: AnnBe
ms.date: 12/17/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

# ms.search.form: HcmACACoverageGroup
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
ms.search.scope: Core, Talent
# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 3b953d5f-6325-4c9e-8b9b-6ab0458a73f8
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2017-07-01
ms.dyn365.ops.version: AX 7.0.0, Talent July 2017 update

---
# Copy a Core HR instance

[!include [banner](../includes/banner.md)]

You can use Microsoft Dynamics Lifecycle Services (LCS) to copy a Dynamics 365 Talent: Core HR database to a sandbox environment. If you have another sandbox environment, you can also copy the database from that environment to a targeted sandbox environment.

> [!IMPORTANT]
> Copying the Core HR database does not copy apps or data contained in a PowerApps environment.  To copy elements in a PowerApps environment see Copy an environment https://docs.microsoft.com/en-us/power-platform/admin/copy-environment

## Copy Core HR database instructions
To ensure all information contained in both the Core HR database along with apps and data in the PowerApps environment be sure to follow the instructions below:

1. Sign into LCS and select the LCS project which contains the environment you want to copy.
2. In your LCS project, select the **Talent App Management** tile
3. Select the instance you want to copy and select the **Copy** action
4. Note the warning and important information as well as read the instrutions
5. Select the instance to overwrite
6. Click **Copy** 
7. Once the copy function is complete the Status will display **Complete**.
8. Log into the Power Platform Admin Center by select the Power Platform link in the Resources section
9. Select the PowerApps environment you want to copy and select the Copy action
10. Once the PowerApps environment copy is complete log into your Talent-Core HR instance and turn on the CDS integration found under System Administration.


### Data elements that aren't copied during the Core HR database copy:

* Email addresses in the LogisticsElectronicAddress table.
* Batch job history in the BatchJobHistory, BatchHistory, and BatchConstraintHistory tables.
* SMTP password in the SysEmailSMTPPassword table.
* SMTP Relay server in the SysEmailParameters table.
* Print Management settings in the PrintMgmtSettings and PrintMgmtDocInstance tables.
* Environment-specific records in the SysServerConfig, SysServerSessions, SysCorpNetPrinters, SysClientSessions, BatchServerConfig, and BatchServerGroup tables.
* Document attachments in the DocuValue table. This includes any Office Templates that were overriden in the source environment.
* Connection string in the PersonnellIntegrationConfiguration table.
* All users except the admin will be set to **Disabled** status.
* All batch jobs are set to **Withhold** status.

Some of these elements aren't copied because they are environment-specific. Examples include BatchServerConfig and SysCorpNetPrinters records. Other elements aren't copied because of the volume of support tickets. For example, duplicate emails might be sent because Simple Mail Transfer Protocol (SMTP) is still enabled in the UAT environment, invalid integration messages might be sent because batch jobs are still enabled, and users might be enabled before admins can perform post-refresh cleanup activities.

### Environment administrator
The System Administrator account in the target environment (UserId of 'Admin') is reset to the value found in the web.config file on the target.  This should be the same value as that of the Administrator from Lifecycle Services.  To preview which account this will be, visit your target sandbox **Environment Details** page in LCS.  The value of the **Environment Administrator** field that was selected when the environment was first deployed is updated to be the System Administrator in the transactional database. This also means that the tenant of the environment will be that of the Environment Administrator.

If you have used the Admin User Provisioning Tool on your environment to change the web.config file to a different value, it may not match what is in Lifecycle Services.  If you require a different account to be used, you will need to deallocate and delete the target sandbox, and redeploy selecting another account. After this, you can perform another refresh database action to restore the data.

### Conditions of a copying a Core HR database:

- Copying erases the existing database in the target environment. The existing database can't be recovered after the copy is completed.
- The target environment will be unavailable until the copy process is completed.
- Documents in Azure blob storage are not copied from one environment to another. This means that attached document handling documents and templates won't be changed and will remain in their current state.
- All users except the Admin user and other internal service user accounts will be unavailable. This process allows the Admin user to delete or obfuscate data before allowing other users back into the system.
- The Admin user must make required configuration changes, such as reconnecting integration endpoints to specific services or URLs.
- All data management framework with recurring import and export jobs must be fully processed and stopped in the target system prior to initiating the restore. In addition, we recommend that you select the database from the source after all recurring import and export jobs have been fully processed. This will ensure there are no orphaned files in Azure storage from either system. This is important because orphaned files cannot be processed after the database is restored in the target environment. After the restore, the integration jobs can be resumed.


