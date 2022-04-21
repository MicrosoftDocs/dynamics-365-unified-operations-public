---
# required metadata

title: Troubleshoot package application issues
description: The topic provides troubleshooting information for issues that might occur when you apply packages on Tier 1 or Tier 2 through Tier 5 environments.  
author: laneswenka
ms.date: 01/21/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.custom: 107013
ms.assetid: 341a229f-d9c3-4678-b353-d08d5b2c1caf
ms.search.region: Global
# ms.search.industry: 
ms.author: laswenka
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: Platform update 1

---

# Troubleshoot package application issues

[!include [banner](../includes/banner.md)]

This topic provides detailed information that will help you troubleshoot issues that might occur when you apply packages on your Tier 1 or Tier 2 through Tier 5 environments. For information about how to apply a package, see [Apply updates to cloud environments](apply-deployable-package-system.md).

## General troubleshooting and diagnostics
If a package isn't successfully applied, you have two options:

- Retry the operation that failed.
- Use the logs.

### Retry the failed operation
If package application fails, and you want to retry the operation, select **Resume**.

### Use the logs
If package application fails, and you want to use the logs, follow these steps.

1. Download and then unzip the log files.
2. Select the role that a step failed for, such as **AOS** or **BI**.
3. Select the virtual machine (VM) where the step failed. You can find this information in the **Machine name** column in the **Environment updates** section.
4. In the VM logs, select the folder that corresponds to the step where the issue occurred. The folder name identifies the step that each folder corresponds to. 

    For example, if the issue occurred during the execution of a step, select the **ExecuteRunbook** folder. The step number is highlighted and is the number after the globally unique identifier (GUID).

## Package application issues

### Issue: The package that was applied isn't valid

**Description**

Because the package that was applied wasn't valid, the servicing status is **Failed**, and no updates are listed in the **Environment updates** section. To verify whether the package is valid, follow these steps.

1. Download and unzip the logs.
2. Navigate to the logs for the Application Object Server (AOS) machine.
3. Verify that the **DownloadFilesAndSlipstreamTools-xxx** and **GenerateRunbook-xxx** folders exist.
4. Open the **GenerateRunbook-xxx folder**, and then open the file for the output type.

    If you find an error message or an exception that states that a file is missing or failed to generate any steps for the runbook, there was an attempt to upload a package that wasn't valid.

**Action**

Select **Abort** to abort the current package, upload a new package, and then restart the servicing flow.

### Issue: Package deployment fails even though no steps failed

**Description**

A time-out occurs when you download the package to the machine. During pre-servicing, a few steps must be completed before steps are completed in the runbook. As part of the pre-servicing, the package must be downloaded to all the machines. The time to download might vary slightly, depending on the datacenter where the environment resides. Any download doesn't occur within 30 minutes is considered a failure in the servicing status and will be stopped.

**Action**

1. Select **Resume** to see whether you can resolve the issue. If this step doesn't work, move on to step 2.
2. Download the logs from the **Environment** page.
3. Verify that the package download on all the machines has logs that include the DownloadFilesAndSlipstreamTools folder.
4. Review the log files. If you don't see the following text at the end of the log file, the issue occurred because the package download wasn't completed: "Completed file download and slipstream successfully"

### Issue: Package deployment fails even though no steps failed

**Description**

There isn't enough disk space to download the package. Inspect all the machines. This issue occurs if the servicing drive of any machines is full.

Note that if you select **Resume** in this situation, you won't resolve the issue.

To verify that the deployment failed because space issues, follow these steps.

1. Navigate to the **DownloadFilesAndSlipstreamTools-xxx** folder.
2. Open the output file, and view the error message to see whether the step failed because space issues.

**Action**

As part of the automated cleanup on topologies, any deployable packages in %ServiceVolume%\\DeployablePackages that are more than 30 days old are deleted. The same timeline is also used to delete servicing-related logs. These logs are usually located in C:\\Dynamics.

However, on dev/one-box machines, there is more flexibility. The number of retention days and the minimum disk space of the ServiceVolume and Logs drives can be customized.

- Under the **HKLM:\\SOFTWARE\\Microsoft\\Dynamics\\Deployment** registry key, you can create the following keys to customize when cleanup should occur. The automated cleanup task will consider these values.

    - **CutoffDaysForCleanup** – The number of days that old packages and logs should be retained. The default value is **30**.
    - **CutoffDiskSpaceLimitForPackages** – The minimum free disk space (in gigabytes [GB]) on the service volume drive where the package folder is located. For example, if the disk space is 200 GB, the cleanup task will remove the packages, based on the number of days.
    - **CutoffDiskSpaceLimitForLogs** – The minimum free disk space (in GB) of the system drive where the log folder is located. For example, if the disk space is 100 GB, the cleanup task will remove the servicing-related logs, based on the number of days.

### Issue: A step failed with errors

**Description**

A step might fail with errors for one of the following reasons:

- The package has customization issues or is missing dependencies.
- There is an issue with the servicing scripts.
- A random failure occurred when the step was executed.

To verify what the issue is, follow these steps.

1. Download and navigate to the step logs.
2. Open the output file for the step, and see whether there are any errors.
3. If any additional log files are available, inspect them for errors.

**Action** 

1. Download the logs.
2. Select **Rerun step** to retry the failed step.

If the step fails again, and the same error occurs, go back to the logs to look for more information. 

- If you notice that there is an issue with the customizations, abort this package, and retry by using the new package.
- See whether a fix for the issue is available in Issue search.
- If you see the following step failure, either database synchronization or report deployment might have failed: "GlobalUpdate script for service model: AOSService"
- Look for the DBSync.err file, and see what the errors are. Inspect the DBSync.log file. For specific failures during the DB Sync step, look in the [Typical database synchronization issues](deployable-package-troubleshooting.md#typical-database-synchronization-issues) section.

### Issue: The deployment status is Servicing but the servicing status is Failed

**Description**

A built-in mechanism enables the system to retry multiple times before it gives up. The following preparation steps can also be retried several times: 

- Download the package to the machines.
- Slipstream the servicing package.
- Generate the runbook.

**Action**

You can download the logs to view the error and take action before all retries are exhausted. If the retry mechanism fails to go beyond the preparation stage, and you see a status of **Failed**, open a ticket so that the Microsoft team can investigate the issue further. 

### Issue: The dashboard doesn't open after package deployment is completed

**Description**

If the dashboard doesn't open after package deployment is completed, a run-time error might be occurring when the AOS machine is started.

**Action**

1. Start Event Viewer.
2. Navigate to **Applications and Services Logs** > **Microsoft** > **Dynamics** > **Ax-SystemRuntime** > **Operational Filter by errors**, see whether there are any errors, and investigate the errors as required.

### Issue: A package application failed with error code : DSU#####

**Description**

You may receive an error stating **A critical component has encountered an error processing your request. Error code: DSU#####**, or similar. The error code of **DSU#####** indicates that there's a temporary outage happening in the underlying Microsoft API.  This type of outage may also impact database movement functionality. 

**Action**

Microsoft is proactively monitoring the service status and this type of outage is expected to be mitigated shortly.

There's no impact on the status and the health of your environment. 

If you experience this error when scheduling a service request or performing a database movement task, please try again at a later time. 

## Typical database synchronization issues
If you see the following step failure, a database synchronization issue might be occurring: "GlobalUpdate script for service model: AOSService"

Follow these steps to look for the DBSync.err file, find the errors, and inspect the DBSync.log file.

1. Download and navigate to the step logs.
2. Open the output file for the step, and see whether there are any errors.
3. If additional log files are available, inspect the logs for any errors.
4. The following table shows the failures that are seen most often and the action that you should take. The **Issue** column shows the error message that you will see in the dbsync.err file. The percentage sign (%) can be replaced with the metadata name of the table, field, index, and so on.

    | Issue | Action |
    |-------|--------|
    | %Table Sync Failed for Table%Create Unique Index% | This issue typically occurs when a unique index is created, but the data isn't unique. Fix the data before you run the step again. |
    | %Application configuration sync failed.%Custom action sync failed with error:% | View the information in the error message and the call stack to determine the application code that is causing the issue. |
    | %cannot be found from underlying query&#39;&#39;s table% | This issue was fixed. For more information, refer to KB 4018815. |
    | %Table Sync Failed for Table%Converting Field% | Follow the error message, fix the issue, and run the step again. |
    | %failed because one or more objects access this column% | See whether the index is in the metadata. If the index is in the metadata, this issue is a SyncEngine product issue. If the index isn't in the metadata, remove the index from the SQL database before you run the step again. |
    | %cannot be found from underlying data source&#39;&#39;s table% | This issue was fixed. For more information, refer to KB 4018815. |
    | &#39;%Table Sync Failed for Table%&#39; and errorMessage like &#39;%There is already an object named%&#39; | The Internal SqlDictionary table and SQL schema are out of sync. There isn't enough information in the logs to understand how this state was reached. |
    | %Table Sync Failed for Table%Column names in each table must be unique% | SqlDictionary entries for the table are corrupted, and the field is missing. There isn't enough information in the logs to understand how this state was reached. |
    | %Column name &#39;LOAD\_&#39; does not exist in the target table or view. CREATE INDEX% | This issue appears to be a SyncEngine issue. Create a ticket on Microsoft Support. |
    | Cannot drop the index &#39;VENDREQUESTPROFILEQUESTIONNAIRE.I\_1301PROFILEQUESTIONNAIRE&#39;, because it does not exist or you do not have permission | This issue appears to be a SyncEngine issue. Create a ticket on Microsoft Support. |
    | %The index entry of length 2046 bytes for the index &#39;I\_65750INDEX1&#39; exceeds the maximum length of 1700 bytes for nonclustered indexes% | Modify the index before you run the step again. |
    | %Incorrect syntax near% | This issue is a SyncEngine issue. Create a ticket on Microsoft Support. |
    | Reference to database and/or server name in &#39;TEMPDB.DBO.T\_TRVREQUISITIONLINE\_C4C3569DD5A14CDABAE71A341743FB61&#39; is not supported in this version of SQL Server | This issue is a SyncEngine issue. Create a ticket on Microsoft Support. |
    | %Error: Timeout expired.  The timeout period elapsed prior to obtaining a connection from the pool.% | Retry the step. |
    | Database execution failed: Invalid column name &#39;DEFAULTDIMENSION&#39;. CREATE VIEW | This issue appears to be a SyncEngine issue. Create a ticket on Microsoft Support. |
    | Database execution failed: Invalid object name &#39;PMBI\_DEPROJECTTIMESHEET&#39;. CREATE VIEW | This issue appears to be a SyncEngine issue. Create a ticket on Microsoft Support. |
    | %provider: Named Pipes Provider, error: 40 - Could not open a connection to SQL Server%  | This issue should have been fixed in Platform Update 3. Retry the step. |


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
