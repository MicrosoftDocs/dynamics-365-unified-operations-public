---
# required metadata

title: Request sandbox database refreshes
description: This topic explains how to request a refresh of the database for Microsoft Dynamics 365 for Finance and Operations, in a sandbox user acceptance testing (UAT) environment.
author: LaneSwenka
manager: AnnBe
ms.date: 11/13/2018
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
ms.custom: 257614
ms.assetid: 558598db-937e-4bfe-80c7-a861be021db1
ms.search.region: Global
# ms.search.industry: 
ms.author: laneswenka
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Request sandbox database refreshes

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

You can use Microsoft Dynamics Lifecycle Services (LCS) to request a refresh of the database for Microsoft Dynamics 365 for Finance and Operations, to a sandbox user acceptance testing (UAT) environment. A database refresh lets you copy the transactional database of your Production environment into the target Sandbox UAT environment.  This process includes copying of the Financial Reporting database. If you have another Sandbox environment, you can also copy the databases from that environment to your target Sandbox UAT environment.

This functionality lets you use Production data to test upcoming code changes in a UAT environment. You can also copy a production database into a UAT environment for debugging purposes.

> [!important]
> Copying Production data to your Sandbox environment for the purpose of Production Reporting is not supported.  

## Database refresh via self-service (public preview)
With the goal of providing Application Lifecycle Management capabilities to our customers without needing to rely on human or manual processes, the Microsoft Dynamics Lifecycle Services team has introduced an automated Refresh Database action.  To refresh your Sandbox environment with data from another environment, you can now perform this action as part of self-service action that is in public preview.  The process is outlined below, and is fully supported functionality.

1. Enable the Public Preview Feature by logging in to Lifecycle Services and selecting **Preview feature management** tile from the home screen.  Find the feature titled "Restore database from another environment" and set the *Preview feature enabled* value to True.
2. Visit your target sandbox environment details page, and click the **Maintain** -> **Move database** menu option.
3. Select the **Refresh database** option and choose your source environment.
4. Note the warnings and see the list of data elements below which are not copied from the source environment.
5. The refresh operation will begin immediately.
6. Once the refresh operation is completed, you must **Sign off** on the operation before being able to perform another servicing ( package deployment, database movement, or upgrade ) operation.

### Refresh operation failed
In case of failure, the option to perform a **Rollback** is available.  By clicking the rollback option after the operation has initially failed, your target sandbox environment will be restored to the state it was before the refresh began.  This is made possible by the Azure SQL Point-in-time restore capability to restore the database.  This is often required if a customization is present in the target sandbox that cannot complete a Database Synchronization with the newly refreshed data.  

To determine the root cause of the failure, download the runbook logs using the available buttons before starting the rollback operation.

### Data elements which aren't copied during refresh
When refreshing a production environment to a sandbox environment, or a sandbox environment to another sandbox environment, there are certain elements of the database that are not copied over to the target environment.  This is because the data is either environment specific, or could cause operational issues such as sending realistic email out of a non-Production environment.  These data elements include:
* Email addresses in the LogisticsElectronicAddress table.
* Batch job history in the BatchJobHistory, BatchHistory, and BatchConstraintHistory tables.
* SMTP password in the SysEmailSMTPPassword table.
* SMTP Relay server in the SysEmailParameters table.
* Mail provider is reset to SMTP in the SysEmailParameters table to prevent accidental outbound mail using the Exchange provider.
* Print Management settings in the PrintMgmtSettings and PrintMgmtDocInstance tables.
* Environment-specific records in the SysServerConfig, SysServerSessions, SysCorpNetPrinters, SysClientSessions, BatchServerConfig, and BatchServerGroup tables.
* Document attachments in the DocuValue table.
* All users except for the administrator and Microsoft service accounts are disabled.
* All batch jobs are set to Withhold status.

### Environment administrator
The System Administrator account in the target environment ( UserId of 'Admin' ) is reset to the value of the Administrator from Lifecycle Services.  To preview which account this will be, visit your target sandbox Environment Details page in LCS.  The value of the Environment Administrator field that was selected when the environment was first deployed is updated to be the System Administrator in the transactional database.  This also means that the Tenant of the environment will be that of the Environment Administrator.  If you require a different account to be used, you will need to Deallocate and Delete the target Sandbox, and redeploy selecting your account of choice.  Thereafter, perform another Refresh Database action to restore the data.

## Database refresh via Service Request

> [!NOTE]
> As of October 2018, database refresh requests must be signed off before another refresh of the same environment can be started. This is to support future automation of database movement operations. To sign off, visit your Environment Details page and click the **Signoff** button. You can create many database refresh service requests out in to the future, however you must sign off in between each one.

> [!IMPORTANT]
> Service requests for Database Refresh will not be accepted for servicing dates after January 31, 2019.  After this date, all refresh operations will be performed via the self-service actions outlined above.

The Microsoft Service Engineering team will take your environment offline, complete the refresh, and then bring the environment back online. You can expect the downtime period to be approximately two hours. The period after you enter your request and before our Service Engineers take action will be longer than your environment's downtime. In the future, we will provide a self-service method that you can use to perform your database refreshes.

1. In LCS, on the Project home page, select **Service requests**.
2. On the **Service requests** page, select **Add** on the toolbar, and then select **Database refresh**.
3. In the **Request for database refresh** dialog box, follow these steps:

    1. In the **Environment name** field, select the environment to refresh.
    2. In the **Database** field, the database to refresh is always the Microsoft Dynamics AX database or the Finance and Operations database. Other databases, such as Entity store aren't currently supported for database refresh.
    3. Carefully read and acknowledge the statements that have check boxes next to them.

4. After you submit your request, you are returned to the list of work items. Here, you can view the status of the request, or reschedule or cancel the request.
5. Ensure no prior servicing request on your environment is awaiting signoff or rollback. Visit your Environment details page and sign off any completed refresh or package deployment.
6. When the Service Engineering team has acknowledged that they can complete your request, the status of the request is changed to **Request accepted**. At this point, you can follow any of these steps:

    - Wait for the Service Engineering team to complete the refresh. When the restore is completed, the status is changed to **Succeeded**.
    - Reschedule the request by selecting the ID, or by selecting the request and then selecting **Reschedule** on the toolbar. You can then change the dates and times for the downtime window.
    - Cancel the request by selecting the request and then selecting **Cancel** on the toolbar.

## Conditions of a database refresh
Here is the list of requirements and conditions of operation for a database refresh:

- Any previous servicing operation, such as a package deployment or prior database refresh, *must be signed off* from your environment details page.
- Requests must be submitted 5 hours before the desired downtime window, to help ensure that resources will be available to complete the request.
- A refresh erases the existing database in the target environment. The existing database can't be recovered after the refresh is completed.
- The target environment will be unavailable until the refresh process is completed.
- The refresh will affect only the Finance and Operations and Financial Reporting databases.
- Documents in Azure blob storage are not copied from one environment to another. This means that attached document handling documents and templates won't be changed and will remain in their current state.
- All users except the Admin user and other internal service user accounts will be disabled. This process allows the Admin user to delete or obfuscate data before allowing others users back into the system.
- The Admin user must make required configuration changes, such as reconnecting integration endpoints to specific services or URLs.
- All data management framework recurring import and export jobs must be fully processed and stopped in the target system prior to initiating the restore. In addition, we recommend that you select the database from the source after all recurring import and export jobs have been fully processed. This will ensure there are no orphaned files in Azure storage from either system. This is important because orphaned files cannot be processed after the database is restored in the target environment. After the restore, the integration jobs can be resumed.
- All batches that were set to run are set to **Withhold** status, to stop batches from running before the environment has been reconfigured.
- The SMTP server configuration, all email addresses, and all **Print management** settings, including network printers are removed.
- Any user with a role of Project owner or Environment manager in LCS will have access to the SQL and machine credentials for all non-production environments.

## Steps to complete after a database refresh for environments that use Retail functionality
[!include [environment-reprovision](../includes/environment-reprovision.md)]

## Known Issues

### Incompatible version of Financial Reporting between Source and Target Environments
The database refresh process (self-service or via Service Request) cannot be completed successfully if the version of Financial Reporting is different between the source and target environment.  To resolve, update both environments to have the latest version of Financial Reporting.

* Visit the **Asset Library** in your implementation project, and then click on the *Software deployable package* section.
* Click the **Import** button and find the latest Microsoft Dynamics Financial Reporting binary update package and pick this for import.
* Apply this package to both the source and target environments to ensure they are both using the latest version.

### Incompatible application versions between Source and Target Environments
The database refresh process (self-service or via Service Request) cannot be completed if the Application Release of your source and target environment are not the same.  This is because the data upgrade process is not executed by database movement operations such as Refresh, and data loss can occur.  

If upgrading your sandbox UAT environment to a newer application version ( 7.3 to 8.1 for example ), then be sure to perform the database refresh action prior to starting the upgrade.  Once your sandbox is upgraded to the newer version, you cannot restore an older Production environment database in to the sandbox UAT environment.  

Conversely, if your Production environment is newer than your target sandbox, you will need to either upgrade the target sandbox prior to the refersh or simply Deallocate, Delete, and Redeploy prior to performing the refresh.
