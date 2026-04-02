---
title: Troubleshoot package application issues
description: Learn about troubleshooting information for issues that might occur when you apply packages on Tier 1 or Tier 2 through Tier 5 environments.  
author: laneswenka
ms.author: laswenka
ms.topic: troubleshooting-general
ms.custom: 
  - bap-template
ms.date: 04/02/2026
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.assetid: 341a229f-d9c3-4678-b353-d08d5b2c1caf
ms.search.region: Global
ms.search.validFrom: 2016-05-31
ms.search.form: 
ms.dyn365.ops.version: Platform update 1
---

# Troubleshoot package application issues

[!include [banner](../includes/banner.md)]

This article helps you troubleshoot problems that might occur when you apply packages on your Tier 1 or Tier 2 through Tier 5 environments. For information about how to apply a package, see [Apply updates to cloud environments](apply-deployable-package-system.md).

## General troubleshooting and diagnostics

If a package isn't successfully applied, you have two options:

- Retry the operation that failed.
- Use the logs.

### Retry the failed operation

If package application fails, and you want to retry the operation, select **Resume**.

### Use the logs

If package application fails, and you want to use the logs, follow these steps:

1. Download and then unzip the log files.
1. Select the role that a step failed for, such as **AOS** or **BI**.
1. Select the virtual machine (VM) where the step failed. You can find this information in the **Machine name** column in the **Environment updates** section.
1. In the VM logs, select the folder that corresponds to the step where the issue occurred. The folder name identifies the step that each folder corresponds to.

    For example, if the issue occurred during the execution of a step, select the **ExecuteRunbook** folder. The step number is highlighted and is the number after the globally unique identifier (GUID).

## Package application issues

### Issue: The package that you applied isn't valid

**Description**

The servicing status is **Failed** because the package that you applied isn't valid. The **Environment updates** section doesn't list any updates. To verify whether the package is valid, follow these steps:

1. Download and unzip the logs.
1. Go to the logs for the Application Object Server (AOS) machine.
1. Check that the **DownloadFilesAndSlipstreamTools-xxx** and **GenerateRunbook-xxx** folders exist.
1. Open the **GenerateRunbook-xxx** folder, and then open the file for the output type.

    If you find an error message or an exception that states that a file is missing or failed to generate any steps for the runbook, the package isn't valid.

**Action**

Select **Abort** to cancel the current package. Upload a new package, and then restart the servicing flow.

### Issue: Package deployment fails even though no steps failed

**Description**

A timeout occurs when you download the package to the machine. During pre-servicing, the process completes a few steps before it completes steps in the runbook. As part of the pre-servicing, the process must download the package to all the machines. The time to download might vary slightly, depending on the datacenter where the environment resides. Any download that doesn't occur within 30 minutes is considered a failure in the servicing status and stops.

**Action**

1. Select **Resume** to see whether you can resolve the issue. If this step doesn't work, move on to step 2.
1. Download the logs from the **Environment** page.
1. Check that the package download on all the machines has logs that include the **DownloadFilesAndSlipstreamTools** folder.
1. Review the log files. If you don't see the following text at the end of the log file, the issue occurred because the package download wasn't completed: "Completed file download and slipstream successfully".

### Issue: Package deployment fails even though no steps failed

**Description**

The process doesn't have enough disk space to download the package. Check all the machines. This problem occurs if the servicing drive of any machines is full.

If you select **Resume** in this situation, you don't resolve the problem.

To verify that the deployment failed because of space problems, follow these steps:

1. Go to the **DownloadFilesAndSlipstreamTools-xxx** folder.
1. Open the output file, and check the error message to see whether the step failed because of space problems.

**Action**

As part of the automated cleanup on topologies, the system deletes any deployable packages in `%ServiceVolume%\DeployablePackages` that are more than 30 days old. The system uses the same timeline to delete servicing-related logs. These logs are usually located in `C:\Dynamics`.

However, on dev or one-box machines, you have more flexibility. You can customize the number of retention days and the minimum disk space of the ServiceVolume and Logs drives.

- Under the **HKLM:\SOFTWARE\Microsoft\Dynamics\Deployment** registry key, create the following keys to customize when cleanup should occur. The automated cleanup task considers these values.

  - **CutoffDaysForCleanup** – The number of days that old packages and logs should be retained. The default value is **30**.
  - **CutoffDiskSpaceLimitForPackages** – The minimum free disk space (in gigabytes [GB]) on the service volume drive where the package folder is located. For example, if the disk space is 200 GB, the cleanup task removes the packages, based on the number of days.
  - **CutoffDiskSpaceLimitForLogs** – The minimum free disk space (in GB) of the system drive where the log folder is located. For example, if the disk space is 100 GB, the cleanup task removes the servicing-related logs, based on the number of days.

### Issue: A step failed with errors

**Description**

A step might fail with errors for one of the following reasons:

- The package has customization problems or is missing dependencies.
- There's an issue with the servicing scripts.
- A random failure occurred when the step executed.

To verify the problem, follow these steps:

1. Download and go to the step logs.
1. Open the output file for the step, and check for any errors.
1. If any additional log files are available, inspect them for errors.

**Action**

1. Download the logs.
1. Select **Rerun step** to retry the failed step.

If the step fails again, and the same error occurs, go back to the logs to look for more information.

- If you find problems with the customizations, cancel this package, and retry by using the new package.
- Check if a fix for the problem is available in Issue search.
- If you see the following step failure, either database synchronization or report deployment might have failed: "GlobalUpdate script for service model: AOSService"
- Look for the DBSync.err file, and check what the errors are. Inspect the DBSync.log file. For specific failures during the DB Sync step, see the [Typical database synchronization issues](deployable-package-troubleshooting.md#typical-database-synchronization-issues) section.

### Issue: The deployment status is Servicing but the servicing status is Failed

**Description**

A built-in mechanism enables the system to retry multiple times before it gives up. The system can retry the following preparation steps several times:

- Download the package to the machines.
- Slipstream the servicing package.
- Generate the runbook.

**Action**

Download the logs to view the error and take action before all retries are exhausted. If the retry mechanism fails to go beyond the preparation stage, and you see a status of **Failed**, open a ticket so that the Microsoft team can investigate the issue further.

### Issue: The dashboard doesn't open after package deployment is completed

**Description**

If the dashboard doesn't open after package deployment is completed, a run-time error might be occurring when the AOS machine starts.

**Action**

1. Start Event Viewer.
1. Go to **Applications and Services Logs** > **Microsoft** > **Dynamics** > **Ax-SystemRuntime** > **Operational Filter by errors**. Check whether there are any errors, and investigate the errors as required.

### Issue: A package application failed with error code : DSU #####

**Description**

You might see an error message that says **A critical component has encountered an error processing your request. Error code: DSU#####**, or a similar message. The error code **DSU#####** indicates a temporary outage in the underlying Microsoft API. This type of outage can also affect database movement functionality.

**Action**

Microsoft is proactively monitoring the service status and expects to resolve this type of outage shortly.

This outage doesn't affect the status or health of your environment.

If you see this error when scheduling a service request or performing a database movement task, try again later.

## Typical database synchronization issues

If you see the following step failure, a database synchronization issue might be occurring: "GlobalUpdate script for service model: AOSService"

Follow these steps to look for the DBSync.err file, find the errors, and inspect the DBSync.log file.

1. Download and go to the step logs.
1. Open the output file for the step, and check for any errors.
1. If additional log files are available, inspect the logs for any errors.
1. The following table shows the failures that are seen most often and the action that you should take. The **Issue** column shows the error message that you see in the dbsync.err file. The percentage sign (%) can be replaced with the metadata name of the table, field, index, and so on.

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
    | %provider: Named Pipes Provider, error: 40 - Could not open a connection to SQL Server%  | This issue should be fixed in Platform Update 3. Retry the step. |

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
