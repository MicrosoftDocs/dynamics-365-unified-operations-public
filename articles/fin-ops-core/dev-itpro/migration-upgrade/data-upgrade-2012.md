---
# required metadata

title: Upgrade from AX 2012 - Data upgrade in development environments
description: This article explains the end-to-end process for upgrading from Microsoft Dynamics AX 2012 to the latest finance and operations development environment.
author: laneswenka
ms.date: 06/03/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.custom: 106163
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: laswenka
ms.search.validFrom: 2017-05-31
ms.dyn365.ops.version: Platform update 8

---

# Upgrade from AX 2012 - Data upgrade in development environments

[!include [banner](../includes/banner.md)]

[!include [upgrade banner](../includes/upgrade-banner.md)]

This is an exciting moment in the upgrade project. The output of this task provides the first upgraded dataset from Microsoft Dynamics AX 2012 to the latest finance and operations development environment.

Before you run this process in a shared sandbox environment, we recommend that you run it in a development environment. There are two reasons for this approach:

- It provides local data that developers can write and test their custom data upgrade scripts against.
- It helps reduce the overall time that is spent on iterations of the data upgrade process. In a development environment, an issue can be debugged immediately, code can be adjusted, and the upgrade can be rerun within minutes. Larger sandbox environments don't allow for this level of agility. In those environments, a minimum of several hours will be required to debug and remediate issues, update code, deploy the updated code, and rerun the upgrade.

We strongly recommend running the [Upgrade analyzer](upgrade-analyzer-tool.md) and respond to the identified issues before running data upgrade. This helps ensure that your data upgrade is quicker and easier.

## End-to-end data upgrade process

![Data upgrade process.](media/endToEndDataUpgradeProcess.png)

### Prerequisites

Ensure that you've completed the preupgrade checklist in AX 2012. For more information, see [Preupgrade checklist for data upgrade](prepare-data-upgrade.md).

> [!IMPORTANT]
> It is recommended that before you run the upgrade, apply the latest **Quality Update** for the Dynamics 365 version you are using.


### Back up your AX 2012 database

Back up your AX 2012 database using the standard Microsoft SQL Server process to produce a BAK file. If you use the compression option when you create the backup, the file size will be smaller, and less time is required in order upload it to and download it from Microsoft Azure Storage.

> [!NOTE]
> The collation of the AX 2012 database must be **SQL_Latin1_General_CP1_CI_AS**. If you're using a different collation, contact Microsoft Support for assistance. 

### Upload the backup to Azure Storage

If your developer environment is hosted as a VM locally or in Azure, you need to transfer the 2012 database backup to it. With a local VM, you may be able to transfer the file directly across the network if the virtual network allows. For an Azure hosted VM, we recommend that you upload your backup to Azure Storage using your own secure file transfer service or SFTP. You would need to provide your own Azure storage account for this. There are free tools to help you to move files between Azure storage, from a command line you can use [Azcopy](/azure/storage/storage-use-azcopy), or for a GUI experience you can use [Microsoft Azure storage explorer](https://storageexplorer.com/). Use one of these tools to first upload the backup from your on-premises environment to Azure storage and then download it in your development environment.

### Download and restore the backup to the customer-managed development environment

> [!NOTE]
> Developer environments are only supported as customer-managed, [cloud-hosted environments](../dev-tools/access-instances.md). By using cloud-hosted environments, you can increase the drive space so that it meets your own specifications.

When you restore the backup to the new development environment, don't overwrite the existing AXDB database. Instead, restore the AX 2012 database next to the original databases. The upgrade process is very disk intensive, consider using premium storage to deploy the cloud-hosted environment to help improve performance and timing.

To speed up the database restore process, you can change the SQL Server service account to the **BuiltIn\\Admin** user. Details about that user account are available on the environment page in Microsoft Dynamics Lifecycle Services (LCS). The restore process can then use instant file initialization. For more information, see [Database Instant File Initialization](/sql/relational-databases/databases/database-instant-file-initialization).

After the database is restored, stop the following services:

- Management Reporter 2012 Process service
- Microsoft Dynamics 365 Unified Operations: Batch Management service
- Microsoft Dynamics 365 Unified Operations: Data Import Export Framework Service
- Microsoft Dynamics Lifecycle Services Diagnostic Service
- World wide web publishing service

> [!NOTE]
> Ensure these services remained stopped during the upgrade. Rebooting the server will start these again. 

Next, rename the original AXDB database **AXDB_orig**. This database might be useful as reference later, when you develop code.
```sql
ALTER DATABASE AXDB SET SINGLE_USER WITH ROLLBACK IMMEDIATE
GO
ALTER DATABASE AXDB MODIFY NAME = AXDB_Orig
GO
ALTER DATABASE AXDB_Orig SET MULTI_USER
GO
```

Finally, rename the newly restored AX 2012 database **AXDB**.

### Run the data upgrade deployable package 

To get the latest data upgrade deployable package for a target environment that is running the latest update, download the latest binary updates from LCS Shared asset library.

1. Sign in to [LCS](https://lcs.dynamics.com/).
1. Select the **Shared asset library** tile.
1. In the **Shared asset** library, under **Select asset type**, select **Software deployable package**.
1. All data upgrade packages start with **AX2012DataUpgrade**. In the list, find the data upgrade package that corresponds to your specific Dynamics 365 version.

    For example, if you're upgrading to version 10.0.26, the package name will be **AX2012DataUpgrade-10.0.26**.

1. Select the data upgrade package to download, and save\copy it to the **C:\\Temp** folder in the cloud-hosted environment.
1. Select and hold (or right-click) the download, and then select **Properties**.
1. Select the **Unblock** checkbox, select **OK**, and then extract the file. 
1. Open a PowerShell Prompt as an admin, and change to the deployable package folder (for example, **C:\\Temp\\AX2012DataUpgrade 10.0.26**).
1. Ensure the services you stopped in the **Download and restore the backup to the customer-managed development environment** step above are still stopped. If these are running, you will get locking issues on the database. 
1. Run the deployable package by using the following script. You can edit the runbook ID and file name in the script.

    ```PowerShell
    .\AXUpdateInstaller.exe generate -runbookid="MajorVersionDataUpgrade-runbook" -topologyfile="DefaultTopologyData.xml" -servicemodelfile="DefaultServiceModelData.xml" -runbookfile="MajorVersionDataUpgrade-runbook.xml"
    .\AXUpdateInstaller.exe import -runbookfile="MajorVersionDataUpgrade-runbook.xml"
    .\AXUpdateInstaller.exe execute -runbookid="MajorVersionDataUpgrade-runbook"
    ```

> [!NOTE]
> The data upgrade can take several hours.

### Monitoring the data upgrade

The deployable package has a single runbook step that processes the whole upgrade. This step consists of the following substeps that are run in the background:

- **PreReqs** – This step patches the SQL dictionary, applies SQL sequences instead of system sequences, modifies user info and system variables, does database synchronization of system tables, and does additive synchronization of new tables.
- **PreSync** – This step invokes the first set of upgrade jobs via batch processing, mostly to disable unique indexes.
- **DBSync** – This step does the first full synchronization. Unique indexes that were disabled during the PreSync step aren't created during this step.
- **PostSync** – This step runs the main data conversion jobs via batch processing.
- **FinalDBSync** – This step does the final database synchronization that synchronizes all remaining objects in the database.

To determine which step the upgrade servicing is on, you can run the following SQL query on the AXDB database.

```SQL
SELECT StartTime, EndTime, Steps, SubSteps, Status
FROM [DBUPGRADE].[DATAUPGRADESTATUS]
ORDER BY EndTime DESC
```

The results will resemble the following example. The dates and times that are given here are for illustration purposes only. Times vary, based on data volumes and the modules that are used in AX 2012.

| StartTime | EndTime | Steps | SubSteps | STATUS |
|---|---|---|---|---|
| 2022-05-20 17:16:07.097 | 2022-05-20 17:16:07.097 | FinalDbSync | DisableDataUpgradeFlag | Completed |
| 2022-05-20 17:16:06.997 | 2022-05-20 17:16:06.997 | FinalDbSync | EnableDbLogTriggers | Completed |
| 2022-05-20 17:16:06.937 | 2022-05-20 17:16:06.937 | FinalDbSync | DisableSafeMode | Completed |
| 2022-05-20 16:48:49.390 | 2022-05-20 17:16:06.802 | FinalDbSync | SyncSchema | Completed |
| 2022-05-20 16:48:49.333 | 2022-05-20 16:48:49.333 | FinalDbSync | EnableSafeMode | Completed |
| 2022-05-20 16:47:30.860 | 2022-05-20 16:48:49.169 | PostSync | RestoreBatchConfiguration | Completed |
| 2022-05-20 16:46:15.207 | 2022-05-20 16:47:30.738 | PostSync | EnableBatchPriorityScheduling | Completed |
| 2022-05-20 16:44:43.403 | 2022-05-20 16:46:15.091 | PostSync | DisableSysDeletedObjects | Completed |
| 2022-05-20 16:44:40.497 | 2022-05-20 16:44:40.497 | PostSync | ImportIsvLicenses | Completed |
| 2022-05-20 16:44:09.190 | 2022-05-20 16:44:40.379 | PostSync | StopBatch | Completed |
| 2022-05-20 15:49:38.207 | 2022-05-20 16:44:09.070 | PostSync | WaitForBatch | Completed |
| 2022-05-20 15:49:37.517 | 2022-05-20 15:49:38.108 | PostSync | StartBatch | Completed |
| 2022-05-20 15:48:31.517 | 2022-05-20 15:49:37.421 | PostSync | ScheduleScripts | Completed |
| 2022-05-20 15:47:13.403 | 2022-05-20 15:48:31.431 | PostSync | StartAos | Completed |
| 2022-05-20 15:47:12.667 | 2022-05-20 16:44:43.286 | PostSync | ExecuteScripts | Completed |
| 2022-05-20 15:47:12.550 | 2022-05-20 15:47:12.550 | DbSync | DisableSafeMode | Completed |
| 2022-05-20 07:49:40.827 | 2022-05-20 15:47:12.466 | DbSync | SyncSchema | Completed |
| 2022-05-20 07:49:40.760 | 2022-05-20 15:31:05.716 | DbSync | EnableSafeMode | Completed |
| 2022-05-20 07:49:06.673 | 2022-05-20 07:49:37.862 | PreSync | StopBatch | Completed |
| 2022-05-20 07:46:59.667 | 2022-05-20 07:49:06.528 | PreSync | WaitForBatch | Completed |
| 2022-05-20 07:46:58.637 | 2022-05-20 07:46:59.529 | PreSync | StartBatch | Completed |
| 2022-05-20 07:46:31.317 | 2022-05-20 07:46:58.497 | PreSync | ScheduleScripts | Completed |
| 2022-05-20 07:45:31.900 | 2022-05-20 07:46:31.180 | PreSync | StartAos | Completed |
| 2022-05-20 07:45:31.780 | 2022-05-20 07:45:31.780 | PreSync | ConfigureBatch | Completed |
| 2022-05-20 07:45:31.220 | 2022-05-20 07:49:40.519 | PreSync | ExecuteScripts | Completed |
| 2022-05-20 07:44:18.410 | 2022-05-20 07:45:31.092 | PreSync | DisaleBatchPriorityScheduling | Completed |
| 2022-05-20 07:43:14.880 | 2022-05-20 07:44:18.273 | PreSync | SaveBatchConfiguration | Completed |
| 2022-05-20 07:42:05.350 | 2022-05-20 07:43:14.749 | PreSync | EnableSysDeletedObjects | Completed |
| 2022-05-20 07:40:44.340 | 2022-05-20 07:42:05.211 | PreSync | CleanupDataUpgradeTables | Completed |
| 2022-05-20 07:40:44.250 | 2022-05-20 07:40:44.250 | PreReqs | DisableSafeMode | Completed |
| 2022-05-20 07:38:29.060 | 2022-05-20 07:40:44.110 | PreReqs | PartialDbSync | Completed |
| 2022-05-20 06:30:01.693 | 2022-05-20 07:38:28.908 | PreReqs | AdditiveDbSync | Completed |
| 2022-05-20 06:30:01.647 | 2022-05-20 06:30:01.647 | PreReqs | EnableSafeMode | Completed |
| 2022-05-20 06:30:01.590 | 2022-05-20 06:30:01.590 | PreReqs | ClearSysLastValue | Completed |
| 2022-05-20 06:30:01.523 | 2022-05-20 06:30:01.523 | PreReqs | ResetAdminUser | Completed |
| 2022-05-20 06:30:01.477 | 2022-05-20 06:30:01.477 | PreReqs | PatchSqlSystemVariables | Completed |
| 2022-05-20 06:30:01.273 | 2022-05-20 06:30:01.367 | PreReqs | PatchUserInfo | Completed |
| 2022-05-20 06:30:00.930 | 2022-05-20 06:30:01.164 | PreReqs | PatchSqlDictionaryPass2 | Completed |
| 2022-05-20 06:30:00.150 | 2022-05-20 06:30:00.820 | PreReqs | PatchSqlDictionaryPass1 | Completed |
| 2022-05-20 06:30:00.043 | 2022-05-20 06:30:00.043 | PreReqs | UpdateKernelSchema | Completed |
| 2022-05-20 06:28:01.157 | 2022-05-20 06:29:59.929 | PreReqs | CreateSqlSequences | Completed |
| 2022-05-20 06:28:01.020 | 2022-05-20 06:28:01.020 | PreReqs | DisableDbLogTriggers | Completed |

## Troubleshooting data upgrade errors

### Rerun the runbook after a failure

If the data upgrade runbook fails, you can retry the last step by using the **-rerunstep** option, as shown in the following example. Edit the step number as required.

```PowerShell
.\AXUpdateInstaller.exe execute -runbookid="MajorVersionDataUpgrade-runbook" -rerunstep=3
```

### Review the runbook logs

Logs are located in a subfolder under the deployable package. Drill into the logs folder to find the logs for the runbook step that you're on, and review errors.

### View details about a PreSync or PostSync upgrade job

Upgrade PreSync and PostSync scripts are run in X++ by using a batch process that the data upgrade process starts. In Application Explorer in Visual Studio, some classes that you can view are prefixed with **ReleaseUpdate**. If an upgrade script fails during the runbook process, you can learn more about the reason for the error by opening SQL Server Management Studio and running the following code to query ReleaseUpdateScriptsErrorLog.

```SQL
select * from RELEASEUPDATESCRIPTSERRORLOG
```

### Additional resources

For more troubleshooting information, see the following articles:

- [Troubleshoot development environments during upgrade](troubleshoot-dev-env.md)
- [Troubleshoot PreSync and PostSync upgrade scripts](pre-post-upgrade-scripts.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

