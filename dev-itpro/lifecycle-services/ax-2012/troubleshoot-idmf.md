---
# required metadata

title: Troubleshoot 
description: This topic contains information about troubleshooting the Microsoft Dynamics AX Intelligent Data Management Framework (IDMF).
author: kfend
manager: AnnBe
ms.date: 2015-12-05 18 - 03 - 50
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: AX 2012
# ms.tgt_pltfrm: 
ms.custom: 18711
ms.assetid: fe0b2255-d44e-42db-9c90-2c6202fc7578
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 
ms.dyn365.ops.version: 2012

---

# Troubleshoot the Intelligent Data Management Framework (AX 2012)

This topic contains information about troubleshooting the Microsoft Dynamics AX Intelligent Data Management Framework (IDMF).

Known issues
------------

-   **Issue** The domain account provided during setup and installation of the service is not granted **permission to log on as a service**, therefore the IDMF service fails when it is started. **Workaround** Open the **Services control** panel. On the **Security** tab, enter the password for the account.
-   **Issue** If the service account for IDMF has not been granted local administrator privileges, the following error message is received: "An unhandled exception occurred and has been logged. Please contact support." **Workaround** Grant the service account for IDMF administrator privileges on the local computer.
-   **Issue** A **ByFiscal** archive task cannot be scheduled when a metadata task is running. **Workaround** Wait until the metadata task completes before scheduling a **ByFiscal** archive task
-   **Issue** Running archive, purge or restore archive tasks at the same time as offline **ALTER INDEX** operations causes database locking issues. **Workaround** Wait until offline **ALTER INDEX** operations for the specified indexes have completed before running archive, purge or restore archive tasks.
-   **Issue** Archive templates and purge template should not be modified when archive or purge tasks are running. **Workaround** Do not modify archive and purge templates when archive or purge tasks are running.
-   **Issue** During a restore, the insert bulk statements can cause a high amount of table lock escalations on tables in the production Microsoft Dynamics AX business database. **Workaround** None.
-   **Issue** In the **ByFiscal** task page and in other pages, expand and collapse icons can show reversed images. **Workaround** None.
-   **Issue** Unable to discover archive objects if the drive table is **AccountingEvent**. The system returns the following message: "Error executing code: Insufficient memory to run script." **Workaround** Update the following registry entries.\[HKEY\_CURRENT\_USERSoftwareMicrosoftDynamics6.0Configurationconfiguration name\]\[HKEY\_LOCAL\_MACHINESoftwareMicrosoftDynamics6.0Configurationconfiguration name\]\[HKEY\_LOCAL\_MACHINESYSTEMCurrentControlSetServicesDynamics Server6.0AOS instance configuration name\]Value name: maxbuffersizeValue type: REG\_SZValue: Maximum amount of memory in MB or 0 for no limit

## View log files
IDMF logs error events in a log file in a folder named**,**under the installation folder. The default installation path is C:Program FilesMicrosoft Dynamics AX Intelligent Data Management Framework. IDMF creates the log file when the first error message is generated. The file is named trace\_mm-dd-yyyy.log, with mm-dd-yyyy providing the current month, day, and year. The IDMF scheduler service creates an error log file called servicetrace\_mm-dd-yyyy.log. The error log files are created for each day. When the first error occurs during the day, the error log file is created, and the error message is appended to the newly created error log file. All subsequent error messages are appended to the existing error log file for the day.

## Database rights are not set correctly
The AOS service account must have **datareader**, **datawriter** and **ddladmin** rights on the IDMF management database.

## IDMF fails to start
When starting IDMF, you may encounter the following error: "An unhandled exception occurred and has been logged. Please contact support." The preceding error message is a generic message that IDMF displays when the error condition is caused by an environmental issue such as permissions. This particular error condition typically occurs when the user does not have read and write permissions on the installation folder of IDMF. To fix the error condition, provide read and write permissions to the installation folder of IDMF. The default path is C:Program FilesMicrosoft Dynamics AX Intelligent Data Management Framework.

## Index defragmentation does not reduce the fragmentation percentage to zero
The index defragmentation schedules do not always achieve a complete defragmentation, or in other words, 0 (zero) percent fragmentation. Some of the indexes may still have a small percentage of fragmentation. The defragmentation process tries to defragment selected indexes to the maximum possible level. However, Microsoft Dynamics AX uses a fill factor of 0 (zero). The fill factor of 0 breaks records out to extra pages without completely filling an index page. As a result, the fragmentation level for some of the indexes remains at a non-zero level, even after the defragmentation schedule is completed successfully.

## Distributed transaction error
You may encounter the following error from the Microsoft SQL Server Integration Services (SSIS) runtime: "The SSIS Runtime has failed to enlist the OLE DB connection in a distributed transaction with error 0x8004D025. The partner transaction manager has disabled its support for remote/network transactions." To fix this error condition, you must configure your servers so that Microsoft Distributed Transaction Coordinator (MSDT) communication flows through the firewall. For instructions, see [Knowledge Base article 306843](http://support.microsoft.com/kb/306843). If the error persists after configuring the **Microsoft Distributed Transaction Coordinator** verify that the firewall settings for **Distributed Transaction Coordinator** under the **Inbound and Outbound Rules** have been enabled.

## Export to Excel fails
The export to Excel functionality may not work in some environments. To fix this problem, you must have Microsoft Excel and the Excel PIAs installed on the computer. Verify that Excel is correctly installed and working on the computer. If required, download and install the Microsoft Office Primary Interop Assemblies (PIAs). For Excel 2003, see [Office 2003 Update: Redistributable Primary Interop Assemblies](http://www.microsoft.com/downloads/details.aspx?familyid=3c9a983a-ac14-4125-8ba0-d36d67e0f4ad&displaylang=en). For Microsoft Excel 2007, see [2007 Microsoft Office System Update: Redistributable Primary Interop Assemblies](http://www.microsoft.com/downloads/details.aspx?FamilyID=59daebaa-bed4-4282-a28c-b864d8bfa513&displaylang=en). Restart IDMF after successful installation of the PIAs.

## The discovery of a driver table fails
When starting a discovery process for an Archive Object or a Purge Object, you may encounter the following error: "Unable to discover the driver table for the Archive Object or Purge Object." This error message is usually caused by metadata synchronization issues. To fix this error condition, you must run the post-installation tasks. Run the post-installation application by clicking **Start** &gt; **All programs** &gt; **Intelligent Data Management Framework** &gt; **Post-installation tasks**, or follow these steps to resolve this error manually. For details, see the [Installation Guide for the Microsoft Dynamics AX Intelligent Data Management Framework (IDMF)](installation-guide-idmf.md).

1.  Verify that **AXDataManagementToolProjectnn.xpo** exists in the Application Object Tree (AOT), where nn is 50, 60, 61, or 62 depending on the version of your Microsoft Dynamics AX application.
2.  Verify that you have successfully completed the post-installation checklist.
3.  Verify that all member of the implementation team are working on the same layer, for example **CUS**, **VAR**, or **USR**.
4.  Verify that the XPOs mentioned in step 1 are imported in the same layer, such as the **VAR** layer or the **USR** layer. Verify that all methods from these XPOs are imported in the same layer, such as **USR** or **VAR**.
5.  Use the AOT to correct any difference you find between your AOT and the XPOs that are included with IDMF. You can delete these XPOs from the layer they are currently in and manually import them to another layer, as described in the [Data Management Framework Installation Guide](http://go.microsoft.com/fwlink/?LinkId=143616&clcid=0x409).

## The database snapshot schedule fails with a permission error
In a distributed SQL Server 2008 environment, you must install Service Pack 2 or a later version on all SQL Server instances when you store your databases on multiple servers. For example, when you store your production database and archive database on two separate servers, you have a distributed SQL Server environment. Both the servers must have SQL Server 2008 or a later version before you install and start IDMF. Failure to do so causes the following error message from a database snapshot schedule: "Syntax error, permission violation, or other nonspecific error."

## The discovery process fails with an error message
The discovery process may display an error message: "Cannot create archive object or purge object." This message may appear if Application Object Server (AOS) is not available or the connection with AOS has failed. Check the availability of AOS. Restart the AOS if necessary, and then restart IDMF.

## Application Object Server error when connecting to the archive database
In some environments, you may receive an error when Application Object Server (AOS) connects to the archive database: "An internal error occurred while creating session for the user." Verify that the account used for the AOS service has sufficient permissions to the archive database. For more information, see the "Rights required for installation" section in the [Data Management Framework Installation Guide](http://go.microsoft.com/fwlink/?LinkId=143616&clcid=0x409). Verify that the account used for the AOS service has the execute permission for stored procedures **CREATESERVERSESSIONS** and **CREATEUSERSESSIONS** in the archive database.

## The analysis snapshot schedule fails with a permission error
The analysis snapshot schedule may fail with an error message: "An OLE DB error has occurred. Error code: 0x80040E14.An OLE DB record is available. Source: "Microsoft SQL Native Client" Hresult: 0x80040E14 Description: "The user does not have permission to perform this action"." This error message appears because of insufficient database permissions. Be sure that the database permissions are assigned by following the instructions in the "Rights required for installation" section in the [Data Management Framework Installation Guide](http://go.microsoft.com/fwlink/?LinkId=143616&clcid=0x409).

## The analysis snapshot schedule fails because of a SQL Server Integration Services error
The analysis snapshot schedule may fail with an error: "Message: Package Error: The file exists. The buffer manager could not get a temporary file name. The call to GetTempFileName failed. The buffer manager could not create a temporary file on the path C:DOCUME~1ADMINI~1.SAMLOCALS~1Temp. The path will not be considered for temporary storage again." To resolve this error, you must install SQL Server 2008 or a later version. For more information, see Microsoft Knowledge Base article [972365](http://support.microsoft.com/kb/972365).

## Unable to create an archive schedule or restore schedule
If an archive schedule fails or is aborted, you must try to restart or revert it before you can create another schedule with the same object. This restriction applies to all Archive Objects.

## Unable to select an archive schedule for restoration
The archive schedule that you want to restore may be disabled, so that you cannot select it. This occurs when your previous attempt to restore the schedule has either been aborted or failed. In the Status window, navigate to the aborted or failed restore schedule. Right-click the schedule, and then select **Restart schedule** or **Revert schedule**, depending on the action you have to perform. If the schedule failed during the initialization state, no data was archived. In that case, there is no need to restore or revert the schedule, and IDMF displays a warning that asks you to create a new schedule. Use the **Schedule** menu to create a new archive schedule.

| **Note**                                                                                                                 |
|--------------------------------------------------------------------------------------------------------------------------|
| Always restart or revert a failed archive schedule before you create a new archive schedule for the same Archive Object. |

## A schedule fails because of insufficient space
Archive and purge schedules fail if the database or log files become full. These schedules require a significant amount of free database and log space, depending on the volume of data you archive or purge. By default, the purge and archive schedules process 100,000 records in a batch. Reduce the batch size to decrease the database and log space required when a schedule processes a batch. Follow these steps to configure the batch size:
1.  Using Notepad, open **AXDataManagementSchedulerService.exe.config** from the installation folder of IDMF. The default path of the installation folder is C:Program FilesMicrosoft Dynamics AX Intelligent Data Management Framework.
2.  To decrease the batch size for an archive task, locate the configuration key BatchSizeForPurge &lt;add key="BatchSizeForArchive" value="4000" /&gt;, and change the key value to a smaller number.
3.  To decrease the batch size for a purge schedule, locate the configuration key BatchSizeForPurge &lt;add key="BatchSizeForPurge" value="4000" /&gt;, and change the key value to a smaller number.

You must carefully determine the location and initial size of data and log files for the archive, production, management, and production replica databases. Be sure that the initial size is sufficient for optimal performance and future growth. For more information about database configuration, see [Planning database configuration for Microsoft Dynamics AX](http://www.microsoft.com/downloads/details.aspx?FamilyID=ab4cd401-b366-4c1c-9a73-88c945ae8191) and the Microsoft Dynamics AX Performance team's [blog](http://blogs.msdn.com/axperf/).

## Troubleshoot failed schedules
Follow these steps to troubleshoot failed schedules:
1.  View the log file and the list of common causes and associated solutions that are described in the previous sections.
2.  Be sure to synchronize any metadata changes in the production database with the archive database via the metadata synchronization schedule. The master data synchronization schedule may fail if the metadata is not synchronized between the two databases.
3.  The purge schedule may fail if the Microsoft Distributed Transaction Coordinator (MSDTC) is not configured correctly.
4.  A schedule may fail if the data file or log file in the database becomes full.

You must fix the error conditions before you rerun the schedule.



