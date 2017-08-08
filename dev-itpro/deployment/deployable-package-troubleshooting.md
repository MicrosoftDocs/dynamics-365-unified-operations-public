---
# required metadata

title: Troubleshoot package application failures
description: The topic provides information about how to troubleshoot issues that might occur when you apply packages on your Tier 1 or Tier 2/3/4/5 environments.  
author: manalidongre
manager: AnnBe
ms.date: 08/08/2017
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
This topic provides detailed information about how to troubleshoot issues that might occur when you apply packages on your Tier 1 or Tier 2/3/4/5 environments. For details on how to apply a package, see [Apply a deployable package](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/deployment/apply-deployable-package-system).

## General troubleshooting and diagnostics
If a package application isn't successful, you have two options:
- Retry the failed operation Click  **Resume**  to retry the operation that failed.
- Use the logs

### Retry the failed operation
If the package application fails and you want to retry the operation, click **Resume**.

### Use the logs
If the package application fails and you want to use the logs, complete the following steps. 
1. Download and then unzip the log files.
2. Select the role that a step failed for, such as  **AOS**  or  **BI**.
3. Select the virtual machine where the step failed. You can find this information in the  **Machine name**  column in the  **Environment updates**  section.
4. In the virtual machine logs, select the folder that corresponds to the step where the issue occurred. The folder name identifies the step that each folder corresponds to. 
For example, if the issue occurred in the executing a step, select the  **ExecuteRunbook\* ** folder. The step number is highlighted and is the number after the globally unique identifier (GUID).

## Address common failures during package application

**Issue:** Servicing status failed without listing any steps in the &quot;Environment updates&quot; section
**Description:** This indicates that package being applied is invalid.
- Download logs
- Unzip and navigate to the AOS machine logs
- Verify that &quot;DownloadFilesAndSlipstreamTools-xxx&quot; folder exist
- Verify that &quot;GenerateRunbook-xxx&quot; folder exists
- Click inside GenerateRunbook-xxx folder and open the output type file
If error is found or an exception is found that a file is missing or failed to generate any steps for runbook etc, it&#39;s mainly due to invalid package being uploaded.
**Action:**
 Click **Abort** to abort the current package, upload a new package and start the servicing flow again.

**Issue:** Package deployment has failed without any step failures.
**Description:** Timed-out when downloading the package into the machine. During servicing, there would be few steps that would be done in pre-servicing before running the actual steps in the runbook. As part of the pre-servicing the important step is downloading the package in all the machines. The time to download might vary a bit based on the data center where the environment is residing. If the download doesn&#39;t happen within 30 minutes, it would give up and result as failure in the servicing status.
If It&#39;s been about 30 minutes since the package deployment is initiated, then you are mostly running into the issue. Resume should fix mostly fix the issue.
**Action:**
- Download the logs from the environment page
- Ensure that the package download step has the logs in all the machines with the following folder DownloadFilesAndSlipstreamTools
- Inspect the log files and if you do not see the following is shown at the end of the log file, then package download is not completed and hence the issue.
  - _Completed file download and slipstream successfully_

**Issue 3 : Package deployment has failed without any step failures.**

**Description:** Disk space is not enough to download the package. During servicing, there would be few steps that would be done in pre-servicing before running the actual steps in the runbook. As part of the pre-servicing the important step is downloading the package in all the machines. If there is not enough disk space to download the package, then the servicing would result as a failure. Inspect all the machines and any of the machines servicing drive is full then you are running into this issue.

         Manually clean up old package deployment folder and free up disk space.

Please note that &quot;resume&quot; would not help here and need manual intervention before you can resume.

- Download the logs from the environment page
- Ensure that the package download step has the logs in all the machines with the following folder DownloadFilesAndSlipstreamTools
- Inspect the log files and if you see the download has failed due to disk space issue, proceed with the how to fix section.

**Action:**

- On all types of topologies, as part of automated cleanup we delete deployablepackages older than 30 days located at %ServiceVolume%\DeployablePackages as well as servicing related logs older than 30 days located usually at C:\Dynamics.
- On Dev/Onebox machines, however, there is a flexibility of customizing number of retention days and minimum disk space of ServiceVolume drive and Logs drive.
- Under registry key **HKLM:\SOFTWARE\Microsoft\Dynamics\Deployment** , we can create following keys to customize when should the cleanup happen and the automated cleanup task will consider these numbers

**CutoffDaysForCleanup** -&gt; number of days old packages/logs that should be retained. - Default value is 30

**CutoffDiskSpaceLimitForPackages** -&gt; (in GB) minimum free disk space of the service volume drive where packages folder is located. In the following case if disk space is &lt;200 GB cleanup task will remove the packages based on number of days.

**CutoffDiskSpaceLimitForLogs** -&gt; (in GB) minimum free disk space of the system drive where logs folder is located. In the following case if disk space is &lt;100 GB cleanup task will remove the servicing related based on number of days.

**Issue 4: Step has failed with errors.**

**Description:**

This indicates that one of the following might be the reasons

- Package has issues due to customizations or missing dependencies
- Servicing scripts has an issue
- Random failure during the step execution

Steps:

- Download logs
- Navigate to the step logs
- Open the output file for the step and see if there any errors.
- If there any additional log files available, please inspect the logs for any errors.

**Action 1** :

Download the logs

Click &quot; **Rerun step**&quot; to re-try the failed step

If it fails again with the same issue

**Action 2** :

- Look into the logs to dig in more
- If you notice that there is an issue with the customizations, abort this package and re-try with the new package.
- Check if there a fix available for the issue in the issue search.
- If you see the following step failure, GlobalUpdate script for service model: AOSService, this indicates that either DBSync or Report deployment might have failed.
- Look for DBSync.err file to see what the errors are and inspect DBSync.log file. For specific failures during DB Sync step, look at the **Common DB Sync Failures** section.

**Issue 5: Deployment status is showing &quot;Servicing&quot; whereas the servicing status is in &quot;Failed state&quot;**

**Description:**

There is a re-try mechanism in-built to retry multiple times before it gives up especially the preparation step failures such as

1. Download the package into the machines
2. Slipstream the servicing package
3. Generate runbook

**Action** : You can download the logs and see what the error is and start looking into it, before it finishes all the re-tries. If the in-built retry mechanism failed to go beyond the preparation stage after all re-tries. Please open a ticket for Microsoft team to investigate further, once you see the status as &quot;Failed&quot; and it&#39;s not due to invalid package issue.

**Issue 6: After the package deployment is done, failed to launch the dashboard**

**Description:**

This indicates that there might be a run-time error when starting the AOS.

1. Launch event viewer
2. Navigate to &quot;Applications and Services Logs &gt; Microsoft &gt; Dynamics &gt; Ax-SystemRuntime &gt; Operational

Filter by errors and see if there are any errors and investigate.


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
