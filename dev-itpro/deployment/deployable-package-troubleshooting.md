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

## Package application issues

**Issue: Applied package is not valid**

**Description:** Because the applied package was not valid, the Servicing status failed and did not list any updates in the **Environment updates** section. To verify, 
1. Download the logs.
2. Unzip and navigate to the AOS machine logs.
3. Verify that the DownloadFilesAndSlipstreamTools-xxx and GenerateRunbook-xxx folders exist.
4. Open the GenerateRunbook-xxx folder and then open the output type file.
If you find an error or an exception that a file is missing or failed to generate any steps for runbook, it is because there was an attempt to upload a package that was not valid.

**Action:** Click **Abort** to abort the current package, upload a new package, and then restart the servicing flow.


**Issue: Package deployment fails without any step failures**

**Description:** A time out occurs when you download the package onto the machine. During pre-servicing, a few steps must be completed before steps are completed in the runbook. As part of the pre-servicing, the package must be downloaded to all of the machines. The time to download might vary a bit based on the data center where the environment is residing. If the download doesn't happen within 30 minutes, it is considered a failure in the servicing status and will be stopped.

**Action:**
1. Click **Resume** to see if you can resolve the issue. If that doesn't work, move to step 2.
2. Download the logs from the **Environment** page.
3. Verify that the package download has logs in all of the machines with the following folder DownloadFilesAndSlipstreamTools.
4. Review the log files. If you do not see the following at the end of the log file, the package download is not completed which is why the issue occurred.
  - _Completed file download and slipstream successfully_


**Issue: Package deployment fails without any step failures**

**Description:** There is not enough disk space to download the package. Inspect all of the machines. If any of the machines' servicing drive is full, that would be the reason that you are running into this issue.
Note that to click **Resume** would not help in this situation. To verify that the deployment failed due to space issues, 

1. Navigate to the DownloadFilesAndSlipstreamTools-xxx folder.
3. Open the output file and check the error message to verify if the step failed due to space issues.

**Action:**

- As part of automated cleanup on topologies, we delete deployable packages located at %ServiceVolume%\DeployablePackages that are older than 30 days. We also use the same timeline to delete servicing related logs, usually located at C:\Dynamics.
- On Dev/Onebox machines however, there is a flexibility of customizing number of retention days and the minimum disk space of the ServiceVolume and Logs drives.
- Under the registry key, **HKLM:\SOFTWARE\Microsoft\Dynamics\Deployment**, we can create the following keys to customize when the cleanup should happen. The automated cleanup task will consider these numbers.

**CutoffDaysForCleanup**: The number of days that old packages and logs should be retained. The default value is 30.

**CutoffDiskSpaceLimitForPackages**: The minimum free disk space (in GB) of the service volume drive where the packages folder is located. For example, if disk space is 200 GB, the cleanup task will remove the packages based on number of days.

**CutoffDiskSpaceLimitForLogs**: The minimum free disk space (in GB) of the system drive where the logs folder is located. For example, if disk space is 100 GB, the cleanup task will remove the servicing related based on number of days.


**Issue: Step has failed with errors**

**Description:**
One of the following items might be the reason that the step failed with errors:
- The package has customization issues or is missing dependencies.
- There is an issue with the servicing scripts.
- There was a random failure when executing the step.

To verify what the issue is, 
1. Download and navigate to the step logs.
2. Open the output file for the step and see if there are any errors.
3. If there any additional log files available, inspect those for any errors.

**Action:** 
1. Download the logs
2. Click **Rerun step** to re-try the failed step.

If it fails again with the same issue, go back to the logs to look for more information. 

- If you notice that there is an issue with the customizations, abort this package and re-try with the new package.
- Check if there a fix available for the issue in the issue search.
- If you see the following step failure, GlobalUpdate script for service model: AOSService, this indicates that either DBSync or Report deployment might have failed.
- Look for DBSync.err file to see what the errors are and inspect DBSync.log file. For specific failures during DB Sync step, look at the **Common DB Sync Failures** section.


**Issue: Deployment status shows as Servicing when the servicing status is in a Failed state**

**Description:**
There is a built in mechanism to retry multiple times before the system gives up. This includes retrying the following preparation steps several times: 
- Package download to the machines
- Slipstreaming the servicing package
- Generating the runbook

**Action** : You can download the logs to view and take action on the error before all retries are exhausted. If the retry mechanism fails to go beyond the preparation stage and you see a status of **Failed**, open a ticket for the Microsoft team to investigate further. 


**Issue: Dashboard doesn't launch after package deployment is complete**

**Description:**
If the dashboard does not launch after the package deployment is complete, there might be a run-time error occurring when the AOS is started.

**Action**
1. Launch event viewer.
2. Navigate to **Applications and Services Logs** > **Microsoft** > **Dynamics** > **Ax-SystemRuntime** > **Operational
Filter by errors**, see if there are any errors, and investigate as necessary.


## Common DB Sync Failures
If you see the following step failure, **GlobalUpdate script for service model: AOSService** , it could be a database sync issue. Complete the following steps to look for DBSync.err file, find the errors, and inspect DBSync.log file.

1. Download and navigate to the step logs.
2. Open the output file for the step and see if there any errors.
3. If there additional log files available, inspect the logs for any errors.
4. The following table shows the most commonly seen failures and the action to take. The **Issue** column shows the error you will see in the dbsync.err file. The % can be replaced with the metadata name of the table, field, index, etc.

| **Issue** | **Action** |
| --- | --- |
| %Table Sync Failed for Table%Create Unique Index% | This typically happens when we create an unique index and the data is not unique. Fix the data before running the step again. |
| %Application configuration sync failed.%Custom action sync failed with error:% | Check the information in the error message and the call stack to determine the application code that is causing the issue. |
| %cannot be found from underlying query&#39;&#39;s table% | Fixed in update 6. KB 4018815 for Update 3. |
| %Table Sync Failed for Table%Converting Field% | Follow the error message, fix, and redo the step. |
| %failed because one or more objects access this column% | Check if the index is in the metadata. If yes, this is a SyncEngine product bug. If no, remove the index from SQL DB before rerunning the step. |
| %cannot be found from underlying data source&#39;&#39;s table% | Fixed in update 6. KB 4018815 for Update 3. |
| &#39;%Table Sync Failed for Table%&#39; and errorMessage like &#39;%There is already an object named%&#39; | The Internal SqlDictionary table and Sql Schema out of sync. There is not enough infomraiton in the logs to understand how we arrived at this state. |
| %Table Sync Failed for Table%Column names in each table must be unique% | SqlDictionary entries for the table is corrupt and the field is missing. There is not enough information in the logs to understand how we arrived at this state. |
| %Column name &#39;LOAD\_&#39; does not exist in the target table or view. CREATE INDEX% | Appears to be SyncEngine issue. Create a ticket on Microsoft Support. |
| Cannot drop the index &#39;VENDREQUESTPROFILEQUESTIONNAIRE.I\_1301PROFILEQUESTIONNAIRE&#39;, because it does not exist or you do not have permission | Appears to be SyncEngine issue. Create a ticket on Microsoft Support. |
| %The index entry of length 2046 bytes for the index &#39;I\_65750INDEX1&#39; exceeds the maximum length of 1700 bytes for nonclustered indexes% | Modify the index before running the step again. |
| %Incorrect syntax near% | SyncEngine issue. Create a ticket on Microsoft Support. |
| Reference to database and/or server name in &#39;TEMPDB.DBO.T\_TRVREQUISITIONLINE\_C4C3569DD5A14CDABAE71A341743FB61&#39; is not supported in this version of SQL Server | SyncEngine issue. Create a ticket on Microsoft Support. |
| %Error: Timeout expired.  The timeout period elapsed prior to obtaining a connection from the pool.% | Please retry the step. |
| Database execution failed: Invalid column name &#39;DEFAULTDIMENSION&#39;. CREATE VIEW | Appears to be SyncEngine issue. Create a ticket on Microsoft Support. |
| Database execution failed: Invalid object name &#39;PMBI\_DEPROJECTTIMESHEET&#39;. CREATE VIEW | Appears to be SyncEngine issue. Create a ticket on Microsoft Support. |
| %provider: Named Pipes Provider, error: 40 - Could not open a connection to SQL Server%  | Should have been fixed in Platform Update 3. Retry the step. |
