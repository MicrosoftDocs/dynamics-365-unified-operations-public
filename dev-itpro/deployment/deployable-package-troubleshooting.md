---
# required metadata

title: Troubleshoot package application failures
description: This topic explains 
author: manalidongre
manager: AnnBe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Operations, Platform, UnifiedOperations, AX Platform
# ms.tgt_pltfrm: 
ms.custom: 107013
ms.assetid: 341a229f-d9c3-4678-b353-d08d5b2c1caf
ms.search.region: Global
# ms.search.industry: 
ms.author: manado
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: Platform update 1

---


# Troubleshooting guide for package deployment failures
The topic below explains in detail how to troubleshoot issues seen when applying packages on your Tier 1 or Tier 2/3/4/5 environments. For details on how to apply a package refer to the [Apply a deployable package](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/deployment/apply-deployable-package-system) wiki.

## General troubleshooting/diagnostics

If package application isn't successful, you have two options:

- Click  **Resume**  to retry the operation that failed.

 
Using the logs

1. Download the logs.
2. Unzip the log files.
3. Select the role that a step failed for, such as  **AOS**  or  **BI**.
4. Select the VM where the step failed. This information appears in the  **Machine name**  column in the  **Environment updates**  section.
5. In the logs for the VM, select the folder that corresponds to the step where the issue occurred. The folder name identifies the step that each folder corresponds to. For example, if the issue occurred in the executing a step, select the  **ExecuteRunbook\** \* folder.

For example, if the folder name is ExecuteRunbook-b0c5c413-dae3-4a7a-a0c4-d558614f7e98-1\_I0\_R0, the step number is highlighted and is the number after the globally unique identifier (GUID).



## How To guide for addressing commonly seen failures during package application

### General failures

| **Issue** | **Troubleshooting details** |   **Action** |
| --- | --- | --- |
| **Servicing status failed without listing any steps in the &quot;Environment updates&quot; section** | This indicates that package being applied is invalid. 
Steps:
1. Download logs
2. Unzip and navigate to the AOS machine logs.
**Verify** that &quot;DownloadFilesAndSlipstreamTools-xxx&quot; folder exist **Verify** that &quot;GenerateRunbook-xxx&quot; folder exists
1. Click inside GenerateRunbook-xxx folder and open the output type file
 If error is found or an exception is found that a file is missing or failed to generate any steps for runbook etc, it&#39;s mainly due to invalid package being uploaded. | **Action** :   Click **Abort** to abort the current package, upload a new package and start the servicing flow again.       |
| **Package deployment has failed without any step failures** | Timed-out when downloading the package into the machine.  **Details** : During servicing there would be few steps that would be done in pre-servicing before running the actual steps in the runbook. As part of the pre-servicing the important step is downloading the package in all the machines. The time to download might vary a bit based on the data center where the environment is residing. If the download doesn&#39;t happen within 30 minutes, it would give up and result as failure in the servicing status. If It&#39;s been about 30 minutes since the package deployment is initiated, then you are mostly running into the issue.  | Resume should fix mostly fix the issue. 
**Quick troubleshooting steps**
  1. Download the logs from the environment page
  2. Ensure that the package download step has the logs in all the machines with the following folder DownloadFilesAndSlipstreamTools
  3. Inspect the log files and if you do not see the following is shown at the end of the log file, then package download is not completed and hence the issue.
_Completed file download and slipstream successfully_  |
| **Package deployment has failed without any step failures** | Disk space is not enough to download the package.  **Details** : During servicing there would be few steps that would be done in pre-servicing before running the actual steps in the runbook. As part of the pre-servicing the important step is downloading the package in all the machines. If there is not enough disk space to download the package then the servicing would result as a failure. Inspect all the machines and any of the machines servicing drive is full then you are running into this issue.  | Manually clean up old package deployment folder and free up disk space.  Please note that &quot;resume&quot; would not help here and need manual intervention before you can resume.  **Quick troubleshooting steps**
-
  1. Download the logs from the environment page
  2. Ensure that the package download step has the logs in all the machines with the following folder DownloadFilesAndSlipstreamTools
  3. Inspect the log files and if you see the download has failed due to disk space issue, proceed with the how to fix section.
  |
| **Step has failed with errors.** | This indicates that one of the following might be the reasons
1. Package has issues due to customizations or missing dependencies
2. Servicing scripts has an issue
3. Random failure during the step execution
  Steps:
1. Download logs
2. Navigate to the step logs
3. Open the output file for the step and see if there any errors.
4. If there any additional log files available, please inspect the logs for any errors.
   |   **Action** :
1. Download the logs
2. Click &quot; **Rerun step**&quot; to re-try the failed step
 If it fails again with the same issue  **Action** :
1. Look into the logs to dig in more
2. If you notice that there is an issue with the customizations, abort this package and re-try with the new package.
3. Check if there a fix available for the issue in the issue search
4. Open a ticket for Microsoft team to investigate further
 If you see the following step failure, GlobalUpdate script for service model: AOSService  This indicates that either DBSync or Report deployment might have failed.  Look for DBSync.err file to see what the errors are and inspect DBSync.log file. For specific failures during DB Sync step, look at the **Common DB Sync Failures** section.    |
| **Deployment status is showing  &quot;Servicing&quot; whereas the servicing status is in &quot;Failed state&quot;** | There is a re-try mechanism in-built to retry multiple times before it gives up especially the preparation step failures such as
1. Download the package into the machines
2. Slipstream the servicing package
3. Generate runbook
4. Upload runbook into blob
 |    **Action** : You can download the logs and see what the error is and start looking into it, before it finishes all the re-tries. ---If the in-built retry mechanism failed to go beyond the preparation stage after all re-tries  **Action** : please open a ticket for Microsoft team to investigate further, once you see the status as &quot;Failed&quot; and it&#39;s not due to invalid package issue.     |
| **After the package deployment is done, failed to launch the dashboard** | This indicates that there might be a run-time error when starting the AOS.
1. Launch event viewer
2. Navigate to &quot;Applications and Services Logs &gt; Microsoft &gt; Dynamics &gt; Ax-SystemRuntime &gt; Operational
3. Filter by errors and see if there was any errors and investigate.
 |    |



**Common DB Sync Failures**

If you see the following step failure, **GlobalUpdate script for service model: AOSService** , it could be a Db Sync issue. Look for DBSync.err file to see what the errors are and inspect DBSync.log file.

Steps:

1. Download logs
2. Navigate to the step logs
3. Open the output file for the step and see if there any errors.
4. If there any additional log files available, please inspect the logs for any errors.
5. Below table shows commonly seen failures and the corresponding action to take. The Issue column shows the error you will see in the dbsync.err file. The % can be replaced with the metadata name of the table, field, index, etc.



| **Issue** | **Action** |
| --- | --- |
| %Table Sync Failed for Table%Create Unique Index% | This typically happens when we create an unique index and the data is not unique. Please fix the data before rerunning the step again. |
| %Application configuration sync failed.%Custom action sync failed with error:% | Check the information in the error message and the call stack to determine the application code that is causing this issue. |
| %cannot be found from underlying query&#39;&#39;s table% | Fixed in update 6.  KB 4018815 for Update 3. |
| %Table Sync Failed for Table%Converting Field% | Error message should be self-explanatory. Please fix and redo the step. |
| %failed because one or more objects access this column% | Check if the index is there in metadata. If yes, this would be a SyncEngine product bug. Otherwise, please remove the index from SQL DB before rerunning the step. |
| %cannot be found from underlying data source&#39;&#39;s table% | Fixed in update 6.  KB 4018815 for Update 3. |
| &#39;%Table Sync Failed for Table%&#39; and errorMessage like &#39;%There is already an object named%&#39; | AX Internal SqlDictionary table and Sql Schema out of sync. There is not enough clue in the logs on how we arrived at this state. |
| %Table Sync Failed for Table%Column names in each table must be unique% | SqlDictionary entries for the table is corrupt. It is missing this field. There is not enough clue in the logs on how we arrived at this state. |
| %Column name &#39;LOAD\_&#39; does not exist in the target table or view. CREATE INDEX% | Appears to be SyncEngine issue. Please create a ticket on Microsoft Support. |
| Cannot drop the index &#39;VENDREQUESTPROFILEQUESTIONNAIRE.I\_1301PROFILEQUESTIONNAIRE&#39;, because it does not exist or you do not have permission | Appears to be SyncEngine issue. Please create a ticket on Microsoft Support. |
| %The index entry of length 2046 bytes for the index &#39;I\_65750INDEX1&#39; exceeds the maximum length of 1700 bytes for nonclustered indexes% | Please modify the index before rerunning the step. |
| %Incorrect syntax near% | SyncEngine issue. Please create a ticket on Microsoft Support. |
| Reference to database and/or server name in &#39;TEMPDB.DBO.T\_TRVREQUISITIONLINE\_C4C3569DD5A14CDABAE71A341743FB61&#39; is not supported in this version of SQL Server | SyncEngine issue, Please create a ticket on Microsoft Support. |
| %Error: Timeout expired.  The timeout period elapsed prior to obtaining a connection from the pool.% | Please retry the step. |
| Database execution failed: Invalid column name &#39;DEFAULTDIMENSION&#39;. CREATE VIEW | Appears to be SyncEngine issue. Please create a ticket on Microsoft Support. |
| Database execution failed: Invalid object name &#39;PMBI\_DEPROJECTTIMESHEET&#39;. CREATE VIEW | Appears to be SyncEngine issue. Please create a ticket on Microsoft Support. |
| %provider: Named Pipes Provider, error: 40 - Could not open a connection to SQL Server%  | Should have been already fixed in Plat Update 3. Please retry the step. |
